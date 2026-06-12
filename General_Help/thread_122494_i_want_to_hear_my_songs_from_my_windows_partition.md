---
title: "i want to hear my songs from my windows partition"
date: 2006-01-27
forum: General Help
---

### Post by rjcoolpix880 on 2006-01-27
i installed ubuntu this morning and i cannot access my /windows or /data (my C: and D: windows directories)  b/c of permissions. I read the [terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal") article and tried the 

**chmod 755 data**

and it wouldnt let me so i then tried

**sudo nautilus**

i could access all my files and songs in both places but one i tried to play a song it wouldnt let me.  so i tried to change the permissions of the file and when i clicked on  any of them it says that its a read-only disk and i cant change it.

remember i installed linux this morning so be easy :)

---

### Post by o_fortuna on 2006-01-27
[QUOTE=rjcoolpix880]i installed ubuntu this morning and i cannot access my /windows or /data (my C: and D: windows directories)  b/c of permissions. I read the [terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal") article and tried the 

**chmod 755 data**

and it wouldnt let me so i then tried

**sudo nautilus**

i could access all my files and songs in both places but one i tried to play a song it wouldnt let me.  so i tried to change the permissions of the file and when i clicked on  any of them it says that its a read-only disk and i cant change it.

remember i installed linux this morning so be easy :)[/QUOTE]
If you can access your windows files, you can copy them to your Ubuntu directory (ie, /home/YOURNAME), where you can use them. Windows is always "read only," which means you can't change it, but you can copy them. You could do this in a terminal, but it's easier not to mess up if you just use the GUI.

---

### Post by rjcoolpix880 on 2006-01-27
thats 15gigs! 
hmm... that seems odd. why cant i access the windows stuff. security? i have used mandrake before and i could access the windows and data drives easily from it.

---

### Post by era86 on 2006-01-27
did you mount your windows hda manually? or did it automatically mount on startup?

---

### Post by rjcoolpix880 on 2006-01-27
in the setup.
it found both the /windows (c: ) and the /data (d: )
i renamed them, of course, in the setup also

---

### Post by MetalMusicAddict on 2006-01-27
NTFS or FAT32?

---

### Post by Ocxic on 2006-01-27
add this to your /etc/fstab
```
 /dev/hdb1       /media/NTFS_Kev ntfs    defaults,umask=0222        0       0
then type: sudo mount -a
to remount your /etc/fstab

```
don't forget to make the mount point. putting the mount point in media will add the drive icon to all of the gnome menus and "computer" in your places menu. and viola, you can see your windows stuff. you'll need to mak a sepreat line for each partiton just modify /dev/hdb?  and the mount point /media/????? to your configuration,.

---

### Post by rjcoolpix880 on 2006-01-27
ntfs


i typed this into my fstab
/dev/hdb1	/media/NTFS_Kev	ntfs	defaults, umask=0222	0	0

then got

ryan@linuxdesktop:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad

line 12 is the line i entered above.

oops found a space

okay i got

ryan@linuxdesktop:~$ sudo mount -a
mount: mount point /media/NTFS_Kev does not exist

---

### Post by aysiu on 2006-01-27
The fourth link of my signature explains everything.
It's all about how you mount it. You can't Chmod NTFS.

---

### Post by rjcoolpix880 on 2006-01-27
ill give it a shot

out of curiosity why cant i chmod ntfs. b/c ntfs doesnt understand chmod?

---

### Post by aysiu on 2006-01-27
[QUOTE=rjcoolpix880]
out of curiosity why cant i chmod ntfs. b/c ntfs doesnt understand chmod?[/QUOTE] I'm not sure, but [this page](http://www.mkssoftware.com/docs/man1/chmod.1.asp) may shed some light.

---

### Post by rjcoolpix880 on 2006-01-28
thank you very much it worked perfectly.

another question is what did the option:* nls=utf8,umask=0222* do.

---

### Post by nszabolcs on 2006-01-28
[QUOTE=rjcoolpix880]another question is what did the option:* nls=utf8,umask=0222* do.[/QUOTE]


man mount
(see at options for ntfs)

umask=0222 => everything is readable and executable by every user on the mounted drive

---

