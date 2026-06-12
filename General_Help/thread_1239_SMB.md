---
title: "SMB"
date: 2004-10-19
forum: General Help
---

### Post by marguz on 2004-10-19
Hello all,
I'm trying to mount some Windows 2000 shares using the Connect to Server option in Nautilus. I select Windows Share and fill in the info, but the thing keeps asking me for the share password. I've read the FAQ and found that a work around was to use servername/share in the Server Field, but that still did not work.

Does anyone have a step-by-step to mounting SMB shares using Nautilus in Ubuntu?

Mark   :?:

---

### Post by marguz on 2004-10-19
AnyOne ??? :-(

Well, 
I installed smbfs using apt-get (why it was not installed, I do not know) and now I can mount using the command line.

-- BUT --

I want to use the GUI !
There has go-to-be an easy way to do this in the GUI. 

Any takers ?

Mark

---

### Post by cordis on 2004-10-19
Hi, I'm also having some samba troubles.  I figured out how to install it through the package manager, and it seems to be running and I can view other shares on my windows network, but I'm having some trouble creating a share on my ubuntu machine.  I'm hoping it doesn't come down to having to edit the smb.conf file and restarting the daemons endlessly until I get it right, is there a simpler tool in the OS somewhere I can use?  I'm trying to decide if ubuntu is worth it over Xandros, which has a very easy way to share directories, you just change a property on the directory in the file browser, does Nautilis have any feature like that?  I know, I'm sure it's a huge security issue and all, but I'm going to have to let my windows boxes mount shared samba directories if my network backup system is going to work.  Thanks!

---

### Post by kkennedy on 2004-10-19
I have an XP share on my home network, that does not require a password.  I used the GNOME network browser to browse to the share.  It prompted me for a user name and password.  I left both blank, and it allowed me to view the files.

---

### Post by cseg on 2004-10-19
I just installed the latest (10/13) Warty Warthog.  I guess this is 4.10, but then, I thought the last one was the same.  Oh, well.

With the previous version (with no nekid people) Samba/smbfs worked for me.  I could see another computer running samba, and access the shares, and use mount to mount them locally.

With this new version (the nekid one) I can't see the other computer via the Network menu option, and when I try to mount them, I get:

mount: wrong fs type, bad option, bad superblock on //host/share,
       or too many mounted file systems

This was working before but now its not, so I guess this is something of a bug report.  Maybe this should be put into Bugzilla.  Has anyone else done this?

---

### Post by marguz on 2004-10-20
CSEG,

I too got that message, I had to install smbfs from apt-get to mount SMB shares from the command line.

I just whish that I could do that via GUI, so that the wife could use this distro. I guess she will continue to use SIMPLEYMEPIS until this is fixed in GNOME :-(

Mark

---

### Post by marguz on 2004-10-21
Boy, This died fast :-(

Well I hope that the SMB issues are fixed in the next version. :-(

Mark

---

