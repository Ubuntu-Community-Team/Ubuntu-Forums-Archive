---
title: "Royally screwed up- edited the sudoers file"
date: 2011-01-03
forum: General Help
---

### Post by cwgosling on 2011-01-03
I was getting some long distance help from a friend tonight. He suggested modifying the doers file so that I didn't have to enter the sudo command and password every time. I misunderstood the advice and edited the /etc/sudoers file directly. In line 21 I changed "=ALL" to "=chris" (my username). I have since learned that this was the wrong way to go about this. Now I'm trying to fix it. I can't run sudo, every time it gives me an error that reads:

no valid sudoers sources found, quitting

I've read a few threads and am now rebooted in recovery mode. I still can't run sudo without errors. Other threads address using chmod to change the properties of the file, but I need to edit the text itself or replace the file with a functional version. Any ideas? Looking to be a long night.... some guidance to a Linux neophyte would be much appreciated.

Thanks,
Chris

---

### Post by cipherboy_loc on 2011-01-03
> **cwgosling said:**
> I was getting some long distance help from a friend tonight. He suggested modifying the doers file so that I didn't have to enter the sudo command and password every time. I misunderstood the advice and edited the /etc/sudoers file directly. In line 21 I changed "=ALL" to "=chris" (my username). I have since learned that this was the wrong way to go about this. Now I'm trying to fix it. I can't run sudo, every time it gives me an error that reads:

no valid sudoers sources found, quitting

I've read a few threads and am now rebooted in recovery mode. I still can't run sudo without errors. Other threads address using chmod to change the properties of the file, but I need to edit the text itself or replace the file with a functional version. Any ideas? Looking to be a long night.... some guidance to a Linux neophyte would be much appreciated.

Thanks,
Chris

If you have a copy of ANY Ubuntu LiveCD around, then boot it up (from the CD) to the desktop, and mount your Ubuntu install partition, and then:

```

sudo su
cd /path/to/ubuntu/etc/
cp sudoers.bak sudoers

```

Reboot into the desktop. This assumes you did not edit the sudoers file again.



Cipherboy

---

### Post by cwgosling on 2011-01-03
That's the problem- no copy of the LiveCD handy. I'll track one down tomorrow and see if I can fix this mess. Thanks for the help- I really appreciate it. 
-Chris

---

### Post by cipherboy_loc on 2011-01-03
I know you can download the LiveCD, I just don't know if you can burn it without needing sudo/su access. Did you happen to change the Root password? You can do something similar with root access:

```

cp /etc/sudoers.bak /etc/sudoers

```


Cipherboy
> **cwgosling said:**
> That's the problem- no copy of the LiveCD handy. I'll track one down tomorrow and see if I can fix this mess. Thanks for the help- I really appreciate it. 
-Chris

---

### Post by WorMzy on 2011-01-03
Read this: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

In the future, only edit the sudoers file with

```
sudo visudo
```

That method will tell you if your changes will have this effect.

---

### Post by cwgosling on 2011-01-03
Thanks to both of you for the help. 

cipherboy_loc: I didn't change the root password, so I can't go that route. Wish I had. I'll make a new LiveCD tomorrow.

WorMzy: thanks for the link. Makes much more sense now. I've certainly learned my lesson...

Hope to be able to mark this thread as solved tomorrow.

---

### Post by cwgosling on 2011-01-04
I burned a new Ubuntu LiveCD today so that I could fix the sudoers file. I just booted from the cd. The Ubuntu logo with the 5 dots came up and everything looked like it was going fine. Now all I've got is a black screen with one line of text:

(process:365): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

Any ideas?

Thanks!
Chris

---

### Post by WorMzy on 2011-01-04
Re-read the link I posted, it explains how to fix sudoers from recovery mode (you don't need a LiveCD).

---

### Post by cwgosling on 2011-01-04
WorMzy: I read your entire link and tried it last night. I believe I'm in what's described as Case 2, but I tried the instructions for case 1 as well. The message that was returned was: 'chris' is already a member of 'admin'

Case 2:
The problem is that when I try to enter:
sudo cp /etc/sudoers /etc/sudoers.backup

I get an error message that reads:

sudo: parse error in /etc/sudoers near line 21
sudo: no valid sudoers sources found, quitting

Since I'm not getting an error message associated with a Mode I didn't try Case 3. 

So I'm at an impasse- the instructions that try to solve the problem without using a LiveCD aren't working, and booting from a LiveCD doesn't work either. 

Other ideas?

Thanks again everyone for your help.
-Chris

---

### Post by matt_symes on 2011-01-04
Hi

Boot into the recovery console to do it. You do not need the LiveCD. Reboot your PC and choose recovery mode from your grub menu. It will look something like

> Ubuntu, with Linux 2.6.35-22-generic (recovery mode) 

(this is one of mine. Yours may differ)

From there you can drop into a root shell and fix it that way. In a root shell you automatically have root privilages.

Kind regards

---

### Post by lithopsian on 2011-01-04
Hope you remember your root password ;)

---

### Post by cwgosling on 2011-01-04
I figured it out using the root shell. If it helps anyone else, I had to use the following line to get the sudoers file to open for editing:

visudo -f /etc/sudoers

Thanks everyone for your help. 

Cheers!
Chris

---

### Post by cwgosling on 2011-01-04
lithopsian-

I don't remember ever changing the root password and have no idea what it is- that was part of the problem. Hopefully this is behind me for now, but I definitely need to do that. 

Thanks,
Chris

---

### Post by hawkmage on 2011-01-04
Also doing with the Live CD is easy.

1: Boot the the Live CD.
2: Open a bash shell
3: Run the command "sudo fdisk -l"
4: Find the the root partition from the list.  Lets say it was /dev/sda2
5: Mount the partition: sudo mount /dev/sda2 /mnt
6: Edit the sudoers file: sudo vi /mnt/etc/sudoers
7: Fix the error and save. (you will need to use wq! to force the save and exit and not just wq)
8: reboot normily

Note: sudo on the Live CD doesn't require a password.

---

