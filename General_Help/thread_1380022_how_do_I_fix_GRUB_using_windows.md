---
title: "how do I fix GRUB using windows?"
date: 2010-01-13
forum: General Help
---

### Post by colobix on 2010-01-13
Hi. I messed up grub. I deleted wrong kernel.
how do I fix this ig Windows?
I tried the terminal method from an Ubuntu live cd but it didnt work. 
please help.

---

### Post by sh4d0w808 on 2010-01-13
If U use linux-filesystem, then there is no recommended ways. U can use Installable Filesystem Driver for read/write ext2/3 partitions, but not recommended to use it for write onto ext partitions.

What was the problem with the LiveCD way?

---

### Post by colobix on 2010-01-13
I tried

sudo grub 
find /boot/grub/stage1 
root (hd0,0) 
setup (hd0) 
quit

Things that didn't work:

root (hd0,0) 
setup (hd0) 

So I couldn't reinstall grub. all I got was error messages.

So there aren't any windows software I can use to fix this?
And what elese can I do?

---

### Post by howefield on 2010-01-13
> **colobix said:**
> So I couldn't reinstall grub. all I got was error messages.

Which version of grub are you using ?

> So there aren't any windows software I can use to fix this?

Yes, there is, but I couldn't tell you how good they are.

---

### Post by colobix on 2010-01-13
I don't know what version of grub I have
And if there are any windows software I can use to restore grub, then please tell me.
EDIT: I have ubuntu 9.04 installed if that helps.

---

### Post by howefield on 2010-01-13
> **colobix said:**
> I don't know what version of grub I have


Open a terminal (Applications > Accessories > Terminal) and type

```
grub-install -v
```

Post back here with the output.

I'm saying that if you have grub2, then what you tried won't work.

> And if there are any windows software I can use to restore grub, then please tell me.

I wouldn't suggest or recommend something I haven't tried, other than tell you it can be done.

---

### Post by colobix on 2010-01-13
It says Invalid opiion.

---

### Post by mr clark25 on 2010-01-13
you might need to run it as root:
sudo grub-install -v

---

### Post by howefield on 2010-01-13
Sorry, re-read your initial post, as I now understand it, you have no access to your Ubuntu install, and can only use Windows or a Live CD.

I'd try the instructions for repairing Grub2, seeing as what you tried above didn't work.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

---

### Post by colobix on 2010-01-13
THat\s right
I tried in root, and then I got this info>
grub-install (GNU GRUB 0.97)

So now what do I do

---

### Post by colobix on 2010-01-13
I don\t think I have grub 2. the output says
grub-install (GNU GRUB 0.97)

---

### Post by howefield on 2010-01-13
I am not sure that is your installed version, maybe the version on the Live CD.

---

### Post by colobix on 2010-01-13
I used the live cd yes, but I does it matter_
EDIT> I really wanna fix this now. please help.
This is SO frustrating.

---

### Post by mechro on 2010-01-13
Are you sure you have your Ubuntu installation on hd0,0 and your bootsector on hd0?

---

### Post by colobix on 2010-01-13
> **mechro said:**
> Are you sure you have your Ubuntu installation on hd0,0 and your bootsector on hd0?


What?
I am not sure about anything. I just wanna fix grub so I can use Ubuntu again. And I don\t wanna reinstall it.

---

### Post by mechro on 2010-01-13
Well, you're not clear on how much knowledge you have. Issuing  Grub commands suggest you know what you are doing.

I can't suggest a fix via Windows but if you give us some more information you may be able to fix it using the LiveCd...

In the LiveCD open a Terminal and do the following command...

```
sudo fdisk -l
```

Post the results back here.

---

### Post by colobix on 2010-01-13
OK here>

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44d344d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d595ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29293   235295991   83  Linux
/dev/sdb2           29294       30515     9815715    5  Extended
/dev/sdb5           29294       30515     9815683+  82  Linux swap / Solaris

Also, I think Ubuntu should have a program on their live CDs that would allow people to fix their grub menus in situations like this.

---

### Post by mechro on 2010-01-13
Right, your Ubuntu is probably on sdb1 or hd1,0 in Grub terms.

From the LiveCD open a Terminal and do...

```
ls /media
```

Post the results here.

---

### Post by colobix on 2010-01-13
ls /media didn\t do anything
it didn\t give me any info at all.
it just took me to the next line

---

### Post by mechro on 2010-01-13
Can you navigate to your Ubuntu using Nautilus. Look in Computer or Places or FileSystem media folder. Do you recognise anything as your Ubuntu installation?

---

### Post by colobix on 2010-01-13
Yes it came up now. ut\s called Disk.

---

### Post by mechro on 2010-01-13
Open Disk to check that it is Ubuntu because Disk might be Windows.

---

### Post by colobix on 2010-01-13
No I am sure.
WIndows is SYSTEM and Ubuntu is disk.
I checked the files.

---

### Post by mechro on 2010-01-13
OK. Open Terminal, try the following...

```
cat /media/disk/boot/grub/menu.lst

cat /media/Disk/boot/grub/menu.lst

sudo cat /media/disk/boot/grub/menu.lst

sudo cat /media/Disk/boot/grub/menu.lst
```

I've given four alternatives as I'm not sure which one will work with your system.

Post results back here.


Edit: Sorry I've got to go out for an hour. Be patient, someone else might chip in and help.

---

### Post by colobix on 2010-01-13
Yea I am sorry. it\s disk not Disk  xD
OK here\s the info>

default saved
timeout 10

title Ubuntu 9.10, kernel 2.6.31-14-generic
root 
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=1f172296-8736-413a-bf43-2ec71506c25b ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=1f172296-8736-413a-bf43-2ec71506c25b ro  single
initrd /boot/initrd.img-2.6.31-14-generic

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

As you can see. I have a kernel here but the wrong one. I had a list of  kernels and i hought the  14 was the right kernel but no no no  heh..

---

### Post by running_rabbit07 on 2010-01-13
The Grub you need for that is Grub2, which is labeled 1.97 not 0.97. Follow the link listed above for Grub2. This would have all been figured out easier if someone had asked which version of Ubuntu you are using.

---

### Post by michy99 on 2010-01-13
> **running_rabbit07 said:**
> The Grub you need for that is Grub2, which is labeled 1.97 not 0.97. Follow the link listed above for Grub2. This would have all been figured out easier if someone had asked which version of Ubuntu you are using.

He does not have Grub2, he has legacy grub. You are just confusing things.

---

### Post by michy99 on 2010-01-13
Please post the output of```
ls /media/disk/boot
```

---

### Post by mechro on 2010-01-13
Ubuntu 9.10 doesn't necessarily mean Grub2 is installed. Since there is a menu.lst, Grub Legacy has been there at some point. It might not work but it's worth trying to fix it as a Grub Legacy installation.

colobix...

Forget the kernel version for the moment, we'll try and see if the version in your Grub will boot...

In LiveCD, open Terminal do..

```
sudo grub

root (hd1,0)

setup (hd1)

quit 
```

Reboot from your sdb drive. If that wasn't how you booted before, please explain your boot procedures for both Windows and Ubuntu and we'll redo the Grub reinstall.

---

### Post by howefield on 2010-01-13
4 hours plus and counting...

Sure you don't want to back up any necessary files and reinstall Ubuntu ?

There is something to be said for the learning experience, but unless your time isn't valuable, installing over the Ubuntu partition(s) will put grub back nice and tidy.

Just a suggestion.

---

### Post by colobix on 2010-01-13
> **mechro said:**
> In LiveCD, open Terminal do..

```
sudo grub

root (hd1,0)

setup (hd1)

quit 
```

Reboot from your sdb drive. If that wasn't how you booted before, please explain your boot procedures for both Windows and Ubuntu and we'll redo the Grub reinstall.

That didn\t work but thanks anyway.
and what do you mean Reboot from your sdb drive?
I reboot like I always to, by clicking the reboot button and when I boot into the live cd I pop it up when I turn on my pc so it comes up before Grub.
When grub comes up there\s a list with the 3 options>
Ubuntu
Ubuntu recovery mode
WInXP.

---

### Post by colobix on 2010-01-13
> **howefield said:**
> 4 hours plus and counting...

Sure you don't want to back up any necessary files and reinstall Ubuntu ?

There is something to be said for the learning experience, but unless your time isn't valuable, installing over the Ubuntu partition(s) will put grub back nice and tidy.

Just a suggestion.

Howefield, first of all. this can happen again and I wanna learn how to deal with this the next time it happens so NO, I will not reinstall and waste like 5 hours on this PC doing backups, installations and all that boring bs.

---

### Post by running_rabbit07 on 2010-01-13
> **colobix said:**
> Howefield, first of all. this can happen again and I wanna learn how to deal with this the next time it happens so NO, I will not reinstall and waste like 5 hours on this PC doing backups, installations and all that boring bs.

It doesn't take that long to back up Ubuntu, any file worth keeping in Windows is worth backing up. When you reinstall, you will get Grub2 and all will be fine.

---

### Post by mechro on 2010-01-13
I have this strange sensation that you have a Wubi installation. If you have, I can't help you and will move into the reinstall backup bs camp.

---

### Post by howefield on 2010-01-13
> **colobix said:**
> first of all. this can happen again

Well actually, only if you don't learn from the first time....

> and I wanna learn how to deal with this the next time it happens

As I said, there is a lot to be said for the learning experience.

> so NO, I will not reinstall and waste like 5 hours on this PC doing backups, installations and all that boring bs.

Good for you :)

---

### Post by colobix on 2010-01-13
> **running_rabbit07 said:**
> It doesn't take that long to back up Ubuntu, any file worth keeping in Windows is worth backing up. When you reinstall, you will get Grub2 and all will be fine.

If I do that, this tread will be useless, plus yes it takes time.
I really wann figure out how to solve this problem without reinstalling anything. Plus, I don\t have space enough to backup everything.

Ok, so the problem here is that the kernel is wrong, so why not just changing the kernel to the one that works_
I have 100 kernels in the list so finding the right one is probably inpossible.
Ubuntu should really fix this kernel bug in an upcoming version.

---

### Post by running_rabbit07 on 2010-01-13
> **colobix said:**
> Ok, so the problem here is that the kernel is wrong, so why not just changing the kernel to the one that works_
I have 100 kernels in the list so finding the right one is probably inpossible.
Ubuntu should really fix this kernel bug in an upcoming version.

Kernel bug? You said that you deleted the wrong one and now you are blaming Ubuntu? If you want to reinstall the kernel that is missing, then ask how to do that.

---

### Post by colobix on 2010-01-13
> **mechro said:**
> I have this strange sensation that you have a Wubi installation. If you have, I can't help you and will move into the reinstall backup bs camp.
No it\s not. It is a real ubuntu installation on its own partition on its own hard driver.
The error I get when I try to start Ubuntu now is
ERROR 11  Unrecognised  device string.

Isn\t it possible to just make these two kernels recognisable?

---

### Post by colobix on 2010-01-13
> **running_rabbit07 said:**
> Kernel bug? You said that you deleted the wrong one and now you are blaming Ubuntu? If you want to reinstall the kernel that is missing, then ask how to do that.
Ok? To me, this kernel thing looks like a bug and if Ubuntu can\t fix it then they should atleast make a program that will let you repair this thing easelier. I am sure there are many people out there with the same problem and now they are forced to reinstall the whole thing. Yea that is so fair.

---

### Post by running_rabbit07 on 2010-01-13
> **colobix said:**
> Ok? To me, this kernel thing looks like a bug and if Ubuntu can\t fix it then they should atleast make a program that will let you repair this thing easelier. I am sure there are many people out there with the same problem and now they are forced to reinstall the whole thing. Yea that is so fair.

So from what you are saying, you just need to get the newer kernel back on your grub list?

---

### Post by colobix on 2010-01-13
> **running_rabbit07 said:**
> So from what you are saying, you just need to get the newer kernel back on your grub list?
I have no idea if I Need a newer or older or whatever. I Just need one that works.
Now I Have the one that ends with 14 I guess but I don\t know which one that will work for my system. I had a list of atleast 10 kernels and I thought the number 14 worked perfectly so I deleted the other kernels.
The one I Have now says ERROR Unrecognised Device String.

---

### Post by michy99 on 2010-01-13
If you will do what I said in my last post I will tell you how to fix it.

---

### Post by running_rabbit07 on 2010-01-13
When you deleted the kernel, how did you do it? Did you open menu.list and edit it or did you actually go to the grub folder and delete files?

---

### Post by colobix on 2010-01-13
> **michy99 said:**
> If you will do what I said in my last post I will tell you how to fix it.
Are you the guy who suggested to reinstall? Well, I could if I Had enough backup space. I could also burn a copy if I Had a cd burner. So you see, I have to do it this way. I could reinstall the OS if I could reinstall everything without doing anything to my home folder where I have all my music and videos and all that crap.

> **running_rabbit07 said:**
> When you deleted the kernel, how did you do it? Did you open menu.list and edit it or did you actually go to the grub folder and delete files?

I used kgrub editor.
I do have a backup file called menu.lst.backup but I can\t delete the menu.lst file or do changes to it for some reason. I tried with both gksudo and sh in nautilus. but maybe I can\t do it coz I am using a live cd.

---

### Post by oldfred on 2010-01-13
Do you have any kernels still in /boot?

To see you entire boot configuration:
Boot Info Script courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by jocko on 2010-01-13
> **colobix said:**
> I used kgrub editor.Then don't call it a bug. It's a user error. If you try to do things the wrong way, chances are you'll end up with a broken system. If you want to remove an entry from the boot menu, just uninstall the kernel version you want to get rid of, and let dpkg/apt/synaptic manage the menu.
> **colobix said:**
> I do have a backup file called menu.lst.backup but I can\t delete the menu.lst file or do changes to it for some reason. I tried with both gksudo and sh in nautilus. but maybe I can\t do it coz I am using a live cd.It shouldn't be any problem to do that.
If the ubuntu partition is mounted in /media/disk, this will take care of it:
```
sudo mv /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bad
sudo cp /media/disk/boot/grub/menu.lst.backup /media/disk/boot/grub/menu.lst
```

---

### Post by colobix on 2010-01-13
> **jocko said:**
> Then don't call it a bug. It's a user error. 
I kinda agree, but I will still call it a bug.
I mean, you don't get 100 kernels for each and every windows update you do.
ANd this kernel thing can really confuse new users and people who doesnt know too much about these things.

But thanks alot for helping me out. That was so awesome of you and now I know what to do if this happens again. I am so glad I didn't reinstalled the whole damn thing. Thanks again.

ANd thanks to all of you who've been trying to help me out here.

---

### Post by colobix on 2010-01-13
1 more thing before it is solved.

What kernel version is the right one? There are like 20 or something. and I wanna remove the wrong kernels.

---

### Post by mechro on 2010-01-13
The right one is usually the latest one that works. Normally if you update to the latest kernel, that will work but if it doesn't then you can carry on using the previous one.

Glad you got it solved. You didn't actually delete any kernels and you didn't need to reinstall grub. All that was required was to edit your menu.lst file or restore the menu.lst backup as jocko helpfully advised you.

---

### Post by colobix on 2010-01-13
> **mechro said:**
> The right one is usually the latest one that works. Normally if you update to the latest kernel, that will work but if it doesn't then you can carry on using the previous one.
I tried 17 but it wouldn't work after I removed the other kernels but it worked when I had them all. THat was weird.
So is there a way to figure out what kernel that works without trying them all?

> **mechro said:**
> Glad you got it solved. 
Me too LOL

> **mechro said:**
> You didn't actually delete any kernels and you didn't need to reinstall grub. All that was required was to edit your menu.lst file or restore the menu.lst backup as jocko helpfully advised you.
Sure I know that, now xD

---

