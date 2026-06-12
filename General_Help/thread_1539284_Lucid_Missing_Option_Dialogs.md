---
title: "Lucid Missing Option Dialogs"
date: 2010-07-26
forum: General Help
---

### Post by VH-BIL on 2010-07-26
Is there a sound dialog I can download for Lucid that will allow me to switch between Pulse, ALSA, etc. like in earlier Ubuntu distributions.

Also is there a dialog that allows me to change the GDM login theme like in earlier Ubuntu distributions. I know I can change the GTK2 control set and background wallpaper but how do I change the login theme?

Isn't Linux about options and freedom?

---

### Post by robsoles on 2010-07-31
BUMP (I might be back with an answer to one or both questions *sometime* but in the meantime I reckon there is no harm showing everyone else the question again!)

---

### Post by VH-BIL on 2010-07-31
That would be great, thanks...

---

### Post by VH-BIL on 2010-08-01
Are you having any luck with this? I have googled this with not luck...

---

### Post by robsoles on 2010-08-01
> **VH-BIL said:**
> Is there a sound dialog I can download for Lucid that will allow me to switch between Pulse, ALSA, etc. like in earlier Ubuntu distributions.

...

I've tried at least a little to prove myself wrong about what I thought is going on, as far as PULSE and ALSA are concerned, and I don't seem to be able to.

To the best of my understanding PULSE relies on ALSA to play (audibly) the clever clever things it can play.

Checkout the 'pacmd' response to 'list-sinks' ( [http://en.wikibooks.org/wiki/Configuring_Sound_on_Linux/Pulse_Audio/Testing](http://en.wikibooks.org/wiki/Configuring_Sound_on_Linux/Pulse_Audio/Testing) ) and it seems fairly certain to me that you cannot really choose between them - no doubt you could remove PULSE if you really wanted to and probable that previous versions of OS were offering to bypass it for the user.


> **VH-BIL said:**
> ...

Also is there a dialog that allows me to change the GDM login theme like  in earlier Ubuntu distributions. I know I can change the GTK2 control  set and background wallpaper but how do I change the login theme?

Hardly a dialog but does [http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13) do what you want neatly enough?

---

### Post by VH-BIL on 2010-08-01
> **robsoles said:**
> ...no doubt you could remove PULSE if you really wanted to and probable that previous versions of OS were offering to bypass it for the user.
I have tried this previously and lost my sound cards, aplay -l returned nothing. Even installing pulse did not solve this problem. There used to be a dialog that enabled you to disable pulse. My problem is Enemy Territory Quake Wars audio is way out of sync since Lucid Lynx. I have been trying to find information about the new 10.04.1 to see if this fixes the bug in Pulse.


> **robsoles said:**
> Hardly a dialog but does [http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13) do what you want neatly enough?
No this is just changing the background and the GTK controls not the login theme. [URL="> **robsoles said:**
> ...no doubt you could remove PULSE if you really wanted to and probable that previous versions of OS were offering to bypass it for the user.
I have tried this previously and lost my sound cards, aplay -l returned nothing. Even installing pulse did not solve this problem. There used to be a dialog that enabled you to disable pulse. My problem is Enemy Territory Quake Wars audio is way out of sync since Lucid Lynx.


> **robsoles said:**
> Hardly a dialog but does [http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13) do what you want neatly enough?
No this is just changing the background and the GTK controls not the login theme as in http://gnome-look.org/index.php?xcontentmode=150&PHPSESSID=d9dfd07c72ed1e42298cf5da345199f6"]_Check this site_[/URL]

---

### Post by robsoles on 2010-08-01
The link in your post is a bit broken but I got to your target anyway: [http://gnome-look.org/index.php?xcontentmode=150](http://gnome-look.org/index.php?xcontentmode=150)

Consensus seems to be that installing those themes isn't supported in 10.04 but the amount of noise out there about it makes me think someone (and probably a couple more 'someones') must be working on an installer for themes - pretty sure the structure has changed so much it will be painful to deliver something that will install older themes without some deal of conversion.


Have you found or submitted a bug report over the problem you experience with Pulse?

---

### Post by Seeked on 2010-08-01
If you want to modify the login appearance you can work with GDM... see the attached PDF

---

### Post by VH-BIL on 2010-08-01
> **robsoles said:**
> Have you found or submitted a bug report over the problem you experience with Pulse?

There is already a report, I just added a +1.

---

### Post by robsoles on 2010-08-01
> **Seeked said:**
> If you want to modify the login appearance you can work with GDM... see the attached PDF

LOL, your PDF is a simile of the link I gave VH-BIL in post #5 to this thread.

---

