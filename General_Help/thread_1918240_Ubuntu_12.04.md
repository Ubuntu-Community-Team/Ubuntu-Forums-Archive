---
title: "Ubuntu 12.04"
date: 2012-01-31
forum: General Help
---

### Post by dRounse on 2012-01-31
I am going to be setting up my server today and I was wondering if Ubuntu 12.04 is stable enough, I know its LTS and I dont want to be messing with it once its up, which is why i would prefer this as opposed to 11.10. Any help would be great.

---

### Post by lykwydchykyn on 2012-01-31
Is it stable? No.

Is it stable *enough*  -- that depends on what you're going to install, your expertise, and how vital the stability of this server is (e.g., is this work or home?).

I will say this:  my 12.04 test machine is getting several dozen updates on an almost daily basis, so if internet bandwidth is an issue you might want to hold off.

---

### Post by seawolf167 on 2012-01-31
I would hold off for a while yet - here is their [work item status page]("http://status.ubuntu.com/ubuntu-precise/all-ubuntu-12.04-beta-1.html"). There is still much to do on it.

---

### Post by mörgæs on 2012-01-31
If you want it to be stable on **your** computer it s a good idea to begin testing now and report the bugs.

---

### Post by QIII on 2012-01-31
I'm voting "Yes" on a test/bug reporting machine and "No" on a production/everyday use machine.

---

### Post by dRounse on 2012-01-31
Thank you, should I use 10.04 for my server, and then update to 12.04 a coulpe of months after the release? Also I have used 10.04 before but how do I update everything to run the most recent applications and programs?

---

### Post by lykwydchykyn on 2012-01-31
Once again, it depends on what you want to do with this server and whether it's being used in a home or work environment, and how important its services are, etc.

If you install 10.04, you're going to get the application versions that it comes with, plus some security updates and the odd backport if you enable those repositories and do an update.

Getting the latest versions of applications on an old version of Ubuntu, when it's possible, is usually a process of locating an appropriate PPA or downloadable .deb, or compiling from source.  If you're just going to upgrade in a couple months, it's probably not worth it.

Either 10.04 or 11.10 should be able to upgrade in-place to 12.04 when it's released.  If you're concerned about the age of the software in 10.04, install 11.10 for now.

---

### Post by dRounse on 2012-01-31
> **lykwydchykyn said:**
> 
Either 10.04 or 11.10 should be able to upgrade in-place to 12.04 when it's released.  If you're concerned about the age of the software in 10.04, install 11.10 for now.

Ok thank you I will install 11.10, and I really like awesome wm so if I update to 12.04 will it install unity? i just need a minimal desktop.

---

### Post by mastablasta on 2012-02-01
> **dRounse said:**
> Ok thank you I will install 11.10, and I really like awesome wm so if I update to 12.04 will it install unity? i just need a minimal desktop.
 
 
unity is already a default in 11.10.
 
for th really minimal desktop it's beetter to use LXDE (Lubuntu) or one of the windows managers (iceWM, Openbox, Fluxbox...).

---

### Post by lykwydchykyn on 2012-02-01
> **dRounse said:**
> Ok thank you I will install 11.10, and I really like awesome wm so if I update to 12.04 will it install unity? i just need a minimal desktop.

It's only going to update packages that are installed, so if you don't install Unity it won't install it on update (unless there's some weird dependency issue that causes it to install).

Even if it does, you can remove that and go back to awesome after the install.

BTW -- I like awesome too, using it on my laptop.

---

