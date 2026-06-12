---
title: "mount/CIFS acting up after last update"
date: 2009-10-04
forum: General Help
---

### Post by j.daniel on 2009-10-04
**Hello,**

  Just a quick check if any of you had the same experience as I have:

  I have a remote file system mounted via CIFS using the "regular" setup with an entry into the fstab and the credentials in /root/my_credentials. I can then mount it as a regular user with the command "mount /NAS/" and all worked fine.

  However I installed the last batch of updates a few days ago (around october 1st). They included a lot of updates to the samba / CIFS system. After this update, when I run the command "mount /NAS/", I get the following error:

[COLOR="DarkRed"]**error - 1 (Unknown error 4294967295) opening credential file /root/my_credentials**[/COLOR]

  ...quite annoying to say the least.

  I can get around this problem by doing the follwoing

```
sudo chmod o+r /root/my_credentials
mount /NAS/
sudo chmod o-r /root/my_credentials
```

  ...but I don't find that very satisfying.

  I have a second ubuntu computer which I have not yet updated, and as things are now, I wont either. Things still works fine on that one.

Anyone else?

Cheers
/ Daniel

---

### Post by scasa on 2009-10-14
I can confim that.

It has been working perfectly before the update using a credentials file without user permissions, but returns an error now. It might be related to a security fix in the latest update. Running "aptitude changelog smbfs" shows

>   * SECURITY UPDATE: credentials file disclosure and unauthorized usage via
    setuid mount.cifs
    - debian/patches/security-CVE-2009-2948.patch: don't open credentials
      file if user doesn't have permission, and don't print password when
      using verbose option in source/client/mount.cifs.c.
    - CVE-2009-2948
and this can also be found in the release note [http://www.samba.org/samba/history/samba-3.4.2.html](http://www.samba.org/samba/history/samba-3.4.2.html).

It's quite annoying since I use mount.cifs every day and I dont want my pwd to just hang around everywhere in plain text.

Cheers, Sandro

---

### Post by j.daniel on 2009-10-16
Aw!

That just stinks. Having the credentials in a normally non-accessible file was a feature! Typical that they remove a feature to fix the problem with --verbose. Why didn't they fix the --verbose option itself? Its like cutting of your arm to fix a broken fingernail.

Well - I will stop upgrading the samba suite on my other linux boxes. See if I can pin the version at whatever it was before this one and downgrade on the computer that I insalled the update on.

/ Daniel

---

### Post by j.daniel on 2009-10-17
**Ok,**

  After much head-bashing I have managed to down-grade my samba suite. It was not the most straightforward thing I've done, so I thought I'd share my experience here.

  Probably the only thing you need to do is to generate the preferences file and run [FONT="Courier New"]apt-get upgrade[/FONT], but as I only got it all together after all the rest, I cannot verify this.

  Anyway: The presence of a correctly formatted file called [FONT="Courier New"]/etc/apt/preferences[/FONT] can pin packages at certain versions and even downgrade some packages (for priorities > 1000).

  So, I fired up gedit through
[FONT="Courier New"]**gksudo gedit /etc/apt/preferences &**[/FONT]

  I did not have such a file before, so I had an empty file to start with. I entered the following text:

```
Explanation: Pin version of the samba suite since later versions
Explanation: loose the ability to read credentials in /root/
Package: samba-common
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

Package: libsmbclient
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

Package: smbclient
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

Package: smbfs
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

Package: libwbclient0
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

Package: winbind
Pin: version 2:3.3.2-1ubuntu3
Pin-Priority: 1001

```

  **Note**: I am not sure, but there seems to be a version 2:3.3.2-1ubuntu3.1 as well, but I cannot really find it as a package, so I cannot downgrade to it. However if you have it installed; pin that version instead - that way you won't downgrade a (working) 3.1 to a 3. It is only a 3.2 system that you'd like to go back to 3.

  After this was saved, I ran [FONT="Courier New"]**sudo apt-get -u upgrade**[/FONT] to check that it seemed to do what I wanted and then I removed the -u option and ran it live ([FONT="Courier New"]**sudo apt-get upgrade**[/FONT]).

  As I had not managed to pin all the packages above I ended up with a mixed system and I had to download and install the deb packages themselves for the other components. I downloaded what I needed from [FONT="Courier New"][http://ftp.acc.umu.se/ubuntu/pool/main/s/samba/](http://ftp.acc.umu.se/ubuntu/pool/main/s/samba/)[/FONT] (that was how I realized that the previous version version was not called 2:3.3.2-1ubuntu3.1 but just 2:3.3.2-1ubuntu3) and ran [FONT="Courier New"]**sudo dpkg -i *package1.deb package2.deb ...***[/FONT].

  In the end I had managed to get all components down from 2:3.3.2-1ubuntu3.2 to 2:3.3.2-1ubuntu3. Use [FONT="Courier New"]**dpkg -l *package***[/FONT] to see the version (i.e. [FONT="Courier New"]**dpkg -l smbfs**[/FONT]) - just make sure that the terminal window is wide enough, otherwise it crops the version number...

  Google was my friend :) I am not really a linux hacker, but with some googling for things like "debian downgrade package" and so on, I managed to fix this. One useful link was the apt-get section of the [**Debian Wiki**]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html"):

  ...and the other one I found useful was [**this**]("http://www.crazysquirrel.com/computing/debian/downgrade.jspx").

Good luck!
/ Daniel

---

### Post by j.daniel on 2009-10-17
Made some edits to my previous post: apparently there are a version 3.1 but I cannot downgrade to it somehow, so a downgrade must go to 3. If you have 3.1 though - pin it!

Cheers
/ Daniel

---

