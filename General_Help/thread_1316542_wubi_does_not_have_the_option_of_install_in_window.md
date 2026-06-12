---
title: "wubi does not have the option of install in windows"
date: 2009-11-06
forum: General Help
---

### Post by lxyscls on 2009-11-06
I customized my ubuntu910&#65292; after that I made the / into a new squashfs(about 400MB).
I need the wubi to install my new customized system in my other computer which has a window xp pro. Unfortunately, it did not show the botton to install ubuntu:)

Where is the probelm? thx~

---

### Post by Uncle Spellbinder on 2009-11-06
I thought Wubi installed proper releases. Custom install? I didn't have a clue that was even possible.

---

### Post by lxyscls on 2009-11-06
> **Uncle Spellbinder said:**
> I thought Wubi installed proper releases. Custom install? I didn't have a clue that was even possible.
proper release? OK, I made another squashfs(more than 700MB, which just add some apps, I just replaced the filesystem.squashfs), wubi pop up the installation button!
I gave some wubi source code in /data/isolist.ini:

[DEFAULT]  [2]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L2")   
version=9.10  [3]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L3")   
info_file=.disk/info  [4]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L4")   
kernel=casper/vmlinuz  [5]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L5")   
initrd=casper/initrd.lz  [6]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L6")   
files_to_check=casper/filesystem.squashfs  [7]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L7")   
md5sums=md5sum.txt  [8]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L8")   
metalink_md5sums=MD5SUMS-metalink  [9]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L9")   
metalink_md5sums_signature=MD5SUMS-metalink.gpg  [10]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L10")   
size=0  [11]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L11")   
min_iso_size=600000000  [12]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L12")   
max_iso_size=900000000  [13]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L13")   
min_disk_space_mb=3000  [14]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L14")   
min_memory_mb=256  [15]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L15")   
support=http://www.ubuntu.com/support  [16]("http://bazaar.launchpad.net/%7Eubuntu-installer/wubi/trunk/annotate/head%3A/data/isolist.ini#L16")   
installation_dir=ubuntuDoes min_iso_size have any relationship with the installation?

---

### Post by Uncle Spellbinder on 2009-11-06
> **lxyscls said:**
> proper release? 

Uh, yes. As in the ISO from Ubuntu. I had no idea someone could create their own and use Wubi.

---

### Post by lxyscls on 2009-11-06
> **Uncle Spellbinder said:**
> Uh, yes. As in the ISO from Ubuntu. I had no idea someone could create their own and use Wubi.
I am sure that wubi can install customized ubuntu now!

I rebuilt the wubi by setting the min_iso_size to 300MB, it works well(My system iso is about 450MB)~

I think there is a little bug in wubi's Makefile( line 62) when I built it in my ubuntu910~

---

