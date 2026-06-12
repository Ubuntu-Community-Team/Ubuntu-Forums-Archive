---
title: "Adobe flash no work"
date: 2010-09-05
forum: General Help
---

### Post by eight-zero-one on 2010-09-05
yhallo i have the newest version of ubuntu installed on my laptop. I have adobe flash installled but it doesnt work. What to do?!?!?:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

EDIT: IT works in chrome but notfirefox how fix

---

### Post by Old_Grey_Wolf on 2010-09-05
You probably need to add Medibuntu, Restricted Extras, and codecs to you computer.

If you are using 10.04 then copy and past these commands in the termainal:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libavcodec52 libavformat52 libavutil49 libcdaudio1 libdc1394-22 libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 sox tagtool twolame vorbis-tools build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf zlib1g-dev libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libsdl-image1.2 jack-tools jackd libjackasyn0 qjackctl libjack0 libdirac-encoder0 libdirac-decoder0 cpp-4.3 diffutils-doc gecko-mediaplayer krb5-multidev libffado2 libkadm5clnt-mit7 libkadm5srv-mit7 raptor-utils jackd-firewire
```

```
sudo apt-get install flashplugin-nonfree flashplugin-installer
```

---

### Post by eight-zero-one on 2010-09-05
>  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring jackd &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;
 &#9474; If you want to run jackd with realtime priorities, the user starting
 &#9474; jackd needs realtime permissions. Accept this option to create the file
 &#9474; /etc/security/limits.d/audio.conf, granting realtime priority and
 &#9474; memlock privileges to the audio group.
 &#9474; 
 &#9474; Running jackd with realtime priority minimizes latency, but may lead to 
 &#9474; complete system lock-ups by requesting all the available physical system
 &#9474; memory, which is unacceptable in multi-user environments.
 &#9474;
 &#9474; Enable realtime process priority?
 &#9474;
 &#9474;                    <Yes>                       <No>

what do

---

### Post by eight-zero-one on 2010-09-05
bump

---

### Post by davidmohammed on 2010-09-05
The simplest approach would be to run the following:

sudo apt-get install ubuntu-restricted-extras


this will install codecs, java and flash etc.

The advice above is quite a complicated way to achieve the same.

---

### Post by Old_Grey_Wolf on 2010-09-05
> **davidmohammed said:**
> ...The advice above is quite a complicated way to achieve the same.

Maybe

:lolflag:

---

### Post by eight-zero-one on 2010-09-05
> **Old_Gray_Wolf said:**
> You probably need to add Medibuntu, Restricted Extras, and codecs to you computer.

If you are using 10.04 then copy and past these commands in the termainal:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
``````
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libavcodec52 libavformat52 libavutil49 libcdaudio1 libdc1394-22 libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 sox tagtool twolame vorbis-tools build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf zlib1g-dev libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libsdl-image1.2 jack-tools jackd libjackasyn0 qjackctl libjack0 libdirac-encoder0 libdirac-decoder0 cpp-4.3 diffutils-doc gecko-mediaplayer krb5-multidev libffado2 libkadm5clnt-mit7 libkadm5srv-mit7 raptor-utils jackd-firewire
``````
sudo apt-get install flashplugin-nonfree flashplugin-installer
```

do this
does the same thing.
what do.
am i suppose to restart my computer?

---

### Post by eight-zero-one on 2010-09-05
restarted laptop
still no work
:confused::mad:](*,):-(:-x:^o:-&:evil:

---

### Post by eight-zero-one on 2010-09-05
So i tested it in an otehr brownerser and it worked. but still doesnt work in firefox

---

### Post by eight-zero-one on 2010-09-05
bump

---

### Post by eight-zero-one on 2010-09-05
bump

---

### Post by eight-zero-one on 2010-09-05
bump

---

### Post by eight-zero-one on 2010-09-05
bummp

---

### Post by lovinglinux on 2010-09-07
Please don't bump your thread like that.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Just install it and restart Firefox. It will prompt for flash installation and execute all the necessary commands for you.

---

### Post by ottosykora on 2010-09-07
tell us also where di you get the flash from.

I had following experience: at some point I was not able to run the flash when installed via regular updates from the ubunztu repository.
I went with the browser in question (firefox) to the website of adobe, selected there to install flash and the it did install the 'downloader' temporary extension first and then the flash and then all did work again.
There is nothing magic behind it, just adobe changes this and that in the flash versions and so it is probably better to take the copy from the manufacturer this time instead of the repositories.

---

### Post by WALu on 2010-09-07
sudo apt-get install flashplugin-nonfree flashplugin-installer

did it

got this:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

please help.!!

---

### Post by davidmohammed on 2010-09-07
you have update manager/synaptic manager open.  Close the window and try again.  If in doubt, just logout and login and rerun the command.

---

### Post by pr1vatepiles on 2010-09-07
> **davidmohammed said:**
> The simplest approach would be to run the following:

sudo apt-get install ubuntu-restricted-extras


this will install codecs, java and flash etc.

The advice above is quite a complicated way to achieve the same.

beautiful thanks.

---

### Post by WALu on 2010-09-08
> **davidmohammed said:**
> you have update manager/synaptic manager open.  Close the window and try again.  If in doubt, just logout and login and rerun the command.

now its giving me
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

please help thnxx

---

### Post by Emmtor on 2010-09-08
@WALu
What version of Ubuntu are you running?

Try this link: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Click on the link below 'Playing Restricted Formats'.

---

### Post by p1xel on 2010-09-08
Ok, now If I'm using keryxto get on the net for pkgs, any advice on what i should search for to get flash up and working savvy?:confused:

---

### Post by lovinglinux on 2010-09-08
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Just install it and restart Firefox. It will prompt for flash installation and execute all the necessary commands for you.

---

