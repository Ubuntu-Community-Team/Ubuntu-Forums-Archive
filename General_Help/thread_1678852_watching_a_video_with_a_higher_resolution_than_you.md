---
title: "watching a video with a higher resolution than your computer has from vlc"
date: 2011-01-31
forum: General Help
---

### Post by COKEDUDE on 2011-01-31
Does anyone know of a way to watch a video with a higher resolution than your computer has from vlc? My monitor has a resolution of only 1024X768. I am trying to watch a video that has a resolution of 1920X1080. How can I adjust vlc's settings to deal with this problem? I tried to shrink the video really small manually and I used the video, zoom, 1:4 quarter setting also. Both ways the video still froze a lot.

---

### Post by Vaphell on 2011-01-31
I think your pc is not beefy enough. My guess is that it doesn't really matter if you scale video down, clip has to be decoded first in its original hi-def resolution which is a non-trivial task when there is no hardware acceleration for video playback and CPU has to do all the work. What are the specs of your computer?

---

### Post by COKEDUDE on 2011-01-31
> **Vaphell said:**
> I think your pc is not beefy enough. My guess is that it doesn't really matter if you scale video down, clip has to be decoded first in its original hi-def resolution which is a non-trivial task when there is no hardware acceleration for video playback and CPU has to do all the work. What are the specs of your computer?

A old 3 year old laptop. What program would you recommend to scale it down?

---

### Post by coldraven on 2011-01-31
Try Handbrake, download from [http://handbrake.fr/](http://handbrake.fr/)

---

### Post by perspectoff on 2011-01-31
> **coldraven said:**
> Try Handbrake, download from [http://handbrake.fr/](http://handbrake.fr/)

Handbrake is available is a package. No need to download and manually install unless some development or cutting edge version is desired.

 sudo apt-get install handbrake

or use Synaptic Package manger, KPackageKit, or Ubuntu Software Center.

Personally, I still use ffmpeg or mencoder and do manual conversions from the command-line, only because there are lots of other manipulations I like to do. But there is a learning curve involved with that.

To be perfectly honest, though, I have never had this problem, and I have a number of older computers. 

I must caution against ripping and copying and attempting to play commercial DVDs (and streams), which is illegal in most jurisdictions. Many commercial DVDs have signals integrated into the stream (that are maintained even when ripped or converted) that cause streams to freeze. The symptom described appears to match that.

Many players (possibly current versions of VLC, possibly not older versions) honor those halt signals (in order to keep compliant with laws that might require it).

I don't know what your activities are, but I point this out so that other readers don't automatically disparage VLC, or the OS, or the hardware, or the graphics, when the problem may be something altogether different.

---

### Post by JohnAStebbins on 2011-01-31
> **perspectoff said:**
> Handbrake is available is a package. No need to download and manually install unless some development or cutting edge version is desired.

 sudo apt-get install handbrake

or use Synaptic Package manger, KPackageKit, or Ubuntu Software Center.

Personally, I still use ffmpeg or mencoder and do manual conversions from the command-line, only because there are lots of other manipulations I like to do. But there is a learning curve involved with that.
HandBrake is not in the official Ubuntu repositories.  You must add HandBrake's PPA to your software sources before you can install it.  There are instructions if you follow the download link the other poster gave.  But the short answer is:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```

---

### Post by perspectoff on 2011-01-31
> **JohnAStebbins said:**
> HandBrake is not in the official Ubuntu repositories.  You must add HandBrake's PPA to your software sources before you can install it.  There are instructions if you follow the download link the other poster gave.  But the short answer is:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```

Heh-heh, you're right. I had forgotten that I had done that. Cheers.

---

### Post by COKEDUDE on 2011-02-01
> **perspectoff said:**
> Handbrake is available is a package. No need to download and manually install unless some development or cutting edge version is desired.

 sudo apt-get install handbrake

or use Synaptic Package manger, KPackageKit, or Ubuntu Software Center.

Personally, I still use ffmpeg or mencoder and do manual conversions from the command-line, only because there are lots of other manipulations I like to do. But there is a learning curve involved with that.

[B]To be perfectly honest, though, I have never had this problem, and I have a number of older computers. 

I must caution against ripping and copying and attempting to play commercial DVDs (and streams), which is illegal in most jurisdictions. Many commercial DVDs have signals integrated into the stream (that are maintained even when ripped or converted) that cause streams to freeze. The symptom described appears to match that.[/B]

Many players (possibly current versions of VLC, possibly not older versions) honor those halt signals (in order to keep compliant with laws that might require it).

I don't know what your activities are, but I point this out so that other readers don't automatically disparage VLC, or the OS, or the hardware, or the graphics, when the problem may be something altogether different.


Wow. You are the first person to think this. I have asked this same question on 4 other forums and no one thinks this. Everyone else is blaming this on my old video card. Since you felt the need to bring up the video it is a video a few of my friends made. They all play wow and cod so the have amazing video cards. So they didn't think about lowering the video resolution since they can see it fine. 

> **JohnAStebbins said:**
> HandBrake is not in the official Ubuntu repositories.  You must add HandBrake's PPA to your software sources before you can install it.  There are instructions if you follow the download link the other poster gave.  But the short answer is:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```

Thank you :).

---

