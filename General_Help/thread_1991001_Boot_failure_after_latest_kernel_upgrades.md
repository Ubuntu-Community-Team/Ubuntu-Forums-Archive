---
title: "Boot failure after latest kernel upgrades"
date: 2012-05-30
forum: General Help
---

### Post by Katla on 2012-05-30
First off, a little bit of history, as I am unsure what exactly my issue is and have had a few since upgrading to 12.04:

During the upgrade process I ran out of room on my drive, despite the prior scan coming back clear, and the installation was canceled. This worried me, but I was able to clear room and complete the upgrade via the terminal. Maybe. 

The reason for the maybe is that I was getting a lot of error messages on start-up and was afraid to reboot as sometimes it took a few attempts before taking. I'd also get a long string of error messages when shutting down. They'd scroll by too fast to read, but looked to be all the same, or very similar. Something about Radeon and "failure to allocate". That, together with problems with VLC not working as it should, as well as games having ridiculously low framerates led me to believe it was something to do with my graphics card drivers. I made a note to get that solved, but it wasn't a major concern. 

Then, last week, I ran an auto-update that included kernels. Rebooting my machine I was unable to get Unity up. It would come up with my wallpaper and give me hope, but then drop into error messages. This was different than my previous problem in booting, as before it wouldn't go to an error screen, just maybe take a few times to start up. Anyway, after rebooting 4-5 times, feeling desperate, I finally got Unity up and running. No apparent issues aside from what was already known. I've not shut down since then as I am afraid to. 

The error message I get on start-up is pretty long, and not always the same. I don't know how to copy it or where to find its logs, so all I've got for now is what seemed to be the main gist of it.

> Bug: unable to handle kernel paging request at 00f19c28 
Corrupted/bad page table

I realize this is all rather vague, and not much to go on, but I am hoping with some investigation we can get to the root of it, at least to where I have some measure of faith that my machine will reboot. Any help is greatly appreciated, Thank you.

---

### Post by anonymous5 on 2012-05-30
> **Katla said:**
> First off, a little bit of history, as I am unsure what exactly my issue is and have had a few since upgrading to 12.04:

During the upgrade process I ran out of room on my drive, despite the prior scan coming back clear, and the installation was canceled. This worried me, but I was able to clear room and complete the upgrade via the terminal. Maybe. 

The reason for the maybe is that I was getting a lot of error messages on start-up and was afraid to reboot as sometimes it took a few attempts before taking. I'd also get a long string of error messages when shutting down. They'd scroll by too fast to read, but looked to be all the same, or very similar. Something about Radeon and "failure to allocate". That, together with problems with VLC not working as it should, as well as games having ridiculously low framerates led me to believe it was something to do with my graphics card drivers. I made a note to get that solved, but it wasn't a major concern. 

Then, last week, I ran an auto-update that included kernels. Rebooting my machine I was unable to get Unity up. It would come up with my wallpaper and give me hope, but then drop into error messages. This was different than my previous problem in booting, as before it wouldn't go to an error screen, just maybe take a few times to start up. Anyway, after rebooting 4-5 times, feeling desperate, I finally got Unity up and running. No apparent issues aside from what was already known. I've not shut down since then as I am afraid to. 

The error message I get on start-up is pretty long, and not always the same. I don't know how to copy it or where to find its logs, so all I've got for now is what seemed to be the main gist of it.



I realize this is all rather vague, and not much to go on, but I am hoping with some investigation we can get to the root of it, at least to where I have some measure of faith that my machine will reboot. Any help is greatly appreciated, Thank you.

If you're using grub2, look in /boot/ and see if you still have the old kernel. If yes, then run `update-grub`, so that the kernels will be listed at startup and you can choose which one to use.

---

### Post by kc1di on 2012-05-30
Can  you get to a terminal?
if you can please run the following commands and let us know the output.

```
uname -r
``` This will tell us what kernel is in use.

```
grep menuentry /boot/grub/grub.cfg
```this will tell us
what kernels are available to grub.

```
lspci | grep VGA
``` this will tell us what video card your machine has.  This may be important as there have been some problems with some video cards in 12.04.

that's a start. we will go from there. 
if you can just copy and past the output of the terminal it would be of help. Use the code button on the forum reply for the pasted items. thanks

---

### Post by Katla on 2012-05-30
```
3.2.0-24-generic-pae
```

```
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
```

 ```
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690 [Radeon X1200 Series]
```

As a note on that last: the driver I have listed is "Gallium 0.4 on llvmpipe (LLVM 0x300)". I assume I want to be using an ATI driver, but any documentation I've seen on it leaves me a little confused and nervous.

---

### Post by kc1di on 2012-05-30
I'm on my way out the door in a moment.
but you do not have 3.4 installed if you want to get rid of the 3.0 and 2.6 kernels you don't really need them at the moment 
you can do so by going to the terminal and type:

```
sudo apt-get purge kernel 3.2.0-24-generic
```

---

### Post by Katla on 2012-05-30
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-24-generic' for regex '3.2.0-24-generic'
Note, selecting 'linux-headers-3.2.0-24-generic' for regex '3.2.0-24-generic'
Note, selecting 'linux-image-3.2.0-24-generic' for regex '3.2.0-24-generic'
Note, selecting 'linux-image-3.2.0-24-generic-pae' for regex '3.2.0-24-generic'
Note, selecting 'linux-headers-lbm-3.2.0-24-generic' for regex '3.2.0-24-generic'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-24-generic-pae' for regex '3.2.0-24-generic'
Note, selecting 'linux-backports-modules-net-3.2.0-24-generic-pae' for regex '3.2.0-24-generic'
Note, selecting 'linux-backports-modules-net-3.2.0-24-generic' for regex '3.2.0-24-generic'
Note, selecting 'linux-headers-lbm-3.2.0-24-generic-pae' for regex '3.2.0-24-generic'
Note, selecting 'linux-headers-3.2.0-24-generic-pae' for regex '3.2.0-24-generic'
**E: Unable to locate package kernel**

```

---

### Post by Katla on 2012-06-02
Bump.

---

