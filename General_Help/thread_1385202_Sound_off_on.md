---
title: "Sound off/ on"
date: 2010-01-19
forum: General Help
---

### Post by Robbyx on 2010-01-19
Is there a program that I can put infront of skype command line in the start program icon,  to turn on the sound when I start skype and turn it off when I exit. If not a simple toggle icon would suffice. 

In order for skype to be clear I have to have the volume up. This gives a background hiss. I do not like the hiss especially when  I am not using skype.

---

### Post by nigel_nb on 2010-01-20
Create a file called increase.sh.  Inside increase.sh, put
```
amixer -c 0 sset Master 100%
```

Then from terminal (make sure you are in the same directory as the script type)
```
$: chmod a+x increase.sh
```

Create another file called decrease.sh.  Inside decrease.sh, put
```
amixer -c 0 sset Master 50%
```

Then from terminal (make sure you are in the same directory as the script type)
```
$: chmod a+x decrease.sh
```

Now right click on the panel and click on 'Add to panel' and add a Launcher.  Select the increase.sh script as the program to run and tick 'run in terminal'.  Repeat for decrease.sh and you'll have something that will automatically reduce and decrease the volume.

In case you want to decrease the volume of something other than Master, then type ```
alsamixer
``` observe the output for the names inside single quotes like 'Master', 'Speaker', etc and replace Master in the script above with appropriate names.

---

### Post by Robbyx on 2010-01-20
Thank you very much for your guidance and help.

---

### Post by Robbyx on 2010-01-31
I found pulseAudio so difficult to control that I removed it. I am now using Alsa Mixer with very good results. One problem remains. Everytime the machine goes into suspend it mutes the mic volume and it stays that way when it wakes up. 

When I follow your Alsamixer command this is what I get:

```
b@rob-desktop:~$ alsamixer
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
rob@rob-desktop:~$ alsamixer
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
rob@rob-desktop:~$ 
```

What I intended to do was to ask for help with a script which tested if the mic was muted and then switched it on. Is that possible? After the mute test I would like to include in the script a run skype command.

---

