---
title: "The age old &quot;shares don't work&quot; question (10.04)"
date: 2010-05-01
forum: General Help
---

### Post by smiley2billion on 2010-05-01
So I've taken a break from Ubuntu recently but decided to give 10.04 a spin and loaded it up on my media server machine.

I've got everything set up and working except for one major part: Network shares.  Specifically SMB network shares.

I know that 10.04 has a feature where you can right click any folder and click "Sharing Options" and proceed to install the proper packages and have a shared folder.  The only problem with this seemingly simple solution is that it doesn't work.  I'd really like to avoid having to manually edit the smb.conf file like in days past, but I think it's going to be my only option.

For clarification I'll give an overview of my current set up and where it breaks down.

1) Ubuntu 10.04 machine that is the main media hub. It has several hard drives, all of which are working fine and can play media locally.

2) Windows 7 desktop used to playback media from media server.

3) Popcorn Hour A110 used to playback media from media server.

None of the other machines/devices I have can actually browse my shared folders.  I can see the folders on both the Windows "network" browser (and drill down to the next folder level, eg. /media/DriveX) and the Popcorn Hour STB but I can't actually browse the folder that the media is in.  Windows complains that it can't find the location and I should check my spelling while the Popcorn Hour gives a similar error message about the location not being found.

The weird thing is that I can see the media server, I can see the folder I want to look in, but once I tell the device to open the folder it acts like it is suddenly gone.  I'm pretty sure this boils down to a permissions error somewhere, but I can't find it for the life of me.

In short, I hate SMB file sharing and wish I could find an alternate no log in simple way to share my media to all my network devices....   also, help?

---

### Post by smiley2billion on 2010-05-01
I should also mention that I've already tried various ways to fix this by using tools that help with sharing files (system-config-samba) and even edit my smb.conf to make sure that every "guest access" flag is proper and that the share are actually pointing to the correct location, and everything seems to be in order.

If anyone knew what was being edited when you share a folder through the GUI using the "Sharing Options" feature that'd be great to know too, as it doesn't seem to be the smb.conf file.

Thanks again.

---

### Post by smiley2billion on 2010-05-01
An update on some things I've tried.

I CAN go to any folder that exists on the main hard drive that ubuntu boots from and share any folder there, such as my "Documents" folder.  I can add and remove files from the windows client just fine.  This was using the "Sharing Options" menu item after right clicking on a folder, so I'm pretty positive this can be solved by figuring out what permissions need to be set for a second hard drive that will allow it to be shared this way as well.

I'll continue to update this as I figure out what's going on so that maybe it'll help someone in the same situation.

---

### Post by smiley2billion on 2010-05-01
Some progress made.

If you use the menu item "Sharing Options" to share the drive by going to Places > Computer > File System > Media > drivename  then this process seems to work.

Even if you go inside of the drive "drivename" and share individual folders they'll show up and work as well, however, if you unshare the original "drivename" those shares you made of the individual folders will no longer work.  This is beyond a mystery as to why this behaves like this.  It does give a different error message in Windows, instead of the folder not being found anymore, it's just simply not accessible.  Once a re-enable the share on the drive itself the once unaccessible share then works again.

It's not all roses just yet, as there's some files that are not working still inside of those folders.  I'm trying to determine if it matters how those files were created and put in those folders (existing files vs. files that I've put in there since installing 10.04) that's effecting this.

[update]  It was the permissions for the files that weren't playing.  If you look at the properties of those files the Permissions must be set for group and others for read access.

---

### Post by smiley2billion on 2010-05-01
Alright, mission accomplished.

I just had to share the entire drive under Computer>File System>Media before anything would work.

Now that I've done that every share I create inside of the secondary drive shows up just fine for all my devices.  The problem I was having with only a few of the media files being able to be played back was with how sabnzbd created new folders and files.  I've fixed that under that programs configuration and it looks like I'm all set.


I hope this thread helps someone with a similar problem.

As an aside, I love the new version of Ubuntu, there's a real sense of progress here since the last time I used it, however, the sharing was a little insane to get working properly.  Hope this gets even more simple in the future.

---

