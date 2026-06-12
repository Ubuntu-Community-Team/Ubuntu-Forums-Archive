---
title: "MHT reader for GNOME"
date: 2006-04-26
forum: General Help
---

### Post by saurabhnanda on 2006-04-26
Hi,

I have a whole lot of these .mht files (written by IE) and want to view them in GNOME. Any application that would let me do that? Preferably integrated with Nautilus so that I can read off a samba share.

TIA
Nandz.

---

### Post by mahoodlum on 2006-07-21
I would like to do the same, have you figured out a work around? Opera claims that it will open them but to no avail, I have opened them in IE on another computer, but I need the files to work on gnome.

---

### Post by Ted_Smith on 2006-07-30
sudo apt-get install kmhtconvert

Works a treat :-)

---

### Post by beameup on 2006-08-24
It's a KDE app. Any probs using it in GNOME?

---

### Post by saurabhnanda on 2006-08-24
I would need to install a *lot* of KDE libs just for one app!

---

### Post by beameup on 2006-08-24
OK what about this FF plugin?
 [http://maf.mozdev.org/](http://maf.mozdev.org/)

I'm at work on Windows and IE, so I can't try it.

---

### Post by beameup on 2006-08-24
Nope, not working.

  [http://www.createforum.com/phpbb/viewtopic.php?t=54&mforum=maf](http://www.createforum.com/phpbb/viewtopic.php?t=54&mforum=maf)

---

### Post by jjalocha on 2007-05-13
I am using the following modified 0.6.3 version of MAF on Xubuntu Feisty with Firefox 2.0.0.3:

[http://atrey.karlin.mff.cuni.cz/~sanda/maf/](http://atrey.karlin.mff.cuni.cz/~sanda/maf/)

It reads a MHTML file created with IE5 perfectly.

I am not sure if there is any version that works with Firefox 1.5 under Linux.

---

### Post by oomingmak on 2007-10-05
> **saurabhnanda said:**
> I have a whole lot of these .mht files (written by IE) and want to view them in GNOME. Any application that would let me do that?
You can just use Firefox to view them (provided that you know how to correctly set up your system).

You'll need to patch the MAF extension, install it in Firefox, and then correctly create and configure the MHT mime type in Ubuntu.

Simple step-by-step instructions on how to do this can be found in this thread:

[**[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?p=3311005[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=3311005")

---

