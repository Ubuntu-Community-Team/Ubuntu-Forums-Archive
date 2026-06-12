---
title: "How can I open a file over a Samba mount?"
date: 2006-05-29
forum: General Help
---

### Post by sugonaut on 2006-05-29
I've got this NAS (network attached storage) device sitting on my network with loads of yummy stuff.  I've successfully mounted it using Samba and can read/write through nautilus.  WhooHoo!

Now - I want to stream my music off it.  I have no preference of player; I've got 3 installed and playing local ogg and mp3 files.  I also want to import my photos into F-Spot.  Whenever I "open this" or "import that" or "add to playlist", I cannot browse to the mounted Samba share.  I have an icon sitting on my desktop that represents the mount, but it doesn't seem to be a true file/dir/link/alias.

What am I missing?  I am new to Ubuntu and Gnome (2 days), so I need instructions that a 6 year-old can follow.

- sugo

---

### Post by kingmonkey on 2006-05-29
This will work if you create a smb mount on your filesystem. The smb://computer option doesnt work.

[https://launchpad.net/distros/ubuntu/+ticket/603](https://launchpad.net/distros/ubuntu/+ticket/603)

---

### Post by sugonaut on 2006-05-29
For those playing along, I discovered a trick...

In Totem, for example, I can play a directory by clicking Movie -> Open Location -> smb://linkstation/share/MP3/Beck/Odelay.

Now I'll try kingmonkey's suggestion.

---

### Post by sugonaut on 2006-05-29
[QUOTE=kingmonkey]This will work if you create a smb mount on your filesystem. The smb://computer option doesnt work.

[https://launchpad.net/distros/ubuntu/+ticket/603](https://launchpad.net/distros/ubuntu/+ticket/603)[/QUOTE]

Success!

I followed the instructions [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") to permanently mount my Samba share.  I'm streaming my music as I write this.  Thanks for the pointer, kingmonkey.

One note regarding the wiki howto above - I followed instructions for "Mounting unprotected network folders", and used the fstab entry

```
//servername/sharename  /media/mountname  smbfs  guest,uid=1000
```

instead of

```
//servername/sharename  /media/mountname  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

Cheers, sugo

---

### Post by petit_prince on 2007-10-04
Also, Rhythmbox will happily import your music from any SMB share (you might want to navigate to the share using nautilus, then copy & paste the smb://... URL). I'm still looking for an application like f-spot which accepts smb shares.

---

