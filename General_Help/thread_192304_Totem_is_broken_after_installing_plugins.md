---
title: "Totem is broken after installing plugins"
date: 2006-06-08
forum: General Help
---

### Post by ph349397 on 2006-06-08
I've followed the instructions  [here]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3") in order to get Totem to play more file formats (mpeg, Xvid, etc).  I installed:

gstreamer0.10-plugins-ugly
gstreamer0.10-ffmpeg 
gstreamer0.10-gl
gstreamer0.10-plugins-ugly-multiverse 
gstreamer0.10-pitfdll
totem-xine 
gxine 
libxine-extracodecs

using the Synaptic Package Manager.

Now, when totem is booting up, it immediately crashes.

What should I do?

---

### Post by givré on 2006-06-08
You installed everything, but you didn't have to:
There is two major engine use by totem in ubuntu : xine and gstreamer. but you couldn't install totem-xine AND totem-gestreamer.
So if totem-xine crash for you, try reinstalling totem-gestreamer
```
sudo apt-get install totem-gstreamer 
```

PS :if you keep this one, you will not need libxine-extracodecs which are plugin for xine, and gxine which is an other mediaplayer which use xine

---

### Post by turni on 2006-06-10
I am having the same problem, and I need to use totem-xine for the DVD support. The last thing I installed was totem-xine and before that it would not crash until I tried to load a file... now it crashes immediately. 

Output:

> ###@###:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Can anyone actually help solve this problem?

---

### Post by yosoyviejo on 2006-06-10
Have you tried [this](http://ubuntuforums.org/showthread.php?t=181948)?

---

### Post by turni on 2006-06-10
I have now and it didn't help. The program crashes even if I load it up with a video as an arguement, meaning that it never actually shows the logo in the first place. The fact is it was working fine when I was just using an upgraded version of the last beta, but since I then reinstalled to gain all default packages it hasn't worked. I have even tried reinstalling everything again.

---

### Post by vivienlynn on 2006-06-18
I have the same problem that totem-xine crashes when it loads up...
However, if I open gxine or xine-ui first and open totem-xine, it works fine
with them in the backgroup.... I have no idea why.

---

### Post by Douglas Royds on 2006-06-19
From my web-trawling, there seem to be 3 different issues with Totem in 6.06. They all cause a BadAlloc error from X:

1. The default /usr/share/totem/totem_logo.png is a bit big. Rename it to something else, and Totem can then be started from the menu. This is [Bug 35229 on Launchpad]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229").

2. With some hardware graphics chips, not enough RAM is being allocated. This is [Bug 4229]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/4229") ([see this post on the ubuntuforums as well]("http://ubuntuforums.org/showthread.php?t=194746&highlight=totem+badalloc")), and needs a couple of lines to be added to /etc/X11/xorg.conf, in Section "Device":

 Option "VideoRam" "32768"
 Option "CacheLines" "1980"

3. There's something else going wrong with Totem, to do with setting up the video driving. Running xine-ui first, as suggested by vivienlynn, did the job for me, too. As soon as you've started playing the DVD in Totem, you can close xine-ui, and Totem continues fine. This all begs the question, "Why not just view the DVD in xine-ui?" Well, it doesn't work, of course, ...

---

### Post by bwbettin on 2006-06-19
[QUOTE=turni]I am having the same problem, and I need to use totem-xine for the DVD support. The last thing I installed was totem-xine and before that it would not crash until I tried to load a file... now it crashes immediately. 

Output:



Can anyone actually help solve this problem?[/QUOTE]

I am having almost the exact same problem.  Here's my output....

```
XXXXXXXX@XXXXXXXX:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I followed all the tutorials on Ubuntu's documents pages for 6.06 Desktop, including the restricted formats and whatnot.  Totem worked without a problem before I installed totem-xine.

Whenever I click on "Movie Player" from my Applications menu, I see Totem's gui for a few moments and then it disapears.  If I double-click a movie file (a .wmv from ign.com for instance), however, it opens up and plays the movie without a problem.  I tried removing the %U from the entry in the Applications menu, but that didn't solve anything either.

I've tried all the things listed in this thread, as well as everything I could find in the first 12 pages of Google results...nothing seems to fix the issue.  If anyone has any further suggestions I'd appreciate it!  Until then...I'll just have to use a "dummy" file to open up Totem.

---

### Post by givré on 2006-06-19
It's due to the stupid picture of totem which is launch at startup, she is too big and cause this crash. You have to resize it:
> Originally Posted by yosoyviejo
I'm trying to find the old thread were this issue has been discussed, but it seems I've lost it. Anyway, Totem still crashes when I start it up, it' because of /usr/share/totem/totem_logo.png beign "too big": if i resize this image to 640x512, it starts up just fine
See this thread for more info : [http://ubuntuforums.org/showthread.php?t=181948](http://ubuntuforums.org/showthread.php?t=181948)

---

