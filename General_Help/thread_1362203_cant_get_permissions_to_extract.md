---
title: "cant get permissions to extract"
date: 2009-12-22
forum: General Help
---

### Post by orin zolis on 2009-12-22
Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///usr/lib/cups/filter"

this happens with all folders/files I try to extract into the filesystem folder

any help?

thanx

P.S. Im running ubuntu desktop 9.10

---

### Post by Some Penguin on 2009-12-22
sudo

---

### Post by orin zolis on 2009-12-22
> **Some Penguin said:**
> sudo

can u give me an example of what i would put after "sudo" im trying to install  

cnijfilter-common-2.70-1.i386.rpm atm

---

### Post by 3rdalbum on 2009-12-22
> **orin zolis said:**
> Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///usr/lib/cups/filter"

this happens with all folders/files I try to extract into the filesystem folder


Your user account can only modify files and folders in your home directory. This is because it's just an ordinary user account, and you don't want ordinary user accounts to be able to modify the system. Windows XP allows the first created user account to administer the system, which is why viruses are rampant on Win XP.

On Ubuntu, uou can run a program as "root" (administrator) by running the program with the "sudo" or "gksudo" commands (the latter is used for graphical programs).

In your case, you'd do:

```
gksudo file-roller
```

because File Roller is the name of the archive program. Then go to File > Open and find your file.

Another popular way is to run a file browser as root:

```
gksudo nautilus
```

(then double-click the archive in the new root file browser, which will run file-roller as root)

And a third popular way of doing it is to install the "nautilus-gksu" package. When you next login, you'll be able to right-click a file or folder and choose "Open as Administrator".

---

### Post by falconindy on 2009-12-22
Whoa.. or a better idea is to simply copy the file to your home folder rather than unnecessarily escalate your privileges.

---

### Post by lavinog on 2009-12-23
+1 to falconindy

What are you trying to accomplish?
You can really break your system if you try and extract an archive to a system folder.

If you need to add files to the folder from the archive, extract the archive to your home folder first, then use sudo to move the files to the system folder...you also might need to chown and chmod the files too.

You might be doing something you don't need to be doing...are you having printer problems?

---

### Post by JoelOl75 on 2009-12-23
A better question is why are you installing .rpm files.

I mean, a better way would be to get a native ubuntu .deb  or if not possible a debian .deb

A few times though I did need to install a .rpm file and use the package alien

sudo apt-get install alien

this converts .rpm packages to .deb packages

I found this unnecessary in the last few years as any 'weird' packages are usually found in ppa's and the like.

---

### Post by orin zolis on 2009-12-23
yes its a canon mp240 that im trying to get working and needs me to instal the cnijfilter-common-2.70-1.i386 in the system folder filter section.

thanks everyone for the feed back and to 3rdalbum for the indepth explaination of sudo, i do want to know how to do this stuff so that is a steping stone tho i wont be to confident yet, dont wanna have to reinstall ubuntu yet :)

---

### Post by lavinog on 2009-12-23
This might help
[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP240](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP240)

When downloading the driver, choose the debian package, not the rpm

I am surprised it doesn't work with karmic.
Does anyone know if this is a license issue?  I try to avoid canon printers because of the lack of support for linux.

---

