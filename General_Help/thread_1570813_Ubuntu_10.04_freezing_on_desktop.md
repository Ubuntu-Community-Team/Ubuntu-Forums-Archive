---
title: "Ubuntu 10.04 freezing on desktop"
date: 2010-09-08
forum: General Help
---

### Post by james182 on 2010-09-08
Hi I am having trouble with my ubuntu 10.04. 
I did an update, but something stuffed up and it only did a partial update. But when I've gone to continue the update it seemed to stop half way and just hang. I had to force shut down but now when I boot up I gets to the desktop and just freezes keyboard and mouse included. 

How do I fix this?

---

### Post by NightwishFan on 2010-09-08
Hold shift while booting and you will get a menu that allows you to choose "Recovery Mode". Do so, and after boot you will be at a blue screen with options. Choose "Root Prompt with Networking" (or similar I forget the exact wording). Please run these commands EXACTLY, one at a time:
```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install ubuntu-desktop
```

Then run:
```
init 0
```

Start back up your machine, and see if you can boot to a desktop.

---

### Post by james182 on 2010-09-09
unfortunately the recovery only sort of worked attached are the images of me selecting the recovery option, and the next image is after the that selection. it just stays on that screen forever (img_034).

Any help

don't get to that blue screen ...

---

### Post by NightwishFan on 2010-09-09
Try the older kernel.

---

### Post by james182 on 2010-09-09
I have tried both and it does the same.

---

### Post by davidmohammed on 2010-09-09
what graphics card do you have?

Maybe you have to use one of the following kernel boot options through grub

nomodeset
i915.modeset=1
i915.modeset=0

---

### Post by NightwishFan on 2010-09-09
The recovery mode should still boot regardless. So if it does not, the problem is not with X. You can try to edit the option for recovery mode with E, go to the line titled "Kernel" and at the end add a space and then: nomodeset

---

### Post by james182 on 2010-09-10
i'm not seeing "kernal" this is all i get. see photo

When i do boot to the desktop the keyboard and mouse don't work, they use to until the update.

---

### Post by NightwishFan on 2010-09-10
My mistake.. Linux. The line that starts with Linux, push end and append what I asked.

---

### Post by james182 on 2010-09-10
How long should it sit on the black screen for (previous IMG 034)?

i added what you said so i looks like this:

linux /boot/vmlinuz-2.6.32-21-generic root=UUID=053a7ae4-da55-42f9-b\7e1-06a5e2cf8d22 ro single **nomodeset**

Still No Joy ... :(

---

### Post by NightwishFan on 2010-09-10
Push  ctrl+x to boot. Still no joy? You can try replacing nomodeset with the following. See if that gets you going.
```
nosmp acpi=off
```

---

### Post by james182 on 2010-09-11
still no joy! 

What other options do i have ? i have data on this machine i need to get off!

Netbook is a Asus EeePC running Ubuntu 10.04.

---

### Post by james182 on 2010-09-13
bump

---

