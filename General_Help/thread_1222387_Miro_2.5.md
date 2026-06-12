---
title: "Miro 2.5"
date: 2009-07-24
forum: General Help
---

### Post by Rob_H on 2009-07-24
Miro 2.5 was released today, allegedly with packages for Ubuntu. But has anyone tried following the [instructions]("http://www.getmiro.com/download/for-ubuntu/") to install it? Am I crazy or are the 2.5 binaries missing from that repository? I filed a [bug report]("http://bugzilla.pculture.org/show_bug.cgi?id=12007") on the off-chance I'm not crazy.

---

### Post by jmszr on 2009-07-24
Rob_H,

No, you're not crazy - I received an e-mail from Miro yesterday and tried to install 2.5. I already had the Hardy repository lines among my 3rd party software sources but only 2.0.5 has been available in Synaptic. I imagine that once the developers have had a chance to go over it Miro 2.5 will show up in the updates.

---

### Post by Widby on 2009-07-25
Same here

---

### Post by Rob_H on 2009-07-25
One of the developers addresses it in a [blog entry]("http://bluesock.org/~willg/blog/miro/miro_2_5_ubuntu_packages.html"). Ubuntu packages should be released soon.

---

### Post by volt4ire on 2009-07-28
just as an update, the 2.5.1 package has been released in Miro's Ubuntu repositories. yay :)

---

### Post by crysys on 2009-07-30
Don't install it, it eats files.

To expand, I updated to 2.5.1 from a PPA and after Miro completed the database update I was missing saved watched files from the drive.  It didn't just remove these files from the database, it deleted them from the disk.  I lost half my saved TED talks and movie trailers.  In fact only the two latest movie trailers that I had viewed and saved were left.  It also doesn't seem to touch unplayed files so everything I haven't yet watched is still there.

This has been a big snafu for the 2.5 release and was one of the reasons the 2.5.1 release for Ubuntu was delayed but it still exists.  I'd recommend waiting and perhaps even putting a lock on your Miro version in Synaptic until this has been addressed.

Does anyone know how to recover missing files from a directory? :(

---

### Post by Rob_H on 2009-07-30
Ouch. Does this affect new downloads or just upgraded ones?

---

### Post by crysys on 2009-07-31
It affects any saved file in Miro before the upgrade save for files marked 'new'.  As I said, I have two trailers that survived as 'watched' but I don't know why.  The other dozen or so trailers I saved are gone along with two dozen TED talks and a handful of other media I was holding, science podcasts of interest, tv episodes of particular merit, etc...

I've had Miro lose track of files when moving everything over to a new OS install but it has never deleted the file on disk.  About half the trailers and TED talks I actually have on disk were saved only because they didn't show up in Miros database.  This really sucks because I use that list of trailers to remember which movies I want to go see or rent later.

I'll get over it but I won't trust Miro to take care of my media in the future.

---

