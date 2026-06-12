---
title: "Is there a way to have system sounds silent but play alerts?"
date: 2011-10-10
forum: General Help
---

### Post by pretty_whistle on 2011-10-10
What I'm trying to do is 2-fold:

1) have system sounds be silent or at a lower volume

2) but be able to play email notification alert loudly regardless.

I have Ubuntu 11.04.

If Ubuntu can't do it is there a program that could get this done?

---

### Post by An Sanct on 2011-10-11
Well, you could delete or rename all the other sounds (location should be: /usr/share/sounds), thus making the email sound the only one playable...

PS. I know, its a lame hack and also your logs will be full of "could not find ____.ogg", for every time a sound should be played, but it should work ;)

---

### Post by pretty_whistle on 2011-10-11
> **An Sanct said:**
> Well, you could delete or rename all the other sounds (location should be: /usr/share/sounds), thus making the email sound the only one playable...

PS. I know, its a lame hack and also your logs will be full of "could not find ____.ogg", for every time a sound should be played, but it should work ;)

Lame hack??  Not really.... I've already tried one sort of similar one but to no avail which is to find the .ogg mail notification file and use an audio editor to increase the volume of it.  

The new file's there now but doesn't play-if I play it separately it works so it's not a bad file.  Go figure.

The sound setting only gives a selection of predefined sounds to choose from and it's not acknowledging some of it's own list.  This is probably why it won't acknowledge my edited sound file.

---

### Post by pretty_whistle on 2011-10-11
Update:

Per my last post I fixed it by inserting the edited sound file into  /usr/share/sounds/ubuntu and named it 'message' and deleted the old one named message.ogg.

---

### Post by An Sanct on 2011-10-11
My message notification file is located here (I do not know about other ppl's locations)

'/usr/share/sounds/ubuntu/stereo/message-new-instant.ogg'

PS. I have Maverick 10.10.

---

### Post by An Sanct on 2011-10-11
> **pretty_whistle said:**
> Update:

Per my last post I fixed it by inserting the edited sound file into  /usr/share/sounds/ubuntu and named it 'message' and deleted the old one named message.ogg.

Okay, now, if it does not play, make sure the added files has the same permissions as the other ones.

---

### Post by pretty_whistle on 2011-10-11
> **An Sanct said:**
> My message notification file is located here (I do not know about other ppl's locations)

'/usr/share/sounds/ubuntu/stereo/message-new-instant.ogg'

PS. I have Maverick 10.10.

That's the same file path as mine I just goofed when I wrote it.

However, I think the file you mentioned is for instant messaging sound.

---

### Post by pretty_whistle on 2011-10-11
> **An Sanct said:**
> Okay, now, if it does not play, make sure the added files has the same permissions as the other ones.

To cure that I opened nautilus as root and browsed to where it was sitting and replaced the edited file for the one I didn't want.

---

