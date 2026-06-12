---
title: "How can a program screws up the sound of another?"
date: 2009-07-12
forum: General Help
---

### Post by UranUtan on 2009-07-12
Hi,

Using Ubuntu 9.04 x64, system up to date. Skype 2.00.72 and all multi media programs are working perfectly.

Just tried a softphone Zoiper 2.10 ([http://www.zoiper.com/downloads/free/linux/zoiper210-linux.tar.gz](http://www.zoiper.com/downloads/free/linux/zoiper210-linux.tar.gz))

After configuring the audio devices and make Zoiper working OK. When Zoiper works. No other program can produce any sound. Even when Zoiper is not rbeing used. Meaning it is still in memory but not used.

If Zopier is exited, other programs works again. But then when I launched Zoiper, it no longer work. If I fooled around with Zoiper audio device setting and make it works again, then the issue recycle itself (other media program no longer produce sounds).

What is the cause of this king of behavior and is there any fix? Thanks in advance for any help.

NOTE: I have also written to Zoiper tech support. Will post answer here when I receive any useful answer.

---

### Post by Frugoo Scape on 2009-07-12
The sounds divers your using are taking complete control of your sound card when your running a program that is using the sound. For this reason, you can only run one program at a time that utilizes these drivers to hear the sounds.

---

### Post by UranUtan on 2009-07-12
> **Frugoo Scape said:**
> The sounds divers your using are taking complete control of your sound card when your running a program that is using the sound. For this reason, you can only run one program at a time that utilizes these drivers to hear the sounds.

I can run simultaneously Totem, Rhythmbox, Skype. All works OK. Of course, the sounds are all mixed together, but they all work independently each other, no one blocking the other.

Or maybe you meant Zoiper is the one which wants to take exclusive control of audio devices? Is it because Zoiper is designed like that? I can still accept that it want exclusive use of audio device. But when it exit and rerun again it no longer work even though if all other media program are closed. Probably a buggy program.

If you happen to know Zoiper or another softphone to recommend, PLEASE jump in, I would greatly appreciate any tips.

---

### Post by yeaitsdark on 2009-07-12
> **UranUtan said:**
> 
Or maybe you meant Zoiper is the one which wants to take exclusive control of audio devices? Is it because Zoiper is designed like that? I can still accept that it want exclusive use of audio device. But when it exit and rerun again it no longer work even though if all other media program are closed. Probably a buggy program.

Some applications use OSS which is exclusive device access, whereas others use ALSA and now with Ubuntu they go through the Pulse sound server and then to the card, but not all applications are compatible with Pulse, or ALSA.

This is often extremely frustrating when you wish to say play a game, and say watch a video with a media player you like that doesn't conform. I often have this problem, and one way that often works for me is simply restarting said sound system. 

This may provide a solution for you:
```
sudo /etc/init.d/alsa-utils restart
```

---

