QUESTION 7:-
def shift_negatives(arr) :
    first_positive = 0
    for i in range(len(arr)):
        if arr[i] < 0:
            temp = arr[i]
            arr[i] = arr[first_positive]
            arr[first_positive]= temp
            
            first_positive += 1
    return arr
 
arr = input().split()
arr = [int(i) for i in arr]
print("Original Array:", arr)

rearranged_array = shift_negatives(arr)
print("Rearranged Array:", rearranged_array)


QUESTION 8:-
from collections import deque
 
 
# Reverse a string using a stack
def reverse(s):
    # build a stack from characters in the string
    stack = deque(s)
    # pop all characters from the stack and join them back into a string
    return ''.join(stack.pop() for _ in range(len(s)))
 
 
if __name__ == '__main__':
 
    s = 'Reverse me'
    s = reverse(s)
    print(s)
 method 2

def createStack():
    stack = []
    return stack
 
# Function to determine the size of the stack
 
 
def size(stack):
    return len(stack)
 
# Stack is empty if the size is 0
 
 
def isEmpty(stack):
    if size(stack) == 0:
        return true
 
# Function to add an item to stack .
# It increases size by 1
 
 
def push(stack, item):
    stack.append(item)
 
# Function to remove an item from stack.
# It decreases size by 1
 
 
def pop(stack):
    if isEmpty(stack):
        return
    return stack.pop()
 
# A stack based function to reverse a string

 METHOD 2:-
 
def reverse(string):
    n = len(string)
 
    # Create a empty stack
    stack = createStack()
 
    # Push all characters of string to stack
    for i in range(0, n, 1):
        push(stack, string[i])
 
    # Making the string empty since all
    # characters are saved in stack
    string = ""
 
    # Pop all characters of string and
    # put them back to string
    for i in range(0, n, 1):
        string += pop(stack)
 
    return string
 
 
# Driver program to test above functions
string = "GeeksQuiz"
string = reverse(string)
print("Reversed string is " + string)

QUESTION 9:-
# Function to evaluate the postfix expression
def evaluatePostfixExpression(expression):
    # Defining an stack of integer type.
    st = []

    # Traversing in the expression from left 
    # to right. 
    for i in range(len(expression)):
        c = expression[i]

        # If 'c' is a digit (operand)
        if (c >= '0' and c <= '9'):
            # Convert 'c' in integer and
            # push it into the stack.
            temp = int(c)
            st.append(temp)
        
        # Otherwise it is an operator.
        else:
            # Pop element from the stack.
            op1 = st.pop()
            # Pop another element from the stack. 
            op2 = st.pop()

            # Use the if else ladder to deal with
            # the operand accordingly.
            if (c == '+'):
                st.append(op2 + op1)
            elif (c == '-'):
                st.append(op2 - op1)
            elif (c == '*'):
                st.append(op2 * op1)
            elif (c == '/'):
                st.append(op2 / op1)
                
            
    # Return the element at the top 
    # of the stack.
    return st.pop()

# Driver code

# Postfix expression.
expression = "23*45+*"

# Calling function to find the result
# of the postfix expression.
print(evaluatePostfixExpression(expression))

METHOD 2:-
class Queue:
    def __init__(self):
        # Initializing the stacks
        self.s1 = []
        self.s2 = []
 
    # Function to implement enqueue
    def enqueue(self, element):
        # Pushing element in the stack
        self.s1.append(element)
 
    # Function to implement dequeue operation 
    def dequeue(self):
        # Condition where the queue is empty
        if (len(self.s1) == 0 and len(self.s2) == 0):
            print("the queue is Empty")
            return
 
        elif (len(self.s2) == 0 and len(self.s1) > 0):
            while len(self.s1):
                element = self.s1.pop()
                self.s2.append(element)
            return self.s2.pop()
 
        else:
            # Popping the top element from the stack
            return self.s2.pop()


method 2
class Queue: 
    def __init__(self):
        # Initializing both the stacks
        self.stack1 = []
        self.stack2 = []
  
    # Function to implement enqeue operation
    def enqueue(self, element):
          
        # Push all the elements of stack1 to stack2
        while len(self.stack1) != 0: 
            self.stack2.append(self.stack1[-1]) 
            self.stack1.pop()
  
        self.stack1.append(element) 
  
        # Push everything back from stack2 to stack1 
        while len(self.stack2) != 0: 
            self.stack1.append(self.stack2[-1]) 
            self.stack2.pop()
  
    # Function to implement deqeue operation
    def dequeue(self):
          
        # If stack1 is empty, return -1 or a message
        if len(self.stack1) == 0: 
            print("the queue is Empty")
      
        # Top of the stack is returned
        element = self.stack1[-1] 
        self.stack1.pop() 
        return element       
QUESTION 10:-
def postfix_evaluation(s):

    s=s.split()

    n=len(s)

    stack =[]

    for i in range(n):

        if s[i].isdigit():

          #append function is equivalent to push

            stack.append(int(s[i]))

        elif s[i]=="+":

            a=stack.pop()

            b=stack.pop()

            stack.append(int(a)+int(b))

        elif s[i]=="*":

            a=stack.pop()

            b=stack.pop()

            stack.append(int(a)*int(b))

        elif s[i]=="/":

            a=stack.pop()

            b=stack.pop()

            stack.append(int(b)/int(a))

        elif s[i]=="-":

            a=stack.pop()

            b=stack.pop()

            stack.append(int(b)-int(a))            

    return stack.pop()

#space separtor is required , for solving 2 or more digits .

s="10 2 8 * + 3 -"

val=postfix_evaluation(s)

print(val)

 

