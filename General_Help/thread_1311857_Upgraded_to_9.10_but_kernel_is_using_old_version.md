---
title: "Upgraded to 9.10 but kernel is using old version"
date: 2009-11-02
forum: General Help
---

### Post by psidrum on 2009-11-02
how do i change my kernel so it uses the new one?

i upgraded using the Update Manager, and i just found out my system is still using the old kernel, how do i use the new one?

---

### Post by ranch hand on 2009-11-02
Please send results of;
```

install-grub -v

```
so we know what we are working with.

---

### Post by gadolinio on 2009-11-02
> **psidrum said:**
> how do i change my kernel so it uses the new one?

i upgraded using the Update Manager, and i just found out my system is still using the old kernel, how do i use the new one?

Install the package called **startupmanager**. Then go to system-->administration-->startup manager. The main tab has a list under the label "default operative system", where you can select the kernel you want to start with, from the ones installed.

---

### Post by ranch hand on 2009-11-02
Start up manager is not really thething to use yet with grub2.

Let us find out what the OP is using before we cause problems that are not needed.

---

### Post by psidrum on 2009-11-02
> **ranch hand said:**
> Please send results of;
```

install-grub -v

```so we know what we are working with.


it came back with a 

"install-grub: command not found
"

---

### Post by psidrum on 2009-11-02
> **gadolinio said:**
> Install the package called **startupmanager**. Then go to system-->administration-->startup manager. The main tab has a list under the label "default operative system", where you can select the kernel you want to start with, from the ones installed.


i only see 9.04 kernels theres no 9.10 available,

---

### Post by psidrum on 2009-11-02
[IMG]http://img249.imageshack.us/img249/3351/screenshotsysinfo.png[/IMG]

---

### Post by ranch hand on 2009-11-02
OK, look in synaptic and search for linux.

This should take you to where the kernels are listed.  See what is there.

Should be 2.6.31, if you have 9.10 installed, listed there as installed.

Also search for grub and look at grub-pc and make sure it is not installed.

If those 2 things are true then startupmanager (that is how it is listed in synaptic) is a good bet to do the job for you.

---

### Post by timothydonohue on 2009-11-02
> **ranch hand said:**
> OK, look in synaptic and search for linux.

This should take you to where the kernels are listed.  See what is there.

Should be 2.6.31, if you have 9.10 installed, listed there as installed.

Also search for grub and look at grub-pc and make sure it is not installed.

If those 2 things are true then startupmanager (that is how it is listed in synaptic) is a good bet to do the job for you.


i'm having the same problem as this person is.  i upgraded to 9.10, but ubuntu is using the old kernel, which i can only assume is also responsible for the fact that now i have absolutely no sound, and all internet traffic is slooooooow as mud now  :/

i installed the new kernel using synaptic, but it still isn't a selectable option in my newly installed startupmanager.

any help would be appreciated

---

### Post by ranch hand on 2009-11-02
It might be a real good idea for both of you to run;
```

dpkg --configure -a

```
and see what happens.

I think your install hung on something and you missed the warning notice somehow.

---

### Post by timothydonohue on 2009-11-02
> **ranch hand said:**
> It might be a real good idea for both of you to run;
```

dpkg --configure -a

```
and see what happens.

I think your install hung on something and you missed the warning notice somehow.

i'm not sure what happened, but i just made a new live cd, deleted all of my linux partitions from the windows disk management, and reinstalled.  no problems now whatsoever, and now my sound is back, and apparently under a better device manager than pulseaudio, because i could natively select 5.1 sound without editing configuration files.  

muy bueno.  dig the new dist, now that it seems to function.

i think my problem was that i had agreed to keep some files the same (a menu.something comes to mind, of a few that came up).  so, not sure why i couldn't select the new kernel before, but everything seems to be hunky dorey now.  only files i lost in the partition deletion were files i didn't really need to have anyway, or else i would have backed them up to external HD first.

yay!

---

### Post by psidrum on 2009-11-03
> **timothydonohue said:**
> i think my problem was that i had agreed to keep some files the same (a menu.something comes to mind, of a few that came up).

I did the same thing, when it asked the same question regarding the menu after everything was installed,

i chose to keep the old menu.lst

---

### Post by psidrum on 2009-11-03
> **ranch hand said:**
> OK, look in synaptic and search for linux.

This should take you to where the kernels are listed.  See what is there.

Should be 2.6.31, if you have 9.10 installed, listed there as installed.

Also search for grub and look at grub-pc and make sure it is not installed.

If those 2 things are true then startupmanager (that is how it is listed in synaptic) is a good bet to do the job for you.


i installed grub-pc since 2.6.31 was already installed, after booting up, my audio started working again, it also read my SB X-Fi card and it is now using the 2.6.31 kernel, thanks!!

the only problem i have now is that my graphic driver is set to default, i cant use compiz 3d cube, 

Xorg version says unknown,

im using ATI Radeon X1600

---

