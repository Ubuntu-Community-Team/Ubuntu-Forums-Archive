---
title: "Messed up sound (static)...but only sometimes"
date: 2009-11-05
forum: General Help
---

### Post by djm227 on 2009-11-05
Not sure what to do about this.  I've done a few searches, but no one has had the exact same problem that I am having.

My sound when running Ubuntu is very finicky.  Right now it's perfect, but a minute ago it was full of static.  Sometimes the static only comes from the left channel, sometimes it comes out of all of the speakers.  A song could start playing with static, and end playing clear as day.

It makes no sense to me....I'm fairly new to Ubuntu, but this seems like a very strange problem.  Is there anything I can do to fix this?  Much of the things I do on my computer involve audio, so this is a huge problem for me.  Not to mention I'm pretty much playing music through it all day.

Running Ubuntu 9.10, all up to date.  Speakers are 5.1.

Terminal spit out these specs for my audio:

*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list


Thanks for the help!
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:91300000-91303fff

---

### Post by Cuddles McKitten on 2009-11-05
The only thing I can think of off the top of my head is that some cable might be slightly loose.  Did you check to make absolutely sure everything's plugged in all the way?

---

### Post by djm227 on 2009-11-05
> **Cuddles McKitten said:**
> The only thing I can think of off the top of my head is that some cable might be slightly loose.  Did you check to make absolutely sure everything's plugged in all the way?

Yes, I ruled out everything hardware related.  It is definitely something to do with the way Ubuntu is running my audio, since it works perfectly on windows.

---

### Post by Cuddles McKitten on 2009-11-05
The only other guess I would have is that it's a pulseaudio difficulty.  See if running this makes it stop:

```
rm -r ~/.pulse
killall pulseaudio
sudo alsa force-reload

```

---

### Post by djm227 on 2009-11-05
I thought that worked at first, but it went right back to the way it was.  Not sure if the command worked though.... this is what the terminal output:



lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
Terminating processes: 5061lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
 5113lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
 5173lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
 5233lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 5290lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 5354(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dan/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5354(pulseaudio). 
Unloading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.

---

### Post by Cuddles McKitten on 2009-11-05
That's what's supposed to happen when you reload ALSA.  I've got nothing then.  Hopefully someone competent can help.

---

### Post by lapoz on 2009-11-06
Hi,

I have the same problem on my laptop since installing Karmic (no pb with Jaunty).

Sound Card : Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Unfortunately, I got no solution, but here is the bug tracker I found on this issue :
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/443293](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/443293)

You might be interested in subscribing to it, a solution could pop out.

I found that one too (much older), but I'm not sure if it's exactly the same problem :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

Hope that will be useful to you.

---

### Post by imjafo on 2009-11-06
DJM227; I had the same problem with 9.10 64 bit. I went into the terminal and entered "alsamixer" without the quotes and a mixer opened, I turned all the levels down to 3/4 settings (one red on top) using the down arrow key. There are more levels to the right side of the mixer that don't show in the terminal, so make sure that you get them all by using the arrow keys to move to the right. To exit the mixer just hit the escape button, and then close the terminal. That fixed the static problems in my sound system. Give it a try, and let us know if it helps. I think that the sound is being overdriven, which causes the static. But I don't know for sure, it is just a guess based on the mixer levels being at maximum when I opened the alsamixer.
Hope this helps.
Edit: I have the intel HDA sound as well

---

### Post by lapoz on 2009-11-06
@imjafo : I don't know for djm227, but for me that's not the issue. I don't know if static is the exact word (I'm french), but in my case it's not "just" interference during the music playing. The sound is good, and then if I move fast forward in the song or at the next file of the playlist, I got this sound :
[http://launchpadlibrarian.net/33043435/VOICE1005_000.MP3](http://launchpadlibrarian.net/33043435/VOICE1005_000.MP3)
It's not random, I can recognize the tempo of the song but the sound is totally messed up.

I need to close Rhythmbox, wait a minute or two and it's back to normal.

---

### Post by djm227 on 2009-11-06
I'm going to be away from my computer for the weekend, but once I get back in town I'll give those a good try and post what happens.  Thanks for the help.

---

### Post by Zylock on 2009-11-07
Like imjafo suggested, I think the new configuration that 9.10 is running for audio is just overblowing (amplifying, augmenting, whatever exact term works best,) audio. 
I really have no idea how to help fix the problem, but I thought I'd weigh in to help define what the exact difficulty is.

All of my sound was running perfectly while I was running 8.04. As soon as I upgraded to 9.10, all of my audio is garbled while I maintain 100% volume software side. If I turn software volume down to around 70-80%, I can run my audio at any hardware level I want without any issue. As soon as I jack the sound levels in Ubuntu, whether the main mixer, the mixer in Rythmbox, or wherever else, the sound becomes garbled again. For the sake of clarity, by garbled I mean that there is an added hiss, a kind of static distortion that muddies the audio track. It's the exact sound you'd get if you turned the volume up on your home stereo system far past what your speakers can handle.

---

### Post by liblamb on 2009-11-07
I have what sounds like the same problem. Intermittent static (or hissing). Right now sound works sometimes and not others. Using Rythmbox, one song played correct and without any user intervention the second had static. Right now I can only set the main volume at about 75% and 33% at which points there is not static but when I move the volume anywhere else it has static. Really strange. It happens in headphones and speakers, which connect to the computer at different spots.

---

### Post by JackOfAllGames on 2009-11-20
I'm having this problem as well. I'm running Ubuntu 9.10 on my Dell XPS 400 system. I first noticed the extra "static" noise coming out of the left speaker (it's static on top of the usual sound) a day or so ago. I've been using 9.10 since the official launch and haven't had this problem before now (including previous Ubuntu versions).

I've tried restarting alsa and all that. I've tried playing with the volume settings. The only thing that seems to remove the static is switching my 2.1 audio into something 4+ (my sound card supports better than the speakers I use). I'm sure I'm probably losing some sound quality (I don't have ears trained for such things), but at least I'm free of that horrid crackling noise for now.

EDIT: I forgot to mention something potentially major. I have NOT tried rebooting my system. That's not an option at the moment. I probably need a new power supply and am short on cash. I often struggle for hours to get my computer to boot and stay on. The problem started around the time I last had to work at getting my computer to boot.

---

