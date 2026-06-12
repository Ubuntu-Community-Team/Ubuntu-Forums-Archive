---
title: "Annoying Drum Sound at Startup"
date: 2010-07-06
forum: General Help
---

### Post by Whisp3r on 2010-07-06
How do I remove that annoying drum sound from the login screen?

I went to PREFERENCES -> LOGIN SCREEN, but there are no tabs or boxes for sound. Only options to determine who I want to log in. 

I tried GCONF-EDITOR, and drilled down to /apps/gdm/simple-greeter/settings-manager-plugins/sound/active and unchecked the active box, rebooted, but it still plays that stupid sound. And the box is unchecked if I check it!

Any thoughts? I've tried the solutions in the forum and nothing seems to kill that annoying sound.

I'm still on 9.10 right now, since 10.04 has a nasty screen flicker problem.

---

### Post by Rubi1200 on 2010-07-06
Try this:

System > Preferences > Startup Applications and either uncheck or remove GNOME login sound

---

### Post by SoFl W on 2010-07-06
I remember I removed it with one version, but was unable to remove it with another.  
Did you try System-> Admin-> Startup Applications-> GNOME Login Sound?

But I do remember that I also had a problem, had two machines, two versions, played the sound on one machine, didn't on the other.

---

### Post by Whisp3r on 2010-07-06
> **Rubi1200 said:**
> Try this:

System > Preferences > Startup Applications and either uncheck or remove GNOME login sound

That works for getting rid of the sound when you log in, but not that annoying drum sound when the login window pops up.

---

### Post by Whisp3r on 2010-07-06
> **Whisp3r said:**
> That works for getting rid of the sound when you log in, but not that annoying drum sound when the login window pops up.

Well, I solved it. I went into /usr/share/sounds/ubuntu/stereo and removed the system-ready.ogg. Too bad there's not a easier way to kill off that sound. Kudos!

---

### Post by mike555 on 2010-07-06
To turn off the (drum-roll) system ready sound while keeping the ability to turn it on again whenever you wish, enter the following into Applications => Accessories => Terminal:
      sudo mv /usr/share/sounds/ubuntu/stereo/system-ready.ogg /usr/share/sounds/ubuntu/stereo/system-ready-off.ogg

---

### Post by Sonsum on 2010-07-07
Does anybody know how to change this sound?

I thought replacing the file would do the trick, but it's still the drum noise :(

---

### Post by Noz3001 on 2010-07-07
I'm sure you can do this by clicking the sound icon and clicking Sound Preferences

---

### Post by KdotJ on 2010-07-07
> **Noz3001 said:**
> I'm sure you can do this by clicking the sound icon and clicking Sound Preferences

I think this only allows you to change the sound themes. Such as when you click on stuff or when error dialog boxes pop up

---

### Post by Noz3001 on 2010-07-07
> **KdotJ said:**
> I think this only allows you to change the sound themes. Such as when you click on stuff or when error dialog boxes pop up

I recall turning it off to get rid of the drum sound.

---

### Post by Strongman332 on 2010-07-07
just rename another file and place it n that folder, after renaming the original

---

### Post by Sonsum on 2010-07-07
> **Strongman332 said:**
> just rename another file and place it n that folder, after renaming the original

I actually found the solution. Unless you edit some gconf file or something, you have to change the file in the ubuntu sound folder, I was doing it in the sound folder of another sound theme.

My solution was to just disable that sound and change the login noise. Two sounds so close to each other is a little redundant!

---

### Post by AMTQ on 2010-10-25
> **Whisp3r said:**
> Well, I solved it. I went into /usr/share/sounds/ubuntu/stereo and removed the system-ready.ogg. Too bad there's not a easier way to kill off that sound. Kudos!

Thank you very much for the solution Whisp3r! 
The internet is full of people who believe that there must be an easy and intuitive way to do this (so do I believe myself!), but it seems that they are wrong...

---

### Post by Scunnered on 2010-10-25
**Noz3001** got the answer in one. 

It is simplicity - change sound theme to No Sounds and all works well. No need to mess about with anything else

---

### Post by John Peschken on 2011-07-26
> **Rubi1200 said:**
> Try this:

System > Preferences > Startup Applications and either uncheck or remove GNOME login sound

Good grief.  For months, I have been looking for it under everything I could find related to sound.   Thank You!

Am I the only one who never would have thought to look under start up applications?

---

