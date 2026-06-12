---
title: "Linux equivalent of Free Hi-Q Recorder"
date: 2009-10-19
forum: General Help
---

### Post by the_monster on 2009-10-19
Does anybody know if there is a program like the Windows program Free Hi-Q Recorder for Linux. What ever is playing to your speakers will be recorded by Free Hi-Q Recorder into mp3. The only way I can run Free Hi-Q Recorder in VirtualBox. Any suggestions?

---

### Post by Giblet5 on 2009-10-19
Did you try "Sound Recorder" from the menu?

Windows gets vendor-specific drivers. Linux does not because the vendors think nobody uses Linux (or, more likely, because they'd have to pay a Linux developer more than $2.50/hour).

I guess the best answer is another question: What, exactly, do you want to accomplish? Ambient monitoring via a microphone?

Mixer output (Music+Mic+Bells/Whistles)? That would be extremely hardware specific, but the "Jack" set of tools may be what you want there. (Search synaptic for "jack")

---

### Post by the_monster on 2009-10-19
I want to record streaming data playing either in a web browser like Seamonkey or Opera or a media player like Amarok or VLC.

---

### Post by the_monster on 2009-10-19
I have tried Streamripper, which works good if you know the address of the stream, but with many web-based streams these days, you cannot do this.

---

### Post by Giblet5 on 2009-10-19
> **the_monster said:**
> I want to record streaming data playing either in a web browser like Seamonkey or Opera or a media player like Amarok or VLC.

In that case, I'd recommend installing audacity.

```
sudo apt-get install audacity
```

and fiddling with the mixer settings until it does what you expect.

I can do all of those things with Audacity on my Audigy2 card. Your mileage may vary.

---

### Post by the_monster on 2009-10-21
Can't get it to work. I will forget about it for now.

---

### Post by oldos2er on 2009-10-21
> **the_monster said:**
> I want to record streaming data playing either in a web browser like Seamonkey or Opera or a media player like Amarok or VLC.

 In vlc, just hit Ctrl-R or the circular red 'record' button.

---

