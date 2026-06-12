---
title: "Why Can I Not Log-In as Root?"
date: 2006-03-04
forum: General Help
---

### Post by annie on 2006-03-04
Hello, I am Annie hear again!

Some Problems I have with my Ubuntu computer cannot log-in as Root.  Why?  I nevre change the Password but it has Reset unknowing.

According my Internet and Sound not working.  My Friend use Ubuntu saying to open Users and Groups but this also not worked.

Plese Help!  Thank-You.

---

### Post by aysiu on 2006-03-04
There is no logging in as root in Ubuntu:
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by annie on 2006-03-04
[QUOTE=aysiu]There is no logging in as root in Ubuntu:
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)[/QUOTE]

Oh, this is unlike my problem.

I try to run sudo su.  Hit enter but nothing happen.

Think my Password has Reset.  Please Help!

---

### Post by mostwanted on 2006-03-04
[QUOTE=annie]Oh, this is unlike my problem.

I try to run sudo su.  Hit enter but nothing happen.

Think my Password has Reset.  Please Help![/QUOTE]

What do you mean "nothing happens"? Something has got to happen. Does it just display a new prompt?

---

### Post by annie on 2006-03-04
[QUOTE=mostwanted]What do you mean "nothing happens"? Something has got to happen. Does it just display a new prompt?[/QUOTE]

It goes such as:

annie@ubuntu:  sudo su (hit enter)
annie@ubuntu:

---

### Post by arctic on 2006-03-04
Was there a time-limit set for root?
This link might help:
[http://www.aplawrence.com/Linux/lostlinuxpassword.html](http://www.aplawrence.com/Linux/lostlinuxpassword.html)

---

### Post by orlox on 2006-03-04
To get root access on the console I simply type 

su root

instead of using sudo su. But I think it shouldn't make much of a difference...

---

### Post by annie on 2006-03-04
Thank You everyone for Help. Still question, though.

In [http://www.aplawrence.com/Linux/lostlinuxpassword.html](http://www.aplawrence.com/Linux/lostlinuxpassword.html) I am not Understand this.  :???: 

su root is not working still :(

---

### Post by tyr1973 on 2006-03-04
Hi!

In order to set a new password for the root account you could try.
sudo passwd root

I can't offer any ideas why your root password is missing though.

cheers

---

### Post by annie on 2006-03-04
Oh No!

None are working.  I Think to format Ubuntu?

---

