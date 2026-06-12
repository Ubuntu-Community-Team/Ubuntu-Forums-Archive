---
title: "How do I install a package from an alternate repo if it exists in an Ubuntu repo?"
date: 2010-01-14
forum: General Help
---

### Post by mjpatey on 2010-01-14
I'm trying to install a specialized version of ffmpeg from the Medibuntu repository.  The problem is, a version of ffmpeg already exists in the main Ubuntu repository.  So even with Medibuntu added, when I do a "sudo apt-get install ffmpeg", it installs from the Ubuntu repository, not Medibuntu.

I can't believe I don't know how to do this yet, as I've been an active user of Ubuntu as my only OS since 6.06... but I've never come across this.  How do I tell Ubuntu to install the version from Medibuntu rather than the main distro repository?  "man apt-get" doesn't seem to list any options for specifying a particular repository.

Thanks for any light you can shed!

-Mark

---

### Post by warfacegod on 2010-01-15
I think you need to go into Synaptic> Settings> Preferences> Distribution tab and select prefer highest version. Assuming your package is a higher release version number. Then look for it in Synaptic.

---

### Post by mjpatey on 2010-01-15
Thanks!  For some reason, I'm not seeing the package I need... but your method seems perfect.  Now I just need to figure out what I really need, if there is no special ffmpeg in Medibuntu!

---

### Post by warfacegod on 2010-01-15
What exactly are you looking to do?

---

### Post by mjpatey on 2010-01-15
I'm running a video editor called OpenShot, and it uses ffmpeg as its playback and encoding engine.  The standard ffmpeg available in Ubuntu doesn't fully support .3gp files, and this causes them to play out of sync (video much faster than audio), making video editing impossible.  The sync issues are also present in the final render, so essentially, 3gp files can't be worked with at all.

So it was recommended that I switch to the ffmpeg that's available in Medibuntu, as it includes full support for 3gp files.  Only problem is, when I use Synaptic to search for ffmpeg in the Medibuntu repository, nothing turns up.

I think I'm just going to try installing the latest ffmpeg from source, unless there's another, easier way.

---

### Post by it_fixxer on 2010-01-15
Take a look here for hoe to add the repo.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hope it helps

---

### Post by mjpatey on 2010-01-15
Thanks, I already had it enabled, but ran the mini-script to enable it again, just in case it had been broken by any recent updates.  Unfortunately, ffmpeg still isn't showing under Medibuntu.

But I'm heading to the OpenShot site to see if anybody there can enlighten me... this ffmpeg issue has been problematic for them for a long time (one PPA they set up caused all media players to lose a lot of their video playback capability because of the odd ffmpeg version OpenShot was using, or the way it was being used... or something).

I really do hope they get this stuff worked out, because it's a nice up-and-coming piece of software other than this mess.

---

### Post by warfacegod on 2010-01-15
Nice keyboard.

If you get it installed from a ppa, I think you'll need to tell Synaptic to prefer the installed version so it doesn't get replaced when you update.

---

