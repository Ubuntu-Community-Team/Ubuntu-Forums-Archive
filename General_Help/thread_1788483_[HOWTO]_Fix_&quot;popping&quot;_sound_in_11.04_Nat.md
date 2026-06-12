---
title: "[HOWTO] Fix &quot;popping&quot; sound in 11.04 Natty"
date: 2011-06-22
forum: General Help
---

### Post by DanneStrat on 2011-06-22
Since I installed Natty recently, I had this "popping" sound from the speakers when the laptop was running on battery. Turns out this popping has to do with a power-saving feature for "hda-intel" sound-chips.

If you're experiencing the same thing, here is how you fix it:

Open terminal and do:

```
gksudo gedit /usr/lib/pm-utils/power.d/intel-audio-powersave
```

Find this line:

[COLOR="Red"]INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

and comment it out by putting a "#" in front of it like this:

[COLOR="Red"]# INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

Just below this line you make a new line, like this: 

[COLOR="Red"]INTEL_AUDIO_POWERSAVE=false[/COLOR]

So now you will have:

[COLOR="Red"]# INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}
INTEL_AUDIO_POWERSAVE=false[/COLOR]

Save the file (File > Save) and exit.

Reboot the computer.

The popping sound will be gone.


NOTE: If you for some reason need to undo the setting, just open the file again and remove the "#" from:

[COLOR="Red"]INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

and delete this line: 

[COLOR="Red"]INTEL_AUDIO_POWERSAVE=false[/COLOR]

Save the file.

Reboot.

---

### Post by rikitikitak on 2011-06-28
> **DanneStrat said:**
> Since I installed Natty recently, I had this "popping" sound from the speakers when the laptop was running on battery. Turns out this popping has to do with a power-saving feature for "hda-intel" sound-chips.

If you're experiencing the same thing, here is how you fix it:

Open terminal and do:

```
gksudo gedit /usr/lib/pm-utils/power.d/intel-audio-powersave
```Find this line:

[COLOR=Red]INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

and comment it out by putting a "#" in front of it like this:

[COLOR=Red]# INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

Just below this line you make a new line, like this: 

[COLOR=Red]INTEL_AUDIO_POWERSAVE=false[/COLOR]

So now you will have:

[COLOR=Red]# INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}
INTEL_AUDIO_POWERSAVE=false[/COLOR]

Save the file (File > Save) and exit.

Reboot the computer.

The popping sound will be gone.


NOTE: If you for some reason need to undo the setting, just open the file again and remove the "#" from:

[COLOR=Red]INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}[/COLOR]

and delete this line: 

[COLOR=Red]INTEL_AUDIO_POWERSAVE=false[/COLOR]

Save the file.

Reboot.


Thank you very much for this post. This did get rid of the crackling/popping noises coming from my hp 

laptop. One thing i've noticed though, the volume output is less now. Is there anyway to restore or boost 

the volume output? Your help would be appreciated!

---

### Post by DanneStrat on 2011-06-28
> Thank you very much for this post. This did get rid of the crackling/popping noises coming from my hp laptop.

You're welcome!

> One thing i've noticed though, the volume output is less now. Is there anyway to restore or boost 

the volume output? Your help would be appreciated!

Hmm, this setting is not supposed to alter the output volume. It's only used to make sure the sound card does not turn on/off repeatedly to save power when not in use(which causes the popping sound).

Maybe your sound settings got a reset after you disabled power-saving.

Open terminal and type:

```
alsamixer
```

Make sure the "Master" and "PCM" channels are turned up.

You use the keyboard up/down arrows to increase/decrease volume.

Use the "escape" key to exit from alsamixer when you're done.

Any difference?

---

### Post by simonjtyler on 2011-07-09
Thanks for the fix DanneStrat - it worked perfectly.

---

### Post by DanneStrat on 2011-07-09
> **simonjtyler said:**
> Thanks for the fix DanneStrat - it worked perfectly.

I'm glad it worked for you!

---

### Post by Surkow on 2011-12-28
Sadly enough it didn't work for me. How can you check if the changes had any effect?

Edit: It's much less frequent though.

---

### Post by apienk01 on 2013-02-04
Thank you for the tip!

If someone doesn't want to make permanent changes, the same can be achieved temporarily with:

```
sudo su
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

Replace "snd_hda_intel" with your soundcard's module if necessary.

---

### Post by codemaniac on 2013-02-04
Ubuntu 11.04 has already reached EOL and not officially supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases).

Also as per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.
Old thread is closed now.

Thanks!

---

