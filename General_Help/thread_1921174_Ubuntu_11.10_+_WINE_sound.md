---
title: "Ubuntu 11.10 + WINE sound"
date: 2012-02-06
forum: General Help
---

### Post by HiImTye on 2012-02-06
ok so, this is going to be a long thread. first: some background. I had [Ubuntu 10.10/11.10 working using OSS4 + PulseAudio]("http://ubuntuforums.org/showthread.php?t=1610680"), which 'just worked' with any program (including Flash apps) and had no latency. Ubuntu 11.10's PulseAudio, however, lacks the 'module-oss' package, making that set up impossible without messing with PulseAudio (which, quite frankly, seems like a lot of work/headache). I knew I would need to upgrade eventually, so I figured after reading that some performance issues had been dealt with (Unity3D still suffers from performance issues when compared to Ubuntu 11.04, forcing me to switch to GNOME-Shell, but that is for another thread), I reluctantly gave it a try again and decided to figure out how to get everything to work without issue. so, once again, I hit upgrade (actually, I installed cleanly, but that was for dramatic effect). I got all my favorite programs installed, and tried out WoW using the default set-up with ALSA + PulseAudio. this resulted in horrible sound latency and also horrible echoes. so, I tried with 'padsp' and also 'pasuspender'. padsp had latency and pasuspender seemed to work OK, until I decided to force all apps to direct sound to PulseAudio (to get flash and others to work properly with PulseAudio). I decided that Dmix was the only answer, so, I got PulseAudio to not respawn, and I started messing with Dmix. I managed to achieve what I needed to, after failing to get a decent 'catch all' setup, by making two setups and having my shell scripts automagically swap them for me. so, here is what I ended up doing:

~/.pulse/client.conf (this tells pulseaudio not to load when you close it. it also causes it to not load when you log in.)
```
autospawn=no
```~/Launchers/.asoundrc_pulsealsa (this is the config for when PulseAudio is running, directing apps that normally don't direct sound to PulseAudio to it, such as flash)
```
#grab everything and direct to pulseaudio
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```~/Launchers/.asoundrc_dmix (this is for when PulseAudio is not running, setting up Dmix for use on the default hardware for sound mixing)
```
# This configuration works for sharing sound in WINE and normal apps
pcm.my_card {
    type hw
    card 0
    device 0
}

ctl.my_card {
  type hw
  card 0
}

pcm.dmixed {
    type dmix 
    ipc_key 1024 
    slave {
        pcm "my_card"
    period_time 0
    period_size 1024
    buffer_size 8192
    rate 44100
    #format "S32_LE"
    #periods 128
    }
}

ctl.dmixed {
  type hw
  card 0
}

pcm.dsnooped {
    type dsnoop 
    ipc_key 2048 
    slave {
        pcm "my_card" 
    }
}

ctl.dsnooped {
  type hw
  card 0
}

pcm.asymed {
    type asym 
    playback.pcm "dmixed" 
    capture.pcm "dsnooped"
}

ctl.asymed {
  type hw
  card 0
}

pcm.pasymed {
    type plug 
    slave.pcm "asymed"
}

ctl.pasymed {
  type hw
  card 0
}

pcm.dsp0 {
    type plug
    slave.pcm "asymed"
}

ctl.dsp0 {
  type hw
  card 0
}

pcm.!default {
    type plug
    slave.pcm "asymed"
}

ctl.!default {
  type hw
  card 0
}
```~/Launchers/WoW.sh (this is to launch WoW - or any other WINE app, and to copy the .asoundrc to get Dmix working)
```
#rm -R /Storage/Windows/World of Warcraft/Cache/
killall conky pulseaudio
if zenity --question --text="load Dmix?"; then
    cp $HOME/Launchers/.asoundrc_dmix $HOME/.asoundrc
else
    rm $HOME/.asoundrc
fi

env WINEPREFIX="/home/tye/.wine/WoW" wine "Z:\World of Warcraft\WoW.exe"
exit
```~/Scripts/tconk.sh (a shell script that I load at log in as well as when I close WoW, which seems like the perfect time to get PulseAudio running and properly configured again)
```
if [ -f $HOME/bash_history ]
then rm $HOME/bash_history
fi
if [ -d $HOME/.thumbnails/fail ]
then rm -R $HOME/.thumbnails/fail
fi
cp $HOME/Launchers/.asoundrc_pulsealsa $HOME/.asoundrc
pulseaudio --start
if [ ! -z "$1" ]
then sleep 25
fi
killall conky
conky -a bm -x 0 -y 48 -d -c$HOME/Scripts/.conkyrc-time &
conky -a br -x 80 -y 0 -d -c$HOME/Scripts/.conkyrc-cpu &
conky -a bl -x 80 -y 0 -d -c$HOME/Scripts/.conkyrc-memory &
conky -a br -x 400 -y 0 -d -c$HOME/Scripts/.conkyrc-netup &
conky -a bl -x 400 -y 0 -d -c$HOME/Scripts/.conkyrc-netdown &

# ** disabled **
#conky -a br -x 80 -y 0 -d c$HOME/Scripts//.conkyrc-music &

exit
```I use a USB headset for Mangler, which isn't configured for Dmix, as it is considered a separate sound card. to set this, I loaded Mangler and changed it from PulseAudio to ALSA and then selected my headset. you might want to do some other set up depending on how you want things.

---

