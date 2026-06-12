---
title: "problems mounting network drive"
date: 2009-07-15
forum: General Help
---

### Post by gavco98uk on 2009-07-15
I have a 500Gb Freecom network drive but I am having trouble mounting it under Ubuntu 9.4. If I select the file browser and enter "smb://10.0.0.101" then I can access it, and it will remain available for the rest of the session. I managed to "bookmark" it, and it now appears in the list under places, and all works fine. However it does not appear from most applications under the open/save dialogs, and I use it for storing all my files, so its a bit of a pain.

I decided to mount it using the mount command, with the eventual plan of setting it to auto mount during boot, but no matter what I try it always fails with error(5) - eg:


[I]sudo mount -t cifs //FND/public /media/networkdrive -o guest,rw,iocharset=utf8
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
[/I]
I have tried mounting by IP and netbios name, I have tried smb and cifs - but every time I get the same error.

Any suggestions?

---

### Post by gavco98uk on 2009-07-16
has anyone encountered this problem before, or know how to resolve it?
 
What exactly is error (5)?

---

### Post by kevbaldry on 2009-07-21
> **gavco98uk said:**
> has anyone encountered this problem before, or know how to resolve it?
 
What exactly is error (5)?

I've been pulling my hair out today, trying to mount a network HDD. I've tried all the different permutations but keep getting this error 5 (input/output).

I've tried on two machines - both running Jaunty and both do the same.

Sorry,**[SIZE=3] I[/SIZE]** can't help, but at least you're not alone.

---

### Post by capscrew on 2009-07-21
The proper method to mount a smb share is:```
sudo mount -t cifs //server/share YourMountPoint -o user=YourLogin
```

You can add your password to a file and use that as the "credentials" and not have to enter your password when mounting the share if you wish.  See the man pages for mount for more information.  NOTE:  The use of the term "guest" is incorrect as you are using it.

---

### Post by Cheesemill on 2009-07-21
> **gavco98uk said:**
> *sudo mount -t cifs //FND/public /media/networkdrive -o guest,rw,iocharset=utf8*
 
SMB/cifs uses a back-slash instead of a forward-slash. Try doing:
```
 
sudo mount -t cifs [COLOR=red]\\[/COLOR]FND[COLOR=red]\[/COLOR]public /media/networkdrive -o guest,rw,iocharset=utf8

```

---

### Post by kevbaldry on 2009-07-21
Still no joy :-(

I'm using a NAS drive which will show up in Nautilus after a few refreshes - so it's definately there. Entering the ip address of the NAS into a browser will bring up a list of files on the box.

HOWEVER - it will not mount manually (i.e. apart from Nautilus)

I have set up a share on a laptop running Jaunty and I can mount that without any problems - so it would appear that it's something to do with the NAS. There is a browser configuration thing - but there aren't many options.

I shall keep at it.

---

### Post by capscrew on 2009-07-21
> SMB/cifs uses a back-slash instead of a forward-slash.
Not according to the man pages for mount.cifs.  See:```
--verbose

    Print additional debugging information for the mount. 
Note that this parameter must be specified before the -o. 
For example:

    mount -t cifs //server/share /mnt --verbose -o user=username
```

Edit: Another example of the correct method is listed [**_here_**]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-samba-connect-share.html")

---

### Post by capscrew on 2009-07-21
> Entering the ip address of the NAS into a browser will bring up a list of files on the box.


this means you *need *some sort of nameserver configuration.  It appears that you are unable to resolve the server name.

---

### Post by kevbaldry on 2009-07-21
> **capscrew said:**
> this means you *need *some sort of nameserver configuration.  It appears that you are unable to resolve the server name.

Probably!?  I'm quite new to all this but learning A LOT. Thanks

---

### Post by kevbaldry on 2009-07-23
Managed to mount my drive by - 

[FONT=Courier New]gvfs-mount smb://192.168.2.50/PUBLIC[/FONT]

This mounts the PUBLIC folder of my NAS in my home directory under /.gvfs/public on 192.168.2.50

Not perfect but in the right direction.

---

### Post by brallan on 2009-07-23
I think it actually IS better to do it that way. i have had a number of problems with using smbmount, as [this thread]("http://ubuntuforums.org/showthread.php?t=1032394") can attest.

you might be frustrated after all you've been through to learn that it is much easier through the Gnome GUI (or through nautilus), just by going to Places>Connect to server. Have a look at the attached image.

For a long time I shied away from that method, as I didn't know I could use the mount point:

/home/username/.gvfs/public on 192.168.2.50/

to do things like using grsync, etc. Now I just bookmark it and never have to look for that command again.

---

