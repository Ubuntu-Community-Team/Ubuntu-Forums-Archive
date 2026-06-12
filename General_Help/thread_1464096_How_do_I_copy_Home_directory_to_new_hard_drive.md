---
title: "How do I copy Home directory to new hard drive?"
date: 2010-04-27
forum: General Help
---

### Post by 3pinner on 2010-04-27
I tried using LuckyBackup but cannot seem to get it to work/
Any suggestions?
Thank You

---

### Post by xebian on 2010-04-27
> **3pinner said:**
> I tried using LuckyBackup but cannot seem to get it to work/
Any suggestions?
Thank You

Make sure it's not in use and then cp -aP <source> <dest>

---

### Post by 3pinner on 2010-04-27
Thank you, but I should have said I installed Ubuntu on a computer, and want to copy my existing Home directory from the old computer to the new one.
I partitioned the new hard disk so it has a  separate Home partition.

---

### Post by warfacegod on 2010-04-27
The most straight forward way is probably to temporarily take the old computers HDD out and put it in the new one. If the old HDD is IDE and the takes SATA then connect the drive to the ribbon cable connected to the CD-ROM, they should be the same.

---

### Post by warfacegod on 2010-04-27
Keep in mind that most of your user settings are in your Home folder and if you copy them to another install, it will start looking and acting like your old one.

---

### Post by 3pinner on 2010-04-27
> **warfacegod said:**
> Keep in mind that most of your user settings are in your Home folder and if you copy them to another install, it will start looking and acting like your old one.

Thanks for both suggestions. I am hoping that the old settings are copied to the new machine. I can always tweak them later.
As for installing the new disk in the old machine;
I used LuckyBackup (which used rsync) to backup my /Home folder on the old machine, to a USB drive. that folder has 4 user folders in it.

I would like to copy (restore) the /home backup onto the new drive, then be able to access the user accounts.

---

### Post by warfacegod on 2010-04-27
It seems like you are over thinking this. If you have an External you can literally Drag 'n Drop you home folder to it. And when it's done, connect it to the new computer, open the Home folder and move all of those folders to your new /home.

If you're looking to move your entire OS with user accounts as well, Remastersys is your friend. Find a .deb for it. It's much easier to install that way.

---

### Post by 3pinner on 2010-04-27
> **warfacegod said:**
> It seems like you are over thinking this. If you have an External you can literally Drag 'n Drop you home folder to it. And when it's done, connect it to the new computer, open the Home folder and move all of those folders to your new /home.

If you're looking to move your entire OS with user accounts as well, Remastersys is your friend. Find a .deb for it. It's much easier to install that way.

Wait a minute..........
That's waaaaaaaaaay too simple!
But I can explain:
    I come  from a Windows background :lolflag:

i'll give it a try and post back, but it won't be this evening.
 I won't have any permissions issues just copying and pasting from one home to another?
Thanks for the help!

---

### Post by warfacegod on 2010-04-27
If you have any Permissions issues, just post and I'll show you how to become the "Owner" of the drives. This is also simple.:biggrin:

---

### Post by 3pinner on 2010-04-28
> **warfacegod said:**
> If you have any Permissions issues, just post and I'll show you how to become the "Owner" of the drives. This is also simple.:biggrin:

I would like to know how to become owner of the drives.
Thank you

---

### Post by warfacegod on 2010-04-28
Open a Terminal. Applications> Accessories> Terminal

```
sudo chown -R username:usergroup /media/drivename
```

username:usergroup should be replaced with your username. If you set up the user accounts or are the only user then user group will be the same as your username.

drivename will be along string of numbers. You can find it by going to Places> Computer> filesystem> /media. Make sure you get the proper one, becoming owner of your OS partition will cause ...issues.

Here's what my code would look like (obviously this one won't work for you):

```
sudo chown -R warfacegod:warfacegod /media/8ea1854b-da0d-4dda-93cb-5996cfb0d6c8
```

---

### Post by rewyllys on 2010-04-28
> **3pinner said:**
> I tried using LuckyBackup but cannot seem to get it to work/
Any suggestions?
Thank You

Here's another possible way to copy your /home folder from your old machine to your new one.

Install Ubuntu One on your old machine and your new one.  Then copy your old machine's /home to Ubuntu One.  

Then working from your new machine, download the old machine's /home from Ubuntu One in the cloud to your new machine.  

Note: I haven't tried the above procedure myself, so I'll appreciate comments from more experienced Ubuntu One users.  What I have done, and successfully, was to use Ubuntu One for a temporary backup of a large portion of my /home folder while I made some changes to my machine that I thought were potentially risky.  The upload to Ubuntu One worked; and, after I'd made the potentially risky changes, I downloaded a few of the uploaded files from Ubuntu One just to ensure that I had the versions I wanted.  This all went smoothly.

---

### Post by warfacegod on 2010-04-28
A decent idea, however...

Ubuntu One only provides 2 GB of free storage, you'll have to pay if you want enough room to house an entire /home folder. Speed is another issue. It is much faster to move large amounts of data to an external than to upload it.

The other drawback, at least in your case, what happens if your changes go very badly and you can't even boot your computer to access the net to get your backup?

---

### Post by philinux on 2010-04-28
I used a usb stick ext4 formatted.

---

### Post by rewyllys on 2010-04-28
> **warfacegod said:**
> . . . Ubuntu One only provides 2 GB of free storage, you'll have to pay if you want enough room to house an entire /home folder. . . .

Good point, but 3pinner's /home folder may be smaller than one might think.  For example, on the laptop I'm using at the moment, the /home directory (to which I've never worried about adding more files) contains only 908MB, less than half of the 2GB free quota in Ubuntu One.

---

### Post by warfacegod on 2010-04-28
> **rewyllys said:**
> Good point, but 3pinner's /home folder may be smaller than one might think.  For example, on the laptop I'm using at the moment, the /home directory (to which I've never worried about adding more files) contains only 908MB, less than half of the 2GB free quota in Ubuntu One.

I have something like 600 GB so I tend to think other folks have similar amounts. Although, I would image that most folks do at least have more than 2 GB.

---

### Post by 3pinner on 2010-04-28
thank you all for the suggestions. this thread will be worth bookmarking for later use.
I am going to just try copying the home folder (or the user folder I really want) on the old machine, and pasting into the home folder on the new machine.
I will post back with results for anyone else that may need assistance, as I assume this is a pretty common occurrence.

---

### Post by 3pinner on 2010-04-28
OK next problem.
I am trying to copy one of the user folders to a memory stick to transfer it to the new computer and getting permissions errors.
I formatted the memory stick  to Ext3, gave myself ownership of the memory stick, opened terminal, entered sudo nautilus, copied the user folder I wanted,and when I go to paste it, I get an immediate error:

The folder ".gvfs" cannot be handled because you do not have permissions to read it.

So I don't think I have full permissions to copy a folder in home (that is not mine) and paste it into another drive (the memory stick)
So what should I do?
Thanks

---

### Post by warfacegod on 2010-04-28
Hit Alt+F2> type gksudo nautilus> Enter> password.

The new file browser that opens will have root privileges. So browse to the file you want to copy and do so.

FAIR WARNING: Being root can be very dangerous. Be certain you do exactly what you want to do. Delete the wrong file by accident and you'll likely regret it.

---

### Post by 3pinner on 2010-04-28
thank you, I'll give it a shot, and i am aware of the potentials of working as root.
Thanks

---

### Post by 3pinner on 2010-04-28
After running gksudo nautilus, I try to copy the folder (lorrim) from home to the memory stick and now get this error:

Files in the folder "lorrim" cannot be handled because you do not have permissions to see them.

lorrim is not my folder, its another user on this computer,and I am trying to move their home folder to the new computer.
Thanks

---

### Post by ttshivers on 2010-04-28
Is it that hard just to backup your home directory?

---

### Post by warfacegod on 2010-04-28
> **3pinner said:**
> After running gksudo nautilus, I try to copy the folder (lorrim) from home to the memory stick and now get this error:

Files in the folder "lorrim" cannot be handled because you do not have permissions to see them.

lorrim is not my folder, its another user on this computer,and I am trying to move their home folder to the new computer.
Thanks

Is the folder encrypted? I can access any folder or file on my family computer using my own user account and password and then become root.

---

### Post by 3pinner on 2010-04-28
> **ttshivers said:**
> Is it that hard just to backup your home directory?

no I'm an idiot.

---

### Post by 3pinner on 2010-04-28
> **warfacegod said:**
> Is the folder encrypted? I can access any folder or file on my family computer using my own user account and password and then become root.

no its not encrypted, but I have been fooling around with permissions (both mine and the lorrim account) to see if I can find the right combination to move her folder.
As it stands now:
my account name is anyname
I am in group anyname 
(I guess that is the default way the system works, if the account name is 'x' then you are in group 'x'

for the lorrim account
it is in group lorrim

would that make any difference?

---

### Post by Leppie on 2010-04-28
you create a compressed backup of your home folder:
```
tar -cvpzf backup-home.tar.gz /home/
```
you can unpack it on your new system like this:
```
tar -xvpf backup-home.tar.gz
```

---

### Post by warfacegod on 2010-04-28
> **3pinner said:**
> no its not encrypted, but I have been fooling around with permissions (both mine and the lorrim account) to see if I can find the right combination to move her folder.
As it stands now:
my account name is anyname
I am in group anyname 
(I guess that is the default way the system works, if the account name is 'x' then you are in group 'x'

for the lorrim account
it is in group lorrim

would that make any difference?

It might. Try changing your group to lorrim. System> Admin.> User & Groups.

---

### Post by warfacegod on 2010-04-28
> **Leppie said:**
> you create a compressed backup of your home folder:
```
tar -cvpzf backup-home.tar.gz /home/
```
you can unpack it on your new system like this:
```
tar -xvpf backup-home.tar.gz
```

Hi Leppie. Was wondering if you'd see this one. 3pinner doesn't own the home folder. Its someones else's on the same computer. We're trying to get everything moved over to a new computer.

Which brings up a thought. Where's this lorrim with the password. Why don't they move their own stuff?

---

### Post by 3pinner on 2010-04-28
thank you leppie,
I'll add this to the list of stuff to try, but it won't be today.
duty calls!
I'll post back tomorrow, but now I'm curious as to the permissions issue.

In windows, I could log on as admin and do whatever I wanted to with any file. I would assume running nautilus as root (either sudo nautilus or gksudo nautilus) should give me the same freedom. I'll have to research that a bit.

---

### Post by Leppie on 2010-04-28
> **warfacegod said:**
> Hi Leppie. Was wondering if you'd see this one. 3pinner doesn't own the home folder. Its someones else's on the same computer. We're trying to get everything moved over to a new computer.

Which brings up a thought. Where's this lorrim with the password. Why don't they move their own stuff?
hullo my friend, you know that i like annoying issues ... lol

the "p" switch causes the user permissions to be preserved ;)
if you don't have read access, throw a "sudo" in front of the whole shebang.

---

### Post by 3pinner on 2010-04-28
not really an annoying issue, but a puzzling one for me!
Another clue:
using gksudo, I can copy any of the other account folders to the memory stick, except the lorrim one (the one I need) so I wonder if there is a permissions or group issue involved????

---

### Post by 3pinner on 2010-04-28
> **warfacegod said:**
> Hi Leppie. Was wondering if you'd see this one. 3pinner doesn't own the home folder. Its someones else's on the same computer. We're trying to get everything moved over to a new computer.

Which brings up a thought. Where's this lorrim with the password. Why don't they move their own stuff?

my usual instructions to lorrim:
heres the on button, heres the keyboard, there is the mouse. you can use these applications. don't touch anything else  :)

---

### Post by warfacegod on 2010-04-28
> **3pinner said:**
> not really an annoying issue, but a puzzling one for me!
Another clue:
using gksudo, I can copy any of the other account folders to the memory stick, except the lorrim one (the one I need) so I wonder if there is a permissions or group issue involved????

Which makes me think the folder is encrypted. Browsing as root should give you near omnipotent powers (usually to break your system:P). Encryption is the only thing I can thing of that would stop root dead in its tracks.

---

### Post by Leppie on 2010-04-28
> **3pinner said:**
> not really an annoying issue, but a puzzling one for me!
Another clue:
using gksudo, I can copy any of the other account folders to the memory stick, except the lorrim one (the one I need) so I wonder if there is a permissions or group issue involved????
launch nautilus in superuser mode:
```
gksudo nautilus
```
browse to the "lorim" folder and check the file permissions.

---

### Post by warfacegod on 2010-04-28
> **3pinner said:**
> my usual instructions to lorrim:
heres the on button, heres the keyboard, there is the mouse. you can use these applications. don't touch anything else  :)

That's what I used to have to tell my wife in Windows. Now with Ubuntu, she *can't* break it. ...And if she does, she can fix it herself. Because I won't.:biggrin:

---

### Post by Leppie on 2010-04-28
> **warfacegod said:**
> That's what I used to have to tell my wife in Windows. Now with Ubuntu, she *can't* break it. ...And if she does, she can fix it herself. Because I won't.:biggrin:
hahaha...
but i don't think lorim would have encrypted her home folder...

[3pinner]("http://ubuntuforums.org/member.php?u=68064"), could you post the output of the following command:
```
id lorrim
```

---

### Post by 3pinner on 2010-04-28
owner: lorrim
folder access: create and delete files
file access ------

Group lorrim
folder access: access files
file access: -----

Others:
folder access: access files
file access: ----

---

### Post by 3pinner on 2010-04-28
forgot to add, encryption is not checked in the menu box, so I assume it is not encrypted.

---

### Post by 3pinner on 2010-04-28
One other clue:
I  temporarily added to her privileges 'administer the system" so I could log on as her, then ran gksudo nautilus and tried to copy the folder, getting the same error message that I dont have the privilege to view the files.
MOre interesting by the minute.

---

### Post by Leppie on 2010-04-28
> **3pinner said:**
> One other clue:
I  temporarily added to her privileges 'administer the system" so I could log on as her, then ran gksudo nautilus and tried to copy the folder, getting the same error message that I dont have the privilege to view the files.
MOre interesting by the minute.
so either her home folder is corrupt, or you really messed up the user permissions... lol
could you still post the results of the id command?

---

### Post by 3pinner on 2010-04-28
Yet another clue.
I tried the obvious (see - I am an idiot, but a happy one)
I just opened the folder using gksudo nautilus and as of right now am copying the files from it to the memory stick.
I'll herd them into a new lorrim folder before pasting into the new hard drive.
Leppie - I will try the tar copy later

and for everybody else - no it really isnt this hard to backup a home folder. I'm just learning other things here, thanks to the helpful forum members.

---

### Post by 3pinner on 2010-04-28
sorry, don't really know how to output this properly but here goes:
uid=1002(lorrim) gid=1002(lorrim) groups=1002(lorrim),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),114(netdev),123(admin),1004(qstrt)

---

### Post by Leppie on 2010-04-28
the id output looks ok.
if you can copy using nautilus in superuser mode, the tar will work with sudo:
```
sudo tar -cvpzf backup-home.tar.gz /home/
```

---

### Post by 3pinner on 2010-04-28
thank you, I will give it a try tomorrow.

Thank you both for the help, I will post back with results.

---

### Post by 3pinner on 2010-04-28
I think I found the issue - why I could not copy the lorrim folder.
I ended up opening users and groups and checking who was in her lorrim group.
Nothing was checked, so I added myself (anyname) and root and some others, logged off, then logged on tried to copy using gksudo nautilus and it started right away.
So it was a group membership problem. Pretty obvious now that I think about it.

Now that I've finished hijacking my own thread:

Leppie: is the tar command you gave me the simplest way to move home from one HDD to another?

and where are the preferences stored - I assume if I copy her home folder to an new HDD with a new installation of Ubuntu, those preferences will come up when she logs in to the new machine?

---

### Post by warfacegod on 2010-04-28
> **3pinner said:**
> I think I found the issue - why I could not copy the lorrim folder.
I ended up opening users and groups and checking who was in her lorrim group.
Nothing was checked, so I added myself (anyname) and root and some others, logged off, then logged on tried to copy using gksudo nautilus and it started right away.
So it was a group membership problem. Pretty obvious now that I think about it.

Now that I've finished hijacking my own thread:

Leppie: is the tar command you gave me the simplest way to move home from one HDD to another?

and where are the preferences stored - I assume if I copy her home folder to an new HDD with a new installation of Ubuntu, those preferences will come up when she logs in to the new machine?

:rolleyes:](*,):biggrin: You know, I *did*, tell you to change usergroup like 20 posts ago.

Somehow, I suspect Leppie's still going to try and take credit for this.

---

### Post by 3pinner on 2010-04-28
if he does, just tell me the correct address to send the beer, and we'll all be happy

Thanks for the help.

---

### Post by gadolinio on 2010-04-28
> **3pinner said:**
> OK next problem.
I am trying to copy one of the user folders to a memory stick to transfer it to the new computer and getting permissions errors.
I formatted the memory stick  to Ext3, gave myself ownership of the memory stick, opened terminal, entered sudo nautilus, copied the user folder I wanted,and when I go to paste it, I get an immediate error:

The folder ".gvfs" cannot be handled because you do not have permissions to read it.

So I don't think I have full permissions to copy a folder in home (that is not mine) and paste it into another drive (the memory stick)
So what should I do?
Thanks


I agree with [warfacegod]("http://ubuntuforums.org/member.php?u=537200"): the copy/paste is OK. I've done that and it worked out well.

Regarding permissions on the copies in the external drive: as far as I've seen, when you copy a file or folder you own to a USB thumb, the copied files are automatically owned by root and have all permissions granted for every user. So when you copy then from the external drive to the new HD there should be no trouble. You'll be allowed to copy those files owned by root , and once they're in your new /home/username they'll be owned by you again (i mean, by the user with which you copied them from the USB to the HD). 

Regarding the post I quoted: i think the problem is that you are not allowed to access another user's files from the one you're using. (Errrr even I don't understand what I'm saying). I mean: if you have four users, A, B, C, and D, and login as A, you can copy A's files to the external drive, but not all of B's, C's, and D's. I'd login as B, copy B's files, then login as C, and the same with all. Once the files are in the memory stick they'll be all root's and you'll be able to copy them inside the current user's folder, again. That is, if you create four new users in the other computer, I think you'll need to do the same to give each of them a copy (A's files to new user "E", B's files to new user "F", etc).

Hope you find this useful...

---

### Post by gadolinio on 2010-04-28
Q: What happens when you open a thread, leave your computer for some time, and then reply to the thread? 
A: you find out that after making your post the topic is over, and the issue was somewhat bigger than you thought. :S
Haha!
Now, just wondering: could a liveCD help in a case like this? Or, as a last resource, logging in as root?

---

### Post by Leppie on 2010-04-29
i'm pretty sure that playing around with permissions lorrim's home folder got messed up. i copy home folders as with superuser permissions all the time and never really had any issues unless the files were corrupt.

using the tar command you should be able to copy the complete contents of the home folder in one go, preserving all the permissions for files and folders. so i guess, yes it is the easiest way to copy the home folder if you have several user accounts on your system. just remember that the user accounts on the new system have to match the ones on the old system, in particular pay attention to the uid and gid which have to be the same as those on the system you're copying from.

---

### Post by warfacegod on 2010-04-29
This has turned into quite a big deal for something I initially said was quite easy. LiveCD is another possibility.

---

### Post by 3pinner on 2010-04-29
> **warfacegod said:**
> This has turned into quite a big deal for something I initially said was quite easy. LiveCD is another possibility.

Well that was my fault. I overlooked a simple group membership issue, and made it more work than necessary.

so the simple answer is;
copy & paste, either logging on as root or as the user. I had to add myself to lorrim group to  have the permissions to move the folder. It was some kind of a fluke I'm sure, as I had no problems moving any of the other folders in Home to the memory stick. Just the lorrim one.
but its where i want it now!

---

### Post by Leppie on 2010-04-29
well, group memberships do not really matter if you copy using sudo or gksudo.
of course, if the user's main group was empty (hence lorrim wasn't in the lorrim group either), things can get a bit more complicated.

---

### Post by 3pinner on 2010-04-29
> **Leppie said:**
> well, group memberships do not really matter if you copy using sudo or gksudo.
of course, if the user's main group was empty (hence lorrim wasn't in the lorrim group either), things can get a bit more complicated.

Interesting - so as good general practice, who should be in a users group other than the user themselves? admin? root? anyone else?

Thanks

---

### Post by Leppie on 2010-04-29
> **3pinner said:**
> Interesting - so as good general practice, who should be in a users group other than the user themselves? admin? root? anyone else?

Thanks
i sometimes put myself in other users' groups in order to be able to access files with my normal account. root normally doesn't need to be in any other group, permissions are implicit.

---

### Post by warfacegod on 2010-05-01
I'm the only one on my laptop so I don't need to add myself to anything there.

On my family computer, I have made everyone a part of my group but I haven't noticed any difference. I still have to log in to my account to do anything of any importance.

---

### Post by Leppie on 2010-05-04
group memberships usually provide read access only, which would work for copying files.

---

### Post by warfacegod on 2010-05-04
> **Leppie said:**
> group memberships usually provide read access only, which would work for copying files.

I had that access before adding them to my usergroup. In fact, I'm pretty sure I already had write access too.

---

### Post by Leppie on 2010-05-04
> **warfacegod said:**
> I had that access before adding them to my usergroup.
that normally depends on what permissions are used for the parent directory.

> In fact, I'm pretty sure I already had write access too.
i don't believe that's the standard setup. i can write in any directory using sudo, but without it i only have read access to other peoples' home folders.

---

### Post by KPDXHAM on 2010-05-04
> **Leppie said:**
> launch nautilus in superuser mode:
```
gksudo nautilus
```browse to the "lorim" folder and check the file permissions.

**THANKS **to Leppie, I'm finally able to copy & paste folders between partitions and drives.

Hooray!!!!

---

### Post by Leppie on 2010-05-04
> **KPDXHAM said:**
> **THANKS **to Leppie, I'm finally able to copy & paste folders between partitions and drives.

Hooray!!!!
i'm glad it was of use to you :)

---

### Post by jerome1232 on 2010-05-04
Just to add, .gvfs is a very special folder, that error is normal. I forget exactly what it is but it houses a virtual file-system something or the other for fuse. Fuse is a daemon (if I'm remembering correctly) that allows regular users to mount ntfs drives and such.



So basically the error about .gvfs is fine, ignore it. Your copy should be fine.

---

### Post by KPDXHAM on 2010-05-05
> **Leppie said:**
> i'm glad it was of use to you :)

Either I spoke too soon,OR I did something wrong. 
I used "gksudo nautilus" and carefully made sure which partitions I was working with.
Having installed a fresh Karmic Koala on a second partition on the same HDD, I wanted to copy my home folder to the new location.

[LIST=1]
[*]I located both home folders
[*]Opened both of them
[*]Highlighted and copied everything in the source folder
[*]Pasted everything into the target folder
[/LIST]
After un-mounting everything and rebooting into the new install I was disappointed to see that my desktop link icons pretty much all had locks on them!
After finding out that a few other things were not working properly also I decided to start over. So, now I have another fresh install besides the original on this same drive.

When I install I have setup like this so that from what I've read over the past few months, I should be able to copy my /home to new location or back it up.

/root/home/swap 

Would anyone like to help this poor old dummy?:?

---

### Post by Jpenguin on 2010-05-05
chmod -R 777 ~/
(not very secure though)

GRSync copies and has an option to keep permisions, mabe you should try that

---

### Post by KPDXHAM on 2010-05-05
> **Jpenguin said:**
> chmod -R 777 ~/
(not very secure though)

GRSync copies and has an option to keep permisions, mabe you should try that

Thanks Jpenguin,
Have you used GRSync in this manner or similar?

---

### Post by Jpenguin on 2010-05-05
> **KPDXHAM said:**
> Thanks Jpenguin,
Have you used GRSync in this manner or similar?

I use GRSync to backup /home to a 2nd HD

---

### Post by KPDXHAM on 2010-05-05
> **Jpenguin said:**
> I use GRSync to backup /home to a 2nd HD

Are you just backing up the folder to a partition for safe storage or do you have another complete OS that you backup into?

Sorry for all the questions! I've been playing around with this Linux for over 6 months now and have had to reinstall systems several times for various reasons besides the fact I'm obviously a novice.

---

### Post by Leppie on 2010-05-07
> **KPDXHAM said:**
> Either I spoke too soon,OR I did something wrong.
I used "gksudo nautilus" and carefully made sure which partitions I was working with.
Having installed a fresh Karmic Koala on a second partition on the same HDD, I wanted to copy my home folder to the new location.

   1. I located both home folders
   2. Opened both of them
   3. Highlighted and copied everything in the source folder
   4. Pasted everything into the target folder

After un-mounting everything and rebooting into the new install I was disappointed to see that my desktop link icons pretty much all had locks on them!
that's because plain copying the folders with nautilus isn't the correct way as permission are lost during the copy process.
to copy your home folders, use the following command to create a compressed archive of all home folders as i wrote in post #43:
```
sudo tar -cvpzf backup-home.tar.gz /home/
```
copy the archive to the new system and unpack like this:
```
sudo tar -xvpf backup-home.tar.gz
```

---

### Post by srs5694 on 2010-05-07
> **Leppie said:**
> that's because plain copying the folders with nautilus isn't the correct way as permission are lost during the copy process.
to copy your home folders, use the following command to create a compressed archive of all home folders as i wrote in post #43:
```
sudo tar -cvpzf backup-home.tar.gz /home/
```copy the archive to the new system and unpack like this:
```
sudo tar -xvpf backup-home.tar.gz
```

You can combine these two commands into one, with no need for the temporary storage. Suppose you want to copy everything from /home to /newhome. You do:

```

cd /home
sudo tar cpf - ./ | (cd /newhome; sudo tar xvpf -)

```

There are other ways to achieve the same goal, too. I believe rsync will do the job, for instance, although I don't know the precise options off the top of my head. (I've used the tar pipeline enough times to copy entire systems that I know it pretty well.)

---

### Post by warfacegod on 2010-05-07
rsync has a fairly useful GUI called grsync. Its available in Synaptic.

---

### Post by KPDXHAM on 2010-05-07
> **warfacegod said:**
> rsync has a fairly useful GUI called grsync. Its available in Synaptic.

Thanks for all the helps!
I'll try the commands when I may have time later this morning. I've tried Grsync a couple times and get error messages when I do the simulation.
Right now I have this tweaked install I'm using now as my primary Linux and one other partition with a fresh install that I'll try to copy this /home into.

I know it's simple for those who know how to do it, or those who understand the commands, or perhaps even algebra or calculus. I'm not there yet, but will keep trying until the light comes on.

---

### Post by warfacegod on 2010-05-07
> **KPDXHAM said:**
> Thanks for all the helps!
I'll try the commands when I may have time later this morning. I've tried Grsync a couple times and get error messages when I do the simulation.
Right now I have this tweaked install I'm using now as my primary Linux and one other partition with a fresh install that I'll try to copy this /home into.

I know it's simple for those who know how to do it, or those who understand the commands, or perhaps even algebra or calculus. I'm not there yet, but will keep trying until the light comes on.

Perhaps man will be of some help. Put man in front of a command in the Terminal and you'll get an explanation of it.

Example: ```
man lshw
```

---

### Post by KPDXHAM on 2010-05-07
> **Leppie said:**
> that's because plain copying the folders with nautilus isn't the correct way as permission are lost during the copy process.
to copy your home folders, use the following command to create a compressed archive of all home folders as i wrote in post #43:
```
sudo tar -cvpzf backup-home.tar.gz /home/
```copy the archive to the new system and unpack like this:
```
sudo tar -xvpf backup-home.tar.gz
```

Should this be done from a live cd or does it make any difference?

---

### Post by warfacegod on 2010-05-07
Shouldn't make any difference.

---

### Post by KPDXHAM on 2010-05-07
> **warfacegod said:**
> Shouldn't make any difference.


Thanks.

---

### Post by KPDXHAM on 2010-05-17
> **Leppie said:**
> that's because plain copying the folders with nautilus isn't the correct way as permission are lost during the copy process.
to copy your home folders, use the following command to create a compressed archive of all home folders as i wrote in post #43:
```
sudo tar -cvpzf backup-home.tar.gz /home/
```copy the archive to the new system and unpack like this:
```
sudo tar -xvpf backup-home.tar.gz
```

I followed these commands exactly and ended up at the destination HDD with 2 Homes! (See Screen shot) I guess I got a bonus...2 fer one...!

[[IMG]http://img295.imageshack.us/img295/7684/20516063.th.png[/IMG]]("http://img295.imageshack.us/i/20516063.png/")  Uploaded with [ImageShack.us]("http://imageshack.us")

Looks like I goofed, eh?:confused:

---

### Post by warfacegod on 2010-05-17
Good grief,this one again?! :P

Perhaps I'm a total idjit but I only see one Home.

---

### Post by KPDXHAM on 2010-05-17
> **warfacegod said:**
> Good grief,this one again?! :P

Perhaps I'm a total idjit but I only see one Home.

Sorry. :(

[[IMG]http://img708.imageshack.us/img708/9581/editpreviewphp.th.png[/IMG]]("http://ubuntuforums.org/[URL=http://img708.imageshack.us/i/editpreviewphp.png/)%20%20Uploaded%20with%20"][/URL][[IMG]http://img708.imageshack.us/img708/9581/editpreviewphp.th.png[/IMG]]("http://img708.imageshack.us/i/editpreviewphp.png/")  Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by warfacegod on 2010-05-17
Yep, I'm an idjit. So now you have a home folder inside of a home folder. Sigh...:P Can you move *that* one?

---

### Post by warfacegod on 2010-05-17
Have you considered logging in as root?

---

### Post by KPDXHAM on 2010-05-17
Sorry for lack of patience, but at present I'm reformatting that 500GB HDD and will try again. This time I'll just zip my documents, music, etc. and not bother trying to transfer settings.

Thanks for the help.:P

Cliff

---

### Post by warfacegod on 2010-05-17
Why don't you have any patience? Get tired of the whole thing?

---

### Post by KPDXHAM on 2010-05-17
Disregard. I've taken another route.

Thanks for the help. :)

---

### Post by Leppie on 2010-06-23
> **KPDXHAM said:**
> I followed these commands exactly and ended up at the destination HDD with 2 Homes! (See Screen shot) I guess I got a bonus...2 fer one...!

Looks like I goofed, eh?:confused:
i know it's a late reply, but this is the result of executing that command in your home folder without specifying the destination folder. this could've been avoided by either specifying the destination folder, or cd-ing into the root folder.

---

