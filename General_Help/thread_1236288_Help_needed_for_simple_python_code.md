---
title: "Help needed for simple python code"
date: 2009-08-10
forum: General Help
---

### Post by James121 on 2009-08-10
Hey im new to the whole python thing can any one help me? I'm trying to write a program that has a simple job to do. It reads three lines of input and has to print the longest one. If there is a tie for the longest line, it should print out the first one. But my code isn't working... can anyone help?
 
a = raw_input("first string? ")b = raw_input("second string? ")c = raw_input("third string? ")longest = ""if len(a) >= len(longest):    longest = aelif len(b) > len(longest):    longest = aelse:    longest = cprint "The longest line was", longest

---

### Post by slakkie on 2009-08-10
> **James121 said:**
> Hey im new to the whole python thing can any one help me? I'm trying to write a program that has a simple job to do. It reads three lines of input and has to print the longest one. If there is a tie for the longest line, it should print out the first one. But my code isn't working... can anyone help?
 
a = raw_input("first string? ")b = raw_input("second string? ")c = raw_input("third string? ")longest = ""if len(a) >= len(longest):    longest = aelif len(b) > len(longest):    longest = aelse:    longest = cprint "The longest line was", longest


Use the [code] [ /code] tags, that way formatting is not lost on the forums.

---

### Post by ladasky on 2009-08-10
```
strings = []
for x in range(3):
    strings.append(raw_input("Enter string: "))
lengths = [len(s) for s in strings]
longest = lengths.index(max(lengths))
print "The longest string was:", strings[longest]
 
>>>
Enter string: First
Enter string: Second
Enter string: Third
The longest string was: Second
```

---

