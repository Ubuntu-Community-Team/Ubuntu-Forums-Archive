---
title: "Playing movie doesn't disable monitor power off"
date: 2011-11-02
forum: General Help
---

### Post by ene_dene on 2011-11-02
I just installed Kubuntu 11.10. I was watching a movie in Dragon Player and the monitor turned off after 10minutes. Is there a way to make Kubuntu disable shutting down monitor after given time if movie player is on? I want my monitor to suspend if I'm not using a computer, but not if I'm watching a movie, and this works fine in Ubuntu, but I was surprised to see this not working in Kubuntu.
Any solutions?

---

### Post by mister_playboy on 2011-11-05
I'm also interested in this topic... digging around in System Settings > Power Management doesn't give any options like "disable screen sleep when program X is running."

---

### Post by ene_dene on 2011-11-06
> **mister_playboy said:**
> I'm also interested in this topic... digging around in System Settings > Power Management doesn't give any options like "disable screen sleep when program X is running."
VLC works.

---

### Post by mister_playboy on 2011-11-11
> **ene_dene said:**
> VLC works.

My screen will certainly turn off while a movie is playing in VLC.

---

### Post by aeronutt on 2011-11-11
> **mister_playboy said:**
> I'm also interested in this topic... digging around in System Settings > Power Management doesn't give any options like "disable screen sleep when program X is running."

This would be a great option.

---

### Post by teamanx on 2011-11-20
Smplayer (and any other MPlayer based app) will inhibit power saving while playing (works on Kubuntu 11.10).

---

### Post by linuxrev on 2011-11-28
> **mister_playboy said:**
> My screen will certainly turn off while a movie is playing in VLC.

+ In VLC go to Tools > Preferences
+ Switch to full preferences view ('All' button bottom left)
+ Click 'Advanced' tab and check 'Inhibit the power management daemon during playback'

That surely works on my machine.

---

### Post by ankspo71 on 2011-11-29
Hi,
Depending on the country, some monitors (like the ones I've used) have a built in power saving option called Energy Star, and they work independently from the screensaver settings. If your monitor has Energy Etar too then you can try the following:

Open a terminal and type this command to check the status of Energy Star:
```
xset q
```

You should see results that say this:
```
DPMS (Energy Star):
  Standby: 600    Suspend: 900    Off: 1200
  DPMS is Enabled
  Monitor is On
```

To turn DPMS off, use this command:
```
xset -dpms
```

To turn DPMS back on again, you can use this command:
```
xset +dpms
```

These changes are only temporary, so if you need to make the change permanent, you could put the "xset -dpms" command at the bottom of the hidden .bashrc file inside your home folder.

---

