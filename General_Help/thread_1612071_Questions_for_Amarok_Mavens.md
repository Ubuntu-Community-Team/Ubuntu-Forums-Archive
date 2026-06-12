---
title: "Questions for Amarok Mavens"
date: 2010-11-02
forum: General Help
---

### Post by Curbuntu on 2010-11-02
It's time to join the 21st Century.  My wife and I have 400-500 CDs, way more than will fit in our Sony 200-CD changer/player.  It's time to digitize the whole collection and put it on its own server.  I'm looking for an Ubuntu-based music manager/player, and (based on touted features), I'm guessing Amarok is it.  But here are three questions generated from problems or frustrations I've encountered so far:


[LIST=1]
[*]While other music players can generate sound (e.g., Rhythmbox, Banshee), I can't get sound working in Amarok under Ubuntu 10.04.1.  Yes, I know that Amarok is technically a KDE-based product, but I run other KDE-based products (most notably K3B) under Ubuntu without a hitch.  **Am I running into some sort of problem with ALSA/PulseAudio here?**
[*]What is the Amarok music file structure?  Because we have digitized a few dozen CDs (on my wife's soon-to-be-converted WinXP box), I want to be able to transfer current music over in a format Amarok will understand.  I just imported a Christmas CD (soon 'twill be the season, so why not start the process with those CDs?), but Amarok stored the tracks in a strange way:
[LIST=1]
[*]First by creating five *language *folders (e.g., English, French, Czech, Danish, "Traditional American");
[*]Next, under each language folder, creating a folder based on the album name;
[*]Lastly, storing the FLAC tracks under whatever language folder it decided should be used.
[/LIST]
 
[/LIST]
[INDENT]Even stranger to say -- all the carols on this album are sung in English (though some tunes may have come from various European countries originally).  So **what organizational strategy is Amarok using?**
[/INDENT][INDENT]3. Lastly, even when Amarok rips the CDs, storing the tracks in the default folder, it keeps reporting that there is no music in its collection.  **What am I overlooking here?**[/INDENT]Thanks in advance.

---

### Post by Mamarok on 2010-11-03
What is Mavens?

Now the answers for your question:

1. Amarok uses Phonon and the xine backend by default, so you need to install the 'kubuntu-restricted-extras' to get the appropriate codecs to read mp3 files

2. I don't really understand what you mean by file structure, but if this is about the folder structure you can use whatever structure you want, as Amarok writes it's own database reading the id3 tags of the files. In absence of id3 tags it will display the file name.

As for file formats: Amarok can read pretty much every audio file format supported by Taglib, so whether you use mp3, ogg, flac or wav doesn't matter, except for the compression quality of course. All you need are the codecs for those file formats which you should have if you install the package I mentioned under 1.

The folder organisation you mention is certainly not done by Amarok, I have never seen such a behavior, and it certainly doesn't create any language folders. Usually, if you copy music to collection (which is the correct way to import music in an existing database) it will display a dialog where you choose yourself the folder structure you want.

3. If you don't see any entries in the database, then you are probably lacking the necessary MySQL packages, which is a packaging problem in Ubuntu 10.04 only found with Gnome and Xfce users. Under KDE it installs the MySQL packages correctly. You should make sure you have all recent updates, that should have been fixed quite some time ago. If that doesn't help I suggest you get the most recent Amarok version, see also [http://kubuntu.org/news/amarok-232-backports-ppa](http://kubuntu.org/news/amarok-232-backports-ppa) This is in the Kubuntu-backports-PPA which is supported by the Kubuntu project members and community.

For more information and help with KDE applications I also suggest you ask in the official KDE forum at [http://forum.kde.org](http://forum.kde.org) where you can talk directly to the KDE developers and community.

---

