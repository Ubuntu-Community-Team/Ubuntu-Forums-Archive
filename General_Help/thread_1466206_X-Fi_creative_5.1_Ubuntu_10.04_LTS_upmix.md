---
title: "X-Fi creative 5.1 Ubuntu 10.04 LTS upmix"
date: 2010-04-30
forum: General Help
---

### Post by avengerus on 2010-04-30
Hello,
im trying to get my X-Fi, soundcard from creative, work in Ubuntu 10.04 LTS. Main goal is setup 5.1 sound and upmix stereo to 5.1.
Before i had Linux Fedora 12 ( gnome ) and used this configuration in asound.conf ( etc/asound.conf )

---------
# Virtual 5.1 device (softvol):
# for volume control
pcm.softvol {
    type            softvol
    slave.pcm        "six"
    control {
        name        "UpMix51"
        card        0
    }
}

# software device with 6 channels 
pcm.six {
        type route
        slave.pcm "multi"
        ttable.0.0 1
        ttable.1.1 1
        ttable.2.2 1
        ttable.3.3 1
        ttable.4.4 1
        ttable.5.5 1
}


# customize this, if your xfi hast not the index=0 
# Splitting the channels into six different devices:
pcm.multi {
    type            multi
    slaves {
        a.pcm        "hw:0,0"
        a.channels    2

        b.pcm        "hw:0,1"
        b.channels    2

        c.pcm        "hw:0,2"
        c.channels    2
    }
    bindings {
        0.slave        a
        0.channel    0
        1.slave        a
        1.channel    1
        2.slave        b
        2.channel    0
        3.slave        b
        3.channel    1
        4.slave        c
        4.channel    0
        5.slave        c
        5.channel    1
    }
}

# Low/Highpass for channel speration
# controls[ x ] specifies the crossover frequency x for the subwoofer.
# 80-120 for most common systems

pcm.lowpass_21to21 {
    type ladspa
    slave.pcm upmix_21to51
    path "/usr/lib/ladspa"
    channels 3
    plugins {
      0 {
         id 1098  # Identity (Audio) (1098/identity_audio)
         policy duplicate
         input.bindings.0 "Input";
         output.bindings.0 "Output";
      }

      1 {
         id 1052  # High-pass filter
     
         policy none
         input.bindings.0 "Input";
         output.bindings.0 "Output";
         input {
            controls [ 120 ]
         }
      }

      2 {
         id 1052  # High-pass filter
     
         policy none
         input.bindings.1 "Input";
         output.bindings.1 "Output";
         input {
            controls [ 120 ]
         }
      }

      3 {
         id 1051  # Low-pass filter
     
         policy none
         input.bindings.2 "Input";
         output.bindings.2 "Output";
         input {
            controls [ 120 ]
         }
      }

   }
}

# upmix 2.0 to 5.1
pcm.upmix_20to51 {
   type plug
   slave.pcm "lowpass_21to21"
   slave.channels 3
   ttable {
      0.0     1       # left channel
      1.1     1       # right channel
      0.2     0.5     # mix left and right ...
      1.2     0.5     # channel for subwoofer
   }
}

#upmix 2.1 to 5.1
pcm.upmix_21to51 {
   type plug
   #For use without software volume control
   slave.pcm softvol
   slave.channels 6
   ttable {
      0.0     1       # front left
      1.1     1       # front right
      0.2     1       # rear left
      1.3     1       # rear right

      # Front left/right to center.
      0.4     0.5
      1.4     0.5

      # Power of the subwoofer, normally 1 (or if you like, more)

      2.5     1
    }
}

# Overwrite your default devices

pcm.!default {
    type            asym
    playback.pcm        "upmix_20to51"
}

pcm.!surround51 {
    type            plug
    slave.pcm        "softvol"
}

---------
It was awesome, lowpass filter was working too. But in Ubuntu 10.04 i get error when i try to play mp3 with this config, using alsa. Something like : Sound device cannot be initialized ( i have czech distro ). So do you have any ideas, how can i get this config work in ubuntu 10.04 ? Thanks  for your suggestions.

---

### Post by avengerus on 2010-05-01
Still nothing, but this can help you :
[http://www.alsa-project.org/db/?f=993da1c1e2d1bac31e820018a524811ee04d81cb](http://www.alsa-project.org/db/?f=993da1c1e2d1bac31e820018a524811ee04d81cb)

when i use "aplay" command in console, i get this :
> $ aplay
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM lowpass_21to21
aplay: main:654: chyba p&#345;i otevírání audia: File exists


---

### Post by avengerus on 2010-05-01
Interesting thing : When i  change hardware output device to 5.1 or something else i can hear 5.1 sound mp3 , but when i pause sond and play it again... 5.1 is gone.. and 2.0 is again here.

---

### Post by avengerus on 2010-05-01
Is  there someone who can help me, please?

---

### Post by Dapilot1 on 2010-05-13
I can't get 5.1 to work at all with my fatal1ty, but setting it to 4.0 worked in the sound preferences. Fine by me since I don't have a spot for the center speaker anyways

---

### Post by oliwek on 2010-11-16
> **Dapilot1 said:**
> I can't get 5.1 to work at all with my fatal1ty, but setting it to 4.0 worked in the sound preferences. Fine by me since I don't have a spot for the center speaker anyways
I know this is a rather old topic, but a search with keywords "ubuntu" and "x-fi" will let people read this...
If you have a soundblaster **X-Fi** and you're using lucid or maverick, trying to get **5.1** sound but hearing **nothing from central channel** (and probably **nothing from subwoofer** either) : you have to use alsamixer to see that center + sub are muted by default!
If you prefer a GUI, install gnome-alsamixer :

> sudo apt-get install gnome-alsamixer

then run it, and check those channels that could be muted.

visually, if you use gnome-alsamixer, you'll see something like this this (in this picture the subwoofer or "LFE" is muted ; however you'll get probably LFE and center channels attached to the same pair of sliders and muted in your case)

[IMG]http://www.automaticable.com/wp-content/uploads/2008/05/ss08-unmute.png[/IMG]

---

