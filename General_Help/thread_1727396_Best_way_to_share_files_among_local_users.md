---
title: "Best way to share files among local users?"
date: 2011-04-12
forum: General Help
---

### Post by trivialpackets on 2011-04-12
I am about to do a reinstall, so I was hoping for a quick response.  I want to have a shared area for movies, music, etc. where files are available for all users.  What is the best way to do this?  I've tried a few different things, (ie. creating a folder and sharing it among a group, but for some reason it doesn't seem to work the way I want it to.  I'm now thinking maybe have a partition like /share and set the permissions to all in fstab, but I'm not sure.  Any quick feedback?

---

### Post by Morbius1 on 2011-04-12
You need to define what you mean as "share".

All users can add to or delete files but can only write ( edit ) to their own files and all others can only read?

Same as above but only the owner of the file can delete it?

All users can add to or delete from the share and all users can write ( edit ) each other's files?

Or some variation of the above?

---

### Post by seawolf167 on 2011-04-12
Here is a [good how-to link ]("https://help.ubuntu.com/10.04/internet/C/networking-shares.html")with some options for how to setup sharing

As long as you set the permissions properly you shouldn't have a problem with sharing files/folders, especially between two Ubuntu machines (right click -> share). For organization purposes it might not hurt having a separate partition though.

You'll have some samba setup to share to a Windows machine, but it's pretty easy. Besides, if you want at any point in the future, creating a new partition and moving/remounting that partition is easy & relatively quick.

---

### Post by Morbius1 on 2011-04-12
I'm probably mistaken but I think the OP was referring to multiple accounts on the same box not on a LAN.

---

### Post by trivialpackets on 2011-04-12
Yes.  I'm planning on creating a /home/share folder, then creating links to it in /etc/skel so new users will have links to it.  I want it fully read/write for all users, as it's going to be the area for most downloads for multiple users to use, as noted for media and the like.

---

### Post by Morbius1 on 2011-04-12
Here's one way:
```
sudo chown :plugdev /home/share
```All local users are members of the plugdev group by default in Ubuntu.
```
sudo chmod 2775 /home/share
```The "2" makes it so every new folder / file "inherits the group.
The "7"'s make sure the group has add / delete access to the share.

But there's one more thing necessary to pull this off:

Edit /etc/profile as root:
```
gksu gedit /etc/profile
```Find the line at the bottom that references umask and change it to:
```
umask 002
```What this will do is change the permissions on newly created folder / files from 755 / 644 to 775 / 664. Now memebers of the group can write to the file.

You will need to logout and log back in again since profile is read only once at login.

---

### Post by seawolf167 on 2011-04-12
Ahh k, you could create your partition as stated, then put the users to have access to that partition (directory tree) in a group and give that group read/write/whatever access to that folder

---

### Post by Morbius1 on 2011-04-12
> **seawolf167 said:**
> Ahh k, you could create your partition as stated, then put the users to have access to that partition (directory tree) in a group and give that group read/write/whatever access to that folder
But every new file added by user2 will save as:
owner : group = user2 : user 2
mode = 644

User1 can read the file but not write to it. Read / write access to the folder does not mean read / write access to it's contents.

Setgid ( the "2" ) will force the new file to have the same group as the parent folder. And changing umask will enable write ( edit ) to the file for that group.

**[COLOR=Blue]EDIT:[/COLOR]** It could be that I'm taking the requirement too literally. Full read / write access to me means just that. All users have read / write access to the directory and all it's contents. That's why I asked my original question about "what fo you mean by share? ? ;)

---

### Post by trivialpackets on 2011-04-12
Thanks!  This has found a way to my blog so I don't forget again!

---

### Post by seawolf167 on 2011-04-12
Good to know - thanks Morbius1

---

### Post by Ralph L on 2011-04-12
My web site has a long discussion on this:  [http://ubuntulinuxnoviceguide.webs.com/](http://ubuntulinuxnoviceguide.webs.com/) See Sections 4 and 5.

---

### Post by Morbius1 on 2011-04-12
> **eric.proctor said:**
> Thanks!  This has found a way to my blog so I don't forget again!
If this is going up on a blog then you might want to look at another option that brings some level of control to all this:

Instead of "sudo chmod 2775 /home/share" change it to:
```
sudo chmod 3775 /home/share
```The "3" is the original setgid bit (2) plus the sticky bit (1). What this will do is allow everyone to do what they did with a "2775" just as before but only the owner of the file, the owner of the "share" directory, or root can delete it.

---

