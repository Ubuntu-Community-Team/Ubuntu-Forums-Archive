---
title: "Installing .tar.xz files"
date: 2011-06-11
forum: General Help
---

### Post by kexus on 2011-06-11
So, I'm trying to install a game.  I've installed most of its dependencies so far, but one of them needs other things to install.  So I'm getting those.  But one of them is a tar.xz.  A quick google search said I use a program called pacman, but when I used *sudo apt-get install pacman* it just installed the game pacman. So does anyone have a download for the *right* pacman or an alternative program?

EDIT: Never mind, I found it.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **kexus said:**
> So, I'm trying to install a game.  I've installed most of its dependencies so far, but one of them needs other things to install.  So I'm getting those.  But one of them is a tar.xz.  A quick google search said I use a program called pacman, but when I used *sudo apt-get install pacman* it just installed the game pacman. So does anyone have a download for the *right* pacman or an alternative program?

Did you install everything you need on your system to work with compressed files?

Scroll down and review:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)


sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils uudeview mpack lha arj cabextract file-roller

---

### Post by 3xp10r3r|X13 on 2011-06-11
pacman is a repository for opensuse.

however, here you go:

for .txz fies type:
```

tar -Jxvf file.txz
```for .xz files type:
```

tar -Jxf file.xz
```that should do it :)

---

### Post by Pekestoemp on 2012-02-11
Hello,

I have also a xz file I cannot open : message from terminal gives me :

sato@sato-laptop:~/rhbx$ tar -Jxf rhythmbox-2.95.tar.xz 
tar: xz: Cannot exec: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
sato@sato-laptop:~/rhbx$ 

ls gives me :

sato@sato-laptop:~/rhbx$ ls
rhythmbox-2.95.tar.xz
sato@sato-laptop:~/rhbx$ 

The sha256sum is identical.
Somewhere I read I should install XZutils, but that didn't work either.:(

Can someone help me ?
Thanks!

---

### Post by raja.genupula on 2012-02-11
[http://ubuntuforums.org/showthread.php?t=1116012](http://ubuntuforums.org/showthread.php?t=1116012)

---

### Post by WorMzy on 2012-02-11
> **3xp10r3r|X13 said:**
> pacman is a repository for opensuse.

pacman is also the package manager for Arch Linux, it uses .tar.xz files as packages (like dpkg uses .deb).

OP: You don't need pacman on Ubuntu. You also cannot "install" .tar.xz archives. If the archive is a precompiled package for Arch Linux, then you may be able to extract the contents, then manually copy the files into their respective destinations; however, I recommend against doing that. For 1) Arch Linux is a much more "cutting edge" distro, meaning that there's a chance that any executables contained in that archive are linked against newer libraries than Ubuntu currently has available, so you won't be able to run the applications anyway, and 2) you might overwrite existing files during the copy process, which could break other applications, and 3) you shouldn't really install files manually, you should let the package manager install and remove things.

If the archive contains source code, then you can compile that, then use [checkinstall]("https://help.ubuntu.com/community/CheckInstall") to make a .deb file.

---

### Post by Pekestoemp on 2012-02-11
Thanks to [raja.genupula]("http://ubuntuforums.org/member.php?u=1184528") I did it !:D
I was as happy as a child ! 

But offcourse, I ran into something ohter : I need to install gobject-introspection and I run into the following error :

make[2]: *** [Gio-2.0.gir] Error 1
make[2]: Leaving directory `/home/sato/Downloads/gobject-introspection-1.30.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sato/Downloads/gobject-introspection-1.30.0'
make: *** [all] Error 2
sato@sato-laptop:~/Downloads/gobject-introspection-1.30.0$ 

I searched this forum and found that I have to rebuild it from scratch (how ??) or that I need to remove  gperiodic.h from  install/include/glib-2.0/gio/ 
but I can't seem to find this file....
(source: [http://ubuntuforums.org/showthread.php?t=1603874&page=34](http://ubuntuforums.org/showthread.php?t=1603874&page=34) )

Can someone walk me through it ?

---

