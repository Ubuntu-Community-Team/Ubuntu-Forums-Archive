---
title: "newbie transferring files &amp; settings from windows, networking..."
date: 2009-08-20
forum: General Help
---

### Post by loosie on 2009-08-20
Hi, Just started using a liveCD Ubuntu desktop version, after Windows crashed on me. Got a few newbie issues....

First & foremost, I want to rescue my files & settings from the machine asap, because it's been suggested that the HD's on it's way out. Can drag & drop from the file browser, but would like to know how to import settings & the likes too. 

I also had my computers working in a network on Window & would like to know how I might network them using this system(Ubuntu on one, Windows on another)? That would be the easiest way of rescuing my files & settings, as it's my other machine which has the DVD burner, not this one.

I was going to load Ubuntu on my machine, side by side with Windows, at least until I've worked out how to get everything from Windows, but because it has to shrink the Windows partition to do that, it sounds like I'll lose my data. Is there some way I can load it onto the HD without risk of losing my stuff??

Thanks people, to anyone who answers. Your help is much appreciated!

---

### Post by treehouse on 2009-08-21
I take it from your post that you have more than one computer. What I would do if it were me, is take the hard drive with the files you need to recover, and simply put it in the other computer, and transfer them to the other hard drive, or burn them to CD/DVD on the other computer. Then when everything's backed up you can put it back in the original box and reinstall whichever operating system you choose to use on it (assuming the HD's still savvy).

As far as I know, you can't really do proper networking and file transfer from the live CD, you'll need to have it fully installed to do that kind of stuff.

There is also the possibility of repartitioning and saving all of the Windows stuff when you repartition, but I'm not an expert on partitioning. The main problem you might run into is that usually you are supposed to defragment a Windows drive before repartitioning it, so all of the data is collected in one section of the drive and there is less of a chance of overwriting it. If you want to go this route, I would be sure to double check that the partitioning program you use is capable of working around a non-defragmented drive, or find some utility that you can use to defragment first.

---

### Post by stinger30au on 2009-08-21
to rescue data from windows pc then u need to use windows ultimate boot cd

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

it has some very handy utils to do it with

---

### Post by The Cog on 2009-08-21
You can do networking from the live CD. Use the menu Places > Connect to server..., but I agree with treehouse it may be best to unplug the drive and install it on another machine temporarily, just to copy the files off. That way, you're not struggling with an unfamiliar operating system at the same time as trying to rescue a broken one.

---

### Post by loosie on 2009-08-21
Hi,

Tried to download UBD twice & it came up as files corrupted(after the hours of downloading). Do you know of a source/mirror that's reliable? I clicked on the first & second ones on the download page of that site. Also, it sounds like I need a genuine XP CD? 

I'm a bit scared of pulling my computers apart to slave the drives. Will I need extra cables? Will I need to change settings, etc?? 

Yes, it looks like I will need to install Ubuntu in order to network the computers. Someone on another forum mentioned I'd need Samba in order to network them properly, which is apparently on Ubuntu already. Will I have to load that or change anything in the Windows machine too?

Repartitioning Windows seems to be a prob too. I was going to install Ubuntu, but when it got to the repartitioning bit, it warned that my data may be lost, so I chickened out. Just bought a 16gb flash drive off ebay, but haven't got it yet. ATM I only have a 1gb drive, which is how I've been transferring files... talk about tedious,:popcorn: when I only have one screen & keyboard, which I have to keep changing to the different machines in order to use them, but we're getting there! Once I finish getting everything off it, I'll then load Ubuntu & reformat Windows.

---

### Post by The Cog on 2009-08-22
You can do networking from a live CD. Just like I said. You only need samba if you are going to share files from Ubuntu - samba is file server software.

Please make sure you have a good backup after this little excercise. I learned the hard way that a hard drive failure can happen any time to anyone, without warning.

---

### Post by loosie on 2009-08-22
> **The Cog said:**
> Please make sure you have a good backup after this little excercise. I learned the hard way that a hard drive failure can happen any time to anyone, without warning.

Yes, thanks for the reminder. After this happening to me a few years ago, I have been backing everything up regularly to DVD. Alas, I tend to do it every week or 2 and I'd had a particularly big couple of weeks since doing it last:(.

You wouldn't read about it, but after trying so many options before using Ubuntu, after spending eons transferring files with only a 1gb thumb drive, I switched on the machine & forgot to press any key to boot from the CD.... & it started fine in Windows, networking & all!

So now, considering the probs, I'm not sure whether to reformat & load Ubuntu, load it on the other machine, use it just as a LiveCD... any opinions on the whys & wherefores?? I want to keep one machine with Windows, at least until I know my way around Ubuntu & work out if it'll do everything I need it to...

If I loaded it on my secondary computer(that which I've been using since the crash), should the network work the same for it as for Windows? My secondary 'puter's got less RAM & is quite slow ATM with Windows. Please excuse all the convoluted questions...

---

### Post by HiImTye on 2009-08-22
tbh I would stick with Windows on whatever computer you use most frequently if that is what you are most familiar with and mess around on Ubuntu on the other one to get the 'feel' of it until you decide whether you like it or not (and whether or not it can do what you need it to do - or until you get fed up with Windows, which seems to be the case for alot of Ubuntu users)

this way you can always have an operating system you are used to and can do everything you *need* it to do and you can still play around with the shiny new toy

as for SAMBA you only need to set it up on the Ubuntu computer as it is the windows filesharing protocol so windows already has it

---

### Post by loosie on 2009-08-22
Thanks very much for your help Guys, 

I'm sure I'll be back, but consider me satisfied with the answers I've got. I'm on my way:popcorn:

---

### Post by treehouse on 2009-08-28
> **loosie said:**
> Hi,


I'm a bit scared of pulling my computers apart to slave the drives. Will I need extra cables? Will I need to change settings, etc?? 


Sorry for the lateness of my reply. If you resort to slaving the drive to another computer, you shouldn't need extra cables. Most drives (made in the last decade) are already configured to automatically choose whether they are master or slave based on cable position AFAIK. There are numerous tutorials around the internet about installing drives that are comprehensive on the subject, but it should really only involve pulling it out of the old computer, and plugging into the new computer. You should have all the cables you need, and the new drive should plug into the port next to the old drive.

---

### Post by loosie on 2009-08-28
Thanks for that. After a few more hiccups - there were errors in Windows that I couldn't fix, due to Windows taking up so much space, the partition for Ubuntu was tiny... I ditched Windows after all! 

Now I need to know how to delete other partitions to make this one bigger. I have the Partition Editor, but resize & delete are not options for those partitions for some reason.

I have been able to access my files through the MS network off my other Windows computer, but I also need to know how to configure it for a Remote Desktop, so I can actually use the programs in it too - & transfer files to it as well as from it??

---

