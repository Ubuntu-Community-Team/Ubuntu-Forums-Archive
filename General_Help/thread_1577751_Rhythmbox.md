---
title: "Rhythmbox"
date: 2010-09-19
forum: General Help
---

### Post by bumder on 2010-09-19
so i've gone back to rhythmbox after using exaile for a while, and updated it to the ubuntu 10.10 version (i'm still using 10.04 though)

quite happy with it (seems less buggy than exaile, less bloaty than banshee/songbird), but after correcting a lot of id3 tags using rhythmbox, upon restarting my system, found that it did not save the edited tags :(

is this a gstreamer thing (as in all players can't edit tags), and is there the capability in the pipe works?

cheers
:guitar:

---

### Post by afrowildo on 2010-09-20
Does this help you any?

[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117600.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117600.html)

---

### Post by bumder on 2010-09-23
hmm, seems gst-plugins-good is not in synaptics, will look at trying to find a tarball off a site then...

surely this should have been installed with the resticted-extras package i installed post-install?

cheers.

---

### Post by Quarkrad on 2010-09-23
Sorry to change tack a little but I too have started the use Rhythmbox.  (I did a silly thing and installed the latest version of Songbird on my winxp side - what an amazing application.  It looks professional and if you set up the lyrics they seem to appear instantly - Rhythmbox seems to take ages.  Certainly light years from Songbird). Anyway - the text looks too big too my eyes; I would like it more like iTunes and Songbird.  Is there a way of changing the font size in Rhythmbox?  The whole thing needs to be smaller so the screen does not look so cluttered.

---

### Post by sydbat on 2010-09-23
> **bumder said:**
> so i've gone back to rhythmbox after using exaile for a while, and updated it to the ubuntu 10.10 version (i'm still using 10.04 though)

quite happy with it (seems less buggy than exaile, less bloaty than banshee/songbird), but after correcting a lot of id3 tags using rhythmbox, upon restarting my system, found that it did not save the edited tags :(

is this a gstreamer thing (as in all players can't edit tags), and is there the capability in the pipe works?

cheers
:guitar:Have you tried using 'Easy Tag' (found in the repositories) to change/update your id3 tags?

---

### Post by bumder on 2010-09-23
Easy Tag would be one way of doing it, but it would be good to be able to change tags in Rhythmbox when using the library, instead of opening a different app.

---

### Post by bumder on 2010-09-23
ok, i think i know whats happening know.

it seems that other mp3 players tend to use and read id3 tags to get the track info, but in some mp3's there are other types of tags, such as APE.

rhythmbox can edit id3 tags, but will read APE tags then revert all info so they match them.

so if i can somehow get rhythmbox to prefer id3 over APE tags...

---

### Post by afrowildo on 2010-09-24
From the looks of things, this is a problem for many [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945)

There's a link in the comments section there that appears to contain a workaround that at least one other commenter can vouch for [http://brej.org/blog/?p=143](http://brej.org/blog/?p=143)

---

