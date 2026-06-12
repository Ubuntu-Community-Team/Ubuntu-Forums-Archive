---
title: "Sound FINALLY works correctly with M-Audio 2496 and Dapper!"
date: 2006-06-01
forum: General Help
---

### Post by shewbox on 2006-06-01
Wasn't sure if this really warranted a new thread, but I installed Xubuntu 6.06 this afternoon, and among the many, many things that make this release a stable, quick, fantastic distro is the fact that my M Audio Audiophile 2496 sound card works perfectly right out of the box.  This has been a major point of frustration to get working right in every other distro I've tried (including previous Ubuntu releases) so I am uber happy right now :D 

I'm sure there are a thousand other posts floating around about good/bad things with this latest release, so forgive me if I'm taking up too much space with my rejoicing for Dapper Drake. :)

---

### Post by GameGod on 2006-06-01
Sweet!

Some of the higher-end M-Audio cards have always been an area of difficulty in Linux - maybe that's finally changed!

(I've got an M-Audio Revolution 7.1, which works pretty good, but there's this volume bug I've had since Hoary... I've upgraded from Hoary->Breezy->Dapper, so I'm gonna give the LiveCD a shot to see if the problem would go away with a fresh install, which I'm due for anyways...)

---

### Post by shewbox on 2006-06-01
Actually, I have had the same problems with volume control in previous versions, and, in fact, still have software volume control issues with Dapper as well.  Xfmedia player's volume control does nothing, and neither does xmms, although Totem's volume control works.  So I suppose everything doesn't work perfectly, but since I have my audio going into a little Eurorack mixer, then to my speakers and headphones, I simply use the volume control on the mixer instead of settings inside the software I use.  However, without adjusting anything, I can play multiple audio threads at once with everything sounding correct.  In Breezy, I could only play one stream at a time, and sound came out of only one channel and played back reeeaaaaaaallllly slow (like it would if you adjusted the sampling rate).  So I am quite pleased with the default settings in Dapper, even though volume control isn't perfect.

---

### Post by doobit on 2006-06-01
Still doesn't work with the FireWire 410. The M-Audio site says Linux not supported for it. I thought they had one a while ago?

---

### Post by cleentrax on 2006-06-01
Congratulations! I couldn't even get that card to work with Windows XP!

---

### Post by hotani on 2006-06-01
Wow - that's amazing. My M-Audio Revolution 5.1 card in my mac is always at 100% volume, system volume setting doesn't change it, and all sound comes out of the right channel!

So maybe there is hope.... M-Audio doesn't even have a decent OS X driver for the card (according to the site they're "working on it" but Tiger is such a "new system" - it's been out how long now?), which is the system I was using it on originally since the on-board sound died.

---

### Post by a13xa on 2006-06-12
on My M-audio revolution 7.1 Digital out - didn't working at all...
so sad...

i'll go back to windows... and w8 for better time... =\

---

### Post by imrazor on 2006-06-25
[quote=hotani]Wow - that's amazing. My M-Audio Revolution 5.1 card in my mac is always at 100% volume, system volume setting doesn't change it, and all sound comes out of the right channel!

So maybe there is hope.... M-Audio doesn't even have a decent OS X driver for the card (according to the site they're "working on it" but Tiger is such a "new system" - it's been out how long now?), which is the system I was using it on originally since the on-board sound died.[/quote]

I've got my Revolution 7.1 working on both channels properly. Yes, the GNOME mixer applet appears to be broken, but alsamixer works properly. Go to a terminal, type "alsamixer", hit enter. What you want to pay attention to is "DAC" and "DAC 1" which represent the left and right stereo channel. At first, only the right channel would work for me, but after I twiddled the volume for both channels, the left channel came to life. Use the right arrow until DAC is highlighted, use the up and down arrows to adjust the volume and then proceed to DAC 1 with the right arrow. Hope that helps!

---

### Post by prkfriryce on 2006-09-12
> **imrazor said:**
> I've got my Revolution 7.1 working on both channels properly. Yes, the GNOME mixer applet appears to be broken, but alsamixer works properly. Go to a terminal, type "alsamixer", hit enter. What you want to pay attention to is "DAC" and "DAC 1" which represent the left and right stereo channel. At first, only the right channel would work for me, but after I twiddled the volume for both channels, the left channel came to life. Use the right arrow until DAC is highlighted, use the up and down arrows to adjust the volume and then proceed to DAC 1 with the right arrow. Hope that helps!

what do the other channels represent in the alsamixer?

---

### Post by stylishpants on 2006-11-02
My M-Audio Revolution 7.1 has had the same problem as imrazor's, where after a reboot only the front right channel works, until you twiddle the volume.

I fixed this by (as root) editing /etc/rc.local, and adding a couple of lines to perform this little volume tweak at boot time.  These are the lines I added:

amixer set PCM 1-
amixer set PCM 1+

That way my volume is fixed automatically, and I can hear the login-screen bongos in full 5.1 channel glory.


I would be very interested to see what others have in their ~/.asoundrc.  Mine took a lot of experimentation to get the 5.1 surround sound set up properly.  It seems to need some more work now that I'm on Edgy Eft, since I get into a state where I can't play any sound, even if no other applications are open at the time.  THe only way to fix it is to log out and log back in.  Might be an esd problem I guess.

Anyway, my .asoundrc is as follows:

###########################################################
# basic minimum, from alsa page for the ice1724 chip.
pcm.ice1724 {
   type hw
   card 0
}

ctl.ice1724 {
   type hw
   card 0
}

pcm_slave.ice1724_S32_LE {
    pcm ice1724
    format S32_LE
}

pcm.ice1724_convert {
    type plug
    slave ice1724_S32_LE
}
## 
## ###########################################################
## # dmix setup
## # pcm.swmix {
## #   type dmix
## #   ipc_key 313
## #   slave {
## #     pcm "hw:0,0"
## #     buffer_size 4096
## #   }
## # }
## 
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

pcm.duplicate {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,2"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
    }
}

---

### Post by imrazor on 2006-11-02
Thanks for the amixer tip, stylish. I'll have to give that a try when I get home from work. I'm still running Dapper Drake, and am unlikely to upgrade any time soon, since everything is running pretty smoothly. If you're still interested in my .asoundrc, I'll be happy to post it.

---

### Post by stylishpants on 2006-11-02
> **imrazor said:**
>  If you're still interested in my .asoundrc, I'll be happy to post it.

Yes, I'd really like to see it.  I had a very hard time finding good configuration advice for this card. The more useful info we can post to help out others, the better.  I basically just had to arrive at my posted configuration by trial and error.  Any improvements you've got would be most welcome.

---

### Post by imrazor on 2006-11-02
I looked at my .asoundrc, and realized it was completely wrong. Firstly, I made no customizations for the Revolution at all (since I only have 2.1 speakers, I'm not concerned with surround sound.) Also, I have onboard sound enabled since it seems to work better with games and Wine than the M-Audio. One customization I had to make was to forcibly unload the snd_intel8x0 module, then unload the ice1724 module, then reload the ice1724 module, then the intel8x0 driver. This makes the Revolution the primary sound card instead of the onboard sound. I then just route output from Cedega to the secondary ALSA mixer or dsp1 if I need to. Looking at the .asoundrc, I realized that it doesn't reflect these changes. It must be left over from the original install, because it shows the intel8x0 as device 0 and the ice1724 as device 2. Here it is for your viewing pleasure:

 pcm.intel8x0 {
          type plug
          slave.pcm "hw:0"
       }

       ctl.intel8x0 {
          type hw
          card 0
       }

       pcm.ice1724 {
          type plug
          slave.pcm "hw:2"
       }

       ctl.snd_ice1724 {
          type hw
          card 2
       }
pcm.48000Hz {
        type plug               # Automatic conversion PCM
        slave {                 # Slave definition
                pcm "hw:2,0"         # Slave PCM name
                rate 48000      # Slave rate (default nearest) or "unchanged"
        }
        route_policy default        # route policy for automatic ttable generation
}

---

### Post by kraymore on 2008-04-05
i have a m-audio revolution 5.1 and noticed people here were having much the same problems i am trying to get sound to output from both left and right channels (instead of just right).  i tried:

amixer set PCM 1-
amixer set PCM 2+

from a terminal (not rc.local) and it did not have any effect.

i notice when i go into gnome sound "open volume control" and if i change to all the pulseaudio channels, and despite them all being at their top levels, i'll move one or more of then down then back up again quickly like a spike and that seems to fix the sound for the current session.  

thats a whole lot of trouble to do when your missing a left channel.  i have not rebuilt alsa since i'm using hardy and i dont believe a newer version than whats on here is necessary (though i could be wrong)

I'd really appreciate some positive help on this.  

thank you very much

---

