---
title: "How do I fix these package dependency issues?"
date: 2012-02-26
forum: General Help
---

### Post by root45 on 2012-02-26
I can't install anything right now (or upgrade anything). When I run

```
sudo apt-get upgrade
```

I get [this list of unmet dependencies]("http://paste.ubuntu.com/858100/"). At the end it says

```
E: Unmet dependencies. Try using -f.
```

When I try `sudo apt-get upgrade -f` I get

```
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... Done
    The following NEW packages will be installed:
      gcc-4.6-base libacl1 libasound2 libasound2-plugins libasyncns0 libatk1.0-0 libattr1 libaudio2 libavahi-client3
      libavahi-common-data libavahi-common3 libc6 libcairo2 libcomerr2 libcups2 libcupsimage2 libcurl3 libdatrie1
      libdb5.1 libdbus-1-3 libdbusmenu-qt2 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libexpat1 libffi6
      libflac8 libfontconfig1 libfreetype6 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0 libgl1-mesa-dri
      libgl1-mesa-glx libglapi-mesa libglib2.0-0 libgnutls26 libgpg-error0 libgssapi-krb5-2 libgtk2.0-0 libice6
      libidn11 libjack-jackd2-0 libjasper1 libjpeg62 libjson0 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0
      liblcms1 libldap-2.4-2 libllvm2.9 libmng1 libnspr4 libnspr4-0d libnss3 libnss3-1d libogg0 libpango1.0-0
      libpciaccess0 libpcre3 libpixman-1-0 libpng12-0 libpulse0 libqt4-dbus libqt4-declarative libqt4-network
      libqt4-opengl libqt4-script libqt4-sql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 librtmp0
      libsamplerate0 libsasl2-2 libsasl2-modules libsdl1.2debian-alsa libselinux1 libsm6 libsndfile1 libspeexdsp1
      libsqlite3-0 libssl1.0.0 libstdc++6 libtasn1-3 libthai0 libtiff4 libuuid1 libvorbis0a libvorbisenc2 libwrap0
      libx11-6 libxau6 libxcb-render0 libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6
      libxfixes3 libxft2 libxi6 libxinerama1 libxrandr2 libxrender1 libxss1 libxt6 libxv1 libxxf86vm1 zlib1g
    The following packages will be upgraded:
      myunity
    1 upgraded, 118 newly installed, 0 to remove and 0 not upgraded.
    1 not fully installed or removed.
    Need to get 0 B/43.5 MB of archives.
    After this operation, 144 MB of additional disk space will be used.
    Do you want to continue [Y/n]? y
    E: Could not perform immediate configuration on 'libc6'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

Nothing happens though. I don't really know what's going on, or how to troubleshoot this. I looked at `man 5 apt.conf` under Immedate-Configure, but it didn't really tell me anything.

I'm kind of skeptical that all these things need to be installed. I think there's just an error reading some package list or something, so it doesn't know what's installed or not. But I could be wrong about that.

How can I fix these dependency issues?

I'm running 11.10.

---

### Post by turinglabs on 2012-02-26
Make sure you've done the 'sudo apt-get update' first. Assuming you have, the note about APT::Immediate-Configure is to try and delay configuration of essential packages (default is to not delay, typically the best option). You can do this on the fly and see if it works, without changing your configuration:

```

sudo apt-get -o APT::Immediate-Configure=no upgrade

```

---

### Post by root45 on 2012-02-26
Thank you, this followed by

```
sudo apt-get autoremove
```

seems to have put things back to normal.

---

