---
title: "boot without password"
date: 2010-02-15
forum: General Help
---

### Post by mjf9642 on 2010-02-15
Hello I have built a Home file sever using Ubuntu desktop 9.10. After I got it working I disconected the mouse, keyboard and monitor and put it out of the way. When the power went out one day I had to reconnect everythig so I could enter in my password. I was wondering if there was a way to set up the sever to start up without a password. Thank you.

---

### Post by bodhi.zazen on 2010-02-15
Enter your password to do what exactly ?

---

### Post by jocko on 2010-02-15
> **bodhi.zazen said:**
> Enter your password to do what exactly ?
Log in, perhaps?

---

### Post by 2hot6ft2 on 2010-02-15
System > Administration > Login Screen
Login Automatically

---

### Post by jocko on 2010-02-15
> **2hot6ft2 said:**
> System > Administration > Login Screen
Login Automatically
Didn't the op say it was a server install (=no gui)? Or maybe I just misunderstood the "server" part and the op asks for how to autologin to gnome... In that case 2hot6ft2 is correct.

---

### Post by bodhi.zazen on 2010-02-15
> **jocko said:**
> Log in, perhaps?
 
What server requires a log in ? The only one I know of is VNC.

If the OP is using a Desktop perhaps the problem is with Network Manager.

We need more information to help.

---

### Post by jocko on 2010-02-15
> **bodhi.zazen said:**
> What server requires a log in ? The only one I know of is VNC.

If the OP is using a Desktop perhaps the problem is with Network Manager.

We need more information to help.
I thought the op wanted to know how to automatically log in (to gnome if he has a desktop install, or to the terminal if he has a server install)... i.e not log in to any server application, but to log in to the actual system...

---

### Post by bodhi.zazen on 2010-02-15
> **jocko said:**
> I thought the op wanted to know how to automatically log in (to gnome if he has a desktop install, or to the terminal if he has a server install)... i.e not log in to any server application, but to log in to the actual system...

Could be most anything. If the OP is running Apache + ssl (https) s/he may need to enter the cert password.

Could be a GRUB password.

Could be an encrypted installation.

We need more information to answer the question.

---

### Post by mjf9642 on 2010-02-15
Thanks for all of the replys.  2hot6ft2's was the one I needed.  I never used Linux before so when I built the file sever I used desktop becuase I read it would be easier.  I am now going to get another computer that I can dedicate to Linux so that I can learn the operating system.  Once again thank you.

---

