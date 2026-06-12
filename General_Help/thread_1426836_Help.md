---
title: "Help"
date: 2010-03-10
forum: General Help
---

### Post by hctib on 2010-03-10
I'm deeply disappointed with ubuntu. I had the same problems that some users of this forum but I just can't fix it. I don't understand half of the stuff that you guys write here and every minute I regret for switching ALL my documents, music and pictures that I have been collecting for years. The only move that I made was put the dvd with the program and reboot it. After I take the dvd out and the same black screen with stupid codes shows up. Is there anyone here who can with a human language help me to recuperate all my documents, after this I'll make sure to leave you guys alone and delete this piece of **** software. Thanks

---

### Post by wojox on 2010-03-10
Sure just reboot from the cd/dvd and choose "Try without installing" . This will load the system into memory and you can then go to Places and see your hard drive and click it to mount. Then retrieve your files.

---

### Post by hctib on 2010-03-10
Ok, now I can access ubuntu but all my files are gone. When I take the dvd out and restart the computer the same screen appears. What should I do?

---

### Post by Alexandre Putt on 2010-03-10
It's not possible to understand your problem with vague description like that. Merely inserting a CD and restarting shouldn't do anything to your computer.

Can you be more specific on what is written on the screen?

---

### Post by hctib on 2010-03-10
Ok sorry for that...
It shows a black screen written GNU GRUB Version 1.97 Beta
Minimal Bash-Like line editing is supported..
SH:Grub>

---

### Post by ubudog on 2010-03-10
Is it froze like that?  Any error message?

---

### Post by hctib on 2010-03-10
It's not frozen but any code that I tried putting in doesn't work, I tried following the steps of the documents about it but nothing seems make sense...
It happened after an update a couple days ago, since then there's no way of getting out of it.

---

### Post by ubudog on 2010-03-10
> **hctib said:**
> It's not frozen but any code that I tried putting in doesn't work, I tried following the steps of the documents about it but nothing seems make sense...
It happened after an update a couple days ago, since then there's no way of getting out of it.

Do you know what type of update it was (kernel, etc.)?

---

### Post by themusicalduck on 2010-03-10
How did you install Ubuntu? Did you install 9.10? Did you install it through Windows? ie, you put the CD in the drive and ran the setup from autorun or from within Windows? Or did you install Ubuntu to it's own partition?

If you did install it from within Windows and you are using 9.10, but not any version older, then follow the solution outlined in this post - [http://ubuntuforums.org/showpost.php?p=8444565&postcount=10](http://ubuntuforums.org/showpost.php?p=8444565&postcount=10)

Sorry it's not in more human language but it should help if it's followed right.

(Don't know if this needs to be pointed out, but *[1] refers to a footnote and doesn't need to be typed in.. someone else was confused by that before so thought I'd mention it.)

Only difference is that once you are booted into Ubuntu you use the command ```
sudo update-grub
``` and not update-grub2 like it says in the post. After that, you should be able to boot normally again.

But this will only work if you installed it through Windows.

If you did install Ubuntu to it's own partition, then boot with the CD and select Try without installing again, type ```
sudo fdisk -l
``` into a terminal (Applications > Accessories > Terminal) and post what it says on here.

---

### Post by hctib on 2010-03-10
I don't think i have the 9.10 update yet, I tried following those steps and after i typed 
sh:grub>initrd /boot/initrd.img-26.31-14-generic

There was an error, so I typed boot then a bunch of codes showed up on the screen and after that, totally frozen.
I installed it through the windows and yes I put the cd in the drive and ran within windows.

---

### Post by themusicalduck on 2010-03-10
So which version did you install? If you installed the latest version that is on the Ubuntu website then it should be 9.10.

The fact that it showed some codes when you typed in boot suggests that it is able to load the kernel. Is there an error message when it freezes? When it does, is the caps lock light blinking? Knowing what error message you get when you use the initrd command would be helpful too.

---

### Post by hctib on 2010-03-10
Yes the caps lock light blinks, what does it mean?
It might be 9.10 then but I'm not sure which version I downloaded, is it normal after I request boot to take more than 15 minutes?

---

### Post by themusicalduck on 2010-03-10
If the caps lock is blinking then the kernel isn't working properly and it won't be able to boot. So we've fixed your boot-up problem but another problem has arisen in its place.

I just noticed something in that post I linked to you. It looks like there's a typo in the "Solution for Windows ME/XP" part. It should be ```
initrd /boot/initrd.img-2.6.31-14-generic
``` not ```
initrd /boot/initrd.img-26.31-14-generic
``` 

That might be why you got an error when using the command before if you copied it exactly. Try it with the dot in and see if it works.

If that isn't the problem you could try using one of the newer kernels. On my updated system, the latest is 2.6.31-20. You could try running those commands again, but replace 2.6.31-14 with 2.6.31-20 and see if it will boot. If not, then give 2.6.31-19 or 2.6.31-17 a try.

---

### Post by hctib on 2010-03-11
Yes dude you were right about the code number, I think I gotta it right BUT after booting the directions said to put SUDO UPDATE-GRUB2 and that did not work, says unknown sudo or something like that... any advices???

---

### Post by nitstorm on 2010-03-11
if you read the post properly ( the one by themusicalduck) it says type in

```
sudo update-grub
```

---

### Post by Alexandre Putt on 2010-03-11
> **hctib said:**
> Yes dude you were right about the code number, I think I gotta it right BUT after booting the directions said to put SUDO UPDATE-GRUB2 and that did not work, says unknown sudo or something like that... any advices???

Linux commands are case-sensitive.

---

### Post by themusicalduck on 2010-03-11
Remember you need to open a terminal (Applications > Accessories > Terminal) and type in ```
sudo update-grub
``` excatly.

---

### Post by hctib on 2010-03-12
It is unbelievable how complicated and pointless this software runs. I HAVEN'T gotten to my old files yet. Once I turn my computer with the ubuntu dvd on, I have access to the software but without any of my old configuration. After installing the 9.10 updates IT GOT EVEN MORE COMPLICATED, if i didn't have important stuff i swear i would have given up already. Is there anyway to go back to track my old files at all??

---

### Post by themusicalduck on 2010-03-12
Did you not manage to fix grub following what I outlined? You aren't clear on what has happened.. When you boot your computer up normally (ie, not from the CD but from the hard drive) can you not boot into Windows or the installed Ubuntu?

You must have done something other than install it with WUBI, because that shouldn't stop you from booting into Windows at any point.

---

