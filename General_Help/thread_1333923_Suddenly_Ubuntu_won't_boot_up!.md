---
title: "Suddenly Ubuntu won't boot up!"
date: 2009-11-21
forum: General Help
---

### Post by Scooter_X on 2009-11-21
Yea. You heard it. My computer running Ubuntu 9.10 isn't booting up. Says some stuff, then mentions (something) grub> and waits for a command. 

I've pretty much deduced that it's that my grub thing (I have no idea what it is) is broken/missing for some odd reason. I've tried to find out how to reinstall it from the liveCD BUT I keep running into two issues for two pottential fixes:


1)
One I keep seeing is that I should check the partition (sudo fdisk -l) that it's on and do something from there, and "if you're unsure use 'df-Th'." I was unsure, so typed 'df-Th' and it said "command not found" - am I typing something wrong? Something I just straight up don't understand?


2)
I found how to get myself to the 'grub>' prompt and it was suggested that I use 'find /boot/grub/stage1' , and that it would return a location (hd?,?) and that I should move on from there. In this case, I get to grub> put in the 'find' bit, and I get: "error 15: file not found" ... WHAT? Yea.


So anyway, I need some help. I was using it earlier today just fine, then I shut down the computer when I left to see a movie. Came back and had to deal with this. I'd appreciate some help. Let me know what other info I can give that would be useful. Thanks.

-Scooter_X

---

### Post by jeb800e on 2009-11-21
Obtain a LiveCD. Run fsck from there.

---

### Post by Scooter_X on 2009-11-21
Thanks. I need a clarification though. I don't know how to do that. I fit in the 'really new at this' group. Thanks again. (edit: I do have a LiveCD already)

---

### Post by Scott753 on 2009-11-21
So, when you boot your computer, do you get something that looks like this

[http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png](http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png)

or is there only text?

If you can, try the command sudo fdisk -l (the letter l as in lion ) and post the result.

---

### Post by Scooter_X on 2009-11-21
Nope. I used to get that, but now it's just text and the 'grub>' prompt. 

Here's what I got:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25f16a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       37988   303594496    7  HPFS/NTFS
/dev/sda3           37988       38914     7439360   17  Hidden HPFS/NTFS


Thanks

---

### Post by Scott753 on 2009-11-21
Ok, try find /boot/grub/stage1

You'll get a response like "(hd0,1)"

Then try

grub>  root  (hdx,y)
grub>  chainloader +1
grub>  boot

and see if it boots

---

### Post by Scooter_X on 2009-11-21
It says there's no such file or directory when I do that. 

Maybe it would've helped if I mentioned that I don't have ONLY ubuntu on the computer, I did the 'install under windows' option. Could that be giving problems?

---

### Post by Scott753 on 2009-11-22
I'm a little confused. You can't boot windows right now either, right?

---

### Post by Scooter_X on 2009-11-22
Oh. sorry for the confusion. Windows DOES boot up. Ubuntu is the only one having issues, currently.

And perhaps to help, here's the exact text that I'm getting when I hit the brick wall

GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]

sh:grub>
(I then hit tab)
Possible commands are:
 . [ badram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rmmod root save_env search set sleep source terminal_input.console terminal_output.console test unset
sh:grub>

---

### Post by Scott753 on 2009-11-22
How do you boot Windows? Oh, btw, did you choose the option to install into an encrypted partition? Also, if you know where you've installed Ubuntu, that would be really helpful. Like is it hd(0,1) or something like that.

---

### Post by Scooter_X on 2009-11-22
screen comes up, asks for me to pick windows or ubuntu. default is windows, gives me 5 seconds to pick and if I don't, it just goes into windows. so, I guess you'd say a regular dual-boot style.

---

### Post by Scott753 on 2009-11-22
So I'm guessing the problem occurs when the screen comes up with Windows and Ubuntu. You select Ubuntu and up pops the "grub>". Just to clarify what the problem is.

Sorry, but I'm not that familiar with grub2. I'll look into it, and maybe I can find you a solution by tomorrow.

---

### Post by Scooter_X on 2009-11-22
Yes. That's it, you're exactly right.

Thanks for your help. Heck, I don't even know what Grub is in the first place! You're far better off than I am. I appreciate it.

---

### Post by darco on 2009-11-22
Looks like you need to reinstall grub...check this link

[https://help.ubuntu.com/community/Grub2#Using CLI to Boot](https://help.ubuntu.com/community/Grub2#Using CLI to Boot)



darco

---

### Post by jeb800e on 2009-11-22
Here you go:
[http://www.everyjoe.com/newlinuxuser/how-to-use-fsck-to-fix-disk-problems/](http://www.everyjoe.com/newlinuxuser/how-to-use-fsck-to-fix-disk-problems/)

---

### Post by john newbuntu on 2009-11-22
Here's an interesting post from QQmike that might help you:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by Scooter_X on 2009-11-22
Hey thanks guys for the info you're giving me. I'd been looking for stuff myself but seemed to find always some super technical info that I didn't understand. I'm being able to understand better what GRUB is and now I'm moving on to how it works.

One thing though. In an earlier post of mine I had put that when I went to Terminal and entered: sudo fdisk -l  I got:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25f16a6

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 37988 303594496 7 HPFS/NTFS
/dev/sda3 37988 38914 7439360 17 Hidden HPFS/NTFS

Now, 3 lines up it says "/dev/sda2 * ..."  does that (*) tell me that that's the partition that I installed on? I notice that partition 2 is the only one that has the asterisk. I was reading about how I could identify which partition I was on from here, and I'm just wondering if that's what tells me. I'm still needing to find the partition so I can reinstall Grub2. I have another idea that I'm going to try later this afternoon (i hope) and I'll report back.

Thanks again

---

### Post by Scooter_X on 2009-11-22
> **john newbuntu said:**
> Here's an interesting post from QQmike that might help you:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

Woohoo!! I found something that helped me tons!

When I got the grub> prompt, I used the 'set' command to display current grub2 settings, and right inside of there it said a line that told me that it was in partition 2 (hd0,2) or something like that. the 'ls' command (I think that is what it was called) listed the partitions that were 'recognized' by Ubuntu, and it gave me partitions 1 thru 3. That itself wasn't too helpful.

Anyway, now I have to simply try to reinstall grub2 on that 2nd partition and see if I can't blow something up! (I mean, fix it ;))

I'll post more when I find more for anyone who ever has this problem in the future.

---

### Post by oldfred on 2009-11-22
Wubi is a lot different than regular Ubuntu since it is really just a program running inside windows. Do not follow any of the standard repairs for Ubuntu, since you are booting windows and from the windows boot selecting to run the Ubuntu program. Its somewhat like the liveCD or a USB install, just running on your windows hard drive.

The * is a boot flag set on the windows partition used to boot from. It is only used by windows, not by Ubuntu.

---

### Post by Scooter_X on 2009-11-22
Oh dang. That's good to know. Thanks.

Eventually I want to only run Ubuntu, and I'd just wipe out my hard drive right now and do that, except for one little thing: I've moved everything from 'my documents' in windows to the 'documents' folder in Ubuntu. Now I can't retrieve what's in it and back it up. I don't think there's anything in there I absolutely couldn't live without, just a few partially complete programs for a class. I'd have to start over on those if I reformatted. 

I keep hearing about people accessing their installation somehow temporarily through the LiveCD, so I'm going to research that and see what I can come up with. If anyone knows where to find all that stuff and access it I would appreciate it. I can't find anything. Google Desktop seems to have found it, but when I go there it takes me to /ubuntu/install and there's only one folder there. Like everything's hidden and encrypted or something, I don't know.

---

### Post by oldfred on 2009-11-22
I know nothing about wubi but this may help

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by FXEF on 2009-11-22
@Scooter_X

Sounds like you did a Wubi install from with in Windows. If you don't have any important data in your /home directory, just go to "add and remove programs" in Windows and remove the Wubi install. Then defrag your C:\ drive using Windows defrag tool. Next reboot computer to Windows and do another Wubi install of Ubuntu.

You should have the dual boot option again.

---

### Post by Scooter_X on 2009-11-22
Thanks, oldfred for that link. I'm finding out bunches of stuff that could help me.

FXEF- yea, I was thinking about just doing that. I was hoping to save some incomplete homework assignments that *are* in the /home directory, is all. You don't know how to get stuff out of that directory through Windows do you?

---

### Post by Scooter_X on 2009-11-23
:KS

SOLVED! To an extent. _I got my documents back._ I found the information where oldfred told me to look (Thanks again!):

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

What I basically did (you can find details on that website if you've got the same issue) is ran Ubuntu off of the liveCD and using the terminal, I mounted the hard drive into ubuntu and was able to access it in another folder within ubuntu. It all was there, just like I had left it. So, I threw it all on my jump drive and ran like heck. 

EDIT: I did still have to know what partition I was on so that I knew which partition to mount. This thread has information about how I found that.

So now this time I'm going to just install Ubuntu normally on it's own partition and fly from there instead of using Wubi.

---

