---
title: "Setting Samba Public Share Owner for Files"
date: 2011-12-24
forum: General Help
---

### Post by Nasair on 2011-12-24
Hey, so this is the problem I'm having with an open (Public) share:
I copy a file and the owner is set to nobody. From another computer I have no issues editing, deleting, opening, etc... on that file but from the computer I have to either change the permissions with sudo nautilus or just access it that way.

What I'd like is to copy files from another computer but have the owner be my default account, say "family" in this case but also not require the user to enter in login information to get to the share.
To be clear I'm right clicking on a folder and going to share, then giving it a name, then clicking on the allow others to create and delete files in this folder, and clicking guest access (for people without a user account), and finally clicking Create Share.
Any ideas? :confused:

I tried editing the smb.config but I didn't see the lines I wanted to edit in this link:
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[global]         security = user         encrypt passwords = true         map to guest = bad user         guest account = nobodyI was guessing I'd just change the "guest account" to "family" in my case, no? :confused:
Also looked at this ([http://manpages.ubuntu.com/manpages/lucid/man5/smb.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/smb.conf.5.html)) to get more info on the smb.config

---

### Post by Morbius1 on 2011-12-25
If "family" is the actual login user name on that box then force nobody to be family by adding the following line to the [COLOR=Blue]**[global]**[/COLOR] section of smb.conf:
```
force user = family
```Then restart samba:
```
sudo service smbd restart
```*[COLOR=Blue]Note[/COLOR]: I'm suggesting you do this in the [global] section because you are creating Samba Usershares - from Nautilus. Had you created a Samba Classic share then I would have suggested you add it to the share definition itself in smb.conf.*

---

### Post by Nasair on 2011-12-26
Thank you, that gives me the ability to edit/move/etc files without needing sudo. It doesn't setup all of the permissions the way I'd like but it does what I need. And what I mean is it setups up the Others permissions to read only but since my share is public with the ability to change files it won't affect me.  ...again, thank you.

---

