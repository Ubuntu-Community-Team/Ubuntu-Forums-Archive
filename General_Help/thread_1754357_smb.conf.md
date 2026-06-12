---
title: "smb.conf"
date: 2011-05-09
forum: General Help
---

### Post by romerje on 2011-05-09
Hello All,

I posted something similar to this a couple weeks ago...and had my issues solved....but since then I have updated to the 11.04 version and I am now having problems....

in myth...you have 4 default directories...music, pictures, recordings, and videos.  I want to change their default location b/c I don't have enough room on my main driver.  Now in the past I have edited the smb.conf file with my correct paths to my data and it worked beautifully....I have tried to repeat this with the new install and I get an error when trying to connect via my windows machine....

"windows cannot access \\Jennifer-Myth\videos..it bascially says check spelling or network issues...I I click on detials it says "the network path was not found"

Below is my smb.conf file....

[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = mythtv
force group = mythtv

[videos]
comment = Videos
path = /media/Big *** Drive/Our Videos
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[music]
comment = Music
path = /media/Big *** Drive/Music
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[pictures]
comment = Pictures
path = /var/lib/mythtv/pictures
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv


any help would be much appreciated!!!!  Thanks Jennifer

---

### Post by jamesjenner on 2011-05-10
G'day Jennifer,

A couple of things come to mind.

First, check the permissions on the directory, make sure that mythtv user and/or group has access to the directory and files within.

The only other thing I can think of is that you haven't restarted smb yet, though I suspect you have. Just mentioning it in case you haven't.

Cheers,

James.

---

### Post by romerje on 2011-05-10
Thanks james....I will check on permissions...I think that is the issue too....as for the restarting...do you know the terminal cammand line for restarting smb?

thanks
Jen

P.S.  Even if I am in "root" user mode I can't change any permissions for user, group or owner...not sure why...I right click on the fold I want to changes permissions on....

---

### Post by jamesjenner on 2011-05-10
The command to restart smb from memory is:

> sudo service restart smbdAs I'm at work I cannot check if you need sudo or not, but I'm pretty sure you do (as I presume smbd isn't running as your account, again I cannot check so could be wrong on that). A reboot will also restart it, a logout/login will not as it's started at startup, not at login.

I'm at work now so don't have access to linux, otherwise I'd do a screen shot of the permissions dialog. I know I could change permissions for group and others quite easily, but I cannot remember if I could change ownership via the dialog. There is a tick box that lets you choose to apply the changes recursively.

You can go to the command line, change to the appropriate directory and do a chgrp (change group) or chown (change owner). you can also do a chmod (change permissions), not sure if there is a recursive option. But to find out your options you can type in:

> man <command>this will tell you the options available for the command. Space bar lets you scroll through.

The man pages (man is short for manual) are a bit esoteric in their definition of how things are done but it's a good resource.

You should be able to do the following command from a shell to change the permissions.

> chown -R mythtv <file/directory>If you run the above command in the shell from the directory above where you have shared, so that your doing it for the directory that you shared then that should fix your problem. Either that or run the command specifying the absolute path of the directory (as in from /, so for example may be* /media/Media/movies*, instead of just *movies*).

Hope that helps.

Cheers,

James.

:edit:

just realised you may be trying to change permissions for a folder that you don't have permissions to change. I'm used to using the shell and I'm not sure how you would do that via the file browser, I can check it out for you tonight though if you like.

---

