---
title: "No sound after wake from suspend, any help?"
date: 2010-05-07
forum: General Help
---

### Post by inameiname on 2010-05-07
For some reason when I wake my computer up, there is no sound. No matter what I try through the terminal, or by playing with the volume controls, no audio. I can only get audio working again by a restart. 

Does anybody know why, and/or how to fix?

---

### Post by dino99 on 2010-05-07
install paprefs and gnome-alsamixer (tweak it) and ubuntu-restricted-extras

sudo dpkg-reconfigure pulseaudio
sudo apt-get install -f

---

### Post by inameiname on 2010-05-07
I'll try that thanks.

While gnome-alsamixer and ubuntu-restricted-extras are already installed, it's only paprefs that wasn't.

Oddly, it says, "paprefs: Depends: pulseaudio-module-zeroconf but it is not going to be installed", saying that pulseaudio-module-zeroconf is a broken package. Though, when I go into Synaptic Package Manager there is no sign of 'broken' packages. It's proposed solution is to downgrade a few of the pulseaudio things, which I try, and then successfully installed paprefs. And then, "sudo dpkg-reconfigure pulseaudio" and "sudo apt-get install -f" after that. Unfortunately, the sound did not return. I'll have to restart to get sound back.


UPDATE: Okay so I restarted and then set it to suspend, and on resume, the same issue occurred, no audio. Guess that 'downgrade' didn't work I'm afraid.

---

### Post by farchumbre on 2010-05-29
i have exactly the same problem, did you find any solution?

thanks

---

### Post by Spr0k3t on 2010-05-29
Just curious, what is the sound card or is it integrated into the mainboard?

I've seen this happen once before where everything works fine but the issue is the hardware did not receive a "wakeup call".  Does the sound card work after suspend/hibernate using a live disc or usb key?

---

### Post by inameiname on 2010-05-30
&#65279;Unfortunately, no, I haven't found a solution.

Ever since Karmic came out has this issue happen, and ever since then, I have searched and searched for a solution, and none of the potential solutions seem to work.

Apparently Ubuntu Hardy first had this issue, and it was fixed at least in Jaunty, but now it's been back for two releases. Not really sure just what it is.

FYI, I've tried a fair number of solutions that I came across:

- Tweaking '/etc/modprobe.d/alsa-base' and inserted at the end of it 'options snd-hda-intel model=(used all the varieties I could)'

- Adding this in /etc/pm/sleep.d/11suspend:

#!/bin/sh
mixers="Master PCM CD"
for mixer in $mixers ; do
  /usr/bin/amixer -q sset $mixer mute
  /usr/bin/amixer -q sset $mixer unmute
done

- sudo alsa force-reload or sudo /sbin/alsa force-reload or no sudo

- Adding this in /etc/pm/sleep.d/99sound:

#!/bin/sh

case "$1" in
        resume|thaw)
                /sbin/alsa-utils restart
                ;;
esac

- Adding this in /etc/pm/sleep.d/49sound (fyi, it doesn't actually work, but just won't put computer into suspend mode so technically when awake it's just like it was when you last used it):

function kill_sound_apps() {
pidsnd=$(lsof | grep /dev/snd | awk '{ print $2 }')
pidmixer=$(lsof | grep /dev/mixer | awk '{ print $2 }')
piddsp=$(lsof | grep /dev/dsp | awk '{ print $2 }')
kill $pidsnd $pidmixer $piddsp
}

case "$1" in
hibernate|suspend)
kill_sound_apps
modprobe -r snd_hda_intel
;;
thaw|resume)
modprobe snd_hda_intel
;;
*)
;;
esac

exit $?

- Script like this:

sudo /sbin/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

And these are just a few of the many I've tried. None seem to work. 

Oh, and as you may have noticed, my soundcard is snd hda intel, and it's in a Gateway laptop.

Finally, no, I've never checked to see if the problem persists while running a LiveCD. I'll have to try that, both the offical Live CD from the Ubuntu website and my custom made Remastersys Live DVD just to see and get back to everybody on it.

---

### Post by CryingFreeman on 2010-06-09
For my sound card , it seems to work if I click on the sound-icon in the notification area and choose **"Sound settings"** -> **Output-tab** 

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

Then there are two settings to choose from: **Analog output** and **Headphone output**

On resume, the setting is Analog output, and then I choose Headphone output and then switch back to Analog output.

And voilá, there's sound. A workaround that worked for me, it's at least worth a try. :)

---

### Post by Belfry on 2010-06-13
Some sound cards, such as the cs46xx in my Thinkpad a20m, require a suspend script.  I used this in /usr/lib/pm-utils/sleep.d/02Alsa in Hardy (don't forget to chmod 755 the script):
```
 
#!/bin/sh
[ -f /sbin/alsa ] || exit $NA

case "$1" in
    hibernate|suspend)
        /sbin/alsa suspend
        ;;

    thaw|resume)
        /sbin/alsa resume
        ;;

    *) exit $NA
        ;;

esac

```
This doesn't work in Lucid, so another method is needed (which I found [here]("https://help.ubuntu.com/community/SoundTroubleshooting")):
```

#!/bin/sh
[ -f /sbin/alsa ] || exit $NA

case "$1" in
    hibernate|suspend)
        ;;

    thaw|resume)
        /sbin/alsa force-reload
        ;;

    *) exit $NA
        ;;

esac

```
My xfce4-mixer-plugin gets killed so I have to unload the panel before alsa reloads:
```

#!/bin/sh
[ -f /sbin/alsa ] || exit $NA

XUSER=`finger| grep -m1 ":0" | awk '{print $1}'`

export XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/etc/xdg
export XDG_DATA_DIRS=/etc/xdg/xdg-xubuntu:/usr/local/share:/usr/share
export DISPLAY=:0.0
export XAUTHORITY=$(find /var/run/gdm -type d -name  auth-for-$XUSER-*)/database

case "$1" in
    hibernate|suspend)
        su ${XUSER} -c 'xfce4-panel -x' &
        ;;

    thaw|resume)
        /sbin/alsa force-reload
        su ${XUSER} -c xfce4-panel &
        ;;

    *) exit $NA
        ;;

esac

```

---

### Post by inameiname on 2010-06-14
To CryingFreeman:

Thanks for the suggestion, however I don't have a 'Headphone output', only 'Internal Audio Analog Stereo', so I can't use this workaround I'm afraid.

To Belfry:

I'll try out those few tips, and see what happens. I think I have before, along with the many failed attempts to resolve my troubles in the past, but I'll try again just to make sure. 

I use Lucid, and one thing I have tried was that:

/sbin/alsa force-reload

with and without 'sudo' and it didn't work, but we'll see.


UPDATE:

I'm afraid the above method didn't work either. If it helps, my Gateway MT6916 laptop's sound card, according to gnome-alsa-mixer, is SigmaTel STAC9200.

---

### Post by inameiname on 2010-07-09
I just wanted to say that some update just in the past few days has fixed this issue that I've been having this Karmic.

Hopefully it's not a fluke. Seems to be working. I'll mark this as solved anyway.

I'm curious though as to which update it was, and whether it's a fix everybody else who has had this issue too has found as well. 

Feel free to comment on it if you have, or have not.

I also wonder if it's an official update that fixed it, or an update from one of my PPAs. It would be great to know so as to figure out what could change it again if and/or when it happens again in another Ubuntu release. 

Finally!!!!!!!!!!!!

---

### Post by uboltun on 2010-07-15
In addition to alsa force-reload I tried to restore original settings for mixer, but constantly failed. Finally, I found that moving alsa to the end of resume queue helped together with a delayed 'alsactl restore'. This is my fix:

```
cd /etc/pm/sleep.d
mv 50alsa 09alsa
```

change content of 09alsa to this:
```
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload > /dev/null
		sleep 1
		/usr/sbin/alsactl restore 
                ;;
        *) exit $NA
                ;;
esac
```

Something that I am still trying to figure out is how to restart kmix. It is being killed when alsa is restarted , but I could not find a way to start it from inside the resume script.

---

