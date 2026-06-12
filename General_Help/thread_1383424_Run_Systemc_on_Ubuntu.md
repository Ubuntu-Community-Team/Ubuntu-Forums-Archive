---
title: "Run Systemc on Ubuntu"
date: 2010-01-17
forum: General Help
---

### Post by Malik_2009 on 2010-01-17
[SIZE=4]Hi everyone. I ma working with systemc. I have downloaded it from [www.systemc.org]("http://www.systemc.org") and extracted it. I followed all the steps to install it,but the problem I can not find the compiler.[/SIZE]
[SIZE=4]Please if anyone has an idea about how to run systemc and whether I still need the terminal to access the compiler or I can access the compiler via other way.[/SIZE]
[SIZE=4]Thanks for all.[/SIZE]

---

### Post by Leppie on 2010-01-17
hi and welcome to the community ;)

i don't know what you downloaded there, but if it's asking for a compiler you need to install one (like gcc, or g++). it might be useful to read all the output when you're trying to compile and install. post all the output here if you don't understand what it means. use the hash sign (#) on the post's toolbar to enclose all the output in code tags.

---

### Post by Malik_2009 on 2010-01-17
[SIZE=4]Thank you Leppie. I did downloaded gcc and I used the usual commands such as gmake.. etc, but when I used the check command I got 1 error. I could not understand this error.[/SIZE]
[SIZE=4]many thanks again[/SIZE]

---

### Post by Leppie on 2010-01-17
could you copy and paste the exact error message you are getting?
it may also be useful to see what commands you issued.

---

### Post by Malik_2009 on 2010-01-17
[SIZE=4]This is what I got when I wrote this command in the terminal(I already moved to systemc directory):[/SIZE]
[SIZE=4]./configure --host=i386 --host=i386 --target=i386 --build=i386.[/SIZE]
[SIZE=4]The result was:[/SIZE]
[SIZE=4]checking for i386-gcc ...no[/SIZE]
[SIZE=4].[/SIZE]
[SIZE=4].[/SIZE]
[SIZE=4].[/SIZE]
[SIZE=4]checking for i386-xlc... no[/SIZE]
[SIZE=4]checking forg++... g++[/SIZE]
[SIZE=4]checking for BCD-compatible install..../usr/bin/install   -c[/SIZE]
[SIZE=4]configure: error:"sorry... architecture not supported"[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]many thanks for help[/SIZE]

---

### Post by Leppie on 2010-01-17
it's saying that you have a different architecture. do you have a 32bit or 64bit system?
and what is the exact link to the package you downloaded?

---

### Post by Malik_2009 on 2010-01-17
[SIZE=4]Thank you. In fact, it is 64 bit architecture but the linke, I found many linkes about that. If you have a speceific links, please send it to me so I can use it. By the way, I use ubuntu9.10, and my computer is Sony CW, Dual 2core with 2.8GHz.[/SIZE]
[SIZE=4]thanks[/SIZE]

---

### Post by Leppie on 2010-01-17
i really don't know systemc, but you could ask them on the [systemc forum]("http://www.systemc.org/Discussion_Forums/systemc-forum/")

---

### Post by Malik_2009 on 2010-01-17
many thanks

---

