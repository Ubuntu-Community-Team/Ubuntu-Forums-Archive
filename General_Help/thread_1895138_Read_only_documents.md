---
title: "Read only documents"
date: 2011-12-14
forum: General Help
---

### Post by shealtiel on 2011-12-14
I keep finding documents I want to work on in Libre and that were created in Windows are set as ***read only*** so I can't do anything with them. I've tried changing this in *properties* but get told the setting cannot be changed. How can I fix this?

---

### Post by MartijnNL on 2011-12-14
Who is the owner of the file? And what are it's permissions?

I will run a test in the mean time.

---

### Post by BC59 on 2011-12-14
The easiest way to change properties is to open root nautilus.

```
gksudo nautilus
``` then right click to the document and change attributes.

---

### Post by MartijnNL on 2011-12-14
Ok, did a test and although I own the file I can't change the permissions, which is logical, because even for me it's read only.

The solution it to change the permissions with root permissions.

If you are familiar with a terminal, you could open one, navigate to the directory in which the file can be found and run:

```
sudo chmod u+w filename.ext
```

Otherwise press Alt+F2, enter:

```
gksu nautilus
```

and press enter. Then navigate to the file in the new nautilus window open its properties (right click) and change the permissions to "Read & Write".

---

### Post by coffeecat on 2011-12-14
@shealtiel, it is possible that this is not a Linux file permissions issue. You can set (and unset) a document as read-only from within LibreOffice itself and this is enforced independently of filesystem permissions and operating system. Have a look under File -> Properties -> Security tab and see whether the "Open file read-only" box is ticked. If that doesn't help, look up "read-only documents" in Libre-Office help.

---

### Post by shealtiel on 2011-12-14
> **MartijnNL said:**
> Who is the owner of the file? And what are it's permissions?

I will run a test in the mean time.
They are my files and I'm the only user of this computer so I am the administrator. It seems that the whole hard drive is set to read only.

---

### Post by MartijnNL on 2011-12-14
Have a look at my second post. If you are the only user, that doesn't give you administrative privileges. The 'root' user has administrative privileges, but in Ubuntu you can't login has root. By using sudo or when using GUI applications gksu/gksudo you can perform actions as the root user, while using your own account.

So please try my solutions. (Edit: of which one was give by BC59 as well while I was typing.)

---

### Post by SeijiSensei on 2011-12-14
If the whole hard drive is marked read-only, it's because the drive has errors.  Linux won't mount a filesystem with errors in read/write mode.

Fixing this problem requires booting from a CD and running "fsck /dev/sdaN" against the faulty filesystem.  You can't safely fix the problem from the system itself, since running fsck against a mounted drive can further corrupt the filesystem.

[This article](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/) indicates that you can run "sudo shutdown -rF now" from a terminal to force a reboot and file system check.  However reading the man page for the shutdown command doesn't list the -F option.  Wouldn't hurt to give it a try though, as that's a lot simpler than booting from a CD.

The other method for forcing a filesystem check, creating the file /forcefsck, won't work for you since the filesystem is marked read-only.  You can get around this by forcing a remount with write privileges:

```

sudo mount -n -o remount,rw /
sudo touch /forcefsck
sudo reboot

```

(Note there's no space in the string "remount,rw".) If you take this approach, don't do anything else other than create the forcefsck file and reboot.

---

### Post by shealtiel on 2011-12-23
I haven't got anywhere in spite of all the help that's been given. In addition I had just composed a reply that I suppose was too long because by the time I had edited and re-edited it I found I'd been logged out and had lost the lot. Had I realised that would happen I'd have written it in Notepad and pasted it in. I had described the results I got with each different approach but maybe that wouldn't have helped anyway.

---

