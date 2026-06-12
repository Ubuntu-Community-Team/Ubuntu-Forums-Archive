---
title: "URGENT HELP! I locked myself out of ROOT!"
date: 2011-07-14
forum: General Help
---

### Post by eladnava on 2011-07-14
Hey all,
I did something very stupid today... I went and chown'ed my /dev/pts/0 file to another user because of this guide: (I first CHmodded and then CHowned)

[http://www.linuxquestions.org/questions/linux-general-1/problem-using-screen-cannot-open-your-terminal-dev-pts-0-please-check-338313/](http://www.linuxquestions.org/questions/linux-general-1/problem-using-screen-cannot-open-your-terminal-dev-pts-0-please-check-338313/)

Now I find myself locked out of SSH! I have another SSH user and I logged in on him but he doesn't have permission to chown the file back! I also tried using su root -c but it is rejecting my root password as if it is invalid, but I know it is valid! I have 2 root accounts on the system and both return "invalid passwords" ever since I chowned the damn file...

Does anyone know what I can do? I am very far from the server I must be able to do it remotely. Maybe a server reboot will help?

---

### Post by mikejonesey on 2011-07-14
whenever i used ubuntu i never had a password for root but was a sudoer; ie sudo su would work...

---

### Post by eladnava on 2011-07-14
Yeah by default you can't login as root on Ubuntu unless you set a password for the root user:

> sudo passwd root

That left me with 2 accounts, the one I created at setup and root. 

I just reset my box to no avail, still can't log into remote terminal.

In theory, would I be able to log in at the server in the actual screen? (E.g. not SSH)

---

### Post by wildmanne39 on 2011-07-14
> **eladnava said:**
> Hey all,
I did something very stupid today... I went and chown'ed my /dev/pts/0 file to another user because of this guide: (I first CHmodded and then CHowned)

[http://www.linuxquestions.org/questions/linux-general-1/problem-using-screen-cannot-open-your-terminal-dev-pts-0-please-check-338313/](http://www.linuxquestions.org/questions/linux-general-1/problem-using-screen-cannot-open-your-terminal-dev-pts-0-please-check-338313/)

Now I find myself locked out of SSH! I have another SSH user and I logged in on him but he doesn't have permission to chown the file back! I also tried using su root -c but it is rejecting my root password as if it is invalid, but I know it is valid! I have 2 root accounts on the system and both return "invalid passwords" ever since I chowned the damn file...

Does anyone know what I can do? I am very far from the server I must be able to do it remotely. Maybe a server reboot will help?
Hi, maybe this link will help.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by eladnava on 2011-07-14
Thanks for your reply, but is there no other way to do it remotely if I have SSH access on another user?

---

### Post by wildmanne39 on 2011-07-14
> **eladnava said:**
> Thanks for your reply, but is there no other way to do it remotely if I have SSH access on another user?
Hi, that I do not know hopefully some one will post an idea.

---

### Post by YK3bug on 2011-07-14
When you boot up your computer, you need to bring up GRUB if it doesn't already come (I think it can be done by holding <Control>. You then need to throw a "1" on the end of the like executing line thing that boots Linux. Then you will get single user access to root. There you can change the root password by typing "passwd", and following the prompts.

---

### Post by eladnava on 2011-07-15
OK I called up my datacenter and guided the resetter into "recovery mode" but unfortunately the root shell there also required a password :(
	
	But then I found another way of gaining access and guided him to add "single" to the kernel boot line and so he did, and then changed my root password to 123 and then I finally had access again.
	
	Whooh! :popcorn:
	
	
	I am never touching /dev/pts again in my life!

---

### Post by wildmanne39 on 2011-07-15
Hi, I am glad you got it fixed.

---

### Post by raja.genupula on 2011-07-15
> **eladnava said:**
> OK I called up my datacenter and guided the resetter into "recovery mode" but unfortunately the root shell there also required a password :(
    
    But then I found another way of gaining access and guided him to add "single" to the kernel boot line and so he did, and then changed my root password to 123 and then I finally had access again.
    
    Whooh! :popcorn:
    
    
    I am never touching /dev/pts again in my life!

         why dont you post the process ,,, that would be helpful to someone whose going to face the same problem in future .

                   please mark the thread as solved .

---

### Post by eladnava on 2011-07-16
Process is explained here:
[http://www.cyberciti.biz/tips/recovering-deleted-etcshadow-password-file.html](http://www.cyberciti.biz/tips/recovering-deleted-etcshadow-password-file.html)

Marked as resolved.

---

