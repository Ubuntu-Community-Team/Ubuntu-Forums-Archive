---
title: "smb4k and ubuntu 10.10 networking"
date: 2010-12-06
forum: General Help
---

### Post by AgentZ86 on 2010-12-06
Hi
I have ubuntu 64 maverick 10.10

Does not work I reported this topic here too:
[https://bugs.launchpad.net/ubuntu/+source/smb4k/+bug/681156](https://bugs.launchpad.net/ubuntu/+source/smb4k/+bug/681156)

If I could use the default networking included with Ubuntu I would, but the full networking features do not appear to be available with the defaults

Sure I can browse the network and connect to samba shares and workgroups etc.

But you can't (save as) to any network location because the network location is not available in the (save-as) window
So the defaults simply don't seem to provide a full solution like smb4k does.
I use this feature all the time when creating webpages, and image albums.
Opening text documents and trying to edit or create new documents and save them to the server is useless with ubuntu defaults.
You cannot browse and (save-as) because those locations are not available on the (save-as) gnome windows with the default networking on ubuntu

Anyhow smb4k has worked well for me for years but does not work now on 10.10

Any tips to get this working would really be appreciated.
I use these features all day everyday for my ebay selling business.

I would be happy with a gnomified version of this I don't really care as long as the features are all there for networking as they are with smb4k


Please advise
Thanks

---

### Post by AgentZ86 on 2010-12-06
OK
It seems to run as root, and is normal

So now what ? 

How do I run it as a regular users like I did before ?

Please advise
Thanks

---

### Post by AgentZ86 on 2011-01-02
In 10.10 Maverick 64bit Smb4K completely useless now.

I can login as root and it will mount shares but only as read-only

If i start smb4k normally as user like I have done for years with no problems at all, it give the standard error messages that I mentioned.

I reported this to the launchpad no reponse.

Any idea ?

Please advise thanks

---

### Post by AgentZ86 on 2011-01-18
Strange

Since I did mount the shares with root, but really can't do much with it, I noticed something new here also

I used kmymoney for my accounting and always kept the file on the server

kmymoney seems to allow me to navigate as if smb4k is actually running but it's not.

kmymoney lets me navigate to the server and select my file as if it's mounted, it asks me for my server login as it normally would.

I have no idea why kmymoney would work as if smb4k is running and operating, but I'm glad it does.

However, nothing else does. smb4k still has the same problem I outlined on Ubuntu 10.10 and I have no idea why or how to fix it.

Anyone else have any problems running smb4k as it normally use to run.

Please advise
Thanks

---

### Post by piedro on 2011-02-04
hi agent! 

Yes I'm annoyed also. Smb4k should be marked as useless and just removed from all the repositories. I don't get why nobody of the developers just has the balls to say: Sorry guys, we messed up and we're not working on fixing it. Plz find some other software. 

It's obviously one of the communication problems with the free software model. I'm not annoyed that someone decides to drop the bug fixing or further development - in contrary: I'm still glad and thankful for what has been done beforehand - no, I'm annoyed by the silence on these matters leaving every user out there alone searching for solutions over and over again, wasting tons of time ... 

It's just a simple notification that's necessary. 

BTW: pyneighborhood degraded also. smb4k has a new verion for natty. I tried to install in maverick, but it messes up my sudoes file - had to fix that via recovery console ... as I said annoying! 

thx for reading, 
piedro

---

### Post by AgentZ86 on 2011-02-05
> **piedro said:**
> hi agent! 

Yes I'm annoyed also. Smb4k should be marked as useless and just removed from all the repositories. I don't get why nobody of the developers just has the balls to say: Sorry guys, we messed up and we're not working on fixing it. Plz find some other software. 

It's obviously one of the communication problems with the free software model. I'm not annoyed that someone decides to drop the bug fixing or further development - in contrary: I'm still glad and thankful for what has been done beforehand - no, I'm annoyed by the silence on these matters leaving every user out there alone searching for solutions over and over again, wasting tons of time ... 

It's just a simple notification that's necessary. 

BTW: pyneighborhood degraded also. smb4k has a new verion for natty. I tried to install in maverick, but it messes up my sudoes file - had to fix that via recovery console ... as I said annoying! 

thx for reading, 
piedro

piedro - Ahhhh, so thats what happened to my sudoes file i can't sudo any programs now

pyneighborhood - oh right because it requires something from the old LinNeighborhood which use to also work perfectly for me too, but I can't find that either.

I don't think it is so much a Smb4k issue exactly but I think it's a maverick issue in how they may have changed things but I can't be sure because it appears to be hard to identify with all my searches.

Some have suggested to include something in the fstab to get smb4k working but I don't know enough about it and having trouble understanding what I'm reading about that particular subject.

It really should just be removed from the repositories and/or marked as dead or something.

I wish I knew what to do now that I really have NO networking solution at all other then the defaults included with Ubuntu but have very little functionality other then to open a shared folder.

Other then that you have absolutely no other function for opening files/saving file to a shared location or even things such as:

For example: You want to upload a pic to facebook or perhaps a file to UPS for a damage claim or something.

You can't do any of that because as soon as you try to browse to the network location / share you can't
It does not exist in any menu so you cannot do it.

You can't upload pictures to ebay from a network share because the location is not there.
The only way to do it with ubuntu defaults are to open the network share, copy the file/folders to you desktop or ubuntu hard drive someplace, then when you go to upload images to ebay you can browse to the folders/file.

Otherwise the default ubuntu shares are also sort of useless too.

Why is this most basic feature not available on linux unless you use smb4k or something similar.

smb4k and Linneighborhood use to provide these basic network features by default ?

It is a sort of annoying subject I thought I had this solved and really enjoyed using smb4k for years on earlier ubuntu.

I may have to resort back to a previous version and dual boot just to get my work done.

Sorry for the long winded response.

Bye the way how did you fix your sudoes I can't figure out how to repair this and hate to reload everything.

Please post that solution if you have it handy.

Thanks


P.S
I also have a problem with xsane which will scan maybe one page but produces errors, for maverick
What a pain, but I can run VO Vendetta online so I guess I'll just have to play game lol

---

### Post by piedro on 2011-02-05
Hello agent! 


Maybe I can at least help you out a little: 

1. I used to add everything in /etc/fstab but since some of the ways things now are mounted by UUID changed I'm not using that anymore ... 
but if you want you're network folder to be mounted all the time it's not that complicated. You should find a lot of tutorials on that. Don't worry you can't break anything, you just add a line at the end of a file ... just make sure the tutorial is up to date! 

2. If you (like me) just want to mount different network folders for different circumstances you can just use the network browser in nautilus or dolphin. 
Add a folder by opening it. If you can't use it as you like (which for some obscure reason is often the case because a lot of programs can only process local files) do the following: 
- open the folder in the network browser 
- open another nautilus window and find the folder ".gvfs" - it's a hidden folder so make sure you checked the option "show hidden files" in nautilus
- within this folder you find all you're network folders which are locally mounted here, you can access this folder with any program (if a program is not able to show the hidden folder: create a folder named "network folders" and within that one add symlinks pointing to your network folders within the .gvfs folder. now browse this one with the problematic programs!)  
- you like to do all that even more convenient via GUI: check out  the program "gigolo" - it's in the software center 

BTW, the sudoers thing is easy to fix: 
- reboot your computer and choose "recovery console" (root console) while booting - you get a black screen root console to enter plain commands 
- enter"cd /etc" meaning "change directory to the folder /etc" 
- now enter "chmod 440 sudoers" meaning "change the permission mode on the file sudoers to 440" 
- reboot and you should be fine :-) 
- alternatively you can install a console filebrowser like "mc" (midnight commander) via softwarecenter and reboot to the recovery console afterwards, type mc to start it and work with the filebrowser interface to do the same thing ... 

[http://catcode.com/teachmod/](http://catcode.com/teachmod/) 
is just one example of a tutorial to chmod if you want to know it all! 

My last advice is: 
If you have specific questions and really want help - go to 
[http://askubuntu.com/](http://askubuntu.com/)
It's a community based q&a system, just register and jump right into it! 

phew! 
that's been a lot (and all I can do for you at this point ...), 
I hope it helps, 
cya around, 
piedro 

p.s.: No! Don't install an old version ...

---

### Post by AgentZ86 on 2011-02-05
> **piedro said:**
> Hello agent! 


Maybe I can at least help you out a little: 

1. I used to add everything in /etc/fstab but since some of the ways things now are mounted by UUID changed I'm not using that anymore ... 
but if you want you're network folder to be mounted all the time it's not that complicated. You should find a lot of tutorials on that. Don't worry you can't break anything, you just add a line at the end of a file ... just make sure the tutorial is up to date! 

2. If you (like me) just want to mount different network folders for different circumstances you can just use the network browser in nautilus or dolphin. 
Add a folder by opening it. If you can't use it as you like (which for some obscure reason is often the case because a lot of programs can only process local files) do the following: 
- open the folder in the network browser 
- open another nautilus window and find the folder ".gvfs" - it's a hidden folder so make sure you checked the option "show hidden files" in nautilus
- within this folder you find all you're network folders which are locally mounted here, you can access this folder with any program (if a program is not able to show the hidden folder: create a folder named "network folders" and within that one add symlinks pointing to your network folders within the .gvfs folder. now browse this one with the problematic programs!)  
- you like to do all that even more convenient via GUI: check out  the program "gigolo" - it's in the software center 

BTW, the sudoers thing is easy to fix: 
- reboot your computer and choose "recovery console" (root console) while booting - you get a black screen root console to enter plain commands 
- enter"cd /etc" meaning "change directory to the folder /etc" 
- now enter "chmod 440 sudoers" meaning "change the permission mode on the file sudoers to 440" 
- reboot and you should be fine :-) 
- alternatively you can install a console filebrowser like "mc" (midnight commander) via softwarecenter and reboot to the recovery console afterwards, type mc to start it and work with the filebrowser interface to do the same thing ... 

[http://catcode.com/teachmod/](http://catcode.com/teachmod/) 
is just one example of a tutorial to chmod if you want to know it all! 

My last advice is: 
If you have specific questions and really want help - go to 
[http://askubuntu.com/](http://askubuntu.com/)
It's a community based q&a system, just register and jump right into it! 

phew! 
that's been a lot (and all I can do for you at this point ...), 
I hope it helps, 
cya around, 
piedro 

p.s.: No! Don't install an old version ...

Hi
Thanks

I also was able to fix it this way by accessing the sudoers file from recovery:

I posted this on the launchpad also.

[https://bugs.launchpad.net/bugs/657900](https://bugs.launchpad.net/bugs/657900)

---

### Post by AgentZ86 on 2011-02-05
Thanks

as far as browsing to .gvfs file thats a good solution for me.

Although it's more work then I would like since I use my system to post images to the server and then post to ebay etc.

But it does work. If Ubuntu could at least allow the places list to show up when you use all the features of file use that would be better.

I have trouble understanding why that feature is not available by default since anyone who uses networking will likely need to save files to the network, open files on the network, and select files from the network to be either uploaded with the email client, uploaded to UPS for damage claims, uploaded to facebook or picasa or any image hosting site etc. 

Why ? I just don't get it.

browsing to .gvfs will work for me for now.

I could not seem to make a symlink , when I try it says target does not support symlink

Oh well back to the drawing board, for now I can browse to the .gvfs

Thanks thats still a big help.

---

### Post by piedro on 2011-02-06
Hi agent! 

that's good news! 
Really: have a look at "gigolo" - I expect this to be just right for you! 
I have it autostart and it mounts all the networkfolders I need at startup. 

For the symlink part: I've done nothing special. Maybe you have to try different folders -  like not every level is linkable. maybe a subfolder works or link the whole .gvfs? Maybe add subfolders within the .gvfs as "Places". I can't remember as I switch to Kubuntu at the moment ...

But  as I said: Use gigolo and most of your troubles should be solveable. 

Still you're right - the situation sucks. 


Good luck further on! 
piedro

---

### Post by AgentZ86 on 2011-02-06
Gigolo seems to have a similar problem as the default networking that comes with Ubuntu

Which is: lets say you want to insert and image on the Ubuntu forums
You start new reply then click manage attachments

Then attempt to browse to you share, it's not there. Nothing in places, no bookmarks that I created etc.

And I seem to have an additional problem with gigolo in that once I connect to one share on the server and create a book mark you can only create a book mark to a connection that you already have mounted, it will not let me connect to any others or create any other bookmarks. Additionally I cannot create any other mounts to the server as it gives me a Dbus error sort of thing pops up.
If I create the share then try to make a bookmark for it, then if I unmount the share, and try to click the bookmark I get the same error as well

> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I'll keep playing with it some more but it looks like the features are very similar to what is already included in ubuntu as far as shares and bookmarks go. At least from what I can tell

Thanks for the tip.

---

### Post by AgentZ86 on 2011-02-06
Well now the computer is basically dead

I added a smb line to fstab and now the computer won't boot at all

I tried to fix with nano but it says the file is read only.

I have only 2 options to S for skip or M for manual fix fstab

This option comes up for either recover mode or regular.

So at this point I cannot edit fstab to fix the machine, all because of adding one line to the fstab.

Might have to reinstall everything now just because of the simple subject of trying to get networking to function properly

What a let down

I can boot to live CD and print my fstab file, I know whats in there, but can't do any editing or even overwriting the file because it's read only.

What a long day this turned out to be
OUCH

---

### Post by AgentZ86 on 2011-02-06
Note to self:

I fixed it whew WOW I was worried

Anyhow after booting to recovery mode and boot to prompt with networking
And trying to use nano to edit the /etc/fstab file and various thing that did not work because the file locked itself and could not be edited from any live CD or from recovery mode

Basically I had to let the machine boot to regular mode which fails.
And gives me the option to hit S to skip the mounts which I do

Then I had to remount the partition with read/write so that I could edit.

Once I ran this from the consol:
> sudo mount -w -o remount /dev/sda5 the machine booted up normally 
and then I could edit the fstab file again, and from the console again I ran sudo gedit then browsed to the /etc/fstab file for editing

And removed the smb line I put in there which caused all this.

Anyhow, just FYI i'm back up and running after all that.

Now I think I need to play VO for a while.

---

### Post by piedro on 2011-02-26
glad you're back up! 

:-)

greetz, piedro

---

