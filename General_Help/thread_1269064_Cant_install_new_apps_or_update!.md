---
title: "Cant install new apps or update!"
date: 2009-09-17
forum: General Help
---

### Post by udunwanan0 on 2009-09-17
I've been having this issue for quite awhile now, whenever I try to install a new app or update the ubuntu system it always starts the installation and halfway fails popping up an error message saying something about cant fetch from something.ubuntu. something.

I cant update or install new apps! 
Please help :confused:

---

### Post by spcwingo on 2009-09-17
What release are you using?  You can find out by opening a terminal and posting the output of this command:

```
lsb_release -a
```

---

### Post by udunwanan0 on 2009-09-17
i have a 7.1

---

### Post by drs305 on 2009-09-17
Welcome to Ubuntu.

EDITED: Written/posted simultaneously with post above. The following is now not necessary. Go to post #6.

If you are running a fairly recent version of Ubuntu, try installing it via the command line and posting the error message(s) you are getting.

Open a terminal via Applications, Accessories, Terminal.
Then try installing one of the apps you are having problems with:
```

sudo apt-get update
sudo apt-get install <packagename>

```
Example: sudo apt-get install 2vcard

You will be asked for your password. Type in in -  you won't see it - then hit ENTER.

---

### Post by udunwanan0 on 2009-09-17
well i followed your instructions and here is the error message

WARNING: The following packages cannot be authenticated!
  libartsc0 libaudio2 libdvdread3 libmp4v2-0 libfaac0 libpulse0 libungif4g
  libxvidcore4 libx264-54 mplayer
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libartsc0 1.5.8-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libaudio2 1.9-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libdvdread3 0.9.7-3ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libungif4g 4.1.4-5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libxvidcore4 2:1.1.2-0.1ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libx264-54 1:0.svn20070309-4ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libpulse0 0.9.6-1ubuntu2.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse mplayer 2:1.0~rc1-0ubuntu13.3
  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.8-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc1-0ubuntu13.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc1-0ubuntu13.3_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
accrc@ubuntu:~$

---

### Post by drs305 on 2009-09-17
Your version is no longer supported. That doesn't mean it won't run - just that the repositories are no longer available on the main site for upgrading.

Here are some links that should be of interest:

Release Schedule: How long a version will be supported.
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

Upgrade to a newer version: How to upgrade 7.10 
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

If you really want to stick to 7.10, there are servers which contain the old repositories.
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")
This site contains the archived repositories. The EOL link above will have you change your sources.list to point to this site. You can always just stop at that point and not upgrade if you really want to keep 7.10, although I am not recommending this course.

---

### Post by Ozitraveller on 2009-09-17
Hi

Could you post the contents of sources.list

on the command line enter this and press enter
sudo gedit /etc/apt/sources.list

Thanks

---

