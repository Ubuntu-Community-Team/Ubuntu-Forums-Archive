---
title: "Setting my primary OP and another question"
date: 2009-07-10
forum: General Help
---

### Post by shelbyfan on 2009-07-10
I did it once before, but I cannot figure out how to do it again.  I used the command line and got it fixed, super easy. I have been searching for awhile and not refound the answer.

I use XP as my primary OP, Ubuntu will not run some programs that I have to use, I had it set as my auto startup.  About 2 days ago I went to use Ubuntu and it was set differently, I also noticed that I have two Ubuntu's selectable for using, I only installed once.

First, how do I reset my primary OP?
Second, how do I get rid of the other Ubuntu? Even if it means deleting all the OP's and starting over, that is fine.

I am not a computer geek, but I can usually figure out what I need to do. So any directions you give you can talk to me like a 10 year old, slowly and clearly :p I do however, prefer a more, uh, direct approach to fixing the problem. Think blitzkrieg.

If I could get Pandora, my CAD programs and Itunes to run, I would not have a use whatsoever for windows.

Thanks for any help.

---

### Post by mikewhatever on 2009-07-10
Hi and welcome.

I really don't understand your first question. Can you clarify what the primary OP is.

As for the second question, you most likely have two kernels showing in the bootloader's menu. It should be safe to remove the one you don't want simply by uninstalling the relevant package from Synaptic. I don't know which version of Ubuntu you have installed, but in case it was Jaunty, you'd most probably needed to remove the following package: **linux-image-2.6.28-11-generic**.

---

### Post by egalvan on 2009-07-10
Startup Manager is an easy, GUI-way to set some options in menu.lst.

---

### Post by shelbyfan on 2009-07-13
Thanks guys, took me a bit to figure it all out but it is running perfect, both suggestions were exactly what I needed. 

Why can't Windows make it that simple? ](*,)

---

