---
title: "Wubi and SWAP problem. Ubuntu 11.04"
date: 2011-05-17
forum: General Help
---

### Post by Patucman on 2011-05-17
I've read this thread...

[http://ubuntuforums.org/showthread.php?t=1275962](http://ubuntuforums.org/showthread.php?t=1275962)

[SIZE="3"]And i've got a similar problem installing Ubuntu with Wubi...[/SIZE]

[B]Checkin the memory with "free -m"...i've seen that Wubi gave me 256Mb for SWAP area...the problem is that i need more SWAP cuz i have 1Gb RAM(at this moment i have 80Mb of SWAP used, RAM 977Mb used).
I was looking for help, and ppl said me i'll need make a file SWAP...but i want install again if i can get a better installation using Wubi and select how much SWAP i want... (Cannot follow other way for this PC). I tried with USB bootable but this f**** machine don't want boot from USB-HDD.
I've installed Ubuntu from Wubi, but first i've created a new partition with 30Gb from Windows with his Manager...and installed Ubuntu there.[/B]

[COLOR="YellowGreen"][SIZE="4"][FONT="Arial"]Please...help me. :([/FONT][/SIZE][/COLOR]

---

### Post by bcbc on 2011-05-18
You can increase the swap on a Wubi install as described [here]("https://wiki.ubuntu.com/WubiGuide#How do I increase my swap space?").

With Wubi you cannot specify swap size at install time. Since you're not using all the existing swap that you have, I've not sure what the issue is. Maybe you can explain that more clearly.

---

### Post by Patucman on 2011-05-18
> **bcbc said:**
> You can increase the swap on a Wubi install as described [here]("https://wiki.ubuntu.com/WubiGuide#How do I increase my swap space?").

With Wubi you cannot specify swap size at install time. Since you're not using all the existing swap that you have, I've not sure what the issue is. Maybe you can explain that more clearly.

Mmmmm...i explained clearly, dude.
Well...here we go.

Logic Partitions : 3
1st: C\ type:NTFS
2nd: D\ type:NTFS
3th: Ubuntu\ type:NTFS

3th Partition have 30 Gb and i installed Ubuntu there, with Wubi.
Now, checkin my memory and partitions with Ubuntu using the "free -m" command, i see this:
 

Total RAM: 997Mb
Total SWAP: 255Mb (now 755 after checked ur link, can't get more)

That means, Wubi asigned only 255Mb for SWAP area...now the OS isn't working with SWAP, but there are moments when Ubuntu begs for more SWAP because RAM can't support it.

---

### Post by bcbc on 2011-05-18
okay... Ubuntu needs more swap. Got it!

You have installed Ubuntu on a 30GB partition and I assume allocated nearly all of that to Ubuntu (so the root.disk is 28 or 29GB?). And you don't have space to create a bigger swap file?

And there's a reason that you want Wubi, because you can't boot from USB on that machine, and I assume no CD drive either... because obviously in this case a native install is better (uses less RAM than Wubi and you can have a real swap partition).

1. So what can you do - reinstall with a smaller root.disk and then create a large swap file manually. 
2. Delete the hidden desktop CD image (\ubuntu\install\.fuse_hidden4000...) to make room for a bigger swap.disk 
3. Reinstall on C: or D: (choose a 3GB root disk), use GParted to delete and replace the third ntfs partition as two logical, one for root and one for swap and then [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi to it. (The size of the root.disk doesn't matter and it's quicker with a 3GB one).

Those are some ideas. 2 is the quickest. 3 is a workaround way to install Ubuntu natively without the use of a CD or USB (it's a good idea to have one of these as a repair disk - so I wouldn't normally recommend this) - but for the long term, it's best to have a direct install.

Edit: warning - if you don't have some way of booting an ubuntu or windows recovery disk, then using the technique in 3. is NOT advised. Even a simple grub failure will not be fixable and could leave your computer unbootable

---

### Post by Patucman on 2011-05-19
Mmmmmm...sounds like a hard work. :s
I'll try ask to my friend to borrow me his DVD recorder, and install again without Wubi.

If he accept...Can I make a backup file for all my configs in Ubuntu? I mean, libs, compiz, apps, etc...(without the SWAP config)?
LOL, i'm asking too much...sorry xD
I'm using Ubuntu Natty Narwhal.

---

### Post by bcbc on 2011-05-19
Have a look at this thread [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) (scroll down and look for the "Alternate Instructions" that show how to copy /home and get a list of packages to reinstall.)

---

