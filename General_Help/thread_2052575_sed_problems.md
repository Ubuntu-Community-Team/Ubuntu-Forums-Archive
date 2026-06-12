---
title: "sed problems"
date: 2012-09-03
forum: General Help
---

### Post by 00oddn4a on 2012-09-03
If i launch the command 'sed -f filescript text' , where  filescript:
```

         #!/usr/bin/sed -f    
         # Put 80 spaces in the buffer
         1 {
           x
           s/^$/        /
           s/^.*$/&&&&&&&&/
           x
         }
         # del leading and trailing spaces
         y/\t/ /
         s/^ *//
         s/ *$//
         # add a newline and 80 spaces to end of line
         G

```and  text:
```

 one
 two

```(there are two initial spaces on every  line)
Sed put the first line in the pattern buffer by removing \n.  After switches the two buffers and so the pattern buffer has 80 spaces  and the hold buffer has " one".After it switches the buffers, so " one"  is on pattern space. sed removes the leading zero, so the pattern buffer  is now "one". After, with 'G' command it put \n and appends the 80  spaces to  the pattern buffer. It finally prints the pattern buffer in  the stdout,move the pattern buffer in hold buffer and start with the  second line of the input,i.e. " two".Here it removes only the leading  zero, so the pattern buffer is "two".After with 'G' it put \n in the  pattern buffer and appends to it the hold buffer (which is "one\n[80  spaces]"). In the stdout it should prints "two\none\n[80 spaces]", but  it prints "two".Why?

---

### Post by Vaphell on 2012-09-03
i don't really see that 'move the pattern buffer in hold buffer' part.
imho in the first iteration you create the content of hold buffer but do nothing but
pattern+hold (G)

```
$ echo $'  one\n  two' | sed '1{x; s/^$/-----/;s/^.*$/&&&&&&&&/;x}; y/\t/ /;s/^ *//;s/ *$//; G;'
one
----------------------------------------
two
----------------------------------------
$ echo $'  one\n  two' | sed '1{x; s/^$/-----/;s/^.*$/&&&&&&&&/;x}; y/\t/ /;s/^ *//;s/ *$//; G;** h;**'
one
----------------------------------------
two
one
----------------------------------------
```

besides, why sed? imho when you need to shuffle stuff back and forth between buffers you should use something more convenient like awk. It's unintuitive and you will strain your brain muscle trying to figure out how to do something fancy with only 2 buffers.

---

### Post by 00oddn4a on 2012-09-03
So here [https://www.gnu.org/software/sed/manual/sed.html#Execution-Cycle](https://www.gnu.org/software/sed/manual/sed.html#Execution-Cycle) what it means when it says " the pattern space is deleted between two cycles"?

---

### Post by Vaphell on 2012-09-03
exactly that, once the the current iteration ends, main buffer is wiped to make space for another line. I don't get what you are trying to say though :-)

---

### Post by 00oddn4a on 2012-09-03
Oh, excuse-me. Now i 've understand. It's that i'm not english native and i had a misunderstanding. Thanks!

---

