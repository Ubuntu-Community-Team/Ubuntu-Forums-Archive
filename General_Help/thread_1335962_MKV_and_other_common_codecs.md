---
title: "MKV and other common codecs"
date: 2009-11-24
forum: General Help
---

### Post by ghostier on 2009-11-24
I'm new to KDE and kubuntu, my experience with linux has been limited to gnome with ubuntu. I noticed that in ubuntu, whenever, you played a media file that didn't have the correct codecs installed, it would automatically ask you to search and install the appropriate codec packages. However, in Kubuntu, that wasn't the case. I'm just wondering if there are any codec collections or packages that's available for kde for me to install to play most of the common media file types.

---

### Post by Andreas1 on 2009-11-24
install "kubuntu-restricted-extras"

it is a meta-package for a lot of commonly used but non-free (hence not included by default) packages, including flash and a lot of codecs.

---

### Post by andrew.46 on 2009-11-24
Hi ghostier,

A small comment a little aside of your main question: mkv is not actually a *codec*, it is a *container* that can hold multiple video, audio and subtitle tracks. If you were ever interested in exploring mkv files in greater depth you could do worse than to install *mkvtoolnix-gui* which is an easy to use program to manipulate the mkv (Maroska) container.

All the best,

Andrew

---

### Post by ghostier on 2009-11-24
I can't seem to install it somehow. I found it in the software manager, selected it for install and when I click apply -> install now it just executes the search again without installing or downloading anything.
Andrew: thanks for the information, I've came across that program when trying to solve my problem.

---

### Post by Darael on 2009-11-24
Hmm... That's interesting.  Have you tried using the terminal?  It's regrettable to have to resort to this, but try opening up Konsole, and running "sudo aptitude install kubuntu-restricted-extras".  When you put your password in, nothing will show up to confirm each keystroke - don't worry about it.

If it still doesn't install, post the output here so we can see what's going on.

---

### Post by ghostier on 2009-11-24
Yeah it was installed successfully using terminal, I'll look into the software manager problem later. Thanks for the help. I should test if the codecs are working properly.

EDIT: the installed codecs worked. SOLVED.

---

