---
title: "Where are my ubuntu files kept on XP?"
date: 2010-12-05
forum: General Help
---

### Post by Toadmund on 2010-12-05
Wubi borked on me, would not boot into Ubuntu, so I installed Ubuntu on it's own partition, now I need to transfer the old wubi home partition to the new install.

Where in XP does wubi put the Ubuntu files?

---

### Post by coffeecat on 2010-12-05
This from the official Wubi guide on mounting the wubi root disk from a live CD:

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

You should be able to adapt that by mounting the Windows XP partition from your Ubuntu installation and substituting your mountpoint where necessary.

---

### Post by Toadmund on 2010-12-05
Thanks, but all I want to do is cut and paste my 'home' and relevant files from wubi on windows XP partition, to my new dedicated Ubuntu partition.

Where are my Ubuntu files stored on XP?


Use the 'KISS' principle please.

---

### Post by coffeecat on 2010-12-05
Simply mount your wubi root.disk according to those instructions and then browse the root.disk where it's mounted in /vdisk to your wubi home folder. I don't know how I could make it much simpler. Do you want a step-by-step howto? I assumed that since you've been an active member for more than 3 years you'd follow the principles, but if you want a more detailed guide, I'm happy to help.

---

### Post by Rubi1200 on 2010-12-05
To access your Wubi files from Windows, you can use  [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

---

### Post by Toadmund on 2010-12-05
I wish to access wubi, but not install it.

I do not wish to complicate things and screw things up, I have other things to do today.
So I must run my live cd and do stuff through it like you say? I cannot simply go to the windows files and cut and paste them over as they are not to be found that way, correct?

---

### Post by Rubi1200 on 2010-12-05
Not to seem pedantic, but did you see what I previously posted?

You can use that program I linked to to read and copy the files from the old Wubi install on the XP partition.

It works from **within** Windows, so no need to use a LiveCD etc.

---

### Post by coffeecat on 2010-12-05
> **Toadmund said:**
> I wish to access wubi, but not install it.

I do not wish to complicate things and screw things up, I have other things to do today.

I have already told you how to access the wubi root disk through Ubuntu and no, you don't have to use a live CD if you don't want to. Rubi1200 has told you how to access the wubi root disk through Windows. So you have a choice. And, as I said before, I am happy to give you clear and fuller directions, but I also have other things to do and I want to be sure that the time I take in giving you simple instructions won't be wasted.

---

### Post by Toadmund on 2010-12-05
> **Rubi1200 said:**
> Not to seem pedantic, but did you see what I previously posted?

You can use that program I linked to to read and copy the files from the old Wubi install on the XP partition.

It works from **within** Windows, so no need to use a LiveCD etc.
Yes, I dl'd the program, however, I am only able to access /dev/sdb1 where my fresh Ubuntu install is, whereas the windows xp partition is /dev/sda (?) which I cannot seem to find.

---

### Post by Toadmund on 2010-12-05
> **coffeecat said:**
> I have already told you how to access the wubi root disk through Ubuntu and no, you don't have to use a live CD if you don't want to. Rubi1200 has told you how to access the wubi root disk through Windows. So you have a choice.

I will use the live cd now to get to this 'wubi root disk' sorry for being so thick, I am really thick headed today as I am not able to dive right into this.

---

### Post by Toadmund on 2010-12-05
> **coffeecat said:**
> Simply mount your wubi root.disk according to those instructions and then browse the root.disk where it's mounted in /vdisk to your wubi home folder. I don't know how I could make it much simpler. Do you want a step-by-step howto? I assumed that since you've been an active member for more than 3 years you'd follow the principles, but if you want a more detailed guide, I'm happy to help.
Thanks, I see my files in vdisk now.
Thanks very much.

---

### Post by Toadmund on 2010-12-05
Problem now is my inability to cut and paste/drag items over, perhaps later I will try booting up without the live cd, find vdisk there(?) or use a usb stick with the live cd.

---

### Post by coffeecat on 2010-12-05
> **Toadmund said:**
> Problem now is my inability to cut and paste/drag items over, perhaps later I will try booting up without the live cd, find vdisk there(?) or use a usb stick with the live cd.

I'm sorry to hear you're encountering problems copying/dragging items. You were using the live CD, correct?  In your wubi install, and in your hard drive install, the first created used has a UID (user identity) of 1000. Unfortunately, the 'ubuntu' account in the live session has a UID of 99 or 501 or something - certainly different from 1000. So you get a permissions problem. If you were to mount the wubi root.disk from your hard drive install you probably won't encounter this particular problem. That is so long as you only have one account in wubi and in your hard drive version. If you have more than one account, the UID for the second will be 1001, and so on.

Alternatively, you could open a root nautilus with 'sudo nautilus' but that *might* transfer ownership to root in the copying. Easily corrected, but an irritation if it occurs.

What happens when you try to copy files? I'm sure it's easily solved. In the meantime you might want to consider mounting the wubi root.disk from your hard drive Ubuntu. It might be easier in the long run.

---

### Post by Toadmund on 2010-12-05
> **coffeecat said:**
>  If you were to mount the wubi root.disk from your hard drive install you probably won't encounter this particular problem. That is so long as you only have one account in wubi and in your hard drive version. 

Thanks, I was thinking that as the live cd has permission issues I think.

I got my... (well; her) home back.

Much appreciated!

Now, to get those bookmarks back?

---

### Post by coffeecat on 2010-12-06
> **Toadmund said:**
> Now, to get those bookmarks back?

/home/username/.mozilla/firefox/randomstring.default/bookmarkbackups. Copy the most recent *.json file. Note that .mozilla is a hidden folder and that the randomstring.default folder really does have an unpredictable random string in its name. Then in the firefox you want to restore the bookmarks to, Bookmarks > Organise Bookmarks > Import and Backup > Restore.

---

### Post by Toadmund on 2010-12-06
All done, thanks a lot!

Appreciated.:guitar:

---

### Post by IndyGunFreak on 2010-12-06
Just another reason to hate wubi.. :)

Glad you got it working!

---

### Post by Toadmund on 2010-12-07
Well, WUBI was good for the reason I needed it for, I am glad it exists now.
But I was eager to get this Ubuntu from riding on MS coat-tails and on to it's own partition. This computer was given to me by my father with MS on it. Then I discovered WUBI and tried it out.

I wanted Ubuntu on this computer FAST, and WUBI filled that need.

PS, WUBI will get more people on Ubuntu than burning an image, partitioning and all that jazz, although WUBI screwed up on me for whatever reason (update broke it?) I think it is a very good thing for the growth of Linux.

---

### Post by coffeecat on 2010-12-07
> **Toadmund said:**
> PS, WUBI will get more people on Ubuntu than burning an image, partitioning and all that jazz, although WUBI screwed up on me for whatever reason (update broke it?) I think it is a very good thing for the growth of Linux.

I think that's a very good point. It's a pity Wubi does break sometimes, but I think some people are too hard on it. Fiddling about with partitions and bootloaders does scare people off. Particularly when the grub os-prober fails to pick up the presence of Windows. :-s

Anyway, I'm glad you've sorted it.

Happy Ubuntuing! :)

---

### Post by Rubi1200 on 2010-12-07
Wubi has its issues, yes, though to be fair to the developers they could probably not have foreseen the flood of posts here on the forums that would arise as a result of something that they were not responsible for, namely, GRUB updates which are breaking Wubi.

For more information, troubleshooting, and solutions see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

