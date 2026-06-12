---
title: "How to extract data from encrypted home partition without booting it"
date: 2010-07-17
forum: General Help
---

### Post by Potters Son on 2010-07-17
OK, here's the deal:

Around six months ago (last time I reinstalled Ubuntu 9.10), on a whim I decided to check that option to "encrypt [my] home directory". I wanted to see what it was like. Mistake. Since then, I've been unable to figure out how to access the data in my home directory using any method besides booting the computer (usb drive, rip-out-and-stick-it-in-an-enclosure, etc.). Specifically, I find that shell script sitting there that tells you to run it in order to see your files, but it gives some kind of error. I also still have the code Ubuntu tells you to write down in order to decrypt your files.

Fast forward to this past week. I brought in the laptop to Best Buy for repairs to the hinge (the hinge! Ace Hardware could fix this problem! But I wanted to make full use of the service plan.), and I got a phone call a few days later, saying that it hit Best Buy's "No Lemon" policy. They were going to keep my computer and give me in-store credit toward a new one. Of course, I refused to pay ~$70 for them to back up my data for me; what could possibly happen to it when they were fixing a hardware problem?

Anyways, I pleaded with them for my hard drive back, and they said that they could ship the hard drive back to the store so I could get my data off of it. I'm planning on going in there with my external backup hard drive and an external enclosure and doing it myself at the counter (If they charge $70 to back up a Windows partition, how much more will they charge for an encrypted Linux one?). I don't want to embarrass myself by standing around and not being able to get into my own data.

---

### Post by HeadHunter00 on 2010-07-17
I have never had any experience with encrypted folders. I think you can try using your ubuntu live cd, mount the filesystem, and use```
gksu nautilus
``` to change permissions so its not encrypted anymore. i will try encryting a foler and see myself how to hack it. if you need to, you can always add another user with adduser command.

---

### Post by HeadHunter00 on 2010-07-17
I got it. I found a fix. Here's what you need to do:
i) Boot from the live cd.
ii) Mount your harddisk.
iii) Open terminal.
iv) Then, cd /whatever/it/shows/for/harddrive/in/the/navigation/bar/
v) After that, type this code: sudo unmount [I]Name of Home folder
[/I]vi) Type this code: sudo chmod -R 777 [I]Name of Home folder
[/I]vii) Enjoy.

---

### Post by HeadHunter00 on 2010-07-17
btw, trust me DONT get it decrypted from best buy. they wont be able to access the drive and you will still be charged. ntfs is much more different from the linux filesystems like ext3 and ext4.

---

### Post by Potters Son on 2010-07-17
Thanks, HeadHunter00, although I'm surprised that it's as simple as changing the permissions on the folder. I thought I had to do some sort of mounting and decrypting.

---

### Post by HeadHunter00 on 2010-07-17
No probs. Remember, dont ever go ask the popular stores like best buy to fix linux stuff. they are amateurs.

---

### Post by Potters Son on 2010-07-18
I never do. :)

I do, however, make them help me with hardware.

---

### Post by jrider on 2010-07-18
From [http://www.linux-mag.com/id/7568](http://www.linux-mag.com/id/7568) 

```
Recovery of an Encrypted Home Directory is possible from an Ubuntu 9.10 LiveCD.

Mount the disk partition containing the Encrypted Home Directory:

ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
Establish a proper chroot environment:

ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu$ sudo chroot /mnt
Become the user whose data needs recovery (i.e. “foo”) and manually add the necessary mount passphrase to the kernel session keyring:

root@ubuntu$ su – foo
foo@ubuntu$ ecryptfs-add-passphrase --fnek
Passphrase:
<Enter the recorded passphrase>
Mount the encrypted directory and then access the data:

foo@ubuntu$ ecryptfs-mount-private
foo@ubuntu$ cd $HOME
foo@ubuntu$ ls -alF

```

---

