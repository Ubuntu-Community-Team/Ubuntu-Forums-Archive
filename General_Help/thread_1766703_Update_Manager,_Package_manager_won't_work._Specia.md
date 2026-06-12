---
title: "Update Manager, Package manager won't work. Special issue!"
date: 2011-05-24
forum: General Help
---

### Post by dmathwizard on 2011-05-24
Ok so I having the same issue as everyone else but it still exists despite the solutions other people are experiencing. 

Update manager, synaptic, and apt-get are not working no aptitude on here. 

Update manager says:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.'

apt-get has errors with headers, finding files, and wrong file types. I have gone to a couple locations and the files exist and the hash is correct, and the file types are correct. 

I have tried replacing the sources file.
I have tried [COLOR=Black]sudo rm -r /var/lib/apt/lists sudo apt-get clean
sudo apt-get update
[/COLOR] with the same problem happening upon updating. In the same exact areas.

---

### Post by plucky on 2011-05-24
> **dmathwizard said:**
> Ok so I having the same issue as everyone else but it still exists despite the solutions other people are experiencing. 

Update manager, synaptic, and apt-get are not working no aptitude on here. 

Update manager says:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.'

apt-get has errors with headers, finding files, and wrong file types. I have gone to a couple locations and the files exist and the hash is correct, and the file types are correct. 

I have tried replacing the sources file.
I have tried [COLOR=Black]sudo rm -r /var/lib/apt/lists sudo apt-get clean
sudo apt-get update
[/COLOR] with the same problem happening upon updating. In the same exact areas.

Try a different server.

Open Software Sources using the Synaptic Package Manager and on the first tab select a different download server

Good Luck

---

### Post by dmathwizard on 2011-05-24
Upon opening up synaptics says:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by linuxinstalledfromhdd on 2011-05-24
And you cut and paste exactly what is happening (the whole thing) when this shows in Terminal?

---

### Post by dmathwizard on 2011-05-24
thats from the synaptics gui

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try this from command line:

sudo apt-get update

sudo apt-get upgrade

Post the results (esp the errors)

---

### Post by dmathwizard on 2011-05-24
nono@acerx:~$ sudo apt-get update -q
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease [322 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease [320 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease [310 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Get:4 [http://archive.canonical.com](http://archive.canonical.com) natty InRelease [312 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease [308 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages/DiffIndex [349 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex [341 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages/DiffIndex
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages/DiffIndex [335 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex [330 B]
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US [344 B]
bzip2: (stdin) is not a bzip2 file.
Get:11 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [334 B]
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US [330 B]
/usr/bin/xz: (stdin): File format not recognized
bzip2: (stdin) is not a bzip2 file.
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en [339 B]
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
  0  Ok
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [329 B]
/usr/bin/lzma: Decoder error
/usr/bin/lzma: Decoder error
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [335 B]
/usr/bin/lzma: Decoder error
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en [340 B]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources
  0  Ok
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
  0  Ok [IP: 91.189.92.167 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
  0  Ok
Get:17 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en [335 B]
/usr/bin/lzma: Decoder error
Err [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
  0  Ok
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US [345 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
  0  Ok [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages
  0  Ok
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Get:19 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US [333 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease [313 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US [335 B]
bzip2: (stdin) is not a bzip2 file.
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [334 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages/DiffIndex
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages/DiffIndex [354 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [343 B]
bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en [334 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US [348 B]
/usr/bin/lzma: Decoder error
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US [342 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en [345 B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
  0  Ok [IP: 91.189.88.30 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources/DiffIndex
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources [323 B]
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/lzma: Decoder error
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources
  
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources [326 B]
Fetched 10.2 kB in 37s (272 B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/source/Sources)  0  Ok

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources)  0  Ok [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages)  0  Ok

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  0  Ok

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  0  Ok

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources)  0  Ok [IP: 91.189.92.167 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  0  Ok

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  0  Ok [IP: 91.189.88.30 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.



>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

nono@acerx:~$ sudo apt-get upgrade -q
Reading package lists...
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
nono@acerx:~$

---

### Post by linuxinstalledfromhdd on 2011-05-24
It could be that you added them or this could be an actual bug. Hang tight while others have a look. 

BUMP

---

### Post by dmathwizard on 2011-05-24
Thank you for looking.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Hang in there for a while. Someone is going to read it, and it's probably something easy that can be fixed from the command line..  Or it's a bug.

---

### Post by plucky on 2011-05-25
> **dmathwizard said:**
> Upon opening up synaptics says:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Did you manage to change the download server? 

If Yes,did you use the "Main Server"

Or does the error cause the Synaptic Package Manager to close and not allow you to change the server?

---

### Post by dmathwizard on 2011-05-25
When this error pops up I have no other option than to press close and it closes out the program, I am have been searching online to a command line version to switch servers to no avail.

---

### Post by plucky on 2011-05-25
> **dmathwizard said:**
> When this error pops up I have no other option than to press close and it closes out the program, I am have been searching online to a command line version to switch servers to no avail.

Try this command in a terminal ```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
``` and see if the Software Sources GUI opens.

Or try opening the "Update Manager" and select the "Settings" button

Good Luck

---

### Post by dmathwizard on 2011-05-25
ok I ran it and selected main server and it downloaded some packages, but at the end I received this:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/source/Sources)  0  Ok
Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages)  0  Ok
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  0  Ok
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  0  Ok
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  0  Ok
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  0  Ok [IP: 91.189.88.40 80]
Some index files failed to download. They have been ignored, or old ones used instead.


Also after closing this came up 

An error occurred

The following details are provided:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by plucky on 2011-05-25
Can you post the output of ```
cat /etc/apt/sources.list
``` and ```

ls -l /etc/apt/sources.list.d/
```

---

### Post by dmathwizard on 2011-05-26
> **plucky said:**
> Can you post the output of ```
cat /etc/apt/sources.list
``` and ```

ls -l /etc/apt/sources.list.d/
```

nono@acerx:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

nono@acerx:~$ ls -l /etc/apt/sources.list.d/
total 8
-rw-r--r-- 1 root root 124 2011-05-25 08:46 hydr0g3n-ppa-natty.list
-rw-r--r-- 1 root root 124 2011-05-25 08:46 hydr0g3n-ppa-natty.list.save

---

### Post by plucky on 2011-05-26
That list looks ok.I would remove the need to download the source files unless you need them.

That box is on the first page of Software Sources GUI.

Now that you have changed the server,run the command ```
sudo rm /var/lib/apt/lists/* -vf
``` and then use the Software Sources GUI to disable and enable repositories to see which one is causing the error > Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://ppa.launchpad.net/hydr0g3n/pp...source/Sources](http://ppa.launchpad.net/hydr0g3n/pp...source/Sources) 0 Ok
Failed to fetch [http://archive.canonical.com/ubuntu/...-i386/Packages](http://archive.canonical.com/ubuntu/...-i386/Packages) 0 Ok
Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...source/Sources](http://extras.ubuntu.com/ubuntu/dist...source/Sources) 0 Ok
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/pp...-i386/Packages](http://ppa.launchpad.net/hydr0g3n/pp...-i386/Packages) 0 Ok
Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...-i386/Packages](http://extras.ubuntu.com/ubuntu/dist...-i386/Packages) 0 Ok
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources](http://archive.ubuntu.com/ubuntu/dis...source/Sources) 0 Ok [IP: 91.189.88.40 80]
Some index files failed to download. They have been ignored, or old ones used instead.


Good Luck

---

### Post by dmathwizard on 2011-06-07
I would have loved to work on the issue that I posted but due to work constraints I had to backup and reinstall. I'm all up and running now. Although I did go with Maverick 10.10 instead of Natty and I haven't had a problems as of yet. Thank you everybody for your help.

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **dmathwizard said:**
> I would have loved to work on the issue that I posted but due to work constraints I had to backup and reinstall. I'm all up and running now. Although I did go with Maverick 10.10 instead of Natty and I haven't had a problems as of yet. Thank you everybody for your help.

I love 10.10 too.  Great stuff.. Here is guide for after you get it installed as well, in case you need one:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Take your time with it. :)

---

