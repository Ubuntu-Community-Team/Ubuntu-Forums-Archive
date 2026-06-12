---
title: "Out of disk space. Any tips?"
date: 2006-05-09
forum: General Help
---

### Post by glotz on 2006-05-09
Hi there!

I'm owner of a very small disk, which has now reached it's capacity. Great! ](*,)  Is there something I could get rid of to make some space? I found out that Synaptic package manager had some cache I cleared and recovered some 200 megs! That's sweet! Any other things to check?

Thanks for any heads ups!

---

### Post by aysiu on 2006-05-09
Try installing *deborphan* to isolate what packages are "orphaned" and, thus, can be removed.

In Dapper, there's a graphical version called [*gtkorphan*](http://www.marzocca.net/linux/gtkorphan.html).

---

### Post by oyvindaa on 2006-05-09
Maybe you should just buy a new harddrive? They're very cheap nowadays! :)

---

### Post by Sef on 2006-05-09
Had a similar problem.  Check out this link.

[http://ubuntuforums.org/showthread.php?t=166240&highlight=trash]("http://ubuntuforums.org/showthread.php?t=166240&highlight=trash")

---

### Post by glotz on 2006-05-09
Thank you all for your speedy replies. I searched this forum with keyword orpha* and came up with this [General - HOWTO: Cleaning up all those unnecessary junk files](http://www.ubuntuforums.org/showthread.php?t=140920). Following your tips and it, I reclaimed some 20 additional megs. I guess I could go to the store too...

So, now the chips aren't so down any more, let's raise the bet shall we? I've used Synaptic to install  [The Ur-Quan Masters](http://www.ubuntuforums.org/showthread.php?t=169640) game. Along with the additional music and voice packages, it takes about 200 megs. Seems to have been installed to /usr/games/share. Is it possible to move it to another disk? How would I go about it? :confused:

I currently dual boot and I have this 'common data disk' HD that's in FAT32 filesystem. Would the non-native filesystem cause any problems if it's possible to move the game? Is there something more to this? Again, thanks for reading this!

---

### Post by Herman on 2006-05-09
I just got home from one of my bi-annual trips to a 'city' (Cairns, Australia, only about twelve hours by road from where I live), and I picked up a couple of USB portable hard drive disk boxes for 2.5" HDD's. They were only around $20.00 each (One Australian Dollar = roughly $0.75 US maybe?). Anyway I consider them a bargian. I had a couple of spare 2.5" (laptop size) hard drives kicking around not really being used for much. Those cost around $120 (Australian) each new. That's not too expensive either in my opinion. They'll hold a few DVD's worth of data each. One's 30.0 GB and the other is 40.0 GB.
And for ease of use! :D Well, really, in Ubuntu (Dapper) they are just plug'n play, and I'd also have to say drag'n drop too.
I am now firmly convinced that everyone should have a USB drive!  A USB hard-drive of any description would be great. If you're on a tight budget maybe see if you can get an old second-hand hard drive from somewhere. You'll really be happy you did! ;) Regards, Herman.

Edit: I'd keep software like games and the like in the main Ubuntu operating system disk and ship out stuff like data files and all that type of thing to the other disk. It won't matter if it's FAT32 for your data, but I use ext3 now.

---

### Post by glotz on 2006-05-09
Offtopic (person worshipping):
Whoa, Herman! Believe it or not but I installed (Ubuntu) Linux not least because of your double booting instructions website! Great job dude! LiveCDs are nice but the difference with LiveCDs and real installs is like the one between girlfriends and wives! You only know for sure, when your up to your neck in it! :)

---

### Post by Herman on 2006-05-09
Thanks, glotz, it's always nice to be able to be helpful to someone. Mr Shuttleworth is really the one we all need to remember to thank for giving us Ubuntu and the developers, the forum moderators, staff, sponsors, and lots of other people working behind the scenes too.  And Aysiu and Sef and azz,  Iha and others answereing a lot of the forum questions. It's a great community! He-he, what I do is miniscule compared with all those others. Thanks for the reply though, it's always nice. I think everyone has a lot of fun with Ubuntu and helps each other at the same time.

Anyhow, how big is this disk of yours? I started off dual booting with a 6.0 GB disk and at the time it seemed okay, but I just like messing with software and learning how to use it. I don't store very many files. Can you fit all your software on your small disk and your files on the other one maybe? :D (Herman)

---

### Post by rcarring on 2006-05-09
I have a 100GB external hard disk complete in caddy (cost $70) that is connected via a USB 2.0 port to the computer I use.

On the external drive I have various hard files to do with Vmware and MSVPC virtual machines.

I had to delete a Windows Server and an XP installation's hard files to make room for the Ubuntu vmware boxes =D

Slightly OT, I ran out of disk space on one of the vms, as it was situated on a Fat32 drive that only allows files up to but no larger than 4GB in size.

---

### Post by glotz on 2006-05-09
My disk is also a 6 gig disk. And the windows partition (NTFS) on it is even slightly bigger than my Linux partition... Then I've got a 80 gig (FAT32) data disk. Yeah, it seemed like a good idea back then but now I'm feeling rather claustrophobic! I think I must rethink my configuration. Suppose I free some space on the big disk. Can it somehow be used to append my existing ext3 partition? Or is there a stop at the shop on my todo list?

I agree that it's a great community. Thanks to everybody for it!

---

### Post by Herman on 2006-05-09
> I have a 100GB external hard disk complete in caddy (cost $70) that is connected via a USB 2.0 port to the computer I use. Gee, rcarring, I was expecting around 75% difference in price, but that's more like 50% less !
Heck, at those kind of prices an extra hard disk would seem  to be worth considering.

glotz, you could avoid buying another hard-disk by copying a lot of that data to CDs or DVDs and re-installing your Windows operating systems on your 80,0 GB disk maybe. It does Windows a lot of good to be re-installed regularly anyway, and it will work  better on a bigger disk with more disk space. Windows needs plenty of extra space for the defrag utility to shuffle files around, so I have read.

Ubuntu installs improve with age, like a good wine. I'm starting to form the opinion that it's nice to keep a Ubuntu install as long as possible. If you do decide to re-install, it would be worth waiting a little and upgrading right to Dapper. 
If you decide to keep it on your 6.0 GB disk, you could run the latest GParted LiveCD maybe and delete the old Windows partition. Copy your entire Ubuntu partition and paste it to the the beginning of the disk, in the free space where Windows used to be. 
I am presuming there will be room, you can paste a partition to a larger area of free space but not to a smaller one, so you will need to do your mathematics and a little planning ahead first. Maybe you'll need to remove data and resize Ubuntu smaller before copying it.
After pasting your copy of your Ubuntu partition to the free space, delete the original Ubuntu partition and re-size the new copy of it to take up the whole disk. (Except for your swap area of course). Re-install GRUB and edit /etc/fstab with your new partition numbers. That way you'll have room for all the extra software (games etc) you want.
You might not have room to put back all your data you backed up onto CD-ROMs or DVDs though.

Really, for the amount of time and effort you might spend, a new, larger hard-disk seems like the only real answer. You could use the 6.0 GB drive as an external USB drive maybe. I think you'll be a lot happier in the long run with a newer, larger, hard-drive. Replacing a hard drive is as easy as replacing a light bulb nowadays, and even on a older computer it isn't too difficult. Even if you don't want to do it yourself, it should not cost very much to have a technician do the job for you, it should only take around half an hour perhaps. Of course, this could vary quite a lot depending on the design of your computer case.
All the best, Regards, Herman. :D

Edit: After all that, I just realized there's a snag in that plan in the middle paragraph. You would have to check up whether or not it's legal to install Windows onto another disk, I think you might not be supposed to, but there might be some clause that allows you to if you still have the original disk or something like that. I'm not sure. Otherwise I guess you'd need to do it the other way around and install Ubuntu to your 80.0 GB disk. That would be a nice, simple way of doing things.

---

### Post by glotz on 2006-05-09
Thank you for all your help. I'm yet undecided how to do it but it's nice to know my options.

---

### Post by glotz on 2006-09-08
I've since formatted my small disk and am now (since some time) Ubuntu all the way. I just found another source to look at when looking for wasted disk space. It's the root's trash. /root/.Trash

Just recovered a few hundred megs. I guess my gksudo nautilus adventures piled them there and I forgot all about them. :-D

---

