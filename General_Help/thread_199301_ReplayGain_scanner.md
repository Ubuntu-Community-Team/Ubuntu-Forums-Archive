---
title: "ReplayGain scanner?"
date: 2006-06-18
forum: General Help
---

### Post by Cable on 2006-06-18
Is there a Linux ReplayGain scanner?  If so, what is it?  I'd prefer some form of frontend, because I have no idea how to use a command line scanner.  Further, I don't even *have* a command line scanner.  If there's no frontend scanner, what should I use?

I'd be willing to use a command line scanner though.  Are there sites I should look at to learn how to use it if that's what I'll need to do?

---

### Post by Demosthenes on 2006-06-18
You can use amaroK and the amarok_replaygain script (install it in the script manager in amaroK) to allow amaroK to scan replaygain.  You will need the neccessary dependencies, the script description tells you what you need for the types of files you have.

I haven't used it myself to scan my files, but I do use it when playing back my music with replaygain tags.  It's not perfect but it is the best I've found under linux.

---

### Post by skralljt on 2006-10-09
Does that script install replaygain itself?  Because in the dependencies it says that replaygain must be installed, yet I don't see replaygain in the synaptic package manager....

---

### Post by Demosthenes on 2006-10-09
The script does not install replaygain.  You will need a different tool for each type of file you use. Musepack (.mpc) uses replaygain, since musepack is not commonly used replaygain itself hasn't made it to the repositories yet.

All the necessary programs are mentioned in the amarok script about dialog, in amarok script manager.   You will need, for instance: vorbis-tools (or vorbisgain) for ogg, mp3gain for mp3s, flac for flac etc. You may also need id3v2.

You should be able to get all of these off synaptic.

---

