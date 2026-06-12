---
title: "Wubi; How does it exactly work ?"
date: 2010-05-02
forum: General Help
---

### Post by Maz7006 on 2010-05-02
Just a small inquiry on how Wubi works. I've never tried it, and it states that it installs in windows ? .... that got me thinking, is it somewhat of a "virtual box" or does it install, partition the drive, then install ? i would like to know also that are ALL the features that Ubuntu has to offer installed and usable under Wubi such as advanced desktop effects.

Thank You.

---

### Post by Frantic_Earthling on 2010-05-02
[http://wubi-installer.org/](http://wubi-installer.org/)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by Nick.Sth on 2010-05-02
With Wubi you basically have the same option as you do with a Cd, you can install it on an other partition, or you can just install it on your Windows drive without losing anything. I did so on my other computer, but on this one it wouldn't work for some reason so I used a Cd and everything was went smoothly.

---

### Post by Maz7006 on 2010-05-02
Thanks for the replies, but will i be able to utilize ALL the functions like any other normal ubuntu install. i.e. will i be able to install packages, programs, drivers etc ?

---

### Post by Frantic_Earthling on 2010-05-02
Yes.

---

### Post by catxk on 2010-05-02
I'm running it right now and it's swell. It installs in Windows just like any other Windows application (and can be uninstalled in the same fashion) but it runs like if you have a dual-boot configuration, as opposed to it being a virtual machine. So upon boot, you get the Windows MBR where you can chose to boot into Ubuntu or Windows. Once in Ubuntu, I doubt you will ever notice you are not in a "clean" dual-booting session, and all effect and such works fine.

The only issue I had was when updating from 9.10 to 10.04 which ended in a complete reinstall of Wubi and Ubuntu. As such, I guess Wubi is no permanent solution, but if you look for that, the extra trouble of setting up dual-boot is probably worth it.

Edit: So to answer your last question: yes, ALL functions *should* work as it *is* a real install, but I guess that the concept in itself is prone to vulnerabilities meaning some things wont work. In my case, the upgrade from 9.10 to 10.04.

---

### Post by dino99 on 2010-05-02
> **Maz7006 said:**
> Thanks for the replies, but will i be able to utilize ALL the functions like any other normal ubuntu install. i.e. will i be able to install packages, programs, drivers etc ?

if you want really test ubuntu or any distro, you have 2 serious ways: installing it or run it into a virtual sandbox, the easiest is virtualbox.

wubi= linux into a windows file  , something strange no ?

---

### Post by Maz7006 on 2010-05-02
> **dino99 said:**
> 

wubi= linux into a windows file  , something strange no ?

Strange, hence my inquiry. 

Just tried this, works like a charm. No need with messing with partitions anymore. THanks for all the replies.

---

### Post by horse_dung on 2010-05-02
Check out this thread if you would like to run both your Windows and WUBI side-by-side at the same time...!  This is a BETA release and I'm looking for testers.

[http://ubuntuforums.org/showthread.php?p=9221317#post9221317](http://ubuntuforums.org/showthread.php?p=9221317#post9221317)

---

