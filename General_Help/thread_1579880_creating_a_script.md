---
title: "creating a script"
date: 2010-09-22
forum: General Help
---

### Post by ghayes on 2010-09-22
Hello, I have never created a script before and I am using the Bash Shell. I tried to do the following and got this return:
 
Well, I am trying to create a script, and inside the script set permissions for certain directories and files. However, when I have completed a script, at least think I have! I try to run the script and it shows that I need an operand after the following command: chmod u+rwe/shipping. However, I cannot find what operand I need. This is an operand I need when creating the script I am assuming.
 
If anyone can show me an example of what I am doing wrong. Again, I am a beginner and fairly ignorang when it comes to Unix or Linux.
 
thanks.

---

### Post by Sin@Sin-Sacrifice on 2010-09-22
What do you want the script to do?

---

### Post by ghayes on 2010-09-22
Well, the script is for my class and it asks that we creat a script that will automate a security scheme that I already created. The scheme has to deal with setting permissins for the direcotries such as /shipping, /shipping/in, shipping/out, /sales, /sales/A, /sales/B. 
 
thanks

---

### Post by Vaphell on 2010-09-22
chmod u+rwx /some/dir should work, are you sure you got spaces right?

---

### Post by Sin@Sin-Sacrifice on 2010-09-22
Is chmod u+rwe/shipping suppose to be chmod u+r ./we/shipping? Because "e" isn't a valid option. Also make sure that the space in between your options and folder is there in the script because it's not in your post. Check out ```
man chmod
``` and [http://www.gtkc.net/kb/entry/56/](http://www.gtkc.net/kb/entry/56/) which may help you figure it out.

---

### Post by blur xc on 2010-09-22
Isn't there some rule about not getting forum member to do your class assignment for you?

BM

---

### Post by CharlesA on 2010-09-22
> **blur xc said:**
> Isn't there some rule about not getting forum member to do your class assignment for you?

BM

Yes. Thread closed.

@OP: Ask yer instructor for information, or look at the man pages/google. That's what I've always done.

---

