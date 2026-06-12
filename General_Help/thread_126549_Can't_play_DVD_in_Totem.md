---
title: "Can't play DVD in Totem"
date: 2006-02-06
forum: General Help
---

### Post by kennethb on 2006-02-06
When I insert a DVD in my DVD-play, Totem starts up, bu the following pop-ups display these error messages:

Totem could not play 'file:///dev/hdc'.
Could not determine type of stream.

Totem could not play 'file:///dev/hdc'.
Could not determine type of stream.

I'm using Ubuntu 5.0 (Breezy), and I've installed totem-xine. Does anyone have any suggestions as to how I can get Totem to play DVDs? Or, should I try installing some other DVD player app?

---

### Post by dcstar on 2006-02-06
[QUOTE=kennethb]When I insert a DVD in my DVD-play, Totem starts up, bu the following pop-ups display these error messages:

Totem could not play 'file:///dev/hdc'.
Could not determine type of stream.

Totem could not play 'file:///dev/hdc'.
Could not determine type of stream.

I'm using Ubuntu 5.0 (Breezy), and I've installed totem-xine. Does anyone have any suggestions as to how I can get Totem to play DVDs? Or, should I try installing some other DVD player app?[/QUOTE]
Try the totem-gstreamer route (it will uninstall the xine one).

You may also have to install various gstreamer codecs.

---

### Post by manicka on 2006-02-06
Do you have libdvdcss2 installed?

[http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)

---

### Post by kennethb on 2006-02-07
I installed 'libdvdcss2' and 'w32codecs' using:

sudo apt-get install libdvdcss2 w32codecs

Still nothing. Totem won't pla a DVD. The error message I get is:

-----------------------------
Totem could not play 'dvd://'.
There were no decoders found to handle the stream, you might need to install the corresponding plugins
-------------------

What plugins do I need to install? How do I install plugins for Totem?

---

### Post by MikeNick42 on 2006-02-07
You may want to try installing and running regionset if you are using a new system.  I couldn't get dvds to play even with libdvdcss2 and w32codecs until I set the region on my drive.

---

### Post by lupinthewhite on 2007-07-17
Thank you for posting the following:

sudo apt-get install libdvdcss2 w32codecs

I didn't have the w32 codecs enabled for some reason. Now watching The Thing on it's first Ubuntu screening.

Thank you

---

### Post by Bablefish on 2007-07-17
All good suggestions but in reality none of them will work. At least they didn't for me. Let me tell you the REAL way to get DVDs to play in Ubuntu.

First install Medibuntu the how to guide in the multimedia section is good. But if you want a real easy way to install it Google Medibuntu and head to their site they have on it a straight terminal install. Which is a simple copy and paste.

Next head on over to Add/Remove and get the Kaffiene player

Finally to get all the codecs your going to need head here: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Download, install and run Automatrix

Other than checking out what else Automatrix has to offer your set.

---

### Post by philidox on 2008-02-26
Alright this is how to get totem to play dvd's!!!  You should mark this SOLVED after these instructions or just follow this link [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

RestrictedFormats/PlayingDVDs

Contents

   1. Starting Fresh with xine Based Players
   2. Installing libdvdcss2
   3. Setting DVD Region Codes
   4. Troubleshooting

Most commercial DVDs are encrypted with CSS (the Content Scrambling System), which attempts to restrict the software that can play a DVD.

By installing the libdvdcss2 package you can play encrypted DVDs with:

    *

      Kaffeine, the Kubuntu video player
    *

      MPlayer
    *

      xine
    *

      Totem-xine
    *

      VLC media player

Note : While Totem-gstreamer can play a DVD automatically when it is inserted into the DVD drive, it cannot navigate the DVD nor play it by selecting Movie &#8594; Play Disc 'DVD Name' (see [WWW] Bug #41335). If you use vlc media player you can navigate through the menu, forward in the movie and select subtitles. Just select open disc, probe Disc(s) and click ok.
Starting Fresh with xine Based Players

After doing a fresh install of any one of the Ubuntu-based Linux distributions, some packages needed for DVD playback are not installed by default because of Ubuntu's commitment to completely free multimedia formats. This section covers what packages are needed and how to acquire and install them onto your system.

    *

      Ubuntu 7.10 "Gutsy Gibbon"

In gutsy to get encrypted DVD playback to work i had to do the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

After that, running gxine from the Applications -> Sound and Video menu played the DVD perfectly. I found this tip at: [WWW] [http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html](http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html) cheers random website!

    *

      Ubuntu 7.04 "Feisty Fawn"

After doing a fresh install of Feisty, be it Ubuntu or Kubuntu, there are two packages not installed by default that need to be installed for DVD playback to work. There's a third package needed to play encrypted DVDs. They are:

    *

      libdvdread3
    *

      libxine1-ffmpeg (Also requires libmad0, therefore libmad0 will be installed automatically along with this package)
    *

      libdvdcss2 (Needed to play encrypted DVDs)

libdvdread3 and libxine1-ffmpeg are in the Ubuntu repository. To install them through the command line, type the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg

libdvdcss2 is not part of the Ubuntu repository because of Ubuntu's commitment to completely free multimedia formats. The next section explains how to acquire libdvdcss2.
Installing libdvdcss2

If you are using Ubuntu 6.06 "Dapper Drake":

    *

      Install the libdvdread3 package from the universe repository.
    *

      Open a terminal and type

      sudo /usr/share/doc/libdvdread3/examples/install-css.sh

      and press the enter key. This will download and install libdvdcss2.

If you are using Ubuntu 6.10 "Edgy Eft":

    *

      Install the libdvdread3 package from the universe repository.
    *

      Open a terminal and type

      sudo /usr/share/doc/libdvdread3/install-css.sh

      and press the enter key. This will download and install libdvdcss2.

If you are using Ubuntu 7.04 or later:

    *

      Install the libdvdcss2 package after adding the unsupported third-party repository Medibuntu.

Your DVD player should now play back encrypted DVDs.
Setting DVD Region Codes

    *

      If your DVD player regularly locks up when you try to play back a DVD, your DVD player probably does not match the DVD's [WikiPedia]Region Code. Region Codes are a form of vendor lock-in. For example, you cannot play a DVD published in Japan (Region 2) on a DVD player in the United States (Region 1) without changing the Region Code of the DVD player (unless you own a region free DVD player). You can view or modify the Region Code of your DVD drive with the [WWW] regionset tool.

      warning.png
      [WWW] The author of regionset writes: "On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more."
    *

      Most players (eg mplayer/vlc) with most DVD drives are able to ignore the value of the region setting. However, it must have been set to something; if it hasn't been initialized, even non-region-restricted DVDs won't play. Also, if it is necessary to crack the CSS key, it can sometimes take up to a few minutes to do so.


    *

      To change the Region Code of your DVD player, insert a DVD from your region in the DVD player, and do the following:
          o

            Install the regionset package from the Universe repositories.
          o

            To launch regionset, issue the command

            regionset

          o

            See the Free Formats page for more information

Troubleshooting

    *

      Jerky Playback
          o

            If DVD playback is noticeably choppy or burning a CD/DVD is slower than it should be, then you may need to enable DMA transfer for the DVD drive. See the DMA (Direct Memory Access) page for details.

---

