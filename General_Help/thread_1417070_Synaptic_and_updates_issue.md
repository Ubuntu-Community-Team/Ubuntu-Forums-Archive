---
title: "Synaptic and updates issue"
date: 2010-02-26
forum: General Help
---

### Post by zombienation on 2010-02-26
Ok, so I do not know what happen but suddenly, I can no longer install updates, or access the synaptic manager. I am using Ubuntu 9.10. all was working fine and then one day, I was not able to install updates. Then I noticed that the synaptic manager was not working also. When attempting to install updates and access the synaptic manager, I get asked for my password, then after entering my password, nothing happens, the password box clears and nothing happens. Funny thing, I can sudo apt-get and install programs via the terminal. But that is the only way for me to download and install apps. 

Any help would be great! I really do not feel like reinstalling but I will if I have too. 

Thanks!

Zombienation

---

### Post by jmszr on 2010-02-26
zombienation,

I had a similar problem, the fix was:

```
sudo rm /var/cache/apt/*.bin
```

Perhaps that will work for you, worth a try.

---

### Post by drs305 on 2010-02-26
I am assuming that this is happening when you try to start synaptic via the GUI/menu.  What happens if you try to start synaptic via command line:
```
gksu synaptic
```
Please post any error messages you get.

A quick fix might be:
```
sudo apt-get install --reinstall synaptic
```
but if not the error message(s) generated above from the first command (if any) should help us determine what is happening.

---

### Post by zombienation on 2010-02-26
> **drs305 said:**
> I am assuming that this is happening when you try to start synaptic via the GUI/menu.  What happens if you try to start synaptic via command line:
```
gksu synaptic
```
Please post any error messages you get.

A quick fix might be:
```
sudo apt-get install --reinstall synaptic
```
but if not the error message(s) generated above from the first command (if any) should help us determine what is happening.

I am not at my computer right now but will try the tips mentioned here. Also, I cannot download and install the updates either. Thanks again everyone for your input and I will report back as soon as I can get home and try these tips. 

Zombienation

---

### Post by houseworkshy on 2010-02-26
It may be worth booting into recovery mode and using the fix broken packages option.  As apt-get is working  you could try fixing broken dependancies, see the manual page for details "man apt-get".    It that doesn't work try purging synaptic, also using apt-get,  and re-installiing it.  It may also be worth looking at your software sources.

---

### Post by zombienation on 2010-02-27
> **drs305 said:**
> I am assuming that this is happening when you try to start synaptic via the GUI/menu.  What happens if you try to start synaptic via command line:
```
gksu synaptic
```
Please post any error messages you get.

A quick fix might be:
```
sudo apt-get install --reinstall synaptic
```
but if not the error message(s) generated above from the first command (if any) should help us determine what is happening.

Ok, so I attempted to open synaptic from the terminal and got this error
sudo: pam_authenticate: Conversation error

Still no luck with any of the other tips, Cannot do ubuntu updates and open synaptic manager. Arggh.....

---

### Post by DeadSuperHero on 2010-02-27
Does "aptitude install" work instead of "apt-get install"?

---

### Post by zombienation on 2010-03-07
Ok, folks, So here is more info on my issue. I noticed that when logging into my user account, I have to type my password TWICE. I thought I was always mistyping my password at first, but then, I noticed that I always had to type my password once, then it will ask for my password again. Then I can gain access to my account. Is my user profile messed up? if so, is there anyway to repair my user profile?

thanks!

zombie nation

---

