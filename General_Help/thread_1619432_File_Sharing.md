---
title: "File Sharing"
date: 2010-11-11
forum: General Help
---

### Post by CensoredBiscuit on 2010-11-11
Hey guys, 

I'm new to Ubuntu and can normally hold my own but I always used to allow family members to access my music and videos over LAN so it could be played anywhere in the house... 

I tried to do this on Ubuntu with a few kinks...

Is there a way to allow someone to access files without having access to my desktop (i.e. having a samba-only user.)

Thanks, 
CB

---

### Post by papibe on 2010-11-11
It is pretty easy:
[INDENT]Right click on the folder you want to share.
Select Share Folder.
Install Samba (maybe called Windows network support, or SMB).
[/INDENT]
After that you'll have the option "Sharing Options" if you right click the folder. There you choose the name and the permitions (read write for all).

You can see more details and pics [here]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/").

Good Luck!

---

### Post by Isaac356 on 2010-11-11
In smb.conf, if you set security to "share" (default is "user"), then samba will allow anonymous access.

```

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = share

```

Also, you may need to change some individual share settings. For example, this is what my music share looks like:

```

[music]
    comment = Free Music!
    path = "/home/ice/Music"
    guest ok = yes
    browseable = yes
    read only = yes

```

Hope that helped!

---

### Post by Win-Smash on 2010-11-13
I just set up file and printer sharing on my Ubuntu 10.10 desktop
for my house hold. In Ubuntu it was easy (with the above suggestion)but my problems were on the window side I have computers running XP, 7 and Ubuntu. In Windows if you type \\(ip address) with out the brackets in the search box by the Start button it should pull up a window with files and printer folders that are shared on that computer. This and TSC saves me a lot of time.

---

### Post by Morbius1 on 2010-11-13
> In smb.conf, if you set security to "share" (default is "user"), then samba will allow anonymous access.That statement as an absolute is not correct. The default smb.conf has two lines which allows guest access:
> security = user
map to guest = Bad UserThose two lines are all you need. It will not require a Unix account in the server for every user accessing the server. Besides share level security hasn't been used since Jimmy Carter was President ( that might be a slight exaggeration :wink:. )

From man smb.conf:
> map to guest:

Bad User - Means user         logins with an invalid password are rejected, unless the username          does not exist, in which case it is treated as a guest login and          mapped into the [guest account]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT"). A guest share will not prompt for authentication so all remote users will be mapped to the guest account.__[]("http://art.ubuntuforums.org/showthread.php?p=8716349#post8716349")

---

