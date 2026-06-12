---
title: "Transfering files from USB HD to Ubuntu hides them"
date: 2010-03-23
forum: General Help
---

### Post by Scunnered on 2010-03-23
I have been informed that as icons are displayed on my desktop that indicates that the files copied from a USB Hard Drive to the Ubuntu system have been hidden.  This seems strange as the files appear in my home folder but as I hate clutter on my screen if I delete the icons the data totally disappears from the Ubuntu system.

My original action was to copy from XP to a USB HD the information that I wished to backup.  Having now done that I connected the HD to the Ubuntu system and copied everything over from there.  It is at this point that icons start appearing on the screen.  When everything is complete I can see that the data is in /home/my name which is fine but if I delete any icon all is lost.

To see if I could replicate the problem I connected the USB HD to my laptop and repeated the operation only to find that in this instance everything appeared as expected.

I am now well confused and would appreciate your guidance in the matter.

---

### Post by pbrane on 2010-03-23
Sounds like you are copying files to ~/Desktop. I don't know why icons would appear on your desktop otherwise. The only icon that may appear is the mounted USB HD itself.

---

### Post by Scunnered on 2010-03-23
**pbrane**

Why would I be copying as you say when using exactly the same method of opening up the /home folder and pasting into it the data that on one system shows up as being hidden and on the other works perfectly.  Surely they both should work exactly the same?

No files are given a dot before the name so they should not be consigned to the hidden section of the system.

It is the inconsistance that is blowing my mind.

---

### Post by pbrane on 2010-03-23
One would think that the two would be the same. I have no idea why those icons show up on your desktop in one but not the other computer. If you find a solution please post back.

---

### Post by dcstar on 2010-03-23
> **Scunnered said:**
> 
Why would I be copying as you say when using exactly the same method of opening up the /home folder and pasting into it the data **that on one system** shows up as being hidden and on the other works perfectly.  Surely they both should work exactly the same?
........

Only **if** they are set up the same, your assumption that they are is invalid.

There is a Gconf setting to make the "Home Folder" as the Desktop, one system has this set and the other has the default of the "Desktop" folder as the actual desktop.

---

### Post by houseworkshy on 2010-03-24
It variance between computers does seem odd, could it be something to do with account types?  Meanwhile you could try renameing ( remove the dot ) and see if that works as a tempory fix.

---

### Post by Scunnered on 2010-03-24
**dcstar**

You state "*There is a Gconf setting to make the "Home Folder" as the Desktop*" which is complete news to me.  Mind you at my level of experience many things in Ubuntu are.

The only difference that I can think of is that the old system that I am using for storage is a 32 bit system whilst the laptop is 64 bit. As I am the only user each system was identical in set up other that the 32 or 64 bits. This was the reason that I fully expected each would act in the same fashion.

My problem is therefore with the 32 bit system as it is there that the icons needlessly appear and when deleted remove the data from the system.

Can you please expand on the Gconf setting.  Where do I find it and what am I looking for ?  

**pbrane**

Have no fear I will mark my post as solved whenever it is achieved. dcstar may have hit on the answer and I hope that his assistance will resolve matters.

**houseworkshy**

As I state earlier in this post everything is identical in set up other than the bits 32 or 64.  None of the files were marked with the dot preceeding the name so the addition of it I suspect wont help.

My thanks to everyone for their contributions.

---

### Post by Scunnered on 2010-03-25
Bump

---

### Post by houseworkshy on 2010-03-25
This is a long winded bump with a couple of ideas rather than a solution as I haven't encountered this one before. 
   First I may not have been clear about the renaming bit, I meant removing the dot to unhide not adding one which of course would hide.   
The thing about accounts you can see by example.  If you boot up as an administer and then open a guest account the guest can use any of the programs installed by the administer but not use or see his/her files.  In this case the guest can not unhide the administer files so the idea is only in the area not the same. 
 If it does have something to do with accounts and permissions then right clicking on a file and having a look at the permissions could be informative.  As would connecting the usb and taking a look at System>Authorisations and System>Users and Groups. I'm guessing that the answer is in there.  As the 32 bit and 64 bit are very similar discovering differences between their respective set-ups may give a strong hint as to what is going on.

---

### Post by Scunnered on 2010-03-25
**houseworkshy**

Thanks for your reply.
  
This is where my limited experience shows up yet again.  As I am the sole user on both the 32 bit and 64 bit systems when I downloaded Karmic both were identical in their set up with one exception that being the user name. The 32 bit as this was going to be on a network was identified differently so that there would be no confusion between systems.  My question is one of the guest account as I have never conciously use a guest account. How does this work particularly as a guest account has not been set up by me?

Your remark about the dreaded dot does not apply.  At no time the information which is stored on the 32 bit system was marked to be hidden yet somehow or other it gets that way.

Looking at permissions other than the owner differing the permissions are identical. Going to the USB HD there is no system on the drive as it was being used purely for the purposes of transfering from firstly XP to the drive and subsequently to the 32 bit system.  

What I did see differing was that opening a folder on the USB drive the properties did not permit folder access for the Group and Others whilst on both systems Access File is allowed. I when connecting to the 32 bit on the network I also find that it is identical to the other 2. If I attempt to change the file on the USB drive it will not allow a change reverting to None in both instances.

I am at a total loss on this so any further assistance you can offer will be most appreciated.

Again my sincere thanks for your assistance

---

### Post by dcstar on 2010-03-26
> **Scunnered said:**
> **dcstar**

You state "*There is a Gconf setting to make the "Home Folder" as the Desktop*" which is complete news to me.  Mind you at my level of experience many things in Ubuntu are.

The only difference that I can think of is that the old system that I am using for storage is a 32 bit system whilst the laptop is 64 bit. As I am the only user each system was identical in set up other that the 32 or 64 bits. This was the reason that I fully expected each would act in the same fashion.

My problem is therefore with the 32 bit system as it is there that the icons needlessly appear and when deleted remove the data from the system.

Can you please expand on the Gconf setting.  Where do I find it and what am I looking for ?  

```
gconf-editor
```
/apps/nautilus/preferences/desktop_is_home_dir

*If set to true, then Nautilus will use the user's home folder as the desktop. If it is false, then it will use ~/Desktop as the desktop. *

---

### Post by Scunnered on 2010-03-26
**dcstar**

Many thanks for your reply.  

Prior to your post I Googled Gconf and when I saw what was there is ran scared.Had I not been presented with your concise instruction I would have run a mile with all the various options on view.

Having followed your guidance I went to the 32 bit system and found that the setting was marked as false so I re-set it to true.  Copied a folder over from the USB drive and found that again it still displayed on the desktop.  

I had a look at the laptop and strangely enough it also displayed as false but it does not shift the data on to the desktop. 

By now I am well confused and as Lucid is on the horizon and it was my intention to go with the next LTS offering I think that I will leave things in abeyance until sometime in May and see how things work then.  Meantime I will keep backing up on the USB drive.

Once Lucid in installed on both systems I will report back.

My sincere thanks for your assistance.

---

### Post by AndyDeGroo on 2010-03-26
If that option in gconf-editor is marked as false, leave it that way or uncheck to make it false.

Could it be that by some mistake the Desktop directory is a symlink to your home directory?

You can check if this is the case by running following command in terminal:
```
ls -lF ~
```which lists contents of your home directory.
And look for entry with arrow (->) which point to your home directory.
That may look like this:
```
lrwxrwxrwx 1 user  user  9 2010-03-27 01:26 Desktop -> /home/user
```If that is true, solution would be to remove that symlink from console:
```
rm -r Desktop
``` But be careful - **do not add slash after Desktop** because that will delete contents of your home directory.

And if symlink is not the cause of problem, try creating new user account and log on with that account to see if problem persists.

I hope this helps.

---

### Post by Scunnered on 2010-03-28
AndyDeGroo

Many thanks for your post

I dont know what is going on but no matter what is advised I am unable to get things to work as described.

In this instance following your advice I get the following result:

scunnered@scunnered-desktop:~$ ls -lF ~
total 12
drwx------ 11 scunnered scunnered 4096 2010-03-21 10:38 Brenda/
drwxr-xr-x  5 scunnered scunnered 4096 2009-12-05 11:00 Inchinnan/
drwxr-xr-x  9 scunnered scunnered 4096 2010-02-25 09:53 My Music/
scunnered@scunnered-desktop:~$ 

These 3 items listed are the result of my copying from the USB drive to my home folder.

Unless you know where this is going wrong I think that I will wait on the next version 10.04 and load this on all my machines and see what results.

---

### Post by Scunnered on 2010-04-26
I am unsure what happened this time around however things are back to normal.

I loaded Lucid beta 2 and currently am on the RC and was able to copy data over to the system and this time it arrived in /home as expected.  

Will mark this as solved and expand on it later if I can see how I managed things

---

