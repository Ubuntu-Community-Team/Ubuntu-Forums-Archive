---
title: "How can I convert Flv into Avi for free in Ubuntu?"
date: 2010-12-18
forum: General Help
---

### Post by wilburlim on 2010-12-18
There are a few encoders on the Internet, but I don't know how to install them because the packages are so different from the *exe.* in Microsoft. 

I am using Firefox. I have just installed an add-on called [DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006/") from Firefox. I tried to convert a video from Youtube from flv into avi, but it says that it needs an external device. I have no inkling on where to download this device/ converter. 

Can anyone give me constructive remedies? Thank you so much! Thank you!

---

### Post by karthick87 on 2010-12-18
You can convert flv into avi using the following command,

```
mencoder -idx input.flv -ovc xvid -xvidencopts bitrate=4500 -oac mp3lame -srate 44100 -o output.avi
```

---

### Post by jmszr on 2010-12-18
wilburlim,

Here's a link to a Ubuntu-Geek tutorial about installing and using WinFF: [http://www.ubuntugeek.com/winff-gui-for-the-command-line-video-converter-ffmpeg.html](http://www.ubuntugeek.com/winff-gui-for-the-command-line-video-converter-ffmpeg.html) .

It looks like it should do the job for you.

---

### Post by lovinglinux on 2010-12-19
Use mencoder as already suggested.

> **wilburlim said:**
> There are a few encoders on the Internet, but I don't know how to install them because the packages are so different from the *exe.* in Microsoft.

I would recommend reading [https://help.ubuntu.com/10.10/add-applications/C/index.html](https://help.ubuntu.com/10.10/add-applications/C/index.html)

Installing software in Linux is a lot easier that in Windows. You just need to get acquainted with how it is done.

---

### Post by amsterdamharu on 2010-12-19
Ubuntu comes with a certain amount of codecs that are open source, not sure if flv and avi fits into that. For example mpeg is closed source, that means that someone has a patent on it and anyone making software using those codecs has to have permission from the patent holder. This can be given for money or just like that, the biggest problem is that the person using the codec for his/her software never owns the codec so cannot re write it to fix something or can have the patent holder change conditions whenever they please.
It can even go so far that the the patent holder suing the software producer or the software user (you) for using their patented piece of software code.

Luckily these software patents are only in the US and Japan so if you're outside you can install the codecs like this.

To install them you can copy and paste the following in the terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install non-free-codecs ffmpeg winff

```Now open winff; it can be in your application menu but you can press alt + F2 and type winff.

Browse to the file you want to convert and then choose to what you want to convert to, this graphic interface is quite easy to use.

---

