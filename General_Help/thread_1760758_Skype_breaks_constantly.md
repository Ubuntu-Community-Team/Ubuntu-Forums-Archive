---
title: "Skype breaks constantly"
date: 2011-05-17
forum: General Help
---

### Post by kernco on 2011-05-17
I use Skype on my computer at work for IMs, I don't even try to use it for voice or video calls, but I constantly have problems with it.

It seems like what's happening is a backend part of the program keeps freezing. The UI is responsive, but I'll notice when I try to send messages, I'll get a 'caution' icon next to them with a tooltip reading "Your message has not been delivered".  If I try to quit Skype, it hangs and I have to kill -9 it.

So my question is, is there a more reliable way to use Skype in Ubuntu, maybe a different program than the official Skype client? Remember, I only care about text chat.

I'm running Ubuntu 10.10 with the latest updates and Skype 2.2.0.25

---

### Post by SynonM on 2011-05-18
[Idea #1(kernco]("http://ubuntuforums.org/member.php?u=145859") u could try upgrading 2 " Ubuntu 11.04 Natty Narwhal ")
[Idea #2]("http://ubuntuforums.org/member.php?u=145859")(or the steps below might help, b/c skype uses audio even when u r texting)

same here though:confused:
I've read it is both a problem with Skype and Pulse Audio.

I'm using 11.04 here, and it works...but it sucks up all :( the CPU's. 

System crash 3 times already.

I don't know what to do...

testing....

with pulse audio

skype = 80-100% CPU's
@ idle... skype < 0% CPU

with pulse audio disabled 

@ idle... skype < 0% CPU 
& just video...  skype = 18% CPU
& audio (usb headset)... skype = 18-26%
& both... skype = 26-32

note: after about 1 min. of being on the CPU's dropped
& just video...  skype = 6% CPU!!!!!
& audio (usb headset)... skype = 8-17%
& both... skype = 16-25


decrease of approx. 50-70%!!!!!

steps taken

this is quoted from ....[http://ubuntuforums.org/archive/index.php/t-886560.html](http://ubuntuforums.org/archive/index.php/t-886560.html) 
**July 31st, 2010, 07:51 AM**
[B]So I have found more edvidence this is a pulse problem, following these instructions:
   1. Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
   2. Kill PulseAudio: $ killall pulseaudio
   3. Shut down and restart Skype
   4. Go to the Skype sound device options, where your devices should now be exposed; Choose something.
   5. Shut down Skype
   6. Turn PulseAudio autospawn back on: $ echo "autospawn = yes" > ~/.pulse/client.conf
   7. Relaunch PulseAudio: $ pulseaudio -D
   8. Launch Skype
   9. Edit and test Skype sound device preferences

[/B]afterward I restarted skype w/ a/v. It maxed @ 60% CPU's staying @ 25-30%!!!
great improvement 
I will try logging out then back in 
see if it happens again

---

### Post by Script Warlock on 2011-05-18
"text chat" why not use the built-in messenger which is empathy...

---

### Post by SynonM on 2011-05-18
> **Script Warlock said:**
> "text chat" why not use the built-in messenger which is empathy...

think he wants to keep the skype account

---

### Post by ianyikos on 2011-07-21
I was having the same problem, but since I installed the proprietary version of java it hasn't happened again, so maybe it has something to do with the version of java that comes with ubuntu.

---

