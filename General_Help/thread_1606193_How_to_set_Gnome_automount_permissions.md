---
title: "How to set Gnome automount permissions?"
date: 2010-10-26
forum: General Help
---

### Post by Vermind on 2010-10-26
Hi,
I have a cross-platform game on a Windows partition. Ubuntu 10.04 and 10.10 do not allow executing files on a NTFS partition when automatically mounted through Nautilus. I would like to know what I need to change to make my system automatically mount NTFS ( and possibly VFAT ) partitions so that the exec bits are set, at least for my user.

I tried ```
gconftool-2 -t list --list-type string -s /system/storage/default_options/ntfs-3g/mount_options "[defaults, exec]"
``` with no luck.

Any ideas?

---

### Post by dino99 on 2010-10-26
two choices:

- tweak /etc/fstab : add this partition
- install & use mountmanager to set your prefs

---

### Post by WorMzy on 2010-10-26
[[COLOR="Blue"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by Vermind on 2010-10-26
thanks for the answers, but if i use fstab, the settings will not apply for any past and future partitions of the given filesystem type. if i connect a bunch of usb hard disks with ntfs, it will not apply to them. I know that udisks or gnome-vfs-mount or whatever its called nowadays has a gconf key that allows setting mount options, i just cannot find it now .... I am happy with any method that lets the automount system that is already there mount them. I.e. I do not want to install extra software to do something that i know is doable without it, and I do not want my partitions automounted on boot or be visible in fstab.
I will look at mountmanager to see what it does later, thanks.

---

### Post by mc4man on 2010-10-26
If you can't find any other way then you can re-build udisks to allow exec's on ntfs and vfat. 
Then main issue is that then all .txt files will be marked as executable, that's why the changes were made .
2 seperate source changes - first for vfat, then ntfs.
(check the changlelog to see.

The edit for vfat is straightforward, for ntfs will take a little digging. (never looked here

This was the last version to allow ntfs, and the one that instituted the change for vfat

[https://launchpad.net/ubuntu/+source/udisks/1.0.1-2](https://launchpad.net/ubuntu/+source/udisks/1.0.1-2)

---

### Post by Vermind on 2010-10-26
Hi,
I found [a question that asks how to set the mount options]("https://answers.launchpad.net/ubuntu/+source/udisks/+question/125527") when udisks mounts some partitions (essentially the mechanism I am looking for). I also tried to mount my ntfs partition manually using udisks, but whatever mount options I set are either not "allowed" or just do nothing and the partition is mounted with the default options which are ```
rw,nosuid,nodev,allow_other,blksize=4096,default_permissions
```

I looked into /lib/udev/rules.d, there are some interesting rules there but sadly none of them mention mount options [like here]("http://wiki.archlinux.org/index.php/Udev#Auto_mounting_USB_devices"). One mentions ntfs, but that is in the context of detecting recovery partitions and not showing them to the user. 

Perhaps I will use the fstab workaround if this becomes urgent.
Mountmanager looks good for fstab tweaking and doing the udev things if this becomes the issue.

---

### Post by mc4man on 2010-10-26
> Ubuntu 10.04 and 10.10 do not allow executing files on a NTFS partition

Are you referring to binaires (.exe's) or text files (scripts) or both
They are somewhat treated differently. (.exe's don't need to be 'set', scripts do.

In any event, as far as 'showing' executable on either in both vfat and ntfs this is the current settings in udisk maverick source (udisks-1.0.1+git20100614/src/device.c

> /* ---------------------- vfat -------------------- */

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1",[COLOR="Blue"] "showexec",[/COLOR] NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", [COLOR="Blue"]"showexec",[/COLOR] NULL };
static const char *vfat_allow_uid_self[] = { "uid=", NULL };
static const char *vfat_allow_gid_self[] = { "gid=", NULL };

/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", [COLOR="Blue"]"fmask=0177",[/COLOR] NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ntfs_allow_uid_self[] = { "uid=", NULL };
static const char *ntfs_allow_gid_self[] = { "gid=", NULL };

What's marked in blue is what's preventing scripts from being executable and .exe's from being set also (even though .exe's don't need to be

As far as scripts - I believe it's all or nothing - either all text files or none. There is no way to set or unset files individually - you can't change/set permissions on ntfs or vfat.

Screens show with blue removed - #3 is an .exe

---

### Post by Vermind on 2010-10-27
Hi and thanks for the response,
I am referring to linux binaries in particular. My current test case is [Dwarf Fortress]("http://www.bay12games.com/dwarves/index.html"), which I have extracted on my Windows desktop. The directory contains both the Linux and Windows versions. To run dwarf fortress, I would run the shell script called df which in turn starts runs an ELF 32-bit executable. when doing this with the NTFS partition mounted, I get:
```
/media/OS/Users/Vermind/Desktop/dfg_31_16 
$ sh ./df
./df: 6: ./libs/Dwarf_Fortress: Permission denied
```

Executing .exe files fails:
```
/media/OS/Program Files/GIMP 2/bin 
$ ./gimp-2.6.exe
bash: ./gimp-2.6.exe: Permission denied
```

Of course I can execute them via double-click or just by prepending wine to the command, so they are not the issue. Also text scripts are not an issue since I can prepend sh or bash to them.

I will try the fix and report back.

---

### Post by Vermind on 2010-10-27
The fix pointed out by mc4man works perfectly, thanks. I am able to run the Linux dwarf fortress from the Windows partition.
Now to wait until I have to open text files on the FAT and NTFS partitions or a virus strikes me from them...

The steps I did, to help people in the future:
[LIST=1]
[*]Download the sources via apt-get:
```
mkdir dev
cd dev
apt-get source udisks
```
[*]Modify src/device.c:
```
cd udisks-1.0.1+git20100614
gedit src/device.c
```
(Remove the parts in blue as shown by mc4man (with the trailing commas).)
The relevant lines (Line 5870-) will look like this:
```
static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1",/*"showexec",*/ NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=","codepage=", "iocharset=", "usefree", /*"showexec",*/ NULL };
static const char *vfat_allow_uid_self[] = { "uid=", NULL };
static const char *vfat_allow_gid_self[] = { "gid=", NULL };

/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", /*"fmask=0177",*/ NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
```

[*]Download the build deps:
```
sudo apt-get build-dep udisks
```
[*]Build it via debuild:
```
debuild
```
[*]Install the package with dpkg:
```
cd ..
sudo dpkg -i udisks_1.0.1+git20100614-3_amd64.deb
```
[/LIST]

Note to people having the same problem: Your version of udisks may differ, so substitute everything after udisks- and udisks_ with your version number.

---

### Post by WorMzy on 2010-10-27
I just run DF from my Linux partition.

You don't need to worry about viruses being on the NTFS partition, unless they're designed for Linux and for some reason you decide to run them with sudo. :P

---

### Post by Vermind on 2010-10-27
Oh,
I would like to run DF from my Linux partition, however, I couldn't find a driver for Windows 7 that would allow me to open ext4 partitions in Windows. The only one that works is called ext4explorer, and it only allows copying files and directories from the partition, not viewing it transparently. Therefore I would not be able to play DF in Windows from the Linux partition.

---

### Post by WorMzy on 2010-10-27
Ah. I suppose if you're often switching from Linux to Windows it'd be best to keep it on an NTFS partition anyway, I wouldn't trust Windows to access my Linux partitions in the first place. fsck could probably detect and fix any problems that might arise, but I'd rather not risk it.

Anyway, it's nice to see a fellow Dwarfer on the forums. :D

---

### Post by cthlhu1987 on 2010-11-29
Thank you SOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO much to mc4man and Vermind for showing how to solve this problem.

---

### Post by ghost_zero on 2010-12-01
I mean yes it is quite simple to compile it yourself but it can't be that I am requried to re-compile udisks to get such a simple change.
Especially, this could be problematic regarding possible future updates of udisks...

Isn't there a way to do this over some configuration files (e.g. polkit-1 or ".rules" or whatever).

But still thanks for the tutorial to compile it myself.

---

### Post by Anessen on 2010-12-08
I like that there is a solution to this (I am having a similar problem), but hard coding something like this is totally absurd. Did nobody think that maybe this would need to be changed for some people?

---

### Post by Vermind on 2010-12-08
> **Anessen said:**
> I like that there is a solution to this (I am having a similar problem), but hard coding something like this is totally absurd. Did nobody think that maybe this would need to be changed for some people?

My sentiments exactly.

---

### Post by bingel on 2011-03-05
Hi everyone and excuse me in advance for my bad English.
I need to resurrect this old thread because I have this problem:

I need to automount through *udisks* a *hfsplus* formatted partition using non standard options and non standard driver.

The file system driver is named *ufsd* and I need to mount the partition in this way:

```
udisks --mount /dev/sdXn --mount-fstype ufsd --mount-options uid=1000,gid=1000;nodev,nosuid,rw

```The answer is that uid and gid options are not allowed.

I watched the */src/device.c* file as you described in this thread, but it doesn't mention any rule for hfsplus mounting.

Do you know how should I modify this file? ...or any other file?

Thanks in advance

---

### Post by WorMzy on 2011-03-05
[http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt)

Those are the hfsplus options, and it should support uid/gid/umask options. As for ufsd, I'm not sure. There's ufs options here: [http://www.mjmwired.net/kernel/Documentation/filesystems/ufs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ufs.txt) I don't know if it's related or not, but it doesn't seem to offer any options either.

You may be out of luck.

---

### Post by bingel on 2011-03-05
Thanks, however UFS and UFSD are not the same thing.

UFSD is a proprietary driver that is able to read and write HFS+ formatted partitions that have journaling enabled.

 As for HFS+, instead, my problem is figuring out how to make *udisks* able to mount this file-system using options that are disabled by default (and therefore not allowed) and that must be enabled (I assume) by changing and rebuilding udisks source code (in a similar way as described in this thread for NTFS file system).

Moreover I have to clarify that I'm using Ubuntu 10.04 and my kernel version is 2.6.32-28-generic

---

### Post by Vermind on 2011-03-06
In the Ubuntu 10.10 sources for udisks, I have this from line 5900 on:
```
static const char *any_allow[] = { "exec", "noexec", "nodev", "nosuid", "atime", "noatime", "nodiratime", "ro", "rw", "sync", "dirsync", NULL };

static const FSMountOptions fs_mount_options[] =
  {
    { "vfat", vfat_defaults, vfat_allow, vfat_allow_uid_self, vfat_allow_gid_self },
    { "ntfs", ntfs_defaults, ntfs_allow, ntfs_allow_uid_self, ntfs_allow_gid_self },
    { "iso9660", iso9660_defaults, iso9660_allow, iso9660_allow_uid_self, iso9660_allow_gid_self },
    { "udf", udf_defaults, udf_allow, udf_allow_uid_self, udf_allow_gid_self },
  };
```
Perhaps changing any_allow to include the options you need or adding something like { "ufs", option, option, option ... }, below would help?

---

### Post by bingel on 2011-03-06
That was my idea but I have seen, for exemple, that NTFS is mentioned in other files than */src/device.c* (excluding the various files in *helpers* directory, I refer mainly to the file /src/*daemon.c* and */tests/run*) therefore I think that if I will add the item UFSD in this file, I will have to do even in the others.

The strange thing, however, is that by mounting in a standard way the file-system hfs+ (however using *udisks* and not *mount*), this is mounted according to strict rules (moreover only certain options are allowed) and the same goes for the old brother (hfs) who, in turn, is mounted under other rules . This makes me think that the binaries that come with ubuntu are compiled with the rules also for hfs and hfsplus despite this rules, in source files, are not included.

What do you think about?

I hope I was clear.

PS:
I must point out that the version of the source that I downloaded is this:

```
apt-get source udisks=1.0.1-1ubuntu1
```(the same currently installed in my system)

---

### Post by bingel on 2011-03-06
I solved by editing the file /src/device.c in this way (the parts I've added are in red):

/* ---------------------- vfat -------------------- */

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", NULL };
static  const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=",  "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", NULL };
static const char *vfat_allow_uid_self[] = { "uid=", NULL };
static const char *vfat_allow_gid_self[] = { "gid=", NULL };

/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ntfs_allow_uid_self[] = { "uid=", NULL };
static const char *ntfs_allow_gid_self[] = { "gid=", NULL };

[COLOR=Red]/* ---------------------- ufsd -------------------- */

static const char *ufsd_defaults[] = { "uid=", "gid=", "dmask=0077", NULL }; [/COLOR] [COLOR=Red]
static const char *ufsd_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ufsd_allow_uid_self[] = { "uid=", NULL };
static const char *ufsd_allow_gid_self[] = { "gid=", NULL };[/COLOR]

/* ---------------------- iso9660 -------------------- */

static const char *iso9660_defaults[] = { "uid=", "gid=", "iocharset=utf8", "mode=0400", "dmode=0500", NULL };
static const char *iso9660_allow[] = { "norock", "nojoliet", "iocharset=", "mode=", "dmode=", NULL };
static const char *iso9660_allow_uid_self[] = { "uid=", NULL };
static const char *iso9660_allow_gid_self[] = { "gid=", NULL };

/* ---------------------- udf -------------------- */

static const char *udf_defaults[] = { "uid=", "gid=", "iocharset=utf8", "umask=0077", NULL };
static const char *udf_allow[] = { "iocharset=", "umask=", NULL };
static const char *udf_allow_uid_self[] = { "uid=", NULL };
static const char *udf_allow_gid_self[] = { "gid=", NULL };

/* ------------------------------------------------ */
/* TODO: support context= */

static  const char *any_allow[] = { "exec", "noexec", "nodev", "nosuid",  "atime", "noatime", "nodiratime", "ro", "rw", "sync", "dirsync", NULL };

static const FSMountOptions fs_mount_options[] =
  {
    { "vfat", vfat_defaults, vfat_allow, vfat_allow_uid_self, vfat_allow_gid_self },
    { "ntfs", ntfs_defaults, ntfs_allow, ntfs_allow_uid_self, ntfs_allow_gid_self },
    [COLOR=Red]{ "ufsd", ufsd_defaults, ufsd_allow, ufsd_allow_uid_self, ufsd_allow_gid_self },[/COLOR]
    { "iso9660", iso9660_defaults, iso9660_allow, iso9660_allow_uid_self, iso9660_allow_gid_self },
    { "udf", udf_defaults, udf_allow, udf_allow_uid_self, udf_allow_gid_self },
  };

/* ------------------------------------------------ */

---

### Post by i30817 on 2011-05-23
This is pathetic. I'm just going to undelete a file and i was mounting my usb disks to hold the program since the main partition has to be unmounted and now i have to compile ******* udisks just because of this.

Who thought it's a good idea to not allow the superuser to change the permissions of a mounted partition without recompiling the automount program?

:mad:

---

### Post by kaefert66014235 on 2012-12-11
Thanks to mc4man and Vermind for the solution, although I agree with you all that its ridiculous that we need to adapt the source code to fulfill this simple requirement.
I post here, because I'm using Ubuntu 12.10 (Linux Mint 14 to be concrete) and here there is a new udisks release (udisks2) that gets used. 

So here is an adapted version of Verminds guide for udisks2:

[LIST=1]
[*]Download the sources via apt-get:
```
mkdir dev
cd dev
apt-get source udisks2
```
[*]Modify src/udiskslinuxfilesystem.c:
```
cd udisks2-2.0.0
gedit src/udiskslinuxfilesystem.c
```
(Remove or comment out the parts in blue as shown by mc4man (including the trailing commas) see [http://ubuntuforums.org/showpost.php?p=10031303&postcount=7](http://ubuntuforums.org/showpost.php?p=10031303&postcount=7))
The relevant lines (277 to 286) will look like this:
```
static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1",/*"showexec",*/ NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=","codepage=", "iocharset=", "usefree", /*"showexec",*/ NULL };
static const char *vfat_allow_uid_self[] = { "uid=", NULL };
static const char *vfat_allow_gid_self[] = { "gid=", NULL };

/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", /*"fmask=0177",*/ NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
```

[*]Download the build deps:
```
sudo apt-get build-dep udisks2
```
[*]Build it via debuild: (you can safely ignore the fatal-error telling you that you can't gpg sign the built deb package because you don't have the secret key
```
debuild
```
[*]Install the package with dpkg:
```
cd ..
sudo dpkg -i udisks2_2.0.0-1ubuntu1_amd64.deb
```
[/LIST]

---

