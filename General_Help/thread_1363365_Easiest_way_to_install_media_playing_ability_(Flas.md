---
title: "Easiest way to install media playing ability (Flash, DVD Video, Quicktime,etc)"
date: 2009-12-24
forum: General Help
---

### Post by willz06jw on 2009-12-24
Hi,

I understand how to install all of the packages and what-not to get everything working on my computer, but I'm about to recommend Ubuntu to a friend of mine that is about average in computer experience.  

Is there a button or menu selection that will enable all of these proprietary technologies without going through the packages/CLI explanation with him?  

The Ubuntu manual only details that way to fix the problem:
 [https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

Thanks for your help,
Will

---

### Post by ibuclaw on 2009-12-24
Have a look at our [Comprehensive Multimedia]("http://ubuntuforums.org/showthread.php?t=766683") guide.

Regards
Iain

---

### Post by wirate on 2009-12-24
I dont get you completely but what about

```

sudo apt-get install adobe-flashplugin
sudo apt-get install vlc

```

?

---

### Post by SuperSonic4 on 2009-12-24
It would probably be easiest if you set up a script to do the job

```
#!/bin/bash
#
# Add medibuntu to sources
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
#
# Install restricted extras and libdvdcss
echo "Installing restricted extras - this is for codecs such as mp3"
sudo apt-get -y ubuntu-restricted-extras sudo apt-get install alsa-oss faac faad flashplugin-nonfree \
gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly \
gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar
#
echo "Installing libdvdcss - this is required to watch DVDs on your PC
sudo apt-get -y install libdvdcss
#
echo "Done"
```

note: this hasn't been tested

---

### Post by willz06jw on 2009-12-24
I bet that the script would work best, but I wish there was a button or menu selection he could use to set it up :(

When he sees me go to the "MS-DOS Prompt" to run the script he'll be turned off of the OS or at least not recommend it to another non-technical user in the future.  

I could direct him to the comprehensive media guide, but I think that's way to technical for most medium users.  It would look like Assember programing manual to him.

In the back of my head I am thinking show him Linux Mint, but I know Ubuntu is the actual innovator and I hate to direct him to the innovation leech.

Thanks,
Will

---

### Post by SuperSonic4 on 2009-12-24
> **willz06jw said:**
> I bet that the script would work best, but I wish there was a button or menu selection he could use to set it up :(

When he sees me go to the "MS-DOS Prompt" to run the script he'll be turned off of the OS or at least not recommend it to another non-technical user in the future.  

I could direct him to the comprehensive media guide, but I think that's way to technical for most medium users.  It would look like Assember programing manual to him.

In the back of my head I am thinking show him Linux Mint, but I know Ubuntu is the actual innovator and I hate to direct him to the innovation leech.

Thanks,
Will

Keep going to Debian then ;)

---

### Post by willz06jw on 2009-12-24
By the way, Merry Christmas from Texas fellow Ubuntu dudes and dudettes

---

