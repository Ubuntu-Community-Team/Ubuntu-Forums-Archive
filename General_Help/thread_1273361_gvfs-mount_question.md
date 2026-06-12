---
title: "gvfs-mount question"
date: 2009-09-23
forum: General Help
---

### Post by bobcat2000 on 2009-09-23
I'm trying to migrate users' worskations to Ubuntu 9.04 in an XP/Windows 2003 server environment.  So right now it's a mix of Ubuntu 9.04, Windows XP and Windows 2003 server (domain controller).  Have deployed some Ubuntu 9.04 workstations with overall success, but running into an issue with gvfs-mount.

Currently, Windows XP users are logging in to the Windows domain and get their appropriate mapped drives upon logging in (based on their domain groups).  Ubuntu users are logging into their workstations locally, and clicking on a script (which is different from one person to the next depending on their group/role) which maps their drives/folders for them. The script is of the form (usually 8-10 shares per user):

gvfs-mount smb://server/share1
gvfs-mount smb://server/share2
...
...


Here's the issue:

When the script is executed, it prompts for workgroup, username, password etc for each gvfs-mount line in the script.  To avoid having to type this info for each share, we can make use of Places->Connect To Server once for a particular share and save the credentials, and then run the script so it maps everything without asking for credentials for each share.  However, for security and ease-of-use reasons, I would like each user to just click on an icon on their panel which runs the gvfs-mount script, have them type in their domain username and password just once for the first share.  They could go to Places->Connect To Server and save their username/password before clicking on the map script but I'm trying to make it easier for them.   

So my question is... when you "Connect To Server" to connect to a Windows Share, and choose to "Save password for this session only"... what happens behind the scenes?  Is "Connect To Server" running gvfs-mount with some parameters to save the username/password?  If so, I'd like to add them to the first gvfs-mount command in my script.

Is what I'm trying to do possible?  Any ideas? 

Thanks for your help.

-bobcat2000

---

### Post by StuartN on 2009-09-23
> **bobcat2000 said:**
> I'm trying to migrate users' worskations to Ubuntu 9.04 in an XP/Windows 2003 server environment.

At a simple level (a couple of users) you can put %U into the smb.conf file to have user accounts, and the keyring will fill with the required passwords as they are used.

If it is more than a couple of users then have a look at [http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/) - Samba by example.

---

### Post by bobcat2000 on 2009-09-23
Thanks for the reply.  I guess I need to read up on Samba.

Do you know what command is executed when you "Connect To Server" (Windows Share in this case) and choose to remember authentication details for the session? 

-bobcat2000

---

### Post by capscrew on 2009-09-23
> **bobcat2000 said:**
> ... Ubuntu users are logging into their workstations locally, and clicking on a script (which is different from one person to the next depending on their group/role) which maps their drives/folders for them. The script is of the form (usually 8-10 shares per user):

gvfs-mount smb://server/share1
gvfs-mount smb://server/share2
...
So my question is... when you "Connect To Server" to connect to a Windows Share, and choose to "Save password for this session only"... what happens behind the scenes? ...

The question brings up one of the peculiarities of using Linux as a desktop OS.  The nice thing about Windows or Mac OSX is that the whole system is  unified and all parts are aware of each other.  Ubuntu just isn't that way.  The OS is Linux and the desktop environment can be Gnome (Nautilus) or KDE, etc.  I use Gnome and therefore the Gnome Virtual File System (GVFS)

Using Samba to share files should be thought from 2 different aspects.  The first way would be configure Samba manually via /etc/samba/smb.conf file.  You *may* choose to mount the "shares" via a script to mount points in the file system.  

The second method is configuring Samba and mounting the shares to .gvfs in the users home directory via Gnome/Nautilus.  Configuration files doing it this way are located at /var/lib/samba.  Most of these config files are binary not text.

As you can see these are vastly different ways of configuring the Samba daemon (smbd).  There are other subtle differences.  Some applications are not fully gvfs "aware".  Open Office is one of those along with Gedit.  This is due to the fact that some applications can't see a **_locally mounted share_** if it is mounted via gvfs.

> 

Is what I'm trying to do possible?  Any ideas? 

Yes indeed. I feel you should create all of the shares manually in /etc/samba/smb.conf and mount them to the local hosts file system at manually created mount points.  This mounting is easily accomplished using shell scripts.  No .gvfs mount points. 

Nautilus will see the shares and you will have full GUI functionality this way.  This sounds like a lot but it really is very simple.

I have examples if you need them.

---

