---
title: "Dual boot 11.10 and 12.04"
date: 2011-11-25
forum: General Help
---

### Post by CaptainMark on 2011-11-25
Ive been plodding along quite happily dual booting between Natty and 12.04 since 11.10 was released, (i stuck with Natty because i found 11.10 too unstable for general use) now enough of the bugs have been ironed out of 11.10 for my liking so i got a live cd and installed 11.10 over Natty, I wish i hadnt because now I cant get into my 12.04 install, its in the grub menu but then just sits there with a blinking cursor, Ive never had dual boot issues before so dont know much about what to do when it doesnt work, ive tried some guides online but cant make sense of them honestly, can anyone be patient enough to talk me through it, heres a pic of my partition setup 
sda1 is my 11.10 install
sda3 is my 12.04 install
sda5 is my home partition
sda6 is swap

---

### Post by jjex22 on 2011-11-25
Hi there, have you tried 

Sudo update-grub

If this doesn't work ,it could possibly be caused by the change in partition numbering in Grub 2 - edit the grub.cfg file to make sure it's pointing to the right partition - probably hd(0,3) - just try adding one to the entry it has as grub used to start from 0, now it starts from 1? if still no luck ,try posting the grub.cfg

---

### Post by raja.genupula on 2011-11-25
Hi man install boot repair and try again from that 
and manager your grub from grub customizer ,

you can get both things from My signature.

all the best.

---

### Post by CaptainMark on 2011-11-25
sudo update-grub isnt doing anything, i did already try that one, trying boot-repair now

---

### Post by drs305 on 2011-11-25
A blinking cursor isn't a normally a sign of Grub problems unless it has an error message associated with it. It is often a video problem after Grub has passed control to the kernel.

One common solution is to remove 'quiet splash' and add 'nomodeset' to the "linux" line of the Grub menuentry. Start the edit mode by pressing 'e' and use the cursor keys to navigate the menuentry. Once you have made the change, press CTRL-x to boot.

If it boots, try adding your video driver.

---

### Post by CaptainMark on 2011-11-25
boot-repairs recommended fix didnt help, it gave me this pastebin link  [http://paste.ubuntu.com/749610/](http://paste.ubuntu.com/749610/) it detected 12.04 okay, ill try and drs305's idea

---

### Post by CaptainMark on 2011-11-25
great thanks, the problem was there was an message
error mounting /dev/sda1 in /mnt/stable_install because the device was not ready
or something much to that effect, but i couldnt see it, i skipped the mounting and commented out the line for this in /etc/fstab for now, is there any reason why it would not be able to mount it on boot, once booted i can run 'sudo mount /dev/sda1 /mnt/stable_install' and it mounts no problem

---

### Post by drs305 on 2011-11-25
> **CaptainMark said:**
> okay there is no entry for quiet splash, do i literally just add nomodeset to the end of this line or is there some specific syntax to use?

Yes, just add "nomodeset" without the quotes.

I don't have time to look at the RESULTS.txt but will return later to check it.

---

### Post by oldfred on 2011-11-25
This is what you should be seeing or similar for 12.04 with the newer kernel:

> linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=796831a8-703d-4f5a-a02f-f1af12de5d3e ro   quiet splash vt.handoff=7

---

### Post by CaptainMark on 2011-11-25
yes i did, i done as you said, i edited my last post must have been at the same time as you were both posting, see my last post, thanks for the help so far

---

