---
title: "possible to install 'make' in home directory"
date: 2009-07-20
forum: General Help
---

### Post by xir_ on 2009-07-20
Hi all

I was wondering if any on of you fine people know if it is possible to install 'make' in a home directory? (from binary naturally)

unfortunately I've been given a system without root access and was tasked to compile some software... without make...

any help/ridicule would be appreciated

---

### Post by Kraut~salat on 2009-07-20
try the dpkg-deb -x <archive> <directory> command.

See the man page. Maybe that does the trick. It should just unpack the .deb archive to <directory>.

---

### Post by xir_ on 2009-07-20
thanks for the reply i believe the server i am on is a suse server.

I've not got much experience with non apt distros, should i be able to use an rpm to do the same thing?

---

### Post by qamelian on 2009-07-20
If the source  code is in your home directory and all you need to do is compile the apps, you can do that fine with out root permissions. You only need root if you are also installing the apps after compiling them. The make command runs fine without root access. It's 'make install' that requires root or sudo.

---

### Post by xir_ on 2009-07-20
> **qamelian said:**
> If the source  code is in your home directory and all you need to do is compile the apps, you can do that fine with out root permissions. You only need root if you are also installing the apps after compiling them. The make command runs fine without root access. It's 'make install' that requires root or sudo.

sorry if im being dumb, but how can i make from source without using the make command. My thoughts to get round this would be to use a binary for this reason.

---

### Post by Simian Man on 2009-07-20
If you have an rpm of make then you can use it in a few ways.  First you can try installing it directly to your home directory:
```
rpm -i make.rpm --prefix=/home/user/wherever
```

What I'd recommend though, is to unarchive it directly.  The gnome archive program has support for this, so type:
```
file-roller make.rpm
```
and you will be able to extract the files wherever you want.

---

### Post by xir_ on 2009-07-21
> **Simian Man said:**
> If you have an rpm of make then you can use it in a few ways.  First you can try installing it directly to your home directory:
```
rpm -i make.rpm --prefix=/home/user/wherever
```What I'd recommend though, is to unarchive it directly.  The gnome archive program has support for this, so type:
```
file-roller make.rpm
```and you will be able to extract the files wherever you want.

thanks for the reply, the system doesn't have file-roller (i think it only has kde installed), i did try locally (on my ubuntu install) and file roller puts out a archive type not support error and there doesnt seem to be anything in the repositories to fix this.

i did try your rpm extraction suggestion but got 
```
XXXXX-#####>rpm -i make-3.81-66.src.rpm --prefix=/home/Simon/rpm
error: cannot write to %sourcedir /usr/src/packages/SOURCES

```

i am trying to get round this by converting to a cpio archive (using rpm2cpio) and from that to a tar but am having no joy.

---

