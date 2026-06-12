---
title: "New install of 10.04 -  Medibunto or ubuntu-restriced-extras ?"
date: 2010-05-06
forum: General Help
---

### Post by davexnet on 2010-05-06
I first installed Ubunto a couple of years ago and at the time
ubuntu-restricted extras was being recommended so that certain
codecs and extras would allow mp3, divx, etc,etc. to be played.

What now?  medibuntu is being mentioned quite a bit.

Should this be used instead?  Install both of them?

Second, I've got a general question, I've been using Ubuntu  
for a while, but don't really understand what I'm doing.
If items such as these are installed, they draw in
a number of packages, can they be uninstalled
cleanly?  How?  By uninstalling all the individual packages?

If you take the repository out of "software sources", 
are all its related packages removed from the system after you
do an update?

---

### Post by mikewhatever on 2010-05-06
I used to add Medibuntu and tried installing ubuntu-restricted-extras in the past, but stopped doing that, as I found out I don't use half of what they offer (java, msfonts, etc). These days, I just click the files, and package manager offers to install the required codecs. In short, you may very well not need to install either.

> **davexnet said:**
> ...

Second, I've got a general question, I've been using Ubuntu  
for a while, but don't really understand what I'm doing.
If items such as these are installed, they draw in
a number of packages, can they be uninstalled
cleanly?  How?  By uninstalling all the individual packages?
These are dependencies, in other words, packages needed by the program you are installing. You probably wouldn't want to uninstall them, at least as long as you want the program you've installed to function properly. To get rid of unclaimed dependencies, use *sudo apt-get --purge autoremove*.

> If you take the repository out of "software sources", 
are all its related packages removed from the system after you
do an update?

No, the packages already installed remain installed.

---

### Post by davexnet on 2010-05-06
Appreciate the info...

Dave

---

### Post by mcooke1 on 2010-05-07
Some more information is [here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by garvinrick4 on 2010-05-07
> **mcooke1 said:**
> Some more information is [here]("https://help.ubuntu.com/community/RestrictedFormats")

If you are new and reading this install Code:

sudo apt-get install ubuntu-restricted-extras

I will show you what it gets and you will need most all and the others will not bother you if you do not use them. At least your flash and music and such will play and you get Java.
Here is what you get.

rick@rick-laptop:~$ aptitude show ubuntu-restricted-extras
Package: ubuntu-restricted-extras
State: installed
Automatically installed: no
Version: 39
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 32.8k
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse,
            ttf-mscorefonts-installer, flashplugin-installer, unrar,
            gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse,
            gstreamer0.10-ffmpeg, libavcodec-extra-52, icedtea6-plugin,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for
 more information.

Notice all these are in multiverse repository, do not forget to check it in Software Sources.


rick@rick-laptop:~$

---

### Post by mcooke1 on 2010-05-07
> **garvinrick4 said:**
> If you are new and reading this install Code:

sudo apt-get install ubuntu-restricted-extras

I will show you what it gets and you will need most all and the others will not bother you if you do not use them. At least your flash and music and such will play and you get Java.
Here is what you get.

rick@rick-laptop:~$ aptitude show ubuntu-restricted-extras
Package: ubuntu-restricted-extras
State: installed
Automatically installed: no
Version: 39
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 32.8k
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse,
            ttf-mscorefonts-installer, flashplugin-installer, unrar,
            gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse,
            gstreamer0.10-ffmpeg, libavcodec-extra-52, icedtea6-plugin,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for
 more information.

Notice all these are in multiverse repository, do not forget to check it in Software Sources.


rick@rick-laptop:~$
 
That code is in the link I posted.

```
sudo apt-get install ubuntu-restricted-extras
```

---

