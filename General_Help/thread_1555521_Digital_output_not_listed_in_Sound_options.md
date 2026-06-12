---
title: "Digital output not listed in Sound options"
date: 2010-08-18
forum: General Help
---

### Post by xelasha on 2010-08-18
Ubuntu seems to see my onboard audio card but I can't select it in the Sound options as my output. In Alsamixer I can adjust settings and have turned on SPIDIF. It's listed when I run the lspci command as ```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

```

So what is the problem?

I'm running Lucid Lynx 64-bit.

Oh and my headphones and VGA audio outputs are in sound options as well.

EDIT:
After some tinkering I managed to fix it. Unfortunately I don't know for sure what tweak fixed it so I can't post a solution. Though I think it might have been this replacement in alsa.conf.

```
  pcm.envy_spdifdmix {
  		type dmix
  		ipc_key 1337
  		slave {
  				pcm "1b"
  				format S32_LE
  				rate 44100
  		}
  }
  
  pcm.envy_spdif {
  		type plug
  		slave {
  				pcm envy_spdifdmix
  		}
  }
  
  pcm.!default {
  		type plug
  		slave {
  				pcm envy_spdifdmix
  		}
  }
  
  # For ogle
  #
  pcm.!spdif {
  		type plug
  		slave {
  				pcm "1b"
  				format S32_LE
  		}
  }
  
  # For mplayer ao (mplayer -ac hwac3 -ao alsa1x:mplayer)
  # For vlc, use mplayer as alsa device
  #
  pcm.!iec958 {
  		type plug
  		slave {
  				pcm "1b"
  				format S32_LE
  		}
  }
  
  pcm.mplayer {
  		type plug
  		slave {
  				pcm "1b"
  				format S32_LE
  		}
  }

```
Of course replacing "1b" with whatever your audio device's physical id is. And turn on SPIDIF via alsamixer because it is off by default. And after reboot it was listed in sound options. Also I acquired that code from another forum during my search and picked it up along the way so I take no credit for it.

Though this COULD be wrong as I this is only my second day of really tinkering with system files and such so some confirmation would be good.

---

### Post by mastablasta on 2010-08-18
Similar issue. I updated the alsa to latest version. fixed it for a short time until it got broke again. had to restart alsa (seems hibernation messed it all up). soon after i had a crashed system. managed to boot in previous kernel version and fixed it from there. has been working now for over a week. and i hope it continues to do so. however no HD sound output.

---

