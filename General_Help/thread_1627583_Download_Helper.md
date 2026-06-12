---
title: "Download Helper"
date: 2010-11-21
forum: General Help
---

### Post by YMS_1975 on 2010-11-21
Ubuntu : 10.10
Download Helper : 4.8.1

Hello,

I recently downloaded a FireFox extension called "Download Helper" ([http://www.downloadhelper.net/](http://www.downloadhelper.net/)).

I did a search for this and was hit with like over 250 hits, so I'm hoping somebody can help me out here. I want to be able to convert YouTube videos to MP3's.

This extension has good reviews, but when I try to convert anything I'm presented with a dialog box that says : 

"**Conversion requires an external application that appears to be missing on your system. Configure Conversion?**" When I select the option to configure it,it lists FFMpeg as the converter with the path : /usr/bin/ffmpeg

When I view the /usr/bin path, I do not see FFMpeg anywhere. I read the instructions on how to install FFMpeg from [**[COLOR="Red"]this link[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=786095") but it still doesn't seem to work. Shouldn't I be able to see that path if FFMpeg installed successfully?

Can anybody help?

---

### Post by Manyette on 2010-11-21
That link is for a compile.  I'd suggest you download ffmpeg from the repo's first, and give that a try before you try a compile.

---

### Post by YMS_1975 on 2010-11-21
> **Manyette said:**
> That link is for a compile.  I'd suggest you download ffmpeg from the repo's first, and give that a try before you try a compile.

Ok....

So would I simply bring up the Ubuntu Software Centre and search for it that way?

---

### Post by carl4926 on 2010-11-21
> **YMS_1975 said:**
> Ok....

So would I simply bring up the Ubuntu Software Centre and search for it that way?
Or synaptic

ffmpeg is command line
Am I right in thinking winff is a UI front end?

Check out the man pages for ffmpeg - but here is an example

```
ffmpeg -i inputfile.flv -vn -acodec copy -y outfile.mp3
```

---

### Post by Manyette on 2010-11-21
That would work, or you could use Synaptic, which is a gui and a bit easier.

---

### Post by YMS_1975 on 2010-11-21
> **carl4926 said:**
> Or synaptic

ffmpeg is command line
Am I right in thinking winff is a UI front end?

Check out the man pages for ffmpeg - but here is an example

```
ffmpeg -i inputfile.flv -vn -acodec copy -y outfile.mp3
```

Well...

ffmpgeg is command line, but I believe the way Download Helper works, is that it merely utilizes the program and provides the user with a GUI.
Through Download Helper I am prompted for the path to store the final mp3.
But it doesn't seem to accept the fact that FFMPeg has been installed.

Something is not right with how it's been set up.

---

### Post by carl4926 on 2010-11-21
> **YMS_1975 said:**
> Well...

ffmpgeg is command line, but I believe the way Download Helper works, is that it merely utilizes the program and provides the user with a GUI.
Through Download Helper I am prompted for the path to store the final mp3.
But it doesn't seem to accept the fact that FFMPeg has been installed.

Something is not right with how it's been set up.

I'm familiar with Downloadhelper addon
I was thinking you were downloading and then converting - rather than trying to use the addon

---

### Post by Bradj47 on 2010-11-21
Whenever I try to use download helper to convert flv to anything, it fails. So I always use **ffmpeg** or **Sound Converter** (from Ubuntu Software Center) to convert it.

---

### Post by Manyette on 2010-11-21
You are correct when you say that it uses ffmpeg, but does not show it.  If there is a GUI, it is from Download Helper. Open a terminal by Applications->Accessories=>Terminal, and type ffmpeg.  If it is loaded, a help screen should appear.  If it does not, it is not present. Try downloading it again.

---

### Post by YMS_1975 on 2010-11-21
> **Manyette said:**
> You are correct when you say that it uses ffmpeg, but does not show it.  If there is a GUI, it is from Download Helper. Open a terminal by Applications->Accessories=>Terminal, and type ffmpeg.  If it is loaded, a help screen should appear.  If it does not, it is not present. Try downloading it again.

It looks like it's installed, because I get the following message when I Type that out : 

[B]FFmpeg version SVN-r25790, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 21 2010 15:58:44 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.14. 0 /  0.14. 0
  libavcodec    52.97. 2 / 52.97. 2
  libavformat   52.85. 0 / 52.85. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.63. 1 /  1.63. 1
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'[/B]

So, it's there.....so....what next?  :confused:

---

### Post by beew on 2010-11-21
I use the dlhelper to convert flv to mp3 and it works flawlessly in Ubuntu (can't do it in Windows btw)

Yes, it uses the ffmpeg backend but probably you need other stuffs as well. Did you install Ubuntu-restricted-extra?

To find out if something is missing you can download a flv file and convert it with ffmpeg and see if it works. Also, if you want a gui with the option of batch conversion you may install WINFF, which is a gui for ffmpeg. It helps me a lot because I don't use ffmpeg frequently and I have problem remembering all the obscure options for the CLI. :)

---

### Post by YMS_1975 on 2010-11-21
> **beew said:**
> I use the dlhelper to convert flv to mp3 and it works flawlessly in Ubuntu (can't do it in Windows btw)

Yes, it uses the ffmpeg backend but probably you need other stuffs as well. Did you install Ubuntu-restricted-extra?

To find out if something is missing you can download a flv file and convert it with ffmpeg and see if it works. Also, if you want a gui with the option of batch conversion you may install WINFF, which is a gui for ffmpeg. It helps me a lot because I don't use ffmpeg frequently and I have problem remembering all the obscure options for the CLI. :)

Ubuntu-restricted extra? I didn't have it, but I JUST installed it. Wow, this is some complicated stuff. Ok....now that I have it installed, what do you suggest I do now?  :D

---

### Post by Manyette on 2010-11-21
Well, it is there, and and the system knows it, so perhaps you have to either reboot, or perhaps download the Download Helper again, since perhaps is only looks for it the first time it runs?  Don't have any better answer at this point.

---

### Post by ajgreeny on 2010-11-21
I don't think the repository version of ffmpeg is capable of encoding mp3s unless you install the "extra" versions of several libav* codecs, so get:-

libavcodec-extra-52
libavdevice-extra-52
libavfilter0-extra
libavformat-extra-52
libavutil-extra-49

from the medibuntu repos and I think you may be OK to do this encoding job.  Just to make sure, I have just tried this on a downloadhelper conversion of an flv file to mp3 with no problem.

---

### Post by YMS_1975 on 2010-11-21
> **Manyette said:**
> Well, it is there, and and the system knows it, so perhaps you have to either reboot, or perhaps download the Download Helper again, since perhaps is only looks for it the first time it runs?  Don't have any better answer at this point.

Well I installed Ubuntu Restricted Extras....rebooted the PC.....re-installed Download Helper, and still have the same problem.

*Deep Sigh* Crap. Damnit....why isn't this working?  ](*,)

I just want to be able to convert YouTube vids to MP3. Can ANYBODY help?
Ok, clearly I have FFMpeg installed on my pc.

I've looked through the documentation for FFMpeg and it's a bit confusing for me. Can somebody give me a command to convert a video on Youtube into my MP3 directory (which is a folder on my desktop) ???

I think it would be something like : 

ffmpeg [http://URL.com](http://URL.com) mynewfilename.mp3

Anyways, if you know of the command, can you help me?

---

### Post by beew on 2010-11-21
Just to find out what is wrong. Try to download a .flv file with dlhelper then convert it and see if it works, if it doesn't the terminal would output some error message.

You can either use the command line for the conversion like others told you before or use  WINFF (get it from the repo, it is very helpful).  Like I said WINFF is the graphic interface for ffmpeg.

P.S. You need Ubuntu-restricted-extras basically for codecs and stuffs because it might be illegal for Canonical to include them by default.

---

### Post by beew on 2010-11-21
> **ajgreeny said:**
> I don't think the repository version of ffmpeg is capable of encoding mp3s unless you install the "extra" versions of several libav* codecs, so get:-

libavcodec-extra-52
libavdevice-extra-52
libavfilter0-extra
libavformat-extra-52
libavutil-extra-49

from the medibuntu repos and I think you may be OK to do this encoding job.  Just to make sure, I have just tried this on a downloadhelper conversion of an flv file to mp3 with no problem.


You may be right. I have all these installed. I activated a whole bunch of PPAs so that most things I installed are not likely from the official repos. :)  (My versions are probably from Lucid-bleed/Maverick-bleed)

---

### Post by YMS_1975 on 2010-11-21
> **ajgreeny said:**
> I don't think the repository version of ffmpeg is capable of encoding mp3s unless you install the "extra" versions of several libav* codecs, so get:-

libavcodec-extra-52
libavdevice-extra-52
libavfilter0-extra
libavformat-extra-52
libavutil-extra-49

from the medibuntu repos and I think you may be OK to do this encoding job.  Just to make sure, I have just tried this on a downloadhelper conversion of an flv file to mp3 with no problem.

Ok....so how do I get all this? Via the terminal? Through the software centre?

---

### Post by beew on 2010-11-21
You can install all that from the Maverick-bleed ppa.[URL="https://launchpad.net/%7Emaverick-bleed/+archive/ppa"]
https://launchpad.net/~maverick-bleed/+archive/ppa[/URL]

You need to add the ppa to your sources list so you can install from its repository and get updates like you would from the Ubuntu repositories (ppas are third party maintained repositories)

To add the ppa you open Synaptic, go to Settings > Repoistories and then choose the tab "Other Software" and click "Add" and add the line ```
ppa:maverick-bleed/ppa
``` Reload Synaptic and you will find the extra packages.  You will be asked to upgrade other packages like ffmpeg as well because the ppa has newer versions than what you find in the Ubuntu repositories.

---

### Post by ajgreeny on 2010-11-22
I'm still on 10.04 and all the "extra" versions of the lib packages I have came from medibuntu, which is also available for maverick.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I always add that repository to my ubuntu sources as it is extremely useful for many multimedia packages.

---

### Post by feranick on 2010-11-30
> **ajgreeny said:**
> I'm still on 10.04 and all the "extra" versions of the lib packages I have came from medibuntu, which is also available for maverick.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I always add that repository to my ubuntu sources as it is extremely useful for many multimedia packages.

An alternative for Lucid is to use the lucid-bleed ppa:

[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa)

---

