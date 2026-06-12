---
title: "cant log out"
date: 2010-07-29
forum: General Help
---

### Post by tal32123 on 2010-07-29
when i press log out then it leaves a black screen and I cant use my computer

---

### Post by quixote on 2010-07-30
Sometimes when the power management isn't working right, that can happen.  The only thing to do is push the off button for 5 seconds and force a shutdown (aka hard reset).  If it does this all the time, it's a good idea to try to figure out what the problem is, since hard resets on a regular basis are a bad idea.  Do you get any error messages?  Any indication of what's wrong?

---

### Post by tal32123 on 2010-07-30
> **quixote said:**
> Sometimes when the power management isn't working right, that can happen.  The only thing to do is push the off button for 5 seconds and force a shutdown (aka hard reset).  If it does this all the time, it's a good idea to try to figure out what the problem is, since hard resets on a regular basis are a bad idea.  Do you get any error messages?  Any indication of what's wrong?

It is happening all the time, once after a hard reset it had a green screen for a second when it was booting but I didn't see what that said.... Please help I can't live without logout as this is a family computer :(

---

### Post by wangkeit on 2010-07-30
> **quixote said:**
> Sometimes when the power management isn't working right, that can happen.  The only thing to do is push the off button for 5 seconds and force a shutdown (aka hard reset).  If it does this all the time, it's a good idea to try to figure out what the problem is, since hard resets on a regular basis are a bad idea.  Do you get any error messages?  Any indication of what's wrong?
force shutdown--> sudo telinit 0
or restart --> sudo teinit 6

---

### Post by tal32123 on 2010-07-30
> **wangkeit said:**
> force shutdown--> sudo telinit 0
or restart --> sudo teinit 6

Sorry if I wasn't clear, my computer totally doesn't work after I press logoff, it's still on with a black screen, yet it doesn't work

---

### Post by tal32123 on 2010-08-22
it still doesnt work :(

---

### Post by quixote on 2010-08-22
I had a similar problem on a couple of computers.  Once it was the power management working badly.  More recently it was an incompatibility with the graphics card. That brief green screen suggests it might be graphics related.  So, let's start with the graphics card and make sure you have the best drivers for that. (Sometimes a driver will work for most things, but have quirks like this, and another driver can work better.)

If you don't know which graphics card you have, the simplest way to find out is via the terminal (Applications > Accessories > Terminal).  At the command line type```
lspci | grep 'VGA'
```and copy the result in your answer.

---

### Post by tal32123 on 2010-08-22
> **quixote said:**
> I had a similar problem on a couple of computers.  Once it was the power management working badly.  More recently it was an incompatibility with the graphics card. That brief green screen suggests it might be graphics related.  So, let's start with the graphics card and make sure you have the best drivers for that. (Sometimes a driver will work for most things, but have quirks like this, and another driver can work better.)

If you don't know which graphics card you have, the simplest way to find out is via the terminal (Applications > Accessories > Terminal).  At the command line type```
lspci | grep 'VGA'
```and copy the result in your answer.

tal@tal-desktop:~$ lspci | grep 'VGA'
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
tal@tal-desktop:~$ 


ok thats it. im using the NVIDIA accelerated graphics driver (version 173)

---

### Post by quixote on 2010-08-22
If you're running Lucid (10.04), then for me the open source driver actually worked way better than Nvidia's own.  (Seriously!) In synaptic, that's xserver-xorg-video-nouveau and any dependencies it pulls in.  When I installed it, I don't remember having had to do anything further to make the system use it. (I'll check around.)  

From my experience and everything I've seen here on the forums, it's a well-behaved driver which won't blow up something else on your system.  You can install it, and if it doesn't solve the problem, uninstall it and the graphics will go back to using your previous driver.

---

### Post by tal32123 on 2010-08-22
> **quixote said:**
> If you're running Lucid (10.04), then for me the open source driver actually worked way better than Nvidia's own.  (Seriously!) In synaptic, that's xserver-xorg-video-nouveau and any dependencies it pulls in.  When I installed it, I don't remember having had to do anything further to make the system use it. (I'll check around.)  

From my experience and everything I've seen here on the forums, it's a well-behaved driver which won't blow up something else on your system.  You can install it, and if it doesn't solve the problem, uninstall it and the graphics will go back to using your previous driver.

It's already installed, I'm assuming it's part of the proprietary driver package I installed.

---

