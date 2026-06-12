---
title: "udevinfo , Logitech V10 USB Speakers"
date: 2009-08-29
forum: General Help
---

### Post by angellika on 2009-08-29
hi. i am totally new in ubuntu. i switched from XP. now trying to give birth to my Logitech V10 USB Portable Speakers. there is the way how to make it 

[http://ubuntuforums.org/showthread.php?t=500208&highlight=udevinfo](http://ubuntuforums.org/showthread.php?t=500208&highlight=udevinfo)

but i am stucked on this line 

[B]udevinfo -a -p $(udevinfo -q path -n /dev/dsp1)

[/B]this command does not work in my terminal. it writes this:

angelika@angelika-laptop:~$ udevinfo -a -p $(udevinfo -q path -n /dev/dsp1)
bash: udevinfo: command not found
bash: udevinfo: command not found

thanks for any help! i need better sound:)

jaro

---

### Post by loomsen on 2009-08-29
Hello.

"command not found" 
usually means you don't have that program installed :)

aptitude search udev will show you which packages are available and what they are called, you can install them then with

sudo aptitude install <pkgname> <another> <third>

for example

sudo aptitude install udev udev-extras 

(The names may differ as I'm using fedora, but aptitude show will tell you.)

---

### Post by kostkon on 2009-08-29
Sorry, but that is a really old thread. Could you open a terminal and give
```
aplay -l
```
and see if your USB speakers are listed in the output.

If yes, then install the *PulseAudio Device Chooser* utility using *Synaptic*. It will allow you to make you to make your USB speakers the default output device in your system and you will be able to do some other interesting things.

For more info check [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by angellika on 2009-08-29
> **kostkon said:**
> Sorry, but that is a really old thread. Could you open a terminal and give
```
aplay -l
```and see if your USB speakers are listed in the output.

If yes, then install the *PulseAudio Device Chooser* utility using *Synaptic*. It will allow you to make you to make your USB speakers the default output device in your system and you will be able to do some other interesting things.

For more info check [here]("http://ubuntuforums.org/showthread.php?t=1130384").

hey, it is working. The PulseAudio Device Chooser is great thing. The sound is thousand times better. i am really happy now for a while :). the control of volume is also working.

thanks a lot .o0


jaro

---

### Post by angellika on 2009-08-29
> **loomsen said:**
> Hello.

"command not found" 
usually means you don't have that program installed :)

aptitude search udev will show you which packages are available and what they are called, you can install them then with

sudo aptitude install <pkgname> <another> <third>

for example

sudo aptitude install udev udev-extras 

(The names may differ as I'm using fedora, but aptitude show will tell you.)

hi.

ok now i understand:) so i installed the udev package your example was working

**sudo aptitude install udev udev-extras **

and i also installed

**sudo aptitude install udev**

but udevinfo was still not working, so maybe it is in different package that is not installed.
but nevermind i used the kostkon solution and it is playing now loudly in my room:)

thanks for time

jaro

---

