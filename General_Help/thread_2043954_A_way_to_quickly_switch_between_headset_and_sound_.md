---
title: "A way to quickly switch between headset and sound card??"
date: 2012-08-17
forum: General Help
---

### Post by BlackoutWorm on 2012-08-17
Hello. I just installed ubuntu studio, and love it.
But one very annoying thing is that I have to use pavucontrol to switch manually between headset and sound card.
Is there a more officiant way to do this?
Maybe a way to make it switch automatically like it does in Windows?
Or maybe a keybinding solution? I already use amixer's keybinders to increase and decrease the volume.
Are there any alternatives at all?
Doesn't matter if I use also or pulse as long as there's a solution for this.
Thanks in advance.

---

### Post by xianbei on 2012-08-17
if you open the sound settings window with both devices active, do you see both devices?

there's probably a way to set a system keyboard shortcut to toggle between the option.

enter more experienced linux user...

---

### Post by BlackoutWorm on 2012-08-18
> **xianbei said:**
> if you open the sound settings window with both devices active, do you see both devices?

there's probably a way to set a system keyboard shortcut to toggle between the option.

enter more experienced linux user...

You mean in settings manager? There's no Sound option there.
Or do u mean pavucontrol or the the xfce4-mixer?
Still can't see the option.
Why are there so many different applications for this?
I wish the was a way to make all sound devices be recognized as the same device like you can in windows. 

But please explain what to do here.
It doesn't matter if it's pulse, alas or whatever I have to install or tweak. I just want this to work.

EDIT: I've successfully been able to add shortcuts for the sound card (amixer sset PCM 10+ and amixer sset PCM 10-), but they don't work for my headphones, and I still need to use pulse volume control or pavucontrol to switch between them two. Is there a shortcut for that somewhere? From what I can see, amixer can not switch between devices
I can't believe it has to be that hard.

---

### Post by BlackoutWorm on 2012-08-19
**bump**

---

### Post by BlackoutWorm on 2012-08-20
I'm finally able to switch between headphones and the built in sound card from keyboard shortcuts using pacmd terminal commands.
```
pacmd -set-default-source "alsa_output.usb-Plantroeless_Audio_Plantronics_Wireless_Audio-00-Audio.analog-stereo.monitor"
```
But I've still not figured out why the volume up/down shortcuts stops working when I use the headphones.
It's really frustrating, as I've spent a lot of time googleing and trying different things.
If you guys can help, please do:)

---

### Post by brainwash on 2012-08-21
> **BlackoutWorm said:**
> But I've still not figured out why the volume up/down shortcuts stops working when I use the headphones.
The volume keys are managed by the daemon **xfce4-volumed**. You will have to change the value of the current active sound card via **xfconf-query** (or the Xfce Settings Editor):

[https://bugs.launchpad.net/xfce4-volumed/+bug/883485/comments/3](https://bugs.launchpad.net/xfce4-volumed/+bug/883485/comments/3)
[https://wiki.archlinux.org/index.php/Xfce#Xfce4-volumed](https://wiki.archlinux.org/index.php/Xfce#Xfce4-volumed)

---

### Post by stinkeye on 2012-08-21
> **BlackoutWorm said:**
> Hello. I just installed ubuntu studio, and love it.
But one very annoying thing is that I have to use pavucontrol to switch manually between headset and sound card.
Is there a more officiant way to do this?
Maybe a way to make it switch automatically like it does in Windows?
Or maybe a keybinding solution? I already use amixer's keybinders to increase and decrease the volume.
Are there any alternatives at all?
Doesn't matter if I use also or pulse as long as there's a solution for this.
Thanks in advance.
I use this script I came across to switch sound output.
```
#!/bin/bash

declare -i sinks=(`pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sinks_count=${#sinks[*]}
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_sink_index=${sinks[0]}

#find the next sink (not always the next index number)
declare -i ord=0
while [ $ord -lt $sinks_count ];
do
    echo ${sinks[$ord]}
    if [ ${sinks[$ord]} -gt $active_sink_index ] ; then
        next_sink_index=${sinks[$ord]}
        break
    fi
    let ord++
done

#change the default sink
pacmd "set-default-sink ${next_sink_index}"


#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
    
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $(( $ord % $sinks_count )) -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high --hint=string:x-canonical-private-synchronous: "Sound output switched to" "$line"
        exit
    fi
    let ndx++
done;

```

It works but sometimes I have to click more than once to get to the right output.
Don't really understand the script or pulse-audio.
I think it must list more than 2 outputs when I'm running some audio programs.

---

### Post by BlackoutWorm on 2012-08-21
Thanks a lot, man. Btw, the workaround to be on the correct output is to disable what you don't use.
So in my case, I only have the built in and usb headphones enabled.
Works like a charm.
And I found a workaround for the keybindings too.0
```
#!/bin/bash
 
SINK_NAME="alsa_output.pci-0000_00_1b.0.analog-stereo"
VOL_MAX="0x20000"
STEPS="16" # 2^n
VOL_STEP=$((VOL_MAX / STEPS))
 
VOL_NOW=`pacmd dump | grep -P "^set-sink-volume $SINK_NAME\s+" | perl -p -i -e 's/.+\s(.x.+)$/$1/'`
MUTE_STATE=`pacmd dump | grep -P "^set-sink-mute $SINK_NAME\s+" | perl -p -i -e 's/.+\s(yes|no)$/$1/'`
 
function plus() {
        VOL_NEW=$((VOL_NOW + VOL_STEP))
        if [ $VOL_NEW -gt $((VOL_MAX)) ]; then
                VOL_NEW=$((VOL_MAX))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
}
 
function minus() {
        VOL_NEW=$((VOL_NOW - VOL_STEP))
        if [ $(($VOL_NEW)) -lt $((0x00000)) ]; then
                VOL_NEW=$((0x00000))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
}
 
function mute() {
        if [ $MUTE_STATE = no ]; then
                pactl set-sink-mute $SINK_NAME 1
        elif [ $MUTE_STATE = yes ]; then
                pactl set-sink-mute $SINK_NAME 0
        fi
}
 
function get() {
        BAR=""
        if [ $MUTE_STATE = yes ]; then
                BAR="mute"
                ITERATOR=$((STEPS / 2 - 2))
                while [ $ITERATOR -gt 0 ]; do
                        BAR=" ${BAR} "
                        ITERATOR=$((ITERATOR - 1))
                done
        else
                DENOMINATOR=$((VOL_MAX / STEPS))
                LINES=$((VOL_NOW / DENOMINATOR))
                DOTS=$((STEPS - LINES))
                while [ $LINES -gt 0 ]; do
                        BAR="${BAR}|"
                        LINES=$((LINES - 1))
                done
                while [ $DOTS -gt 0 ]; do
                        BAR="${BAR}."
                        DOTS=$((DOTS - 1))
                done
        fi
        echo "$BAR"
}
 
case "$1" in
        plus)
                plus
        ;;
        minus)
                minus
        ;;
        mute)
                mute
        ;;
        get)
                get
esac
```

I use one for the built in device and one for my headphones.
As you can see, the commands are **filename plus**, **filename minus** and **filename mute**

So make the scripts executable and add them to the startup session.

I have no idea why pulseaudio doesn't include these features by default. It's so stupid.
But okay, Thanks a lot, guys:)

---

### Post by stinkeye on 2012-08-21
> Btw, the workaround to be on the correct output is to disable what you don't use.
How do I disable the S/PDIF output.
My normal sound settings shows 3 outputs while pavucontrol
only shows 2.

---

### Post by BlackoutWorm on 2012-08-21
> **stinkeye said:**
> How do I disable the S/PDIF output.
My normal sound settings shows 3 outputs while pavucontrol
only shows 2.
From your BIOS.

If you can't find it there or if your bios doesn't allow that, add it to /etc/modprobe.d/blacklist.conf.
The exact name should show up in **paman**.
Hope that helps

---

