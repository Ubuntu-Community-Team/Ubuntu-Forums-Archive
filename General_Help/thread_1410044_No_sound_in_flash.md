---
title: "No sound in flash"
date: 2010-02-18
forum: General Help
---

### Post by ckop64 on 2010-02-18
Hello!
I've been using ubuntu since last year, i've decided to move over KDE, so i choose Kubuntu. The system runs fine, everything looks to be normal, except for 1 thing: I can't getflash to work properly. The sound of my flash player to be exact. 
After I've installed Kubuntu, i immedeately downloaded the flash player, because one thing i regularly do: watch flash movies (youtube, etc.). So I got the flash player, and susprisingly i **had sound.** So, the most important thing was up, so I've downloaded the nVidia graphics driver. It installed fine. After reboot: **sound of flash gone.**
On the restricted drivers page I installed the second option (maybe version 187, and that was the recommended one).
Any ideas?
I didn't have such a problem back in Ubuntu, and I googled pretty much, but none of the methods worked this far. Tried both in Konqueror and Firefox.

---

### Post by prem1er on 2010-02-18
How did you install flash? Did you download from adobe and install manually or did you use the Software Center?

---

### Post by ckop64 on 2010-02-18
> **prem1er said:**
> How did you install flash? Did you download from adobe and install manually or did you use the Software Center?

I used adobe's *.deb.

---

### Post by GamePad64 on 2010-02-18
type in terminal "pulseaudio" and run. Then try to play your flash. Is there sound now?

BTW: If you get message that "Unknown command: pulseaudio" and so on, you should install it:

```
sudo apt-get install pulseaudio
```

---

### Post by BigCityCat on 2010-02-18
One thing that happens in Kubuntu a lot is that the pcm is turned all the way down. If you click on the speaker icon in the task manager and open the mixer. then slide the pcm all te way up. I'm not sure if that is what it is, but look there 1st.

---

### Post by sedawk on 2010-02-18
Most likely I'm suffering from similar effect with a default
Ubuntu with Gnome desktop.
Learn more in the PulseAudio article on Wikipedia:
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

Might be a good time to reactivate my triple-boot configuration
to install/upgrade Fedora to version 12 and see if all my (sound) issues go away ...

---

### Post by ckop64 on 2010-02-18
> **GamePad64 said:**
> type in terminal "pulseaudio" and run. Then try to play your flash. Is there sound now?

BTW: If you get message that "Unknown command: pulseaudio" and so on, you should install it:

```
sudo apt-get install pulseaudio
```

Tried this. 
I hear a little change, some weird sizzle, except, that now nothing has a sound, and kde seems to be gone. I still csan operate windows with alt+tab, and open up a konsole, but thats all.

---

### Post by lovinglinux on 2010-02-19
Open "System Settings >> Computer Administration >> Multimedia >> Audio Output" and put PulseAudio on the top of all options, then click apply.

I also would recommend removing flash and installing it with these instructions:

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by Zorael on 2010-02-19
> **BigCityCat said:**
> One thing that happens in Kubuntu a lot is that the pcm is turned all the way down. If you click on the speaker icon in the task manager and open the mixer. then slide the pcm all te way up. I'm not sure if that is what it is, but look there 1st.
This.

There's really no need to install pulseaudio. (Unless you want to, of course.)

---

