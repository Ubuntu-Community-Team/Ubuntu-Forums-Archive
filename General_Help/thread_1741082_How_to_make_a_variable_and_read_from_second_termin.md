---
title: "How to make a variable and read from second terminal?"
date: 2011-04-27
forum: General Help
---

### Post by Pithikos on 2011-04-27
I always wondered about this but never found a way to do it. Say I have two terminals open and I want to save the current path in a variable and read it from the second terminal that I have open. Then in the first terminal I type:

```
A=$(pwd)
```And in the second I type:

```
echo $A
```that doesn't work though. I have tryied also with
```
export A=$(pwd)
```and
```
alias A=$(pwd)
```but nothing seems to work. Is there a way to do this?

---

### Post by piratebill on 2011-04-27
Variables created in a bash  session stay within that session only.  Other than saving the value of pwd to a file, the second terminal wont be able to get it.

---

### Post by Pithikos on 2011-04-27
> **piratebill said:**
> Variables created in a bash  session stay within that session only.  Other than saving the value of pwd to a file, the second terminal wont be able to get it.

Thanks for your reply. You sir saved me from a headache :)

---

### Post by btindie on 2011-04-27
The only way you could do is if it was a sub process of the parent e.g.

Start a new terminal then type the following:
```
$ export MSG="Hello World"
$ gnome-terminal
```From the newly created terminal type ```
$ echo $MSG
```Or you can use sockets
```
$ A=$(nc -l 1234)
$ echo $A
``````
$ pwd | nc localhost 1234
```but then I'm going way OT....

---

### Post by Pithikos on 2011-04-27
> **btindie said:**
> The only way you could do is if it was a sub process of the parent e.g.

Start a new terminal then type the following:
```
$ export MSG="Hello World"
$ gnome-terminal
```From the newly created terminal type ```
$ echo $MSG
```Or you can use sockets
```
$ A=$(nc -l 1234)
$ echo $A
``````
$ pwd | nc localhost 1234
```but then I'm going way OT....

Wow! That nc was such a neato thing!! I playied a bit with it and "I'm lovin it"! Finally understood also what the export is all about :D

---

