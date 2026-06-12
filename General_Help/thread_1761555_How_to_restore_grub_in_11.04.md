---
title: "How to restore grub in 11.04"
date: 2011-05-18
forum: General Help
---

### Post by sambonfante on 2011-05-18
I installed win7 after installing ubuntu, and now grub is gone. I looked around for tutorials, but none of them have worked so far.


So, how do you restore grub in 11.04?

PS
I've heard about grub 2? I'm not sure what the differences are. Enlighten me, please. :)

---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]Hello there,

Did you just install win 7 on top of ubuntu without creating a specific partition for win 7 or using another hard drive?

I'm just asking, because win7 thinks of itself as the only OS being installed. I doubt you can install it next to another operating system. --> sure you didn't just erase ubuntu?

However this might help:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)  <-- guide

here's the whole discussion 

[http://forums.whirlpool.net.au/archive/1151884](http://forums.whirlpool.net.au/archive/1151884)  <-- thread


Hope this helped :)
[/FONT]

---

### Post by PowerBarry43 on 2011-05-18
Hi,
 
your grub is gone because the windows installer overwrites the MBR (master boot record) which is the fisrt few bytes on the hard drive that point ot your bootloader. when you installed windows it made the MBR point to you the windows 7 bootloader so your grub is t#still there its just not being used.
 
to restore grub you need to boot into ubuntu. to do that you need to either use a live CD or use a supergrub boot disk which you can puton a USB drive or a cd and can be downloaded here [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5) 
 
thatll let you boot into your installation on the hard drive which is a lot faster than a live cd plus you can use it to boot into pretty much any other linux distro.
 
once you're in open up a termial and type:
 
```
sudo grub-install /dev/sda
sudo update-grub
```
 
this will generate a conifg file and instalol grub to the MBR. It should also detect windows 7s bootloader and allow you to boot into that as well.
 
ive not got much experience with grub becuase I mostly tend to stick to grub 2 so imno really sure about the differences between them but i dont think you can generate a config file for the menu enrties in grub you have to do it manually whereas you have one generated for you in grub 2.
 
(plus in grub 2 you get a picture background which is cool)
 
Hope that helped :)
 
Barry

---

### Post by sambonfante on 2011-05-18
@3xp10r3r|X13

This is how I have my partitions set up:
| Windows | Ubuntu |       Storage    |   

Thanks for the help!

@powerbarry43
I did the terminal thing, and it tells me "error: cannot find a device for /boot/grub (is /dev mounted?)"

And I think I had grub2. It had a purple background,right?

Thanks again guys! :)

---

### Post by PowerBarry43 on 2011-05-18
yeah thats grub 2 did you try doing just "sudo update-grub"?

---

### Post by sambonfante on 2011-05-18
I tried... 

sudo grub-install /dev/sda
sudo update-grub

and also just...

sudo update-grub

Either one gives me the same error. :/

---

### Post by oldfred on 2011-05-18
The instructions from PowerBarry43 are after you have booted using Supergrub to boot.

If you are using a liveCD then you have to mount the partition(s) first. With grub2 version 1.99 there have been some changes and you have to use a 11.04 liveCD and boot not root in the command.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

If you still have troubles post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and really requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by PowerBarry43 on 2011-05-18
Yeah I take it you didn't use supergrub if you use supergrub it forces you to mount the correct devices becasue you're booting from them.
 
If you want to use a live cd you need to mount the drives first. thats why you got that error message.
 
Edit: yeah what oldfred said :)

---

