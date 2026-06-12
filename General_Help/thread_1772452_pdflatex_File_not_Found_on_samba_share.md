---
title: "pdflatex File not Found on samba share"
date: 2011-05-31
forum: General Help
---

### Post by Netgull on 2011-05-31
Hi,

I am trying to compile a LaTeX document using pdflatex on a CIFS/SAMBA network share.

The file compiles fine on the local drive.

Then if I copy it on to the network share and run pdflatex foo.tex
I get:
```

This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
entering extended mode
! I can't find file `foo.tex'.
<*> foo.tex
```

I can view the file with less, so it's not permissions.

My fstab mounts the drive as:
```

//someserver/dir /mnt/mountpoint cifs user,username=****,rw 0 0

```

Any ideas?

---

### Post by Netgull on 2011-06-02
Bump?

---

### Post by hawthornso23 on 2011-06-02
I've just run pdflatex on a tex file on a samba share on my local network. It worked just fine. I don't have a permanent fstab entry set up.  The resources are shared via password and not via login. I browsed to the file across the local network using nautilus, then opened a terminal there using "open terminal here". The directory mounted as 

~/.gvfs/username %28g%29 on machinename/mountname/path/to/file

So I don't know why it isn't working for you. It works for me. I can only hope that you will find this knowledge helpful and not just frustrating.

---

### Post by whingo on 2011-10-27
I have the exact same problem. A .tex file on a samba share and when I latex it I get: 

>$ latex foo.tex
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
entering extended mode
! I can't find file `foo.tex'.
<*> foo.tex

It works fine on a local drive.
Ubuntu version: 10.04 LTS

The samba share is monted in fstab.

Can anyone find out what the problem is?

---

### Post by Cardinal Cracker on 2012-01-30
Hi,

I had the same problem and solved it by getting rid of the "nounix" mount option (using mount option "unix" instead). This option does something I don't quite understand to the inode numbers reported by the Samba server.

Hope this helps

---

### Post by usterk on 2012-03-30
unix option doesn't work for me. I didn't find any workaround.

---

### Post by la1234uk on 2013-02-05
exactly same problem here. I have files on a remote RAID disk, and I cannot compile pdflatex or latex on those files. I have same "file not found" error. At first I lost quite a lot of time thinking it was my tex editor that was misconfigured, but then I realized it was the tex compiler. Everything works as usual if I transfer the files on the local machine.

My system is a 12.04 Ubuntu, gnome 3.4.
My fstab line to mount the disk is 

//xxx.xxx.xx.xx/netwk /media/teraDATA cifs credentials=/etc/samba/credentials-teraDATA,rw,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,iocharset=utf8 0 0   

============================================================================

followed the suggestion of hawthornso23 (thanks for sharing man!) and it worked...(!!)

I navigated with nautilus to the samba folder, used my password, then I opened a terminal in that folder (I had to install nautilus-open-terminal to do that, sudo apt-get install nautilus-open-terminal). From the terminal I fired pdflatex myfile.tex. In this case it worked no problem.

The conclusion is that there is a workaround for me, but still it is an open question why pdflatex does not process files on an apparently properly mounted disk. I tested for example to compile a remote myfile.c file with CC and found no problems. It is something it has to do with how pdflatex compiler access remote files.

Presumably modifying fstab mount command can fix the problem, but do not know how.

---

