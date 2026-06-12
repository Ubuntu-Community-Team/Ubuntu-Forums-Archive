---
title: "Changes in theme"
date: 2011-03-22
forum: General Help
---

### Post by DeMus on 2011-03-22
Hi,
I wrote this before, a long time ago, but I still witness strange things happening to my installation.
Whenever I keep the computer on overnight, the next morning I am using a different theme OR the same theme with different settings. My normally dark colored lower panel is now bright colored, icons are different, some of them don't exist (hence the other theme I presume) plus the extra keys on my keyboard (for audio control) work with a huge delay. When I press Volume-up for example, the volume will be changed after several minutes. Really several minutes.
I have had this with all kinds of Ubuntu versions. At the moment I use LinuxMint 9 Isadora and I am having the same problems.
I hear so many people say they always use their computer 24/7 without any problem. Why can't I do that? Why do I always have these problems? What is going on here?
Who can tell me what is wrong here? I sure could use some help because I hate this situation. This should not happen. So please, somebody, help me.

---

### Post by Krytarik on 2011-03-22
I suppose "gnome-settings-daemon" is crashing for some reason. Maybe because of some power management features?

When that happens the next time, you could try restarting it:
```
killall gnome-settings-daemon && gnome-settings-daemon
```
Greetings.

---

### Post by DeMus on 2011-03-23
> **Krytarik said:**
> I suppose "gnome-settings-daemon" is crashing for some reason. Maybe because of some power management features?

When that happens the next time, you could try restarting it:
```
killall gnome-settings-daemon && gnome-settings-daemon
```
Greetings.

Thank you for your answer. I, unfortunately, had just restarted the computer before I opened this page otherwise I could have tried it. I will do so the next time I experience it. Thanks again.

Edit: Does this also explain the volume-button to react so slow, or is this just about the theme?

---

### Post by Krytarik on 2011-03-23
> **DeMus said:**
> Does this also explain the volume-button to react so slow, or is this just about the theme?
"gnome-settings-daemon" also manages keyboard and mouse settings, so yes, it can affect it as well. I just checked it before posting, because it isn't so obvious:
[http://packages.ubuntu.com/maverick-updates/gnome-settings-daemon](http://packages.ubuntu.com/maverick-updates/gnome-settings-daemon)

---

### Post by DeMus on 2011-03-24
Sorry for the late reply but thank you for your help. The next time it happens I will follow you advice.
What also seems to help, and I did not write that, but only for the way the screen looks is to start Appearance (Preferences | Appearance). Just starting is enough. I don't have to change anything, just wait a few seconds and the screen is okay again. The media buttons still don't work correctly at that time.
So I will do what you wrote when it happens again. I just wonder are there any others who experience this? Since I had it with different Ubuntu versions and now also with linuxMint, it's a bit hard to understand I am the only one.

---

### Post by Krytarik on 2011-03-24
> **DeMus said:**
> 
What also seems to help, and I did not write that, but only for the way the screen looks is to start Appearance (Preferences | Appearance). Just starting is enough. I don't have to change anything, just wait a few seconds and the screen is okay again. The media buttons still don't work correctly at that time.

That makes sense, opening the Appearance settings also restarts gnome-settings-daemon if it isn't running at that time. That is the same people are experiencing with the current major gnome-settings-daemon startup bug:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

But that also reduces the chance that restarting gnome-settings-daemon will be enough to also fix the buttons issue. We will need to restart another related service, or reload the USB-HIDs.

Do you use any power management feature which comes into effect during the night?

---

### Post by DeMus on 2011-03-24
Well, that answered some questions: I am not alone in this. I followed your link to the other thread and see many people having the same issue.
I see that some show they have a segfault in a program. I have this several time:
```
linuxmint9 kernel: [ 1566.490895] npviewer.bin[4992]: segfault at f58620ac ip 00000000f622c8d7 sp 00000000ff93df50 error 4 in libflashplayer.so[f5e64000+b5f000]
```
It's always in libflashplayer.so. When it happens Google Chrome is running. I use this as my main browser. Before, when still using Firefox, I also had the same problem.
I see a lot of so called solutions but they all do the same as I do, start Appearance and it's over, for the time being.
Knowing I am not the only one tells me that some day a real solution will be found because it must be known to the programmers.
Thanks again for all your help.

---

### Post by Krytarik on 2011-03-24
To make it absolutely clear, the issue you are experiencing is completely different from those described in the thread I posted. The one handled by those thread is about gnome-settings-daemon crashing at startup, and it apparently affects only Ubuntu 10.10. But your issue arises somewhere in the middle of a session, after some hours of inactivity, maybe related to Flash, and with *every* Ubuntu/Linux version you run. I didn't see a similar issue in the forums so far.

---

### Post by DeMus on 2011-04-24
Tonight I had the same thing again, a different theme, volume buttons on keyboard which don't work, a very very slow computer with 8% max CPU load. What can this be? How is it possible that so many people have their computer switched on 24/7 and I can't even survive one night. I just had to reboot this morning to make it alive again.
Who can help me please, I am so tired of this. I want to use Linux because I know the alternative is terrible. I found out yesterday when I had to prepare a laptop with windows 7 for a neighbor.
So please help me. If you need more info just ask and I'll try to give it to you. Thanks.

---

### Post by debd on 2011-04-24
I'm no expert in Ubuntu nor Linux. But for me, several problems have been solved after reinstalling the corresponding packages from synaptic.
I have no idea about LinuxMint 9 Isadora, but for Ubuntu I'd have reinstalled 'gnome-settings-daemon' from synaptic. Have you tried this yet?

---

### Post by DeMus on 2011-04-24
> **debd said:**
> I'm no expert in Ubuntu nor Linux. But for me, several problems have been solved after reinstalling the corresponding packages from synaptic.
I have no idea about LinuxMint 9 Isadora, but for Ubuntu I'd have reinstalled 'gnome-settings-daemon' from synaptic. Have you tried this yet?

No, I did not do that. I wanted to do it just now but I see a whole lot of other stuff will be uninstalled as well. Things like gnome-panel, gnome-session, gnome-controlpanel, etc. Can I just do that and will they be re-installed when I re-install the settings daemon?

---

### Post by debd on 2011-04-24
you dont need to unninstall it and then reinstall. In synaptics, after clicking on the square box right to 'gnome-settings-daemon', there's an option : 'mark for re-installation'. check it and click apply. only the package gnome-settings-daemon will be reinstalled.

---

