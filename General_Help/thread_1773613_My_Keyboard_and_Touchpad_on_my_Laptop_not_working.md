---
title: "My Keyboard and Touchpad on my Laptop not working"
date: 2011-06-02
forum: General Help
---

### Post by aldee96 on 2011-06-02
I was going to render the video that i made last night, and then in the morning, My ubuntu 10.10 boot normally, but when in the Ubuntu plymouth(the ubuntu logo with 5 dots) showed, there are text told me like this 

```
Keys: Press S to skip Mounting or M for manual Recovery
```since that moment my keyboard and touchpad are not working, but if i use an external keyboard and mouse it would working flawlessly, note that i don't have an external keyboard.

i'm trying to boot into recovery mode, my keyboard is working very good, but i don't have any idea what is the problem.

i did no updates, so i think that's not he problem

PS; I'm using macbuntu UI modification

---

### Post by aldee96 on 2011-06-02
i need some help please :(

---

### Post by z0mmer on 2011-06-06
Hi yesterday i installed ubuntu from official site to my netbook "Gateway",  and have the same problem. Tryed to connect usb mouse but it not working correctly too.:(

---

### Post by aldee96 on 2011-06-09
when using usb mouse it working flawlessly, my problem is a little bit different with yours

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **aldee96 said:**
> I was going to render the video that i made last night, and then in the morning, My ubuntu 10.10 boot normally, but when in the Ubuntu plymouth(the ubuntu logo with 5 dots) showed, there are text told me like this 

```
Keys: Press S to skip Mounting or M for manual Recovery
```since that moment my keyboard and touchpad are not working, but if i use an external keyboard and mouse it would working flawlessly, note that i don't have an external keyboard.

i'm trying to boot into recovery mode, my keyboard is working very good, but i don't have any idea what is the problem.

i did no updates, so i think that's not he problem

PS; I'm using macbuntu UI modification

I would check /etc/fstab and I would check the logs to see if there is anything strange going on with your system. 

Also do a hard drive checkup with Disk Utility.  Check the SMART Status and see the condition of your hard drive.

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **aldee96 said:**
> when using usb mouse it working flawlessly, my problem is a little bit different with yours

What kind of computer is this? Make and model?  Any upgrades to it?

---

### Post by bleedingpowers on 2011-06-12
I'm facing a similar situation on a HP TouchSmart tm2. The usb mouse, keyboard, and touchscreen stop working after resuming from a suspend. This started happening right after I upgraded to Natty.

**Update:** I realized that the problem seems to be more like a power problem since modules unload and reload properly after suspend/resume-from-suspend. There's got to be another reason for this to be happening. The usb modules (usb_hid, usb_storage) seem to work, but the power on the hub seems gone.

---

### Post by aldee96 on 2011-06-16
> **linuxinstalledfromhdd said:**
> What kind of computer is this? Make and model?  Any upgrades to it?

it's Sony VAIO VGN-CR11GH-L

---

### Post by aldee96 on 2011-06-16
> > **aldee96 said:**
> I was going to render the video that i made last night, and then in the morning, My ubuntu 10.10 boot normally, but when in the Ubuntu plymouth(the ubuntu logo with 5 dots) showed, there are text told me like this 

```
Keys: Press S to skip Mounting or M for manual Recovery
```since that moment my keyboard and touchpad are not working, but if i use an external keyboard and mouse it would working flawlessly, note that i don't have an external keyboard.

i'm trying to boot into recovery mode, my keyboard is working very good, but i don't have any idea what is the problem.

i did no updates, so i think that's not he problem

PS; I'm using macbuntu UI modification

> **linuxinstalledfromhdd said:**
> I would check /etc/fstab and I  would check the logs to see if there is anything strange going on with  your system. 

Also do a hard drive checkup with Disk Utility.  Check the SMART Status and see the condition of your hard drive.

How do i did that? I can't even login into my ubuntu account without keyboard, i think the solutions is through recovery mode, but how?

---

### Post by Mark Phelps on 2011-06-16
> How do i did that? I can't even login into my ubuntu account without keyboard, i think the solutions is through recovery mode, but how?

> but if i use an external keyboard and mouse it would working flawlessly, note that i don't have an external keyboard.

You will need to use an external keyboard -- which you claim works flawlessly -- even though you said you don't have one!

---

