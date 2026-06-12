---
title: "Newbie question"
date: 2010-04-19
forum: General Help
---

### Post by lindelof on 2010-04-19
I am quite new to linux. Recently, I've just downloaded a software, but get 
a painful problem. I install all correct path configurations as stated in 
the software manual, but get the following result,
# ls -l
total 2640
lrwxrwxrwx 1 vadmin vadmin      10 2010-04-19 10:24 alvis -> alvis-mesa
-rwxr-xr-x 1 vadmin vadmin 2258976 1996-11-04 19:47 alvis-mesa
-rwxr-xr-x 1 vadmin vadmin  117824 1996-11-04 19:47 delcx
-rwxr-xr-x 1 vadmin vadmin  153204 1996-11-04 19:47 mkalf
-rwxr-xr-x 1 vadmin vadmin    8764 1996-11-04 19:47 pdb2alf
-rwxr-xr-x 1 vadmin vadmin  138796 1996-11-04 19:47 volbl
# ./alvis-mesa
./alvis-mesa: Command not found.


Anyone could tell me the reason. Thanks a lot.
--

---

### Post by akakingess on 2010-04-19
Try either just running the app by typing just alvis-mesa or to actual install maybe ./configure    -   just a couple of suggestions.

---

### Post by linden940 on 2010-04-19
for someone who is very new to Linux.....you should use the Ubuntu Software center to install software

---

### Post by lindelof on 2010-04-19
I forget to mention that the software is a visualisation application. I am wondering whether I need to install certain graphics library just like OpenGL in windows.

---

### Post by linden940 on 2010-04-19
I'm not sure but I bet google could help you find out real easy

---

### Post by gordintoronto on 2010-04-19
What is the name of the program?  Perhaps it is available from Administration/Synaptic, which means it always installs perfectly with just a couple of mouse clicks.

---

### Post by lisati on 2010-04-19
> **akakingess said:**
> Try either just running the app by typing just alvis-mesa <snip>
Good suggestion, but I'd suggest that the OP returns to regular user privileges first. (I spotted the # prompt, you can return to the $ prompt with the "exit" command)
> **linden940 said:**
> for someone who is very new to Linux.....you should use the Ubuntu Software center to install software
Also a good suggestion.

---

