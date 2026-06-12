---
title: "Flash Player Sound Lag Issue"
date: 2011-05-16
forum: General Help
---

### Post by mclizardman on 2011-05-16
Hello, I am using Ubuntu 11.04 on a dual boot with Windows 7, done through Wubi. Whenever I try to play a flash game, I get about a 2 second lag between the action and the sound. Very strange. When I have searched the Internet, some people claim to have the same problem and others don't. This leads me to believe that there is a hardware incompatibility somewhere along the line. But really, I have no clue as to why this would happen. This problem isn't restricted to Ubuntu, as I have used the other popular Linux distribution Fedora, and had the exact same problem. If you do find a solution, please give me set by step instructions on how to fix it, as I am fairly knew to Linux and Ubuntu. Thanks for the help.:KS

---

### Post by mclizardman on 2011-05-17
Bump.

---

### Post by mclizardman on 2011-05-20
bump

---

### Post by linuxinstalledfromhdd on 2011-05-20
Install firefox, and install Flash Aid plugin, and use it to clean out your flash and install the correct flash plugin for your system.  I had the same problem in Beta 11.04 and it totally solved it in less than a couple of minutes.

---

### Post by mclizardman on 2011-05-20
> **linuxinstalledfromhdd said:**
> Install firefox, and install Flash Aid plugin, and use it to clean out your flash and install the correct flash plugin for your system.  I had the same problem in Beta 11.04 and it totally solved it in less than a couple of minutes.

Do you mean uninstall the current version of firefox I am using, then install it again along with flash aide? Couldn't I just install flash aide without reinstalling?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Easy peezy.

Open firefox. Google "Flash Aid" plugin for Firefox.  Install it. Run it. And you should be good to go.

---

### Post by mclizardman on 2011-05-20
Just tried it. Ran the program, restated the browser. tried a game and the same issue.

---

### Post by linuxinstalledfromhdd on 2011-05-20
fixed my issue.  Sounds like a hardware issue at your end probably

---

### Post by mclizardman on 2011-05-20
I'm quite sure my computer is capable of handling flash games. A dual core 3.2 ghz phenom shouldn't be tripped up by crush the castle from armorgames.com. Could it be an incompatibility with Linux? It happened in Fedora as well....

---

### Post by linuxinstalledfromhdd on 2011-05-20
you gotta reboot that too

---

### Post by linuxinstalledfromhdd on 2011-05-20
If it happens in all versions of Linux, that doesn't make it a linux issue. That makes it a hardware issue or maybe just a driver issue.

---

### Post by mclizardman on 2011-05-20
You mean restart? okay tried that still the same...

---

### Post by linuxinstalledfromhdd on 2011-05-20
reboot means restart friend

---

### Post by mclizardman on 2011-05-20
> **linuxinstalledfromhdd said:**
> If it happens in all versions of Linux, that doesn't make it a linux issue. That makes it a hardware issue or maybe just a driver issue.

I didn't mean to make it sound like a Linux issue. I just figured since most hardware is made for use with windows machines there might be some incompatibility.

---

### Post by lovinglinux on 2011-05-20
If you are using Flash-Aid 2.1.x, please click the "Help" menu, then "Generate Report", then attach the file *firefox-report.txt* created in your Desktop. If you are using 2.0.x, this feature is in the "Help" tab.

It is only the games that have this problem? Does it happen with any game or just a few? Can you post a link? Does YouTube work fine?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Downgrade Flash from Beta to Normal version with Flash Aid and reboot your system friend.

---

### Post by mclizardman on 2011-05-20
> **lovinglinux said:**
> If you are using Flash-Aid 2.1.x, please click the "Help" menu, then "Generate Report", then attach the file *firefox-report.txt* created in your Desktop. If you are using 2.0.x, this feature is in the "Help" tab.

It is only the games that have this problem? Does it happen with any game or just a few? Can you post a link? Does YouTube work fine?

Here is the report. 

All flash created games have this issue. Videos (including Youtube) stay in sync while playing, but when pause is hit the sound continues to run for about a second or 2. Here is a link to a good example of a laggy game: [http://armorgames.com/play/6137/crush-the-castle-2](http://armorgames.com/play/6137/crush-the-castle-2)

---

### Post by linuxinstalledfromhdd on 2011-05-20
if you have running a 64-bit version ubuntu with 64-bit adobe flash plugin this will happen every time.

---

### Post by mclizardman on 2011-05-20
It also happened with the 32 bit version of flash. I'm honestly not sure if im using the 32 bit version of Ubuntu or not.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I think you have a 64 bit version of Ubuntu running.. And you have 32bit libraries installed to support 32-bit Adobe flash plugins.   

Best thing to do is find out what you have. 32-bit or 64-bit ..  If you are serious about making these games work, downgrade everything to 32bit including your ubuntu.. then install Flash 32-bit in native 32bit environment.

---

### Post by lovinglinux on 2011-05-21
Just tested the link you provided with flash stable from the repos, flash beta from Adobe Labs and flash from Chrome. All 32bit. They all exhibit the same problems. The game interface has glitches and the sound has delay.

Tried to disable hardware acceleration, remove Flash-Aid tweaks and even disabled effects. Nothing solves the problem.

So I believe is not your machine. Is flash or the video driver.

What video card are you using? I am using a nVidia 7300GT.

BTW, I am using Kubuntu 11.04.

---

### Post by mclizardman on 2011-05-21
> **lovinglinux said:**
> Just tested the link you provided with flash stable from the repos, flash beta from Adobe Labs and flash from Chrome. All 32bit. They all exhibit the same problems. The game interface has glitches and the sound has delay.

Tried to disable hardware acceleration, remove Flash-Aid tweaks and even disabled effects. Nothing solves the problem.

So I believe is not your machine. Is flash or the video driver.

What video card are you using? I am using a nVidia 7300GT.

BTW, I am using Kubuntu 11.04.

I think I am using a Radeon HD 5750.

---

### Post by mclizardman on 2011-05-21
Bump.

---

### Post by mclizardman on 2011-05-22
Bump.

---

### Post by lovinglinux on 2011-05-22
I just tested on Maverick 32bit on a VM and the same sound delay occurs.

---

### Post by lovinglinux on 2011-05-22
Tested using esound instead of pulseaudio and got the same delay.

---

### Post by lovinglinux on 2011-05-22
Solution for the audio delay:

Create a new firefox script under **/usr/local/bin/firefox** with the following command:

```
gksudo gedit /usr/local/bin/firefox
```

Paste the following into the blank file and save it:

```
#!/bin/bash
export PULSE_LATENCY_MSEC=20
exec /usr/bin/firefox "$@"
```

Then run this:

```
sudo chmod a+x /usr/local/bin/firefox
```

Start firefox with the command:

```
/usr/local/bin/firefox
```

**Source:** [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666/comments/34](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666/comments/34)

I recommend that you add yourself to the bug [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666)

---

### Post by mclizardman on 2011-05-22
> **lovinglinux said:**
> Solution for the audio delay:

Create a new firefox script under **/usr/local/bin/firefox** with the following command:

```
gksudo gedit /usr/local/bin/firefox
```Paste the following into the blank file and save it:

```
#!/bin/bash
export PULSE_LATENCY_MSEC=20
exec /usr/bin/firefox "$@"
```Then run this:

```
sudo chmod a+x /usr/local/bin/firefox
```Start firefox with the command:

```
/usr/local/bin/firefox
```**Source:** [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666/comments/34](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666/comments/34)

I recommend that you add yourself to the bug [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/294666)

HOLY! It worked!!!!! I have had this problem for so long and now its fixed! You're awesome! The only weird thing is that now firefox isn't the default web browser, but I just set it as default again. You are amazing!

---

### Post by lovinglinux on 2011-05-22
> **mclizardman said:**
> HOLY! It worked!!!!! I have had this problem for so long and now its fixed! You're awesome! The only weird thing is that now firefox isn't the default web browser, but I just set it as default again. You are amazing!

You are welcome.

I had no idea how to fix this, but I was lucky to find the bug report.

---

### Post by mclizardman on 2011-05-22
well I'm glad you did. It's a shame that the flash for Linux is still really resource heavy for what it is. My system is sometimes bogged down by little flash games when in Windows it can play StarCraft 2 on ultra settings with 60 Frame Rates per second.

---

### Post by abelandlinux on 2011-06-09
Oh my god! 

I had this sound delay issue while trying to play some little melodies with today's Google doodle (Les Paul) and searched for a solution. Now it works perfectly!

You gotta love the Ubuntu/Linux community!


By the way, how do I do the same thing for Chrome?

---

### Post by linuxinstalledfromhdd on 2011-06-09
Chrome uses it's own flash plugin.  And Firefox is usings the actual plugin from Adobe. They are separate. I don't know of a way to update the Chrome flash plugin since it is browser specific.  Chromium should use the same plugin as firefox however. :)

---

### Post by lovinglinux on 2011-06-10
> **abelandlinux said:**
> Oh my god! 

I had this sound delay issue while trying to play some little melodies with today's Google doodle (Les Paul) and searched for a solution. Now it works perfectly!

You gotta love the Ubuntu/Linux community!


By the way, how do I do the same thing for Chrome?

Use the same procedure, but instead of /usr/local/bin/firefox use /usr/local/bin/google-chrome and so on.

---

### Post by abelandlinux on 2011-06-10
Didn't get this to work on an Ubuntu 11.04 VirtualBox guest on a Win XP 64-bit host at work.

I wonder why would that be...

---

### Post by iamanidiot123 on 2011-06-28
And for google chrome, you do the same thing, right?

---

### Post by iamanidiot123 on 2011-06-28
Actually, instead of making a new file, go to the /usr/bin directory.

```
$ sudo gedit google-chrome
```

or:

```
$ sudo vi google-chrome
```

or the same with firefox, whichever one you prefer.  
They, awesomelly, are not binary files.
Therefore, insert this code which came from a previous post in this thread:
```
export PULSE_LATENCY_MSEC=20
```
right after this existing code:
```
#!/bin/bash
```

and then you can just run the stuff normally.  I think.

In my firefox executable, it says 
```
#!/bin/sh
```
at the beginning instead.  

You don't have to do anything else.

---

### Post by g0ph3r on 2011-10-31
> **iamanidiot123 said:**
> Actually, instead of making a new file, go to the /usr/bin directory. ...

You are the MAN! Thank you very much! I searched for this fix for days.. Finally I got it and works!!! Thanks again!

---

### Post by L815 on 2011-11-28
The proposed solution works! I've had this issue for quite a few releases across many distros. 

According to the docs, you can put the export in /etc/environment to apply it globally.

I did just that and it works using the default firefox launch (no bash hack).

---

