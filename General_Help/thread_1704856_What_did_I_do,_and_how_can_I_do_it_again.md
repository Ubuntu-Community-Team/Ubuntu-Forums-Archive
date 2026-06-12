---
title: "What did I do, and how can I do it again"
date: 2011-03-11
forum: General Help
---

### Post by Hollyecho_Montgomery on 2011-03-11
I downloaded and installed ....something.... that made my windows games play in full screen mode for the 1st time (bejeweled and zuma), and I can't remember what it was, or why I was trying it in the first place.  

My question is, is there a way to see what I did on the machine last?  For I would like to put the same .... something.... on my husband's machine:confused: so, his windows games (ZUMA AND BEJEWELED) will run that well on his machine.

Before they could only come up in a small window, and if you put in options 'full screen' it would lock up and not show anything, and you would have to uninstall it and then re-install it and keep it in a small window.

Any ideas anyone?  I remember following a apt-get from a forum, but since I was so busy on other peoples (paying customers) computers, I forgot what I did, or even why .....

---

### Post by Hippytaff on 2011-03-11
*I've never done this, but these are a few suggestions I found on the forums for you to try to get a history of what has been installed.*
 
*sudo cat /var/log/apt/term.log*
 
**synaptic>file>history**
 
**cat /var/log/aptitude**

---

### Post by cchhrriiss121212 on 2011-03-11
> **Hollyecho_Montgomery said:**
> 
Any ideas anyone?  I remember following a apt-get from a forum, .....
Browser history?

---

### Post by Hollyecho_Montgomery on 2011-03-11
> **Hippytaff said:**
> *I've never done this, but these are a few suggestions I found on the forums for you to try to get a history of what has been installed.*
 
*sudo cat /var/log/apt/term.log*
 
**synaptic>file>history**
 
**cat /var/log/aptitude**t 


Thank you !!  It looks like I installed new version of Wine !
"wine1.3 (from .../wine1.3_1.3.15-0ubuntu1~maverickppa2_i386.deb"

Thank you ever so much.  I then thought I would try the **synaptic **but didn't find file history, your  *sudo cat /var/log/apt/term.log *is what I got the information from.  Thank you again ever so much.     :guitar:

---

### Post by Hippytaff on 2011-03-11
Your welcome :-)
 
Remember to mark the thread as solved inthe thread tools at the top of the page :-)

---

### Post by Hollyecho_Montgomery on 2011-03-11
> **Hippytaff said:**
> Your welcome :-)
 
Remember to mark the thread as solved inthe thread tools at the top of the page :-)


Ok, sorry about that - thank you !

---

### Post by Hippytaff on 2011-03-11
> **Hollyecho_Montgomery said:**
> Ok, sorry about that - thank you !
 
Don't apologise - and again, your welcome :-)

---

