---
title: "Wish LAMP to use same www folder as my WAMP"
date: 2012-07-26
forum: General Help
---

### Post by aqk on 2012-07-26
**IGNORE THIS THREAD- I HAVE POSTED A NEWER ONE, ASKING ABOUT APACHE ACCESS TO NTFS FILES**

HI-  I have a Ubuntu 12.04 system and Windows-7 dual-booting, and each has a web-server-
LAMP for Ubuntu, and WAMP for Windows, each with its own www folder.
Both work satisfactorily.
However I tried pointing the Apache to my WAMP folder ***DATA-175gig/wamp/www/*** (on a NTFS partition) to eliminate duplication of www files. 

I now get the usual **[COLOR="DarkRed"]403 forbidden[/COLOR]** message that so many other folks here seem to get.

Here's the details 
Apache /etc/apache2/sites-enabled/000-default -
   changed references to ***/media/DATA-175gig/wamp/www/*** 

FSTAB - added the following -
  ***UUID=588A35268A350254  /media/DATA-175gig/  ntfs auto,users,utf8,uid=1000,gid=1000,umask=002 0 0***
# --FROM  [COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1577717[/COLOR] ----
[SIZE="1"]# The uid=1000,gid=1000 sets the owner and group of the partition to the first user/group.
#The umask=002 sets the file permissions for every file to 775 (-rwxrwxr-x), alter this as need be. 
#  Just remember that the value of umask is the inverse of what permissions you want.
#  The utf8 probably isn't necessary, but I use it anyway.
#  The UUID for your drive will be different. You can use /dev/sda1 or whatever if you prefer.
#    ...............   aqk, July,2012 [/SIZE]

BLKID includes  ***/dev/sda5: LABEL="DATA-175gig" UUID="588A35268A350254" TYPE="ntfs" ***

The Apache2 error log shows -
[B][I][Thu Jul 26 13:59:49 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jul 26 14:00:02 2012] [error] [client 127.0.0.1] (13)Permission denied: access to / denied[/I][/B]

As well, I have done all manner of chmods, chowns and greps to this  ***DATA-175gig/wamp/www/*** folder   At wits end now. Should I go back to using my EXT4  www folder again?

Any suggestions?

---

### Post by aqk on 2012-07-26
I unmounted the above partition DATA-175gig  NTFS partition and now can no longer mount it.
The error I get is 
[I]Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)[/I]

Would this be due to my use of partition labels > 8 characters?

---

