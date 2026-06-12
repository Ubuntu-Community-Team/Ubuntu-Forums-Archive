---
title: "Can't run Synaptic"
date: 2010-09-25
forum: General Help
---

### Post by rafussen on 2010-09-25
I am new to Ubuntu and have been running v.9.10 for about 8 months. In trying to learn how to maneuver within the OS I most likely created some problems. The most recent one is with Synaptic, as I can't seem to be able to run it. Every time I run it, by either clicking the icon or in a terminal, it brings up this error:

E: Problem parsing dependency Depends
E: Error occurred while processing libspeexdsp1 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I run the 'sudo apt-get dist-upgrade' I get the same problem and error message. I obviously need synaptic working to get software and updates, but I mostly want to upgrade to the latest version of Ubuntu. Any help would be appreciated. Thanks in advance.

---

### Post by philinux on 2010-09-25
Try this

```
sudo dpkg --configure -a
```

Then this.

```
sudo apt-get -f install
```

Then.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any remaining errors.

---

### Post by rafussen on 2010-09-25
I tried your suggestions. This was the result:

rafussen@rafussen-desktop:~$ sudo dpkg --configure -a
[sudo] password for rafussen: 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 14741 package 'libpcap0.8':
 field name `Source2' must be followed by colon
rafussen@rafussen-desktop:~$ sudo apt-get -f install
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libspeexdsp1 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
rafussen@rafussen-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by philinux on 2010-09-25
[http://ubuntuforums.org/showthread.php?p=9517069#post9517069](http://ubuntuforums.org/showthread.php?p=9517069#post9517069)

From post 18 onwards you just need to modify for you errant package.

Or this, post 2.

[http://ubuntuforums.org/showthread.php?t=231301](http://ubuntuforums.org/showthread.php?t=231301)

---

### Post by rafussen on 2010-09-25
I tried both suggestions (posts), but to no avail: I used gksu gedit and deleted all references to humanity-icon-theme, saved and rebooted, and I also deleted the four humanity-icon-theme files found 'gksu nautilus /var/lib/dpkg/info'.

Are there any other possible remedies that are straightforward enough? Did I do something wrong? Is my only option to reinstall Ubuntu? I actually have a boot/install disc for Ubuntu 10.04.01 and am able to run a live session, but for some reason it won't install Ubuntu OS as an error comes up. Is that related to this synaptic problem?

Additionally, I retried your original suggestions in your first post and got the exact same results.

Any more help would be appreciated, thanks.

---

### Post by jmszr on 2010-09-25
rafussen,

Just a thought - all that output about cdrom made me wonder: 

Try going to System > Administration > Software Sources > Third-Party Software > and uncheckmark (if it's not already) the line at the top that says something like: cdrom:[//Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted]. I'm not sure of the exact wording as I'm running 8.04.

Try un-marking that line (if it's not already) and then reloading the Software Sources.

Hope that helps.

---

### Post by rafussen on 2010-09-25
It was checked, so I unmarked it. However, upon reload, and after downloading 42 of 42 packages, the same error message came up:

E: Problem parsing dependency Depends
E: Error occurred while processing libspeexdsp1 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Presumably it was then unable to update/reload the packages it attempted to. Obviously all of this has something to do with the updating software, but it is just beyond me on how to fix it. If you have any other suggestions, that would be great. But if you can't think of something else, then I will just have to reinstall Ubuntu. I am interested as to why the 10.04.1 install disc has an error in attempting to install it despite being able to use the live version off the disc. Do you think it is related to the problem I currently have with the installed version of Ubuntu? Anyways...

---

### Post by drs305 on 2010-09-25
It is either a problem with the downloaded package lists or with the APT status file. 

Dealing with the lists, we can clear them via Synaptic or Software Sources. In Synaptic, untick (but remember which ones) all the repositories in Ubuntu Software and Other/Third-Party Software. Change to another server via the Ubuntu Software tab, Download from:...

Next reselect the repositories that were previously selected and click the "Reload" button to refresh the lists.

---

### Post by rafussen on 2010-09-25
Well, that is the thing, I am unable to use Synaptic. In Software Sources, though, I can see the repositories and uncheck them. There appears to be only two repositories, which were unchecked to begin with, and they are 1) [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner AND 2) [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code). I don't know if that is normal or what. However, even after checking/unchecking them and choosing a different server, upon reload and after the downloading of all the packages, the same error message comes up (E: Problem parsing dependency Depends
E: Error occurred while processing libspeexdsp1 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.) and then the application closes.

I guess I am just going to have to reinstall Ubuntu, unless anyone else has any suggestions, and I would prefer to fix this instead of reinstalling.

---

### Post by mc4man on 2010-09-25
I think I'd open /var/lib/dpkg/status in a text editor, search libspeexdsp1, find the package section and post up what it shows. (also compare the same package section in /var/lib/dpkg/status_old

ex. (this is on  maverick, just an example of package section to look for and post.

> Package: libspeexdsp1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 204
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: speex
Version: 1.2~rc1-1ubuntu1
Depends: libc6 (>= 2.4)
Description: The Speex extended runtime library
 Speex is an audio codec especially designed for compressing voice at low
 bit-rates for applications such as voice over IP (VoIP). In some senses,
 it is meant to be complementary to the Vorbis codec which places a greater
 emphasis on high-quality music reproduction.
 .
 This package provides the runtime library of additional functions that
 are part of the Speex distribution.
Homepage: [http://www.speex.org/](http://www.speex.org/)
Original-Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>


---

### Post by rafussen on 2010-09-26
I located the relevant package, and this is what it says:

Package: libspeexdsp1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 208
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: speex
Version: 1.2~rc1-1
Depends: libc6 (>= 2.4)Description: The Speex extended runtime library
 Speex is an audio codec especially designed for compressing voice at low
 bit-rates for applications such as voice over IP (VoIP). In some senses,
 it is meant to be complementary to the Vorbis codec which places a greater
 emphasis on high-quality music reproduction.
 .
 This package provides the runtime library of additional functions that
 are part of the Speex distribution.
Original-Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Homepage: [http://www.speex.org/](http://www.speex.org/)

---

### Post by drs305 on 2010-09-26
> **rafussen said:**
> In Software Sources, though, I can see the repositories and uncheck them. There appears to be only two repositories, which were unchecked to begin with, and they are 1) [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner AND 2) [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code). I don't know if that is normal or what. 

Those are normal for the Other Software tab. You should have had 2-4 ticked in the Ubuntu Software tab as well and these would also need to be unticked.

If you didn't deselect them all (in both tabs), rerun what I recommended just to see if that solves things. I think there are more substantive issues, but this is the easiest fix.

If you still get errors, next try switching *status* files. APT keeps a backup of the file in case it gets corrupted. We can replace the current file with the backup. If that doesn't fix it, we will restore the original.

```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename status file
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status # copy status backup file and name it status  
sudo apt-get update  # see if problem is solved

```
If the problem remains, restore the original file:
```
sudo cp /var/lib/dpkg/status.bad /var/lib/dpkg/status
```

If this doesn't fix it either, the problem is definitely with the installation of the libspeexdsp1 package even though it's status shows the install was "ok".

---

### Post by mc4man on 2010-09-26
Maybe it's the way you copied/posted from the status file but it looks 'odd' to have the Description:... on the same line as Depends:...

---

### Post by rafussen on 2010-09-27
Sweet! It worked. I ran the code for switching the "status" file as you suggested. I still don't understand exactly all of what I did, but I hope to in the future for my learning of Ubuntu/linux. Maybe you could respond with a brief and general explanation of happened, or not. Anyways, I will mark this solved shortly.

---

### Post by drs305 on 2010-09-27
> **rafussen said:**
> Sweet! It worked. I ran the code for switching the "status" file as you suggested. I still don't understand exactly all of what I did, but I hope to in the future for my learning of Ubuntu/linux. Maybe you could respond with a brief and general explanation of happened, or not. Anyways, I will mark this solved shortly.

Glad you got your system restored.  :-)

I explained it a bit in [_post #10 of this thread_]("http://newyork.ubuntuforums.org/showpost.php?p=9864468&postcount=10").

As *mc4man* pointed out, the way the status file was copied to this thread, there is an odd character embedded. I can't reproduce the odd character here but it still shows in the post you made.
> Depends: libc6 (>= 2.4)Description: The Speex extended runtime library
If that really existed in the *status* file, that may have been enough to trigger the error message. Replacing the entire file with the backup apparently removed whatever was wrong with the file.

If you don't have any other questions, would you please mark this thread SOLVED via the "Thread Tools" link near the top right of the first post? Thanks.

---

### Post by mc4man on 2010-09-27
I guess if your curiosity extended that far you could compare the current working entry to the previous one. (unless you deleted it the status_old file is still there.
Whether is was the symbol or something else, you could probably figure it out, the orig. post indicated an issue with parsing depends, maybe because the descript was on same line? (if it was..

> E: Problem parsing dependency Depends
It's also possible there were other errors and it failed on first found.

---

