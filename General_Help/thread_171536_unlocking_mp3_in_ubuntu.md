---
title: "unlocking mp3 in ubuntu"
date: 2006-05-06
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-06
can someone plz tell me how i can play mp3 in the ubutu media player becasue all my media is mp3 and i cant play it.

---

### Post by superhew on 2006-05-06
[https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

---

### Post by r53s on 2006-05-06
Another option is to install mp32ogg, a command line converter from mp3 to Ogg Vorbis format, that is supported out of the box in Ubuntu...
They're usable if you have good quality mp3s...

---

### Post by capt_cope on 2006-05-06
Well since I'm a complete new comer to linux (had it installed less than 24 hours) and I managed to get it running mp3s, I know you can. [http://ubuntuforums.org/showthread.php?t=157589&page=2](http://ubuntuforums.org/showthread.php?t=157589&page=2)
Patrick's version 2 script works. That's all there is to it. I'm sure I did it wrong, but I just popped that into terminal and badabing mp3s work. Well I did actually chop off the echo bit, it was hanging up the rest of the script for me. Kudos to Patrick for posting that script, saved my rear-end!

---

### Post by clay on 2006-05-06
get "quod" from the app adder. i like "quod" been using from start

---

### Post by wikiguy on 2006-05-06
you also need to install mpg123 but actually i think that with the wiki guide you must solve your problem also try this to enable multiple sounds. withput the S symbol of course:p 

$killall esd
$sudo aptitude install libesd-alsa0 alsa-oss
$gedit .asoundrc

then copy this to the .asoundrc that youve just created

IF YOU HAVE A AC97(INTEL)

# .asoundrc for use with ALSA and the dmix plugin, for ALSA-level
# software mixing across all apps.
#
# [http://alsa.opensrc.org/index.php?page=AlsaSharing](http://alsa.opensrc.org/index.php?page=AlsaSharing)
# [http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)

pcm.dmix0 {
    type dmix
    ipc_key 219345           # any unique number here
    slave {
            pcm "hw:0,0"
            period_time 0
            buffer_time 0
            period_size 2048    # jm: much smoother than 1024/8192!
            buffer_size 32768
            rate 48000
    }

    bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
    }
}

pcm.dsp0 {
  type plug
  slave.pcm "dmix0"
}

# this makes native ALSA apps default to using dmix
pcm.!default {
  type plug
  slave.pcm "dmix0"
}

ctl.dsp0 {
  type hw
  card 0
}

ctl.!default {
  type hw
  card 0
}

OR NFORCE 2

pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}

THEN GO TO SELECT MULTMEDIA SYSTEMS AN PUT ALSA IN BOTH IF YOU HAVE UBUNTU DAPPER DOESNT MATTER THIS THING IS ALREADY SET.

---

