---
title: "Success with gmailfs under 5.10!"
date: 2006-03-04
forum: General Help
---

### Post by Prospero2006 on 2006-03-04
Hello folks:
I have been tinkering with making gmailfs work with kubuntu breezy for some time now. I finally got it to work, and I thought I'd share with you
all how I did it. It's really nice to have. Follow these directions, and you too can make it work.

All packages are installed from source except FUSE. 

So, if you have gmailfs or libgmailfs installed, remove them now.

(Keep Fuse.)

-Download libgmail from [http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/)

-Download gmailfs-0.7.2.tar.gz from the author's site

-Unpack those directories and copy everything into /usr/local/bin

-Copy gmailfs.conf to /etc

-Open up gmailfs.py in a text editor:
        **-Lines 42 and 43**
              -Replace:
'defaultUser' and 'defaultPassword' to reflect your actual login information.
        
        **-Lines 153-160**
--Quotation Marks are important!!--
-Replace: 
self.username = DefaultUsername 
self.username = "YOUR_ACTUAL_USERNAME"
               
               -Replace:
self.username = username
self.username = "YOUR_ACTUAL_USERNAME"

-- Do the same for the password entries! --

Open up:
**/usr/lib/python2.5/site-packages/fuse.py** in a text editor:
       **-Line 68**
              -Replace:
self.mountpoint = None
self.mountpoint = "YOUR_MOUNTPOINT_HERE"

Mount it once with this command

mount.gmailfs "/usr/local/bin/libgmail.py" YOUR/MOUNT/POINT/
 -o  username=YOUR_ACTUAL_USERNAME, password=YOUR_ACTUAL_PASSWORD,
fsname=zOlRRa

type:

chmod 777 YOUR/MOUNT/POINT
umount YOUR/MOUNT/POINT

Fstab entries won't work so:

Add this line to /etc/init.d/bootmisc.sh at the end: 

mount.gmailfs "/usr/local/bin/libgmail.py" YOUR/MOUNT/POINT/ -o username=YOUR_ACTUAL_USERNAME,
password=YOUR_ACTUAL_PASSWORD,
fsname=zOlRRa

(This will mount it at bootup.)


Please leave feedback here to tell me if this worked for you. I just figured all of this out. So, I'm not sure if I missed something.

[http://www.webloguniverse.com](http://www.webloguniverse.com)  
  -Click on the email link. (I'm the admin) 

Good Luck,
Pros

---

### Post by RaptorRaider on 2006-03-04
Looks promising.

[QUOTE=Prospero2006]-Download gmailfs-0.7.2.tar.gz from the author's site[/QUOTE]
[Here]("http://richard.jones.name/google-hacks/gmail-filesystem/gmailfs-0.7.2.tar.gz")?

Perhaps this thread should be moved to "Customization Tips & Tricks"?

---

### Post by Prospero2006 on 2006-03-04
Problem and Solution:

Problem:
  -When I created an icon on the desktop for my nifty now gmail hard drive, gmail
   promptly froze my account for 15 minutes citing a 'Sector 4 Lockdown.'
   It did not like the 'create link to location' choice for creating  a new icon.

Solution:
  -I created a link to the folder just below the mount point.
   My gmail drive is mounted a /mnt/gmail
   My icon on the desktop points to /mnt

-I haven't experienced any problems.

Pros

---

