---
title: "What does &quot;|&quot; mean in a terminal command?"
date: 2011-10-18
forum: General Help
---

### Post by Lrpbpb on 2011-10-18
I'm quite unexperienced with the terminal (I have used Linux for a while, though) and I would like to learn more about commands in the terminal, how to interpret them. Usually you can just go to a tutorial in a web page, plug in whatever command the give and voila its fixed. But I would like to actually *know* what the command does. 

For example, some commands use the " | " and I want to know what it does to the command. One such example is: ```
echo 'ndiswrapper' | sudo tee -a /etc/modules 			 		
```
 
Can anyone tell me what "|" does? Also, do you know of any good newbie site to start learning these commands?

---

### Post by haqking on 2011-10-18
> **Lrpbpb said:**
> I'm quite unexperienced with the terminal (I have used Linux for a while, though) and I would like to learn more about commands in the terminal, how to interpret them. Usually you can just go to a tutorial in a web page, plug in whatever command the give and voila its fixed. But I would like to actually *know* what the command does. 

For example, some commands use the " | " and I want to know what it does to the command. One such example is: ```
echo 'ndiswrapper' | sudo tee -a /etc/modules 			 		
```
 
Can anyone tell me what "|" does? Also, do you know of any good newbie site to start learning these commands?

it is a pipe which means pipe one command's results to another command

see here [http://www.linux-tutorial.info/modules.php?name=MContent&pageid=21](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=21)

and [http://linuxcommand.org/](http://linuxcommand.org/) for a good tutorial on CLI

---

### Post by galvatron408 on 2011-10-18
> **haqking said:**
> it is a pipe which means pipe one command to another command


It does NOT mean pipe one command to another command!

It means, send the results of the first command to the next command. Here is a very simple way of seeing it in action.

#1 - I send a bunch of text in to a file named temp.out.
#2 - I grep for the character 1 and the results include "test1a and test1b"
#3 - When I use the | character and use "grep a", I'm saying search for "a" in the result of "grep 1 temp.out" (which of course, the result is "test1a and test1b"

ThinkPad-T61:~$ echo test1a >> temp.out
ThinkPad-T61:~$ echo test1b >> temp.out
ThinkPad-T61:~$ echo test2a >> temp.out
ThinkPad-T61:~$ echo test2b >> temp.out
ThinkPad-T61:~$ 
ThinkPad-T61:~$ grep 1 temp.out
test1a
test1b
ThinkPad-T61:~$ grep 1 temp.out | grep a
test1a
ThinkPad-T61:~$

---

### Post by haqking on 2011-10-18
> **galvatron408 said:**
> It does NOT mean pipe one command to another command!

It means, send the results of the first command to the next command. Here is a very simple way of seeing it in action.

#1 - I send a bunch of text in to a file named temp.out.
#2 - I grep for the character 1 and the results include "test1a and test1b"
#3 - When I use the | character and use "grep a", I'm saying search for "a" in the result of "grep 1 temp.out" (which of course, the result is "test1a and test1b"

ThinkPad-T61:~$ echo test1a >> temp.out
ThinkPad-T61:~$ echo test1b >> temp.out
ThinkPad-T61:~$ echo test2a >> temp.out
ThinkPad-T61:~$ echo test2b >> temp.out
ThinkPad-T61:~$ 
ThinkPad-T61:~$ grep 1 temp.out
test1a
test1b
ThinkPad-T61:~$ grep 1 temp.out | grep a
test1a
ThinkPad-T61:~$

yeah its what i meant, bad wording, i meant pipe one commands results.

edited

---

