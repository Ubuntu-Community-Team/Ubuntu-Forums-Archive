---
title: "install apache2 not working"
date: 2011-06-08
forum: General Help
---

### Post by mparker1113 on 2011-06-08
Hi,

I am running ubuntu 9.x on VMWare and have tried sudo apt-get install apache. When doing so, it reports "couldn't find package apache2. I did apt-get update, and there appeared to be many failures. I know that i am connected to the interenet because I can ping urls. 

Any sugggestion as to how i can get this installed ?

---

### Post by Peter09 on 2011-06-09
Can you tell us what errors you are getting?

---

### Post by wambo on 2011-06-09
one thing to check is what your network settings are? eg. NAT or Bridged? If your using a network cable in your machine set this to bridged but if you using wireless set it to NAT as I personally have had issues when using VMs on wireless.
 
run the command **sudo /etc/init.d/networking restart**
 
Then run **sudo apt-get update**
 
Followed by **sudo apt-get install apache2**
 
Let us know how you get on.

---

### Post by mparker1113 on 2011-06-09
I ran those commands. Still getting:
Reading package lists... Done
Building dependency tree
reading state informatin...Done
E: Couldn't find packaage apache2

---

### Post by _oOMOo_ on 2011-06-09
Do you see errors when running sudo apt-get update? If so could you paste the output here?

---

### Post by Christmas on 2011-06-09
Are you sure you still have the right repositories in your /etc/apt/sources.list file?

---

### Post by mparker1113 on 2011-06-09
> **_oOMOo_ said:**
> Do you see errors when running sudo apt-get update? If so could you paste the output here?

[IMG]file:///C:/Users/Michael/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/Michael/AppData/Local/Temp/moz-screenshot-1.png[/IMG]I don't have a UI, don't know how i can copy the text from VM Linux to browser :(.

---

