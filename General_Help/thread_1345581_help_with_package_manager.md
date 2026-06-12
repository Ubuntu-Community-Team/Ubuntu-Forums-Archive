---
title: "help with package manager"
date: 2009-12-04
forum: General Help
---

### Post by margaretw1 on 2009-12-04
Help! only just started with ubuntu 9,1 and know little about it.
I tried to install a package and got this message

An Error Occured

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anybody tell me in simple terms how to correct this error please

---

### Post by hardfire_avk on 2009-12-04
Open a terminal and execute the following commands. this should do thw work

```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by margaretw1 on 2009-12-04
That worked fine, things started happening and then stopped.
went to package manager again and got a further error.
This time it was 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Don't know whether this is correct but went to terminal to enter sudo dpkg --configure-a
It  asked for password but I can't enter my password, nothing happens when I type!!

---

### Post by kellemes on 2009-12-04
> **margaretw1 said:**
> That worked fine, things started happening and then stopped.
went to package manager again and got a further error.
This time it was 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Don't know whether this is correct but went to terminal to enter sudo dpkg --configure-a
It  asked for password but I can't enter my password, nothing happens when I type!!

type password and press enter.

---

### Post by audiomick on 2009-12-04
do you know that the terminal doesn't show you what you are typing when you are typing a password?

You have to type "blind", then press enter.

---

### Post by margaretw1 on 2009-12-04
This is what I was trying to do.
I opened terminal and I get 
margaret@margaret-desktop:~$password
password: command not found
so I type
margaret@margaret-desktop:~$ sudo dpkg --configure -a
and it asks for password
[sudo] password for margaret: here I get a black flashing square but I cannot input any letters from my keyboard

---

### Post by jordanae on 2009-12-04
Actually even though you can't see any characters showing up on the screen you are typing. The way Ubuntu does it is that you type in your password but nothing shows up on the screen. It's a security thing.

And if you aren't comfortable with the terminal you can always go to System> Administration> Synaptic Package Manager. When you type in your password on there you will notice it. 

But if you do use this GUI tool then you will have to enable third party repositories. When the package manager is open go to Settings> Repositories and under the "Other Software" tab check all sources. Click apply and exit out of that window. now in Synaptic Package Manager type in the name of the package you want and the results should come up.

---

### Post by margaretw1 on 2009-12-04
Ahh I understand now, tried it, everything appears normal.
Many thanks for your help.

How do I close the thread as solved?

---

