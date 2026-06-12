---
title: "sudo password for 'persistent' install on flash drive?"
date: 2012-04-17
forum: General Help
---

### Post by fiestaforever on 2012-04-17
Hi, 

I installed Xubuntu 11.10 on a USB flash drive (stick) as a 'persistent' live system, and I want to make it ask for the user password on 'sudo'. 
On examining /etc/sudoers, I noticed that there were *lots* of lines 
"# Members of the admin group may gain root privileges 
%admin ALL=(ALL) NOPASSWD: ALL"
I deleted most of them, and changed the first and last instance to 
"%admin ALL=(ALL) ALL". 
This worked (although I'm still not completely familiar with the syntax), and I was asked for a password the next time. 

But it didn't survive a reboot. 
After the reboot, I could sudo again w/o password. 
In /etc/sudoers, both instances had been switched back to 
"%admin ALL=(ALL) NOPASSWD: ALL"
Something must have overwritten my changes. It clearly hadn't simply reverted back to the 'original' file, because there were still only those two instances, no more. 

What is overriding my changes, and how can I make it stop? 

I'm actually a little surprised I couldn't find a thread on that subject.

BTW: I had a *lot* of problems with these 'persistent' live sticks, had 3 installs break within days (on 3 different sticks, and breaking in different ways, mostly known bugs). Now I keep copying and shuffeling casper-rw around different sticks.

BTW (2): Editor doesn't work correctly for me (no bold/italic).

Thanks in advance for help.
Alex

---

### Post by wojox on 2012-04-17
Did you try:
```
sudo passwd fiestaforever
```

Also are you using visudo to edit sudoers?

---

### Post by fiestaforever on 2012-04-17
> **wojox said:**
> Did you try:
```
sudo passwd fiestaforever
```
Yes. Doesn't make a difference. I'm not even sure it remembers the pw beyond reboot.
Edit: No, it doesn't. I can log out and back in w/o password. The password I had set seems to be gone.

> Also are you using visudo to edit sudoers?
Yes. And I just noticed that the proliferation of 
"%admin ALL=(ALL) NOPASSWD: ALL" in /etc/sudoers has happened again. 
There are already at least six such lines in there again now.

---

### Post by wojox on 2012-04-18
What user name do you have? You changed it from "ubuntu"? You can save other files on the drive?

---

### Post by Cheesemill on 2012-04-18
This is why I don't go for persistent bootable USB drives.

Instead I just do a normal full installation onto the USB drive, this way it acts exactly the same as a regular installation.

---

### Post by fiestaforever on 2012-04-18
> **wojox said:**
> What user name do you have? You changed it from "ubuntu"? 
No. Although I *do** consider this generic username a security risk.

> You can save other files on the drive?
Yes. You're probably after whether persistence in general works. :)
It does. 
(Another thing that doesn't work at all, though, is the trash: Everything is deleted immediately.)

* Surprisingly, italics do work now in the editor.

---

### Post by fiestaforever on 2012-04-18
> **Cheesemill said:**
> I just do a normal full installation onto the USB drive, this way it acts exactly the same as a regular installation.
This, I'm afraid, will wear out a USB (flash) drive quite quickly. With a USB hdd, I'd probably also do a normal install. It's just that a hdd wont't fit on my key ring easily ;)

---

### Post by Cheesemill on 2012-04-18
> **fiestaforever said:**
> This, I'm afraid, will wear out a USB (flash) drive quite quickly. With a USB hdd, I'd probably also do a normal install. It's just that a hdd wont't fit on my key ring easily ;)

Not if you use a file system which doesn't use journalling such as ext2.
Alternatively you can use ext4 and switch off journalling (this is the method I use).
This way you won't do any more writes to the USB than you would do using a casper-rw file.
You also have the advantage of being able to update the entire installation including the kernel which you can't do with a persistent installation.

---

### Post by fiestaforever on 2012-04-20
To my knowledge, journaling isn't the only thing wearing out the flash drive. Swap would be another reason. 'Live' systems don't use a swap file, AFAIK.

Anyone able to give more hints on the original question?

---

