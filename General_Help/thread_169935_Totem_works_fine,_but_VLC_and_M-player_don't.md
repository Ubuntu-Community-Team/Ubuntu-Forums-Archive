---
title: "Totem works fine, but VLC and M-player don't"
date: 2006-05-03
forum: General Help
---

### Post by Riekie on 2006-05-03
I just did a fresh install from the latest dapper release.

When i try to play a DVD Totem works fine but VLC and M-player don't they give a strange greenish/distorted picture. 

I got all the needed codecs. 

I didn't have these problems under Breezy.

Is there someone who can help me?

---

### Post by ade234uk on 2006-05-03
Why dont you use Automatix and reinstall everything over again.

---

### Post by enopepsoo on 2006-05-03
usually my totem doesn't work and everything else does.  I never understood why it is the default player, when it works the least.

I second the suggestion of using Automatix to install the dvd codec.

---

### Post by Riekie on 2006-05-04
Thanks, i'm going to try automatix.

---

### Post by richbarna on 2006-05-04
It sounds to me that you are trying to play .wmv files.
If you try to play downloaded clips that are in wmv format, the website that it came from sometimes has it's own codec. If you play them with Windows media player it automatically goes to the site for the codec and normally opens internet explorer as well (for registering or spam etc)
As the commands in the wmv aren't recognised by linux VLC will just try to play the file, hence all green and blocky (not the right wmv codec.

---

### Post by Riekie on 2006-05-04
Nope, i'm trying to play DVD's

When i insert a dvd totem starts to play the dvd with no problems at all.

When i open vlc or mplayer to play the same DVD it plays, but with washed out colors. 

I tried the script to install the codecs.  The codecs are installed but this didn't solve the problem.

Automatix isn't recommended for Dapper. So i didn't try.

I need some advice !!

---

### Post by AndyCooll on 2006-05-04
One of the reasons might be that VLC and mplayer use their own codecs (which are different from the ones Totem uses). Totem uses either the Xine or gstreamer engines.

:cool:

---

