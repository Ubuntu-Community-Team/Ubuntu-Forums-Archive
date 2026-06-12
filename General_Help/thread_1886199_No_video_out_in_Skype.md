---
title: "No video out in Skype"
date: 2011-11-24
forum: General Help
---

### Post by pierreu1 on 2011-11-24
I am re-posting this in the hope that someone can help.

Still, rocketfish webcam is not working. lsusb returned this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 2222:3085 MacAlly 
Bus 004 Device 002: ID 04a9:1086 Canon, Inc. i560
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I googled 2222:3085 and skype, and got 1 single post, which did not help because many people say their cam work in the test video in Skype: 

[http://ubuntuforums.org/archive/inde...t-1748952.html](http://ubuntuforums.org/archive/inde...t-1748952.html)

BTW, the cam does work anywhere else and worked when I was using 10.04. Now, 11.04.

I am at a loss as to what I should do! 

If I should post this somewhere else, let me know, please.

Thanks.

---

### Post by gordintoronto on 2011-11-24
Isn't 0c45:6288 your webcam?

---

### Post by pierreu1 on 2011-11-24
> **gordintoronto said:**
> Isn't 0c45:6288 your webcam?

Oh! Thank you for trying to help! I think that is a great question because I don't have a camera of the sort! I have a headphone with mic combo though that I hook to the headphone and mic jacks in front of my computer. The camera is a USB device. Does that help? The MacAlly is the mouse. I have a rocketfish cam, but it is not indicated as such ...

---

### Post by gordintoronto on 2011-11-24
So the thing which identifies itself as a camera, is not a camera?

---

### Post by pierreu1 on 2011-11-24
> **gordintoronto said:**
> So the thing which identifies itself as a camera, is not a camera?


Actually, I Googled Microdia SN9C202 and I got this:

[http://digamy.blogspot.com/2010/09/sn9c202-web-cameras-microdia-type.html](http://digamy.blogspot.com/2010/09/sn9c202-web-cameras-microdia-type.html)

Although I am running Natty, maybe I need to follow these steps to make it work. 

"From a command-line prompt, cd to a directory where you want to download it."

Which directory should I put it in, if I need to follow these steps, of course!

Thanks!

---

### Post by gordintoronto on 2011-11-25
If you are highly organized. you might want to use a Downloads directory:
cd Downloads

I'm not sure if Natty has a Downloads directory by default. If not:
mkdir Downloads

Note that Linux pays attention to upper and lower case. Downloads and downloads are two different places.

---

### Post by Fred Doolie on 2011-11-25
Mine doesn't either unless I used this little script


11.04 and under version

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


11.10 version

sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279;

---

### Post by pierreu1 on 2011-11-26
> **Fred Doolie said:**
> Mine doesn't either unless I used this little script


11.04 and under version

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


11.10 version

sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279;

Thanks, but now I get this error under application properties of the icon. What to do now? I cannot launch it now.

---

### Post by plucky on 2011-11-26
> **pierreu1 said:**
> Thanks, but now I get this error under application properties of the icon. What to do now? I cannot launch it now.

What error?

Try the command in a **terminal** window and show us what the error is.

---

### Post by pierreu1 on 2011-11-26
> **plucky said:**
> What error?

Try the command in a **terminal** window and show us what the error is.

Oh! Thanks for the help.

Here is the error in terminal command. I think I meant to include the screenshot. I've incl. here nonetheless. My apologies.

It is launching from terminal command, BTW. But, still no video in the test area. What do you advise me to try now.

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by no2498 on 2011-11-26
in a terminal type dmesg click enter
after it stops try skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype



#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

64 bit has a different preload

---

### Post by pierreu1 on 2011-11-26
> **no2498 said:**
> in a terminal type dmesg click enter
after it stops try skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype



#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

64 bit has a different preload

Oh! Thanks a lot, but the cam in the test area in Skype still does not work!

I did this is the terminal and then type the preloader command, which launched Skype.

I did not type this though. 

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
/usr/bin/skype


I wasn't sure. Should I do that? I have a 32 bit system.  

Jeesh! I have a pretty nasty issue here. 

Thanks for the help!

Any other idea?

---

### Post by gordintoronto on 2011-11-26
Your webcam uses a v4l2 driver, so anything which says v4l1 is not helpful.

---

### Post by pierreu1 on 2011-11-27
> **gordintoronto said:**
> Your webcam uses a v4l2 driver, so anything which says v4l1 is not helpful.

Thanks! Oh! Okay! Wrong driver! After dmesg,...


pierre2@Pierre-Vancouver:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l2compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
pierre2@Pierre-Vancouver:~$ #!/bin/bash
pierre2@Pierre-Vancouver:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so
pierre2@Pierre-Vancouver:~$ /usr/bin/skype
pierre2@Pierre-Vancouver:~$ 


Skype launches, but no camera after testing in Skype. I tried in Cheese to confirm that it works and it does, BTW.

Thanks for trying to help. I hope I am doing okay.

---

### Post by gordintoronto on 2011-11-27
Is there a file called /usr/lib/libv4l/v4l2compat.so skype?

---

### Post by pierreu1 on 2011-11-27
> **gordintoronto said:**
> Is there a file called /usr/lib/libv4l/v4l2compat.so skype?

Oh! Thanks!

No! I do not have v4l2compat I have v4l2convert and v4l1compat.

Ah! I think I need to have v4l2compat. Right? If so, how do I install it?

Thanks!

---

### Post by vangop on 2011-11-28
Can you check your video settings in gstreamer?
Run multimedia systems selector in menues (or % gstreamer-properties), check Video tab

---

### Post by pierreu1 on 2011-11-28
> **vangop said:**
> Can you check your video settings in gstreamer?
Run multimedia systems selector in menues (or % gstreamer-properties), check Video tab

Hi! Thanks for the help!

The input tab test worked! I have included an attachment on how it is set up. Do you think there is there a problem with the set up?

Thanks.

---

### Post by vangop on 2011-11-30
> **pierreu1 said:**
>  Do you think there is there a problem with the set up?

No, as long as it works :)
I have it working with "Default" device

---

### Post by pierreu1 on 2011-11-30
> **vangop said:**
> No, as long as it works :)
I have it working with "Default" device

I hope I did not lead you to believe that my video is working in Skype! It isn't! I changed to default to see if that changed things, but to no avail! The camera works outside of Skype, no problem!

Boy! This is really complicated! This is really frustrating because it used to work in 10.04! Not that I don't like this version because there is only one minor, but annoying element to Skype that does not work! 

Oh! Well! Thanks for trying! Thanks for the help!

---

### Post by vangop on 2011-11-30
I was a bit lazy to read the whole thread :)
Just noticed that you try to preload compat shared lib, but then you see that dmesg is complaining.
I've checked, and I don't have v4l1compat.so in that location. Try to provide a proper path in the preload instruction.
```
$ locate -r 'v4l.*so' | grep compat
```
or if you have some issues with that
```
$ find /usr -name 'v4l*so'
```

On my system I have
```
/usr/lib32/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so

```

---

### Post by pierreu1 on 2011-11-30
> **vangop said:**
> I was a bit lazy to read the whole thread :)
Just noticed that you try to preload compat shared lib, but then you see that dmesg is complaining.
I've checked, and I don't have v4l1compat.so in that location. Try to provide a proper path in the preload instruction.
```
$ locate -r 'v4l.*so' | grep compat
```


or if you have some issues with that
```
$ find /usr -name 'v4l*so'
```

On my system I have
```
/usr/lib32/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so

```


Oh! Thanks! I wasn't too sure if I had to run that code in the terminal or put that in the skype/properties/command line. I hope I did not have to do a dmesg before pasting the code in the terminal window. In any case, in the terminal, it returned this:

/home/pierre2/.gnome2/panel2.d/default/launchers/v4l1compat.so.desktop
/usr/lib/libv4l/v4l1compat.so

The preload command (for the shortcut icon I have) is:

 bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

How am I doing? I hope I did not screw up!

BTW, the camera still doesn't work in Skype! I have included a screenshot of the multimedia selector window i the hope this can assist you. 

I am interested to know more about the programming bit, but it takes time, which I should have more now that I am through with some major renovations I did! :) I have zero background in programming though, but willing to learn! Oh! I am lying! I did take one year of programming in 1980! The language I learned at the time I think was WATFIV. I doubt anyone knows anything about this dinosaur of a language! Not that I was proficient at it and, of course, I have never used it, so I am actually surprised I remember its name! :)

Thanks for your help!

---

### Post by vangop on 2011-11-30
Try to change the path of the LD_PRELOAD to your actual location - /usr/lib/libv4l/v4l1compat.so
Making it 
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
What's your system again? (version and is it 32/64 bit)?

---

### Post by pierreu1 on 2011-11-30
> **vangop said:**
> Try to change the path of the LD_PRELOAD to your actual location - /usr/lib/libv4l/v4l1compat.so
Making it 
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
What's your system again? (version and is it 32/64 bit)?

Ok! Done! 

32 bit and 11.04

---

### Post by vangop on 2011-12-01
Did it help? :) If you run this command, do you see any changes?
Also plz check dmesg

---

### Post by super123hit on 2011-12-01
Oh! Appreciate attempting to help! I believe that's an excellent question because I do not possess a camera from the sort! I've got a earphone with mic combo though which i hook towards the earphone and mic jacks before my computer. Your camera is really a USB device. Does which help? The MacAlly may be the cam.
_____________________
[Hip Hop Music]("http://www.music4hiphop.com/")

---

### Post by pierreu1 on 2011-12-01
> **vangop said:**
> Did it help? :) If you run this command, do you see any changes?
Also plz check dmesg

Oh! Sorry! I did not get back to you! Yes! It does launch, but still no camera! Very! Very Strange!

I ran dmesg and there is a long string of similar-looking code lines.

I think all the ducks are in a row. Why doesn't it work now?

---

### Post by pierreu1 on 2011-12-01
> **super123hit said:**
> Oh! Appreciate attempting to help! I believe that's an excellent question because I do not possess a camera from the sort! I've got a earphone with mic combo though which i hook towards the earphone and mic jacks before my computer. Your camera is really a USB device. Does which help? The MacAlly may be the cam.
_____________________
[Hip Hop Music]("http://www.music4hiphop.com/")

I also have a mic and headphones (for the audio part). Yes! My camera is a USB device. Yes! The MacAlly is the camera!

---

### Post by koftis on 2011-12-07
I'm on a pc using 10.10 x64 my solution is 



> desktop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skypelibv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error allocating conversion buffer

can sb explain the error (although my video is working):D

---

### Post by pierreu1 on 2011-12-07
> **vangop said:**
> Did it help? :) If you run this command, do you see any changes?
Also plz check dmesg

So, I do have this in the properties of the shortcut.

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Why isn't it working?

Should I re-install some piece of software?

---

### Post by koftis on 2011-12-07
> **pierreu1 said:**
> So, I do have this in the properties of the shortcut.

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Why isn't it working?

Should I re-install some piece of software?
  have you tried

 open terminal and

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

or using the bash

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

---

### Post by pierreu1 on 2011-12-07
> **koftis said:**
> have you tried

 LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

without the "bash ..." and changing the lib to lib32?

So, you mean as just:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Precisely like that?

No like that, it does not work at all: it doesn't even launch!

Thanks.

---

### Post by pierreu1 on 2011-12-10
I went into /usr/local/bin/ and found two "icons": Skype and Skype-cam-fix.

When I clicked on BOTH in the terminal I get the following error message, but it launches the Skype window. Still no camera though!


ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Please, help me! This is quite frustrating!

Thank you!

---

### Post by koftis on 2011-12-10
solution for editing launcher in unity 11.04 and 11.10
 

 1. go to terminal
 

 1.a>  sudo su                       (getting Root powers permanently!!!in order to change the launcher )
 

 1.b > sudo gedit /usr/share/applications/skype.desktop
 2. Now edit in line 4, replace;[INDENT]*Exec=skype *[/INDENT]with:[INDENT]*Exec=bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'     ** For 11.04***[/INDENT]For 64bit systems:[INDENT] *Exec=bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'*[/INDENT]**For Ubuntu 11.10**[INDENT]*Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'*[/INDENT][INDENT]
[IMG]http://3.bp.blogspot.com/-wX5Byim-XEk/TbQNvn6es5I/AAAAAAAABDo/Epp65-cJ_TM/s1600/skype.png[/IMG]
[/INDENT][INDENT]*Don;t forget to go to terminal * [/INDENT][INDENT]> exit* (When you’ve finished your work and want to return to your ordinary *[/INDENT][INDENT][I]user account – **not have root power**, just type exit, or hit Ctrl+D. )

original source [http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)
[/I][/INDENT]

---

### Post by pierreu1 on 2011-12-10
> **koftis said:**
> solution for editing launcher in unity 11.04 and 11.10
 

 1. go to terminal
 

 1.a                       (getting Root powers permanently!!!in order to change the launcher )
 

 1.b 
 2. Now edit in line 4, replace;[INDENT]*Exec=skype *[/INDENT]with:[INDENT]*Exec=bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'     ** For 11.04***[/INDENT]For 64bit systems:[INDENT] *Exec=bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'*[/INDENT]**For Ubuntu 11.10**[INDENT]*Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'*[/INDENT][INDENT]
[IMG]http://3.bp.blogspot.com/-wX5Byim-XEk/TbQNvn6es5I/AAAAAAAABDo/Epp65-cJ_TM/s1600/skype.png[/IMG]
[/INDENT][INDENT]*Don;t forget to go to terminal * [/INDENT][INDENT]* (When you’ve finished your work and want to return to your ordinary *[/INDENT][INDENT][I]user account – **not have root power**, just type exit, or hit Ctrl+D. )

original source [http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)
[/I][/INDENT]

Oh! Thanks very much!

I did exactly what the message showed and checked twice after to see if everything was done as it was written.

It did launch, but the camera is still not working when I hit "test".

Jeesh! I am sorry that I asking so many to help me and nothing seems to work!

BTW, after I wrote sudo su, it asked me a password. I gave my user account password. That was correct. Right?

After doing all the editing in the special window that launched, I saved and then when to "terminal' and typed exit, but it did not. Then, I quit terminal window. I hope that did not mess anything.

Thanks for all the help.

---

### Post by pierreu1 on 2011-12-12
Okay now I have no audio! Apparently it is a problem with pulse audio.

I followed this post, but skype still shows pulse audio in the audio setting of Skype.

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

This is what I did. I did not do anything below.

[COLOR="blue"]To do that, we can run the following four commands:

sudo dpkg-divert --add --divert /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu --rename /usr/lib/gstreamer-0.10/libgstpulse.so
sudo dpkg-divert --add --divert /usr/bin/pulseaudio.ubuntu --rename /usr/bin/pulseaudio
sudo sh -c 'echo '\''#!/bin/sh'\'' > /usr/bin/pulseaudio'
sudo chmod a+x /usr/bin/pulseaudio
Note that there are no double quotes in the above—they are all single quotes, sometimes adjacent.

Now we need to make sure that gstreamer uses ALSA instead of PulseAudio. Run:

gstreamer-properties
and set everything from PulseAudio to ALSA.

As of Ubuntu 10.04, the ubuntu-desktop metapackage also depends on libsdl1.2debian-pulseaudio, but we want libsdl applications (games, typically) to use alsa instead. To do this, we can trick the package management system into thinking we have libsdl1.2debian-pulseaudio installed by installing the following dummy package: libsdl1.2debian-pulseaudio-dummy_1.0_all.deb. You can save it somewhere and double-click it to install it or, in a terminal, type

sudo dpkg -i libsdl1.2debian-pulseaudio-dummy_1.0_all.deb
...in the directory where you saved it.

After you have installed the dummy package, now type the following:

sudo apt-get install libsdl1.2debian-all[/COLOR]

In the multimedia settings, I have alsa now. I guess they must be the same. Right? If so, how do I do that? How do I get Alsa in Skype, if that is what I need to do!

Thank you.

---

### Post by pierreu1 on 2011-12-12
Okay! I am a newbie. Can you could help me?

I have had issues with skype as soon as I installed Natty.

I have had this problem for 5 months now. No one seems to be able to help me with this.

Can I go back to 10.04. If so, will it be painless? Will I need to back up everything because there will be problems? 

I removed the pulseaudio nightmare.

But, I have tried so many fixes that I don't know what to do next.

---

### Post by pierreu1 on 2011-12-12
> **vangop said:**
> I was a bit lazy to read the whole thread :)
Just noticed that you try to preload compat shared lib, but then you see that dmesg is complaining.
I've checked, and I don't have v4l1compat.so in that location. Try to provide a proper path in the preload instruction.
```
$ locate -r 'v4l.*so' | grep compat
```
or if you have some issues with that
```
$ find /usr -name 'v4l*so'
```

On my system I have
```
/usr/lib32/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so

```

When I use the find command, I get this:

/usr/lib/gegl-0.0/v4l.so
/usr/lib/libv4l/v4l1compat.so
/usr/lib/libv4l/v4l2convert.so

I guess I need to change things. Right? How and to what?

I have incl. 2 screenshots.

Thanks. Much appreciated!

---

### Post by pierreu1 on 2011-12-12
And, to add to the last message, I ran dmseg and I got this:


[40665.986391] [UFW BLOCK] IN=eth0 OUT= MAC=00:a0:d1:46:d8:ce:c8:4c:75:77:4d:d9:08:00 SRC=41.101.114.171 DST=70.71.130.214 LEN=48 TOS=0x00 PREC=0x00 TTL=242 ID=22739 DF PROTO=TCP SPT=59407 DPT=53482 WINDOW=65535 RES=0x00 SYN URGP=0 

 ... shortened after editing, since it did not seem to help.

---

### Post by vangop on 2011-12-14
Just FYI
There's a similar [thread]("http://ubuntuforums.org/showthread.php?t=966882") and here's the [solution]("http://ubuntuforums.org/showpost.php?p=11398370&postcount=35")
See if it helps.

---

### Post by pierreu1 on 2011-12-14
> **vangop said:**
> Just FYI
There's a similar [thread]("http://ubuntuforums.org/showthread.php?t=966882") and here's the [solution]("http://ubuntuforums.org/showpost.php?p=11398370&postcount=35")
See if it helps.

Oh! Thank you!

I went into synaptic to look for libv4l-0:i386, but I only could find libv4l, which was installed. There was a dev package, but I doubt that is needed, from the description. In desperation, I looked in Ubuntu software and could not find it. 

I went into terminal and tried to install the other package, but I don't think that worked: 0/0/0!

sudo apt-get install libv4l-0:i386
[sudo] password for pierre2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libv4l-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Maybe I need to do a force install? Just guessing! If so, how do I do that?

Thanks for your incredible patience!

---

### Post by pierreu1 on 2011-12-19
If you insert this line of code after right clicking on the Skype icon and going to properties and entering it in the command section, then the test in the video section of Skype will work for the Rocketfish USBCAM.

sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279;&#65279;

(found here: [http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/m-p/216792/highlight/true#M377](http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/m-p/216792/highlight/true#M377))

I will test in a few days to see if it is stable in a call, as I have had many instances of video in crashing and dropping after a few minutes of use. I suspect my video card cannot handle that much work. Some people claim that Compiz and Cairo-dock might overload the video card (which, in my case, is an cheap embedded intel).

After testing it in a call, the video lasted maybe a few minutes. It worked, but then I couldn't get it back after many trials. I could get the video feed from the other person though! I noticed that I had loads of Chrome programs and other stuff cluttering in my system, grabbing a share of the CPU, which shot up faster that to 100% a few times. The test video did not work either. I then rebooted it and tried the video test in Skype and it worked again. I noticed that I had way fewer stuff grabbing a share of my CPU. I will try next time to do a fresh boot and not open any other app and see if that makes a diff. I suspect it will.

I am not sure what happened before, but it seems that when I open many tabs in Chrome, initially, I get a high CPU load, but then thinks tends to level off to reasonable levels (40% to 60%). I have not tested this while doing a call, which I would assume --as in the past-- would strain the system more. Maybe a reboot is important, but I am nto sure why!

---

