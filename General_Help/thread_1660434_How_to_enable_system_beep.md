---
title: "How to enable system beep?"
date: 2011-01-05
forum: General Help
---

### Post by suber on 2011-01-05
I've been trying to get the system beep to work but to no avail. The beep does sound on startup and shutdown and at the "beep" command, but doesn't when invoked anyhow from a terminal window or an application.

I've made all the tweaks I'm aware of:

[LIST]
[*]the pcspkr module is loaded
[*]set the bell on using xset b
[*]terminal bell enabled
[*]beep in alsamixer is turned on
[*]gnome keyboard bell mode set to on
[*]bell-style in inputrc is set to visible
[/LIST]
What could be causing the beep muted in the apps or for the entire desktop? Any help would be greatly appreciated.

---

### Post by KJ KJ KJ on 2011-01-05
Well, I think the beep is the work of The Devil, so I spend time trying to persuade other people to turn it OFF for the sanity and goodwill of their colleagues. 

I think there's one you haven't tried.

```

setterm -blength [0-2000]
Sets the bell duration in milliseconds.  Without an argument, defaults to 0.

```

Have you looked in the Sound Preferences to see if the system alert volume is enabled? - it *might* be stomping on the beep. 

As a long shot, if you're using pulseaudio, I'd try a Pulseaudio mixer rather than alsamixer.

---

### Post by suber on 2011-01-05
> **KJ KJ KJ said:**
> Well, I think the beep is the work of The Devil, so I spend time trying to persuade other people to turn it OFF for the sanity and goodwill of their colleagues. 

I think there's one you haven't tried.

```

setterm -blength [0-2000]
Sets the bell duration in milliseconds.  Without an argument, defaults to 0.

```Have you looked in the Sound Preferences to see if the system alert volume is enabled? - it *might* be stomping on the beep. 

As a long shot, if you're using pulseaudio, I'd try a Pulseaudio mixer rather than alsamixer.


The beep can be useful sometimes, like, to notify mail arrival in Evolution, or to run the "echo -e '\a'" command. I'd like to have it working as an option.

I ran
```

setterm -blength 2000

```
and adjusted the alert volume in Sound Preferences to max. Made no difference.

I think I'm using pulseaudio, but not sure. What's the command to open its mixer?

Thanks.

---

### Post by cariboo on 2011-01-05
The pcspkr module is blacklisted in /etc/modprobe.d/blacklist.conf, you may want to remove it from the blacklist and try again.

---

### Post by suber on 2011-01-05
> **cariboo907 said:**
> The pcspkr module is blacklisted in /etc/modprobe.d/blacklist.conf, you may want to remove it from the blacklist and try again.

Yes. I'm aware of that. I did comment out the pcspkr line in blacklist.conf. The module loads at start with no problem. The problem is with that loaded and all the bell options set to on, there is no beep when there should be.

---

### Post by KJ KJ KJ on 2011-01-05
> **suber said:**
> I think I'm using pulseaudio, but not sure. What's the command to open its mixer?

I loathe pulseaudio (I must sound so cantankerous) 'cos ALSA just worked for me in the past. There's a mixer of sorts if you click on the volume control icon in your panel and choose Sound Preferences.

I rummaged around, and all I have under Sound Preferences Hardware is the onboard sound card, there's no PC speaker device. 

Now I haven't done everything you've done to restore the PC speaker, so all I can suggest is you look under Sound Preferences Hardware, to see if your PC speaker shows up.

As a workaround, if you want Evolution to make a nice sound on incoming mail, why not try Evolution | Edit | Plugins | Mail Notification | Configuration ?

---

### Post by suber on 2011-01-05
> **KJ KJ KJ said:**
> I loathe pulseaudio (I must sound so cantankerous) 'cos ALSA just worked for me in the past. There's a mixer of sorts if you click on the volume control icon in your panel and choose Sound Preferences.

I rummaged around, and all I have under Sound Preferences Hardware is the onboard sound card, there's no PC speaker device. 

Now I haven't done everything you've done to restore the PC speaker, so all I can suggest is you look under Sound Preferences Hardware, to see if your PC speaker shows up.

As a workaround, if you want Evolution to make a nice sound on incoming mail, why not try Evolution | Edit | Plugins | Mail Notification | Configuration ?

I'm using ALSA, will skip tweaking Pulse. Yes, Evolution can play a nicer sound than beep, but beep works without speakers.

Btw, do you happen to know where the gnome config files are located? It seems to me using the gconf-editor to tweak the bell settings under /desktop/gnome/peripherals/keyboard can cause the beep not work properly. If the bell_custom_file can be fixed to work, one may even get a softer sound instead of beep.

---

### Post by Splat_NJ on 2011-01-11
Wondering if the OP got this working? I'm getting no system beep either, though I have everything seemingly set correctly.

---

### Post by Awareness on 2011-01-28
Yep, i wonder as well :)

---

### Post by suber on 2011-01-28
No, I didn't get it to work. Probably it's in the kernel. Didn't try to delve further. It'd be nice to have the beep working as something you can turn on and off.

---

### Post by Splat_NJ on 2011-01-28
Actually, I should have replied back here. I did get the system beep working for my application. See my post [here]("http://ubuntuforums.org/showthread.php?t=1665513").

---

### Post by Awareness on 2011-01-29
> **Splat_NJ said:**
> Actually, I should have replied back here. I did get the system beep working for my application. See my post [here]("http://ubuntuforums.org/showthread.php?t=1665513").

Well, sudo apt-get install beep and then using the program from the command line, does work for me, but when i ping -a does not :(

I had to remove pcspkr from the modules blacklist so it is able to load. A single place to enable and disable would be nice :)

---

