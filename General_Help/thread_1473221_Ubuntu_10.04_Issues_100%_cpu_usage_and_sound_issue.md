---
title: "Ubuntu 10.04 Issues: 100% cpu usage and sound issue"
date: 2010-05-05
forum: General Help
---

### Post by travlemon on 2010-05-05
Hello!

I decided to upgrade my laptop from Ubuntu 9.10 to 10.04.  Instead of using the upgrade feature, I backed up the important stuff and just did a clean install of 10.[U]04.  

Issue 1:[/U] I was experiencing some performance issues with 10.04.  I was getting 100% cpu usage reported by System Monitor.  The 100% cpu usage, strangely enough, switched from CPU0 to CPU1, and back again sometimes.  I don't know if there was a pattern to it.  I also noticed video lag when using Super+E (or Window+E) to switch between desktops.  This was running incredibly smooth on this laptop when I was using 9.10.  I know it's just a minor issue, but the video in the laptop is more than powerful enough to handle it, and I'm worried about the performance having a bottleneck of some kind.

_Issue 2:_ Trying to fix issue 1, I was googling around to find a solution.  I found a thread on another site that suggested running a couple terminal commands to do something with Pulseaudio, I think.  I wasn't familiar with the commands, as my Linux knowledge doesn't stray far from my generic list of fixes for things I've encountered.  Here are the commands I ran:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update && sudo apt-get dist-upgrade

There may have been a couple other steps, however I cannot find the page anymore :(
My sound still works, but I cannot control the volume with the icon in the system tray anymore.  I had to download the Alsa Gui volume control to adjust the volume.

_My hopes for this thread:_ I would like to first know if anyone possibly understands what I may have done with _Issue 2_ (the sound issue), and can help me reverse it? 

And with _Issue 1_, have there been any reported performance bugs?  10.04 seems to run fine on my desktop, super smooth (including Window+E desktop switching).  

Any help on these issues would be MUCH appreciated, as always! Thanks in advance!

EDIT: I forgot to mention that the processes tab in System Monitor does not show any applications that are coming anywhere near the 100% cpu usage that the Resources tab is reporting. Sorry!

---

### Post by zvacet on 2010-05-05
For fixing sound issue in terminal

```
gksudo gedit /etc/apt/sources.list
```

and remove lines you added (ppa repos).Save and close file.

```
sudo apt-get update
```

---

### Post by travlemon on 2010-05-05
> **zvacet said:**
> For fixing sound issue in terminal

```
gksudo gedit /etc/apt/sources.list
```and remove lines you added (ppa repos).Save and close file.

```
sudo apt-get update
```

Thanks for responding!

Ok, I've removed the unwanted PPA line from software sources. I updated the system with any updates that just came through, and restarted.  However, my sound is still in the same state.  It works, but volume control is through the Alsa GUI program, and the tray icon does not control it.  

Is there anything else I can try?

---

### Post by lidex on 2010-05-05
Try this. Right-click on your volume icon and select 'Remove from panel'. Now right-click on panel and select 'add to panel>indicator applet' and see if that one works.

---

### Post by philinux on 2010-05-05
@trevelmon.

Your issue one could be this.

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328)

---

### Post by travlemon on 2010-05-05
> **lidex said:**
> Try this. Right-click on your volume icon and select 'Remove from panel'. Now right-click on panel and select 'add to panel>indicator applet' and see if that one works.

thank you for your suggestion. unfortunately, the applet is still doing the same thing. i'm wondering if i can reinstall pulseaudio somehow? if i go to sound preferences, i get the infamous "waiting for sound system to respond" message.

---

### Post by travlemon on 2010-05-05
> **philinux said:**
> @trevelmon.

Your issue one could be this.

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328)

thanks philinux, i think the CPU usage issue may be resolved, as some system updates came through today and the laptop now appears to be behaving more normal.

---

### Post by lidex on 2010-05-05
What happens with this command:
```
pulseaudio & pavucontrol
```

---

### Post by travlemon on 2010-05-05
> **lidex said:**
> What happens with this command:
```
pulseaudio & pavucontrol
```

lidex, thanks for responding.  i ended up screwing things up worse but removing pulseaudio in hopes of being able to reinstall it.  ultimately, i just reinstalled Ubuntu 10.04 from scratch.  I really don't have much to ever back up, as all my important data is stored remotely.

i did a system update, and a bunch of new updates came through. the system seems to be running better now, but it seems like the fan is at a high speed more constant than it should be.  i am going to go out to run a couple errands, and see if it's still running the fan like that, when i get back. if not, i will mark this thread as solved.

thanks everyone so far for the responses!

---

### Post by travlemon on 2010-05-05
> **travlemon said:**
> lidex, thanks for responding.  i ended up screwing things up worse but removing pulseaudio in hopes of being able to reinstall it.  ultimately, i just reinstalled Ubuntu 10.04 from scratch.  I really don't have much to ever back up, as all my important data is stored remotely.

i did a system update, and a bunch of new updates came through. the system seems to be running better now, but it seems like the fan is at a high speed more constant than it should be.  i am going to go out to run a couple errands, and see if it's still running the fan like that, when i get back. if not, i will mark this thread as solved.

thanks everyone so far for the responses!

to follow up on my previous message, i am going to mark this thread as solved.  i might just be over thinking the fan speed, as i can't quite remember what it sounded like before i upgraded from 9.10. thanks for all your help!

---

### Post by Andres1967 on 2010-05-07
> **travlemon said:**
> Hello!

I decided to upgrade my laptop from Ubuntu 9.10 to 10.04.  Instead of using the upgrade feature, I backed up the important stuff and just did a clean install of 10.[U]04.  

Issue 1:[/U] I was experiencing some performance issues with 10.04.  I was getting 100% cpu usage reported by System Monitor.  The 100% cpu usage, strangely enough, switched from CPU0 to CPU1, and back again sometimes.  I don't know if there was a pattern to it.  I also noticed video lag when using Super+E (or Window+E) to switch between desktops.  This was running incredibly smooth on this laptop when I was using 9.10.  I know it's just a minor issue, but the video in the laptop is more than powerful enough to handle it, and I'm worried about the performance having a bottleneck of some kind.

_Issue 2:_ Trying to fix issue 1, I was googling around to find a solution.  I found a thread on another site that suggested running a couple terminal commands to do something with Pulseaudio, I think.  I wasn't familiar with the commands, as my Linux knowledge doesn't stray far from my generic list of fixes for things I've encountered.  Here are the commands I ran:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update && sudo apt-get dist-upgrade

There may have been a couple other steps, however I cannot find the page anymore :(
My sound still works, but I cannot control the volume with the icon in the system tray anymore.  I had to download the Alsa Gui volume control to adjust the volume.

_My hopes for this thread:_ I would like to first know if anyone possibly understands what I may have done with _Issue 2_ (the sound issue), and can help me reverse it? 

And with _Issue 1_, have there been any reported performance bugs?  10.04 seems to run fine on my desktop, super smooth (including Window+E desktop switching).  

Any help on these issues would be MUCH appreciated, as always! Thanks in advance!

EDIT: I forgot to mention that the processes tab in System Monitor does not show any applications that are coming anywhere near the 100% cpu usage that the Resources tab is reporting. Sorry!

I am having the same problem with the CPU. I have an old PC with one processor and it runs at 100% even though I am not running any programs - it's virtually unusable. This same PC, booting with XP works perfectly; but I don't want to use XP! I have a laptop with 10.04 also and this one is Ok.

---

### Post by travlemon on 2010-05-07
> **Andres1967 said:**
> I am having the same problem with the CPU. I have an old PC with one processor and it runs at 100% even though I am not running any programs - it's virtually unusable. This same PC, booting with XP works perfectly; but I don't want to use XP! I have a laptop with 10.04 also and this one is Ok.

sorry for the delayed response! my only suggestion so far, as a non linux savvy user, is that you can try seeing if some system updates will come through.  i did that and it appears that i'm not getting the 100% cpu issue anymore. though my graphics still are choppy a bit when switching desktops.  it's only a minor issue, but it bothers me that there's an issue when my card should handle it just fine.  :( hopefully some more updates will do the trick!

---

### Post by travlemon on 2010-05-07
> **travlemon said:**
> sorry for the delayed response! my only suggestion so far, as a non linux savvy user, is that you can try seeing if some system updates will come through.  i did that and it appears that i'm not getting the 100% cpu issue anymore. though my graphics still are choppy a bit when switching desktops.  it's only a minor issue, but it bothers me that there's an issue when my card should handle it just fine.  :( hopefully some more updates will do the trick!

Ok, one last comment on this issue, for future readers of this thread! Apparently, the Nvidia driver decided to install with "Adaptive Mode" enabled.  It appears to be for power saving, I think.  It basically just clocks down your video card, or clocks it up when it needs more power.  If you go into the Nvidia X Server Settings, you can find this feature in the Powermizer section.  Put that sucker in "Prefer Maximum Performance" mode.  This seemed to totally solve those issue was having. The card is now using it's full power!

---

### Post by panitcz on 2011-01-21
Try to uninsatall indicator-me:

sudo apt-get remove -y indicator-me

then logout and login again, after that the problem disappeared for me.

---

### Post by travlemon on 2011-02-27
I just wanted to post something here, related to the 100% cpu usage.  It's been a long time since I had that issue.  I switched to Mandriva very briefly, and I noticed that the Nvidia Powermizer feature on my GPU was causing all sorts of issues.  Performance was lacking everywhere.  

One thing I noticed that was Firefox was running at 100% cpu usage while idle.  I later realized that any pages with flash would sky rocket the "plugin-container" process to 100% or sometimes 200%.  Oddly enough, disabling Nvidia Powermizer eliminated this annoying issue.

I don't remember enough about the original issue I had to say whether I think this was it.  Also, I don't know if this is specific to Mandriva.  However, I'm back on Ubuntu and I just wanted to throw this out there to shed more light to anyone that has CPU spiking issues.

If you need help with Powermizer, check out this thread:

[http://ubuntuforums.org/showthread.php?t=1478192](http://ubuntuforums.org/showthread.php?t=1478192)

---

