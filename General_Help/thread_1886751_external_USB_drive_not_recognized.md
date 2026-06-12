---
title: "external USB drive not recognized"
date: 2011-11-25
forum: General Help
---

### Post by choochoousmc on 2011-11-25
[SIZE=2]try this again
Using Ububtu 11.04       seagate freeaent go 350 gig usb ext HD.
everything was fine until 1 day boom!!
I plug in the ext USB.  Ubuntu won't recognize it at all, no matter what I do.  Even using terminal commands.
Plug it into windows 7
                         shows up in directory tree, and can read and write to it.    BUT
                         right click drive to get menu, to eject or safely remove....... No option to do so
  So drive is not fully recognized.

Back over to the Ubuntu computer: Now plug it back in get this error (paraphrase)  Drive was unexpectedly
removed from a windows computer without using a safe remove or eject option.

Says to run chkdisk on the drive in Windows.   Fine,   but I can't as Chkdsk does NOT recognize the drive being there.

Seagate is no help, as they don't support Linux (they said) and don't recommend using the drive in Linux.

I'm thinking the original partition table has been damaged.   Would format it, But Ubuntu doesn't even see the drive. And windows can't complete the format.

Anybody know of a LOW LEVEL format tool that will access it either in Linux or windows And allow a full complete low level format back to factory std's and then I can try reformatting?[/SIZE]
TIA

---

### Post by raja.genupula on 2011-11-25
```
lsusb
```

show me the output

---

### Post by oldtimer7777 on 2011-11-25
Did you upgrade to 11.10 from 11.04 recently, because there was an issue similar to this..  In 11.10 they removed ntfs-3g package.

This usually fixes it:

sudo apt-get install ntfs-3g

> **choochoousmc said:**
> [SIZE=2]try this again
Using Ububtu 11.04       seagate freeaent go 350 gig usb ext HD.
everything was fine until 1 day boom!!
I plug in the ext USB.  Ubuntu won't recognize it at all, no matter what I do.  Even using terminal commands.
Plug it into windows 7
                         shows up in directory tree, and can read and write to it.    BUT
                         right click drive to get menu, to eject or safely remove....... No option to do so
  So drive is not fully recognized.

Back over to the Ubuntu computer: Now plug it back in get this error (paraphrase)  Drive was unexpectedly
removed from a windows computer without using a safe remove or eject option.

Says to run chkdisk on the drive in Windows.   Fine,   but I can't as Chkdsk does NOT recognize the drive being there.

Seagate is no help, as they don't support Linux (they said) and don't recommend using the drive in Linux.

I'm thinking the original partition table has been damaged.   Would format it, But Ubuntu doesn't even see the drive. And windows can't complete the format.

Anybody know of a LOW LEVEL format tool that will access it either in Linux or windows And allow a full complete low level format back to factory std's and then I can try reformatting?[/SIZE]
TIA

---

### Post by choochoousmc on 2011-11-25
> **raja.genupula said:**
> ```
lsusb
```show me the output

[SIZE=2]Output you requested is below:   But something strange just happened.  I have two identical ext USB drives.
Been having same problems with both BUT:
The problem started with one drive, It has important files on it.
I tried the extra drive and got the same problem   BUT since nothing important on it, I have been using it to try to fix the problem.
Formatting did not work neither did chkdsk  etc.
I was using 11.04 when it happened.
did a fresh install of 11.10  still did not fix.
could NOT stand unity and the way 11.10 was being sluggish.
So wiped my internal drive and went back to 11.04 with a fresh install and rebuilt all my directories and data etc.

Now following your request: I plugged the drive in. Voila!!  after almost two months, now Ubuntu recognizes the one drive.[/SIZE]   will try the other later.

[B][SIZE=2]Here is the output from lsusb
[/SIZE][/B]
[SIZE=2]ubuntu@ubuntu-Aspire-5532:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bc2:2120 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu-Aspire-5532:~$ [/SIZE]

So now that it is finally recognized, what would you suggest I do:   Erase the partition and rebuild it.
Reformat:   I need windows & linux compatibility so which  Fat or NTFS?

thanks

---

### Post by choochoousmc on 2011-11-25
> **oldtimer7777 said:**
> Did you upgrade to 11.10 from 11.04 recently, because there was an issue similar to this..  In 11.10 they removed ntfs-3g package.

This usually fixes it:

sudo apt-get install ntfs-3g


I did the command you suggested, along with several others that were previously suggested a month ago.
Totally corrupted the 11.10 upgrade.
I wiped my internal hard drive and did a fresh install of 11.10 still same problems.
wipe the drive again and went back to 11.04  all my other issues went away. Except the ext usb drive problem.

Another thing that happened in 11.10  I tried formatting the usb drive. It formatted it as read only.
Now why in the h3ll do that. No data on the drive and drive is useless. People told me how to correct that. And it did. But as I said there were too many issues with 11.10, so went back to 11.04.
see my other quoted reply to the lsusb post here.
thanks for your input.

---

### Post by choochoousmc on 2011-11-25
I just plugged the one drive back into windows after safely removing from Ubuntu. 
Win 7 recognizes it in the directory tree and I can read and write to it still.
But the right click menu still does not offer the eject button.
So I will shut down windows and see what happens.

Also the other drive, the one where the problem began in the first place is again being recognized by
Ubuntu, and I can again do a safe remove with it. 

I don't know why, it just all of a sudden started working again after about 2 months!!!!!

Now I will put it back into the Win7 computer, try to copy the data to Win 7, then see if the eject is back over there.   If not will shut windows down again and remove it (PIA).

Then will copy the info to the other drive, make sure it still works in Ubuntu, then if it does it will be dedicated to the Ubuntu Machine.
Then the one with the original problem, will dry to do a low level format on it. If I can, and get the safe remove / eject option back in windows, then I will see what Ubuntu does with it.

This has been a nightmare and still no reason why it happened or a solution.!!

gremlins I guess!!

---

### Post by choochoousmc on 2011-11-25
Well that didn't work.
I copied the files to Win7 hard drive, then over to the other USB seagte.
connected to the Ubuntu computer.
Ubuntu could read all the folders, but none of the files in the folders.
Video, pics, text, would not read.
But yet the same files copied onto a USB stick, it could read.

Chkdsk, did not find any errors....... yes I got it to run on one drive.

But yet Ubuntu popped up an error saying the drive was defective either physically or logically.
Also Drive utility will delete and create a partition and mount and unmount it.
But sometimes during mount it can't decide if it is a 195 or 350 gig or a 2.2 tg.
Actually it is 350 g
So something is totally confusing Ubuntu.
I'm running chkdsk /f on drive now  It just finished and said it had found problems and fixed them.
So will try a reformat again and see what happens.

If anybody has any idea what is happening and something to try let me know.

---

### Post by raja.genupula on 2011-11-25
By the output what i can say is 
your USB recognized . well in this we have a suggestion for automount USB

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by choochoousmc on 2011-11-26
> **raja.genupula said:**
> By the output what i can say is 
your USB recognized . well in this we have a suggestion for automount USB

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
Yes I have read that page before, and have left automount on.
Basically under 11.04 I was using a usb powered 4 way hub. Plugged a usb stick into it and the usb ext seagate hard drive. did this for several months so I could transfer files back and forth as needed.
when done I always used the safe remove and waited for lights to go out.
One day right after connecting both, everything went hay wire.
Could no longer mount the ext drive, stick worked fine.

Now currently: Usb stick still works fine. Now the USB ext drive mounts, but Ubuntu can not read the data on it, only opens and closes the folders and files.
And if it fails to mount it has the error, physical or logical damage. If logical place in a windows machine and run chkdsk /f.   DID that, copied new files to it, put back in Ubuntu.
Still can't read and still says run chkdsk again.
so either Ubuntu is confused, or chkdsk really is not fixing the problem.
So I am going to try the low level format to completely wipe the drive and then re partition and format it.
But I need windows compatibility for work. So stuck with FAT or NTFS

Thanks, and if you think of something I will try as soon as possible so check back when you have time.

---

### Post by raja.genupula on 2011-11-26
Man , i wanna say something .

Sometimes eventhough everything is good , we are going to have isssues . I too have faced issue like this  all my drives are mounting with only read attribute, no solution , what i did to resolve this is keep updating my system. 

so keep updating my system.

---

### Post by oldtimer7777 on 2011-11-26
I hear you.  

But they removed ntfs-3g package from 11.10.

You will need to always reinstall it in 11.10 to read -and- write to NTFS.  No way around it.

> **raja.genupula said:**
> Man , i wanna say something .

Sometimes eventhough everything is good , we are going to have isssues . I too have faced issue like this  all my drives are mounting with only read attribute, no solution , what i did to resolve this is keep updating my system. 

so keep updating my system.

---

### Post by fdrake on 2011-11-27
plug your usb and post the results of these commands:
```

mount
sudo fdisk -l


```

---

### Post by choochoousmc on 2011-11-27
> **raja.genupula said:**
> Man , i wanna say something .

Sometimes eventhough everything is good , we are going to have isssues . I too have faced issue like this  all my drives are mounting with only read attribute, no solution , what i did to resolve this is keep updating my system. 

so keep updating my system.

I did update, but the issues got worse not better.

---

### Post by choochoousmc on 2011-11-27
continuation but here's something new.
Because the drive is not reliable.  But I thought it was.
I tried building a truecrypt volume  Failed in the middle and warning to do chkdsk again
So back to win 7  chkdsk did not find any errors

So I went ahead and did the low level format. Theoretically drive should be wiped and ALL zeroes.
Then using WIN 7 to reformat back to NTFS  everything seemed fine

Brought back to Ubuntu.
The true crypt volume was still there!

Plus the drive would mount about a minute later it would unmount, then remount all on it's own.
And again could not decide if it was 190gig, 320 gig or 2.2 tg.
Driving me crazy.

Drive utility will not check file system unless unmounted. So I unmount from there, run the check.
A window pops up instantly saying it is good.

Well the drive is under warranty so think I will return it and hope a new one works.
But still can use all the info tips tricks you all think I should try. A learning experience if nothing else.

---

### Post by oldtimer7777 on 2011-11-27
Don't forget to mark your thread as "solved" at the top. 

It is always good to use new parts when attempting something like this too. 

> **choochoousmc said:**
> continuation but here's something new.
Because the drive is not reliable.  But I thought it was.
I tried building a truecrypt volume  Failed in the middle and warning to do chkdsk again
So back to win 7  chkdsk did not find any errors

So I went ahead and did the low level format. Theoretically drive should be wiped and ALL zeroes.
Then using WIN 7 to reformat back to NTFS  everything seemed fine

Brought back to Ubuntu.
The true crypt volume was still there!

Plus the drive would mount about a minute later it would unmount, then remount all on it's own.
And again could not decide if it was 190gig, 320 gig or 2.2 tg.
Driving me crazy.

Drive utility will not check file system unless unmounted. So I unmount from there, run the check.
A window pops up instantly saying it is good.

Well the drive is under warranty so think I will return it and hope a new one works.
But still can use all the info tips tricks you all think I should try. A learning experience if nothing else.

---

