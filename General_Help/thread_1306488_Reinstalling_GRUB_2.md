---
title: "Reinstalling GRUB 2"
date: 2009-10-30
forum: General Help
---

### Post by besweeet on 2009-10-30
I'm just about to lose my ******* mind over here. I CAN'T FIND ANYTHING ANYWHERE ONLINE THAT TELLS ME HOW TO INSTALL GRUB 2!!!!! I originally had it installed fro Ubuntu 9.10, but it wouldn't boot Windows 7, so I reinstalled the Windows boot loader from the DVD, but now I can't boot into Ubuntu! So, I want to try GRUB 2 again. ANYONE?! There has to be some way to get it back on here without reinstalling!!!!!

---

### Post by wojox on 2009-10-30
Sounds like a vicious circle. Here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by besweeet on 2009-10-30
I'm at the reinstalling GRUB 2 part. When I do:
```
grub-install /dev/sda
```
I get an error:
```
grub-setup: error: Cannot read `/boot/grub/core.img' correctly
```

So I'm stuck. Don't know what to do. Getting extremely mad.

---

### Post by grandtoubab on 2009-10-30
> **besweeet said:**
> I'm at the reinstalling GRUB 2 part. When I do:
```
grub-install /dev/sda
```I get an error:
```
grub-setup: error: Cannot read `/boot/grub/core.img' correctly
```So I'm stuck. Don't know what to do. Getting extremely mad.


I do prefer that one to chroot

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)


about grub2
[https://wiki.ubuntu.com/Grub2#](https://wiki.ubuntu.com/Grub2#)

recovery
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by ssican on 2010-01-17
Command for Reinstall Grub:

**sudo** grub-instal /dev/sda

---

### Post by Leppie on 2010-01-17
> **ssican said:**
> Command for Reinstall Grub:

**sudo** grub-instal /dev/sda
i wonder if besweet still needed help with that...  lol

---

### Post by besweeet on 2010-01-27
I do now. Needed to reinstall (restore from a backup, actually) all my OSs due to a new hard drive. I was able to boot from the live CD to dd the image I made of my Ubuntu partition to the new one, and all the files seemed to have been copied. I just need to get GRUB2 installed.

If I try to boot the Ubuntu partition, it'll say GRUB.. and have a blinking cursor and won't actually do anything.

What do I need to do?

---

### Post by synapsys on 2010-01-28
Boot a live cd...

Mount your root partition (substitute sda1 if yours is different)
```
sudo mount /dev/sda1 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```reboot.

Since you already have Ubuntu installed, all you need to do is re-install grub to the mbr and point it in the direction of your root partition.

---

### Post by Leppie on 2010-01-28
> **synapsys said:**
> Mount your root partition (substitute sda1 if yours is different)
```
sudo mount /dev/sda1 /mnt
```
since 7 is installed as well, most likely it's something like sda5, sda6

---

### Post by besweeet on 2010-01-28
> **synapsys said:**
> Boot a live cd...

Mount your root partition (substitute sda1 if yours is different)
```
sudo mount /dev/sda1 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```reboot.

Since you already have Ubuntu installed, all you need to do is re-install grub to the mbr and point it in the direction of your root partition.

It says it can't find a GRUB drive for /dev/sda3 (which is where Ubutu is installed). Then it says to check my device.map.

If I open device.map, it's empty.

---

### Post by oldfred on 2010-01-28
Do you still have your old drive installed? When you did a dd copy it copies everything including UUID's which have to be unique. There is a way to change UUID's if you still want to use the old drive. The device.map is normally recreated on a update-grub if it is missing?

You can try this, it will give several screens for edits to the grub file in case you have custom entries, generally just accept them and then choose drive to install to. Be sure to know which is sda, sdb before running this:
sudo dpkg-reconfigure grub-pc

---

### Post by Leppie on 2010-01-28
> **besweeet said:**
> It says it can't find a GRUB drive for /dev/sda3 (which is where Ubutu is installed). Then it says to check my device.map.

If I open device.map, it's empty.
use the --recheck option:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by besweeet on 2010-01-28
> **oldfred said:**
> Do you still have your old drive installed? When you did a dd copy it copies everything including UUID's which have to be unique. There is a way to change UUID's if you still want to use the old drive. The device.map is normally recreated on a update-grub if it is missing?

You can try this, it will give several screens for edits to the grub file in case you have custom entries, generally just accept them and then choose drive to install to. Be sure to know which is sda, sdb before running this:
sudo dpkg-reconfigure grub-pc

Did that. Went through the screens. Didn't seem to do anything. 

> **Leppie said:**
> use the --recheck option:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

Did. Last line says /grub/core.img cannot be read correctly. That file is in /boot/grub anyway...

---

### Post by meierfra. on 2010-01-28
> it can't find a GRUB drive for /dev/sda3 
 /grub/core.img cannot be read correctly.

Just to make sure. Are you using

```
sudo grub-install --recheck --root-directory=/mnt /dev/[COLOR="Red"]sda [/COLOR]
```

or 

```
sudo grub-install --recheck --root-directory=/mnt /dev/[COLOR="Red"]sda3[/COLOR]
```

---

### Post by besweeet on 2010-01-28
> **meierfra. said:**
> Just to make sure. Are you using

```
sudo grub-install --recheck --root-directory=/mnt /dev/[COLOR="Red"]sda [/COLOR]
```

or 

```
sudo grub-install --recheck --root-directory=/mnt /dev/[COLOR="Red"]sda3[/COLOR]
```

I actually tried both... Same result.

---

### Post by meierfra. on 2010-01-28
Let's have a better look at your system. Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt

---

### Post by besweeet on 2010-01-28
> **meierfra. said:**
> Let's have a better look at your system. Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt

I'll do that. But, would it possibly be easier if I just install a clean install of Ubuntu? That'll get GRUB2 going again. Then I should be able to dd my backed up image over and hopefully it'll all be normal again. Or will the dd screw GRUB up?

---

### Post by meierfra. on 2010-01-28
> would it possibly be easier if I just install a clean install of Ubuntu? 
No idea, since I don't know what is causing your problem.

---

### Post by besweeet on 2010-01-28
Thanks guys for all your help. 

I'm just going to install Ubuntu from scratch. It's a lot easier than trying to reinstall GRUB2. You'd think that there'd be a simple installer to do this, but I guess it's not supposed to be easy. I wasn't using my Ubuntu install for nothing more than a time waster anyway. It won't take more than 30 minutes to get all my hardware working again so I didn't lose anything.

---

### Post by Leppie on 2010-01-28
> **besweeet said:**
> It won't take more than 30 minutes to get all my hardware working again so I didn't lose anything.
resolving the issue might give you a better understanding of how your system works.

---

### Post by smartgilli on 2013-01-11
This might help 
[http://ssatish.wordpress.com/2013/01/11/how-to-re-install-grub-2-in-mbr-from-ubuntu-live-disk/](http://ssatish.wordpress.com/2013/01/11/how-to-re-install-grub-2-in-mbr-from-ubuntu-live-disk/)
Cheerz :)

---

### Post by oldfred on 2013-01-11
necromancy 
Closed, necromancy. Old thread closed.

From the Ubuntu Forums Code of Conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

