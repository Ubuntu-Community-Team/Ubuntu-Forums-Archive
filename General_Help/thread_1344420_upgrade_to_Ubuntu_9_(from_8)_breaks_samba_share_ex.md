---
title: "upgrade to Ubuntu 9 (from 8) breaks samba share external hard drive"
date: 2009-12-02
forum: General Help
---

### Post by t42 on 2009-12-02
I use my Ubuntu box to share an external hard drive for everyone on the network. (I am not concerned about security at all). I used samba to share /media/external drive on Ubunti 7 and 8. This does not work on Ubuntu 9.

I think this is a result of me being not allowed to set permissions on the disk in Ubuntu 9. "sudo chmod 777 extenal drive" does nothing except ask for password (it worked on earlier versions of ubuntu). i used the gui as root and it does not allow me to change permissions. 

The result of this is that the drive is visible on the network and no one can look at it. this should be obvious as the permissions are "drwx------" and no matter what I do as sudo i can not change this.

Is this the result of different auto mount flags? Is this some security feature?

I know this is not a format of the external disk issue, the same computer and hard drive worked for me, this happened after i upgraded from 8 to 9)

please help me set permissions on my hard drive

---

### Post by bradsthompson on 2009-12-03
good luck... i'm having similar problems.. the only difference being that my hd is internal.  so far, no help.  also, mine worked in 9.04 just fine.  all i did was install the samba gui and everything worked great.  no such luck with 9.10.

---

### Post by RonaldCruz on 2010-02-17
Hi guys. I have the same issue with you. I'm in a home network, previously I'm using windows XP and it is easier to share an external HDD and my internal HDD. Few clicks I can share my folders right away. It is my current stumbling block for Ubuntu and it forces me to go back to windows because of this. I love Ubuntu since then but this is my current dilemma.

I hope someone will help us out and hear our cries!](*,)

---

### Post by laughlin.bill on 2010-10-14
I'm in the same boat, and I think I can describe the problem a little more clearly.

Ubuntu automounts the external hard drive as the currently-logged-in user and assigns it rwx------ permissions by default, meaning no one else can access it.

The question is, how dows one change this default behavior?  I can't seem to find the response anywhere

---

