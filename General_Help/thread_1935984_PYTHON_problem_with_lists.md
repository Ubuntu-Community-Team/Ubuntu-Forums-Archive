---
title: "PYTHON: problem with lists"
date: 2012-03-05
forum: General Help
---

### Post by nischalinn on 2012-03-05
Here is the problem:
a function that takes two strings and removes from the first string any character that appears in the second string. eg. if the first string is “IamLearningPython” and the second string is “aeiou” the result is “mLrnngPythn”.

I've written the code for this, but I can not figure out the error:
Can any one tell me what is the error with this code:

```

def attenuate(sequence1, sequence2):
	newSeq = []
	n = len(sequence2)
	for m in range(len(sequence1)):
		print(m)
		while(n in range(len(sequence2)) and sequence1[m] != sequence2[n]):
			'''checks for the condn of matched string if no match found then append the string to the list newSeq '''
			if n == len(sequence2):
				entry = sequence1[m]
				newSeq.append(entry)
				
			n =+1
	return newSeq
		
def main():
	
	return 0

if __name__ == '__main__':
	inp1 = str(input('please give your input: '))
	'''input string = IamLearningPython'''
	seq1 = list(inp1)	
	inp2 = str(input('please give next input: '))
	'''aeiou'''
	seq2 = list(inp2)
	newSeq1 = attenuate(seq1,seq2)
	print(newSeq1)
	
	
	main()

```

---

### Post by Topsiho on 2012-03-05
I did not follow the logic yet, but want to indicate an error:
You write: n=+1, which results in n being assigned the value 1.
I guess you need n +=1; which results in n=n+1.
You can try this out in a terminal, in which you started Python or Python3

Topsiho

---

### Post by Topsiho on 2012-03-05
I am not solving this for you, the fun is for you to do it yourself.
But reading your code I have several hints:

1. You can use strings as well as lists.
2. The result of input() is already a string, no need to make it a string. To the contrary, if you need to input numbers, you must convert the input strings to numbers, int(input()) or float(input()).
3. No need to use integers in a for loop. You can code:
   for n in string1:
       statement  (indented)
       statement  (indented)

n will be a character if string1 is a string (wich is a sequence of characters)
4. Strings can be concatenated with the + operator: string1 + 'a', for example.
5. What is the main() function for. You can drop that.
6. The real fun you have is to solve yourself: what should happen when you find matching characters n and m? The best thing to do is to try this out using two sequences (strings) with cardboard letters, on the table. If you find a solution, write this up schematically, in your own words and language. And only then code this into python  code.

7. Trying the program, after the if __name__ == '__main__' part,
it is far easier to first define the strings like:
seq1="whatever you want to put here"
seq2="and here"
in stead of having to input the same strings over and over again.
Only when the program seems to work you can make them inputable like:
seq1=input("input the first string: ")
seq2=input("input the other string: ")

No need to use the intermediate variables inp1 and inp2.

8 And drop main() here too.

Success,

Topsiho

---

