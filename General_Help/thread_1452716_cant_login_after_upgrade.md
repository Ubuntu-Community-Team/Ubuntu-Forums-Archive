---
title: "cant login after upgrade"
date: 2010-04-12
forum: General Help
---

### Post by who901 on 2010-04-12
Please help me to login. First post ever:) I have ubuntu on my pc on its own partion. It was working fine till I upgraded packages, like 195 of them! I read other post on fixing the problem and tryed goinig to the drop to boot shell in the recovery boot but keep getting now were , it seems like it just wont take any passwd. It also looks like i have two ubuntu programes in my bios start up, it reads. Can this be cleaned up?
 
 
2.6.31-20-generic
2.6.31-20-recovery
2.6.31-14-generic
2.6.31-14-recovery
memory test(memtest86+)
memory test(memorytest 86+,serial console 115200
windows 7 (loader) (on/dev/sda1)

---

### Post by nischalinn on 2010-04-12
To which version do you upgraded?

---

### Post by quadproc on 2010-04-12
> **who901 said:**
> Please help me to login. First post ever:) I have ubuntu on my pc on its own partion. It was working fine till I upgraded packages, like 195 of them! I read other post on fixing the problem and tryed goinig to the drop to boot shell in the recovery boot but keep getting now were , it seems like it just wont take any passwd. It also looks like i have two ubuntu programes in my bios start up, it reads. Can this be cleaned up?To answer this part first, yes, but...
It is usually a good idea to keep a fallback version of some release on your system.  That way, if something goes seriously wrong with your usual release then you can use the fallback version to get things fixed.  If you have decided that you really don't need a particular version then you can use Synaptic to uninstall the appropriate kernel-image.  I suggest using web searches to learn the details of this process.  There are also other tools such as apt-get which can be used for the removal operation but Synaptic is easy and convenient.

Now for the password question: are you trying to log in as root?  If so, I recommend against it.  Being root is quite dangerous and it is unnecessary.  For this reason, the standard distribution does not allow root logins.

If you are trying to log in as a user and not succeeding then you may need to reset the password.  Since it isn't practical to recover a password it is best to just set the password to some known characters.  Once you are logged in then you can change it to something else if you like.

Welcome to the forums!

quadproc

---

### Post by who901 on 2010-04-14
The upgrade was for ubuntu 9.1

---

### Post by who901 on 2010-04-14
dont know what a fallback version is? But i tryed to change the password in the root shell promt. and it said the password was sucssfully changed but I still cant login?

---

### Post by quadproc on 2010-04-14
> **who901 said:**
> dont know what a fallback version is? But i tryed to change the password in the root shell promt. and it said the password was sucssfully changed but I still cant login?
By "fallback version", I mean a different installation of the system software that you can use when your usual version has malfunctioned for some reason.  For instance, I usually use Karmic (version 9.10) but if something happened to it (for example, say that I erroneously edited my xorg.conf file and consequently the X windows server could no longer function) then I could use one of the older releases such as Intrepid (8.10) which I had saved for fallback usage.  then I could repair the damage and resume using Karmic.

Regarding your immediate problem, I think that we may be writing about different things.  The root shell prompt doesn't have a password in it.  And, unless you have enabled the root account (a very bad thing to do) then you cannot log in as root.  When you need root privileges then you can temporarily get them by using sudo.  Type```
 man sudo
``` in a terminal to learn more.  Unless you have a nonstandard recovery mode setup then you are root when you get a command line prompt in recovery mode.

If I knew more about what your system is saying and doing then I might be able to suggest something helpful.

quadproc

---

### Post by who901 on 2010-04-21
thanks for your help I deleated ubuntu and re loaded it to try again
.:P

---

