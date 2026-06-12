---
title: "Using an external NTFS drive as 2 different users"
date: 2010-01-06
forum: General Help
---

### Post by 2coolfool on 2010-01-06
Hello,

I currently have an external (USB) NTFS drive that I use on my main user account (A). It auto-mounts and there's no problem. But now I wanted to add another user (B). The problem I'm having is the following:

System boots - logon as A, the disk is auto mounted and usable
Log off user account A and log into account B
The disk is not mounted, and I cannot see it in nautilus to mount it through the GUI.

What I want is that the disk should be automounted on both user accounts, so that I can use it directly upon login.

OS Version: Karmic 64 bit.

Thanks in advance.

---

### Post by cariboo on 2010-01-06
Is your second user a member of the plugdev group? To check go to System-->Administration-->Users & Groups, Click on the authorization buttn, the highlight the user and select properties. Click the User privileges tab and make sure **Access external storage devices automatically** is enabled.

The second way is to open a terminal, su to the other user and type groups:

```
su <otheruser>
```

you will be asked for the other users password next type:

```
groups
```

you should get an output that looks something like this:

```
adm dialout cdrom dip plugdev fuse lpadmin netdev admin sambashare
```

the other users name should be in the list too. If they are a member of the plugdev group just add them:

```
gpasswd -a <user 2> plugdev
```

you will then have to logout as that user and login again in order for the changes to take effect.

---

