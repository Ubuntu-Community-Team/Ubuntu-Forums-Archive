---
title: "Um... I messed up my grub"
date: 2009-07-20
forum: General Help
---

### Post by raptor29a on 2009-07-20
Hi everyone,

I am new to the forums. I checked out the search options and browsed a lot... but I haven't quite found a thread with the same grub problem.

So to give some background...It started like this...
I told my friend over aim I wanted windows to boot first. So he gave me all the commands. I did a simple cut and paste job of what his grub said to mine (only the menu order nothing else). And when a restarted my computer the list of options couldn't be recognized...

I remembered that the only thing changed with windows-xp was(h0,0) to (h0,1) so I changed it back and got windows up and going. 

Now I am on the forums... I trying to figure out how to get back into ubuntu. 

I was thinking maybe a version mismatch or something. I probably need to find out which version of ubuntu I have and then get the right path to the kernel or something.

oh and by the way I am not really computer savvy, I just have a common base knowledge of how things work.

---

### Post by Bucky Ball on 2009-07-20
Are you getting a grub menu which gives you the option to boot into Ubuntu?

If not, try hitting escape when you are booting up (after the first splash and before it starts to boot into windows). That might bring up a grub screen at least.

You are probably going to need to give a bit more detail about exactly how you went about things (your friend's instructions). :)

---

### Post by raptor29a on 2009-07-20
ok first he told me to type this...

sudo gedit /boot/grub/menu.lst

Then Scroll down to a list...

(I had too many boot options I told him so he told me to delete the copies and I did...)

Then he said, you know it would just be faster to paste what I have. So I pasted this......

default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot

Then I restarted my computer and found I couldn't boot windows or Ubuntu

---

### Post by prem1er on 2009-07-20
Just some general things. Never copy and paste someone else's configuration settings without making a backup of your own.  This will almost certainly never work as their are too many differences between systems.  Also, in these forums it is very helpful if you post code or config file output between the [code] tags.  If you select the # in the editing icons and then paste between the tags it is much easier to read.

---

### Post by Bucky Ball on 2009-07-20
Unless you have your partitions set up identically to your friend, that doesn't suprise.

What have you got installed where? You are booting into Windows with (hd0,1)?

This menu.lst suggests a missing (hd0,0), the first partition, and Windows on another partition, perhaps the second partition.

* Edit: And I second prem1er, this was not a good idea. You might even be better starting again and going in knowing what is going where. :)

The other option is burning a copy of Super Grub Disk and letting it do it's magic (hopefully). That works out your grub for you nine out of ten.

(hd0,0) = first physical drive, first partition
(hd0,1) = first physical drive, second partition
(hd1,0) = second physical drive, first partition

... and so on. Also, (hd0,0) = /sda1; (hd0,1) = /sda2; (hd1,0) = /sdb1; etc ...

---

### Post by raptor29a on 2009-07-20
Well...

I know I should have backed it up...

I should have seen this coming when I was pasting...

If it's any consolation, I can still see my options and edit them in the grub start up screen.

I think I just need the right path or something, so I can access ubuntu... unless there is something I don't know... although in order to have the right path I figure I'll have to know what version of ubuntu I have.

---

### Post by Bucky Ball on 2009-07-20
Not really. Read my last post again, I updated it. If you can boot into Windows, fine. Edit one of the entries for Ubuntu (hit 'e' and edit the kernel line), changing the (hd0,4) part until you hit success. If you know it is in installed, you should be able to find it.

---

### Post by prem1er on 2009-07-20
edit: didn't mean to post.

---

### Post by estyles on 2009-07-20
if you can boot to the LiveCD, run ```
sudo fdisk -l
``` in a terminal, and post the output.  I'm pretty sure the problem is that your menu.lst is looking for Ubuntu on the wrong partition, so you just need to find the partition and change it to that in menu.lst, and you should be good to go!

---

### Post by Bucky Ball on 2009-07-20
Good call and straightest route. You may well be able to see where the Ubuntu install is by the results of fdisk -l. The partition will be in EXT3 format.

You can also run:
```

sudo blkid
```

for some info.

---

### Post by irv on 2009-07-20
Boot with the Ubuntu CD and boot to the desktop. Goto System>Administration>Partition Editor. It will show what partition your Ubuntu is booting from. Make sure it is the same in the boot menu. You can mount your filesystem from the live CD and run
```
sudo gedit //boot/grub/menu.lst
``` 
Edit the partition information under the Ubuntu boot.
Here is a partial of what mind looks like
> 

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR]
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR] ro quiet splash vga=788 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR]
kernel		/boot/vmlinuz-2.6.28-13-generic root=[COLOR="Red"]UUID=b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR] ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR]
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR] ro quiet splash vga=788 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR]
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR] ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		[COLOR="Red"]b7a65782-aa8a-4cc3-a891-032a38f56b76[/COLOR]
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1




See my uuid number: I have it in RED.
Now see the screen shot of my partition information and you will see the number is the same. Also make sure the sda or sdb or whatever your mount point is, make it the same in the grub menu.
This is why you never paste someone's information in a configuration file. There uuid would be different then your. 
[ATTACH]121768[/ATTACH]

---

### Post by raptor29a on 2009-07-20
First off, thanks for telling me what the (hd0,0) means.
Secondly I found that windows is (hd0,0) and my ubuntu partition is (hd0,1)

So... I got Error 17 with (hd0,4)... BUT
      I got Error 15 file not found with (hd0,1)

Thus I have the right partition all I need now is the right file.

Lastly I think I need to get an ubuntu cd

---

### Post by jarene on 2009-07-20
sorry for my bad enlish

To automatically boot to system, the key is the default value.

You could try to restore you're grub using instruction from [here]("http://ubuntuforums.org/showthread.php?t=24113") or [here]("http://ubuntuforums.org/showthread.php?t=224351"). Or, if you can boot to ubuntu, you can try to update grub using update-grub command (man update-grub to read the manual), i never try it myself so it's your own responsibility.

Then edit menu.lst and change the default value to the number of the system image you want to auto boot on. The numbering start from 0.

---

### Post by irv on 2009-07-20
I think there is a grub repair on the Live CD. But someone will have to verify this? 
I just found this check it out: [http://ubuntuforums.org/archive/index.php/t-210820.html ]("http://ubuntuforums.org/archive/index.php/t-210820.html")
I don't have time to look it over I have to go pick up my wife. Will check back later.

---

### Post by raptor29a on 2009-07-20
Thanks everyone for your input I have to go to work now, but I will make sure to get back to you all if I fix it or find out anything.

p.s. the cd might help me fix my error 15 message

---

### Post by jarene on 2009-07-20
just found another link

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I think you can use information from that page to fix your problem :)

---

### Post by Bucky Ball on 2009-07-21
The easiest and most reliable is Super Grub Disk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

SuperGrub can get you out of a mess but is also a powerful tool that can teach you a lot about all things grub. It will figure out where things are and re-write the menu.lst for you (among other things). :)

---

### Post by raptor29a on 2009-07-21
Thanks everyone it looks like I have some reading to do

---

### Post by Bucky Ball on 2009-07-21
Oh, incidentally, you download the ISO of SuperGrub and boot from that, but you probably figured that out already.

---

### Post by egalvan on 2009-07-21
And to safely make changes to menu.lst, use startupmanager".

It's found under

System -> Administration


If it's not installed, use either Add/Remove or use Synaptic to install it.

StarUpManager is very easy to use, and will let you make the kind of changes that  a beginer would need.

For instance, if you want to cut down on the list of kernels, there is an option for that

"Number of kernels to keep"

Install it, and post back if you need further help

---

### Post by raptor29a on 2009-07-22
Good idea... because that's All I was trying to do was to take the list of like 13 things and make it 4, lol

---

### Post by raptor29a on 2009-07-23
Ok here's an Update, I've been fooling around with supergrub haven't fixed the problem yet but I have more information...

hda2 sda 2 (hd0,1) hd0s2 ext 2fs 19GB Ubuntu 8.04.1 \n \1

That's about as far as I've gotten. So now I know what partition it is on and what version of Ubuntu I have... but I'm still getting error messages... anyways I'll keep you posted on any developments.

As for now I have to head off to work Thanks Every One

---

### Post by raptor29a on 2009-07-25
One last updated I'd like to thank you all on a job well done...

I got the info I needed Kernal= Vmlinuz-2.6.22-14-generic
 UUIC: 21fggbe4-f4cf-4dlc-8b6a-6b2a3a8b254

Thanks :popcorn:

---

### Post by irv on 2009-07-25
> **raptor29a said:**
> One last updated I'd like to thank you all on a job well done...

I got the info I needed Kernal= Vmlinuz-2.6.22-14-generic
 UUIC: 21fggbe4-f4cf-4dlc-8b6a-6b2a3a8b254

Thanks :popcorn:

One thing about making mistakes, we do learn from them.

---

### Post by Bucky Ball on 2009-07-26
> **irv said:**
> One thing about making mistakes, we do learn from them.

... and so say all of us. What it's about. :)

---

