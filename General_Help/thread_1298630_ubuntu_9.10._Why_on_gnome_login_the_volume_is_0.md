---
title: "ubuntu 9.10. Why on gnome login the volume is 0"
date: 2009-10-23
forum: General Help
---

### Post by odror on 2009-10-23
Each time that I log in gnome start with volume 0.
Where can I change this default.

-Thanks

---

### Post by SunnyRabbiera on 2009-10-23
does sound work afterward, or are you just getting no sound?

---

### Post by prshah on 2009-10-23
> **odror said:**
> Each time that I log in gnome start with volume 0.
Where can I change this default.

Log in as usual, setup your volume controls to your satisfaction. Then, open a terminal, and give the command```
sudo alsactl store 0
sudp cp -p /etc/asound.state .
```.

This will store your current sound settings to a file in /etc/asound.state, and create a copy of that file in your home directory.

You can now reboot and check if the saved values  "stick". If they don't try reloading the saved settings with the command```
sudo alsactl restore
``` Your saved sound settings should be loaded immediately.

If they don't, you may not have permissions on /etc/asound.state, or the file itself may be marked immutable.

In this case, copy back the asound.state file saved in your home directory, then restore: ```
sudo cp -p asound.state /etc/asound.state && alsactl restore
``` If this works, then you need to check why your asound.state file is getting replaced on every bootup.

You can copy your custom asound.state file to /etc, and make it immutable (unchangeable) with the command```
sudo chattr +i /etc/asound.state
``` WARNING: With this, your laptop will always START with the custom set volume levels; you can adjust the settings, but they will not be "remembered" across reboots.

If nothing works, please post back the output to the following commands```
locate asound.state
sudo lsattr /etc/asound.state
sudo ls -l /etc/asound.state
```

---

### Post by odror on 2009-10-23
I will try your method later this evening.

Why it has to be so complicated, There should be a gui for that.

-Oz

---

### Post by directcharitycontribution on 2009-10-23
Why not status information first? > **prshah said:**
>  the output to the following commands```
locate asound.state
sudo lsattr /etc/asound.state
sudo ls -l /etc/asound.state
```

---

### Post by odror on 2009-10-24
I do not have the file /etc/asound.state

How do I generate it.

-Thanks

---

### Post by bpeyser on 2009-11-08
I have the same problem--sound is at 0 (muted) when I log in, always. What I was thinking is that I could have asound.state updated at logout every time. That way when I log in it will be as I left it.

Before I try this, I wanted to find out more about asound.state. I have a file with that name, but it is not in /etc/

```
$ locate asound.state
/var/lib/alsa/asound.state

$ less /var/lib/alsa/asound.state
state.Intel {
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Master Playback Volume'
                value.0 12
                value.1 12
        }
....(snip)

```

Now that looks to me as though the file thinks my Master Playback Volume should be 12 for left and right. However, when I log in the volume is always 0 (muted). if I put the asound.state file I have in /etc/ should it start at volume 12?

And what do you think about running 'sudo alsactl store 0' as suggested by prshah at every logout? Is there a way to have it save to /etc/ instead of copying it there afterward? I may just monkey around with this and see what I get, but thought it would be good to ask first.

Thanks,

bpeyser

---

### Post by bpeyser on 2009-11-17
Seems like it's mostly fixed now--here's what I did:

I went to the menu, System -> Preferences -> Startup Applications
and I added an application with the following command line:

```
alsactl restore 0
```

It defaults to /var/lib/alsa/asound.state so it reads my file. I think this is working correctly, though the volume at the login screen is whatever the setting was two logouts ago. I don't restart a lot so I'm not sure this is solid, but seems to be better than it was.

-bpeyser

---

### Post by prshah on 2009-12-16
Very sorry to bring up this old thread again, but...

I recently ran into this problem on a system, and here is what I did for a permanent fix (sticks even across kernel upgrades).

Problem: Volume settings are not remembered across reboots. Jack settings (re-assignments of line-in and mic to line-out) are not remembered.

Solution: (Possibly only one of many).

a) First, I deleted any existing asound.state files (Warning this command is risky, please be careful):```
sudo updatedb && sudo rm `locate asound.state`
```

b) After this, I used alsamixer from the command line to setup the volume and jack assignments. Then, I used the alsactl command to save the settings.```
sudo alsactl store
```

c) A search for asound.state showed that it existed in /var/lib/alsa/; rather than move it to /etc (where I think it is looked for in Ubuntu), I just linked it```
sudo ln -s /var/lib/alsa/asound.state /etc/asound.state
```

```
Wed Dec 16 13:35:47 ~:$ sudo updatedb && locate asound.state
/etc/asound.state
/var/lib/alsa/asound.state

```

After this, the volume and line (jack) settings are persistent across reboots, logouts, etc.

Just an attempt to bring some clarity.

---

### Post by rickabillie on 2010-07-29
Hmmm,
I tried all of the above but I still get all of the sliders (had unchecked all but three) when I reboot, though it does save my volume level.

Any Ideas on how to get just the sliders I want to appear?

/Rickabillie

---

