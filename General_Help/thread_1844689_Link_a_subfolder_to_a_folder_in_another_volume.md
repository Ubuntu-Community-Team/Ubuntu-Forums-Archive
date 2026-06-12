---
title: "Link a subfolder to a folder in another volume"
date: 2011-09-15
forum: General Help
---

### Post by eh? on 2011-09-15
I have a folder on an ubuntu server that I have built which contains a file structure for storing various types of media (for iTunes on a Mac)
The folder is shared and it works pretty well and looks like this:

media-
          |-Music
          |-Movies
          |-TV Shows


my problem is that the volume containing this folder is beginning to get a bit full and I want to relocated the TV Shows folder to another drive with loads of free space that I have mounted under /home

I have copied the folder TV Shows to /home/media/TV Shows

I have renamed the original TV Shows folder and attempted to create a link in the original location to the destination on the other volume. 

I tried these:
sudo ln -s "/home/media/TV Shows" "./TV Shows"
This sort of worked and on the ubuntu server if I changed to the TV Shows folder it was as if that folder still existed in the original location. But if I browse to that location via the share on another computer, the link appeared as a file rather than a folder and I couldn't get to the files in the new location.

So I removed the link and tried another way:

sudo ln -d "/home/media/TV Shows" "./TV Shows"

This throws up an error because my destination for the link is on another device:

ln: creating hard link `./TV Shows' => `/home/media/TV Shows': Invalid cross-device link

Can anybody suggest a way for me to accomplish what I am trying to achieve?

(If it is any advantage, I am using LVM, however the volume mounted under /home contains some data that I want to avoid erasing, so I don't think I can simply extend the size of my existing volume into this other drive. )

---

### Post by Morbius1 on 2011-09-15
Give this a shot and see if it does what you want:
```
sudo mount --bind /home/media/"TV Shows" /path/to/original/"TV Shows"
```If it does what you want you can create an Upstart job that will bind it at boot or even add it to rc.local ( above the exit 0 line ).

---

### Post by eh? on 2011-09-15
Thanks Morbius1
That works beautifully.

I added this to /etc/rc.local as suggested but not rebooted yet to see if it sticks.

```
sudo mount --bind /home/media/"TV Shows" /media/media/itunes/iTunes/"TV Shows"

```

---

### Post by Morbius1 on 2011-09-15
Get rid of the sudo. It's not necessary if you put it in rc.local since it's run by root already.

If it doesn't work in rc.local ( there may be a race condition where the bind is executed before the parent partition is mounted ) you can set up an upstart job:

Create an upstart file:
```
gksu gedit /etc/init/bind-mount.conf
```With content that looks something like this:
```
# Bind Remounts
#
description "Bind /home/media subdirectories to someplace else"
start on stopped mountall

script
mount --bind /home/media/"TV Shows" /media/media/itunes/iTunes/"TV Shows"
end script
```The "start on stopped mountall" will make sure the bind doesn't happen until everything specified in fstab is mounted first.

Then issue the following command to execute the upstart job so that you can check for any errors before you do an actual reboot:
```
sudo initctl start bind-mount
```

---

### Post by eh? on 2011-09-19
Thank you, I went with your upstart scenario and that works very well.
I may have to roll it back as this doesn't seem to play well with netatalk / afpd

Whenever I drop content into iTunes, it copies it to the Ubuntu server using netatalk and places it in the folder structure as appropriate.
If I drop movie content into iTunes it is quite happy and the content ends up in a subdirectory of the Movies folder.
If I try and drop a TV Show content in iTunes it seems to copy the content to the iTunes folder above "TV Shows" and the Mac loses connection to the netatalk service.

In syslog I see these messages repeated over and over.

```
Sep 19 18:28:42 nasbox afpd[3703]: AFP3.3 Login by username
Sep 19 18:28:42 nasbox afpd[3703]: afp_disconnect: trying primary reconnect
Sep 19 18:28:42 nasbox afpd[3027]: Reconnect: no child[3702]
Sep 19 18:28:47 nasbox afpd[3703]: afp_disconnect: primary reconnect failed
Sep 19 18:28:47 nasbox afpd[3703]: ad_openat: cant chdir back, exiting
Sep 19 18:28:48 nasbox afpd[3704]: AFP3.3 Login by username
Sep 19 18:28:48 nasbox afpd[3704]: afp_disconnect: trying primary reconnect
Sep 19 18:28:48 nasbox afpd[3027]: Reconnect: no child[3703]

```

I need to restart netatalk to get things working properly again.

I wondered if this might have something to do with extended file attributes which I am aware get used extensively by Apple filesystems.
This is the output from the mount command, and I can see the "TV Shows" folder is not getting these extended attributes (though it is in fact within the path above, which does)

```
/dev/mapper/nasbox-store on /home type ext4 (rw,user_xattr)
/dev/mapper/nasbox-media on /media/media type ext4 (rw,user_xattr)
/home/media/TV Shows on /media/media/itunes/iTunes/TV Shows type none (rw,bind)
```

I'm going to see if there is any way to explicitly enable these through this method of mounting the path but wondered if anybody might have some other insight about what the problem could be.

---

### Post by Morbius1 on 2011-09-19
Unfortunately I know nothing of netatalk or afp. 

I don't think this is a bind issue though as it's just like a regular mount in that the permissions and ownership of the folder it's binding to are lost and it assumes the permissions of the source. And since the data now exists on 2 locations at the same time whatever you do to one happens to the other automatically.

There is a similar phenomenon to what you are describing in Samba when it comes to OSX's extended attributes. I managed to stumble on a fix for Samba here: [http://ubuntuforums.org/showthread.php?t=1614254](http://ubuntuforums.org/showthread.php?t=1614254)

In that thread you had to take possession of the shared folder on the server and then force the remote user ( using an ownership mask after authentication) to appear to be that user for the extended attributes to save correctly. Maybe there is something similar in netatalk.

Sorry I can't be more helpful.

---

