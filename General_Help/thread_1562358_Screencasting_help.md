---
title: "Screencasting help"
date: 2010-08-27
forum: General Help
---

### Post by MetaMs on 2010-08-27
I need to create a couple of screencast tutorials. I did a test using gtk-recordmydesktop, then used Pitivi to edit. I rendered the file as AVI and attempted to open it in Windows (most of my viewers will be Windows users). 

Windows Media player was not able to open the file. VLC (in Windows) which I generally use, produced the following error:
[COLOR=#000000]VLC does not support the audio or video format "MJ2C". Unfortunately there is no way for you to fix this.

Can anyone help me accomplish this successfully? FYI...I'm relatively new to Ubuntu (4 months or so) and very new to audio and video stuff. [/COLOR]I would like to produce files appropriate for upload to YouTube. I understand AVI or MP4 would be the best options.
[COLOR=#000000]
Using Ubuntu 10.04.
Thanks!
[/COLOR]

---

### Post by howefield on 2010-08-28
Try converting to avi, then editing the .avi file if required.

[http://karuppuswamy.com/wordpress/2010/06/25/application-desktop-recorder-software-for-ubuntu-and-uploading-to-youtube/](http://karuppuswamy.com/wordpress/2010/06/25/application-desktop-recorder-software-for-ubuntu-and-uploading-to-youtube/)

---

### Post by MetaMs on 2010-08-28
I tried again this morning. New video made with recordmydesktop. Converted to avi using Transmageddon (the only thing that would convert it).

Everything looked fine until I uploaded it to YouTube. Now the audio and video are way off The video is way ahead of the audio. 

Wasted a lot of time on this. I'm once again ready to go back to windows. :o(

---

### Post by MooPi on 2010-08-28
What codec is used in the original for sound. Can you use lame ? or is it just vorbis codec in recordmydesktop. I would use ffmpeg or mencoder to convert you original to .avi. You can specify the codec to used with either.

---

### Post by MetaMs on 2010-08-28
Not a clue. And I admit I know nothing about codecs. I guess this used to work in Ubuntu 9.04 and stopped working in 10.04. Apparently, unless you do it from a command line, screencasting is no longer possible in Ubuntu if you want to use the result anywhere else...like YouTube.

---

### Post by MooPi on 2010-08-28
I'm going to test this on another computer and will get back with results. It is just a matter of getting my mic to function. I now have my mic configured and did that take to long. I've recorded the session for your viewing pleasure.
[http://dl.dropbox.com/u/5209151/recordmydektop.avi]("http://dl.dropbox.com/u/5209151/recordmydektop.avi")

---

### Post by MetaMs on 2010-08-28
After many failed attempts using various methods and packages, I have finally managed to do this using DeVeDe. You can find the instructions here:
[http://www.rwdubsreviews.com/2010/03/devede-using-devede-on-ubuntu-to.html](http://www.rwdubsreviews.com/2010/03/devede-using-devede-on-ubuntu-to.html)

The video seems to play correctly on YouTube. Too bad I'm too tired now to do anymore videos. I need to do two or three more. This was exhausting.

Thanks MooPi, for your willingness to help!

---

### Post by ngrieb on 2010-08-28
Avidemux would have also worked. I have used this many times to convert to other formats and there are some nifty presets like iPod which is a preset for the .mp4 video and audio settings used by an iPod...etc.

---

### Post by Baldrick_NZ on 2010-08-29
As a relative newbie to this, I have found the following works a treat for me:

GTK RecordMyDesktop: To record from your desktop (ogv format)

Handbrake: To convert the ogv format to H.264 (MP4)

OpenShot: to edit the video (cut, splice, add titles, effects and transitions) and save to high quality video (as above).

All 3 apps can be found in your repositories using the "Ubuntu Software Centre".

Here's an example of what I did using this formula. [http://www.youtube.com/watch?v=zo4b6U4fYkw](http://www.youtube.com/watch?v=zo4b6U4fYkw) 
Btw, I have a very slow PC, so the jerking/freezing at times throughout the vid is related to that, not the process I used. 

There maybe better ways, but this does it for me right now.

Hope it helps.

---

### Post by MetaMs on 2010-08-29
Thanks Baldrick_NZ,
I did read about handbrake, but I cannot find it in the repository and I'm not yet comfortable installing apps from websites not in the repository. Also, the webpate on handbrake only shows Ubuntu 9.04 and no download even for that.

---

### Post by howefield on 2010-08-29
> **MetaMs said:**
> I did read about handbrake, but I cannot find it in the repository and I'm not yet comfortable installing apps from websites not in the repository. Also, the webpate on handbrake only shows Ubuntu 9.04 and no download even for that.

You would need to add the Handbrake repository to your sources.list to get handbrake. It is a bit easier than it appears.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

Open a terminal (Applications > Accessories > Terminal) and type

```
gksudo gedit /etc/apt/sources.list
```

Add the following to the end of the file and save...

```
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu lucid main 
deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu lucid main 
```

Then add the authentication key - copy the contents of the following webpage to a text file on your desktop.
 
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x8771ADB0816950D8](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x8771ADB0816950D8)

and go to System > Administration > Software Sources > Authentication and import the key file that you just created.

Reload your software sources and you will be able to install handbrake using Synaptic Package Manager.

---

### Post by MetaMs on 2010-08-29
Oh my! Thanks howefield, but I'm afraid this is above and beyond my current comfort level. I've only been using Ubuntu since April and although I do use the terminal for fairly straightforward commands, this appears very complex.

I do appreciate the support, and I'm sure someone else will come along who will utilize your suggestion. I think, since I've found a method that works, I will stick to what I clearly understand and am confident with!

---

### Post by howefield on 2010-08-29
> **MetaMs said:**
> Oh my! Thanks howefield, but I'm afraid this is above and beyond my current comfort level.

Keep at it, you said it... "current comfort level" There is a learning curve with any operating system, your current level will keep rising the longer you use it.  

> I think, since I've found a method that works, I will stick to what I clearly understand and am confident with!

A lot to be said for that.

Good luck.

---

