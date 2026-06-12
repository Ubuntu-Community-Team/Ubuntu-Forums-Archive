---
title: "Help with a tricky situation please"
date: 2011-07-07
forum: General Help
---

### Post by verymadpip on 2011-07-07
Hello all.

I've been using 11.04 Unity, & quite like it.

I fired up Blender 2.49b the other day (not used it for a long time) & its behaviour was very erratic.  Due to this I decided to reinstall 10.10 for the time being, until October or maybe even the 12.04 LTS.

I backed everything up & reinstalled 10.10.

I then tried to restore my Evolution from the Natty backup file, which simply didn't work.  The message was something about it not being a valid file.  I'm assuming this is a non backwards compatibility issue.

My question s are:

Can anyone help me with either getting Blender to work or restoring Evolution?

With regard to Blender (in Natty); I've not tried proprietary drivers for my GPU yet as the open source defaults have always been fine, so that's an option.  It means another reinstall (of Natty), but that really isn't such a big deal at this point.

With regard to Evolution (in Maverick); I found a ppa but I'm unsure how to proceed once I've added it.  Would I do an apt-get update & an apt-get install evolution?

My last resort would be to do a distro hop until October.

Although I've been using Ubuntu for a couple of years I'm still pretty much a novice BTW. 

If I've put this in the wrong section I apologise. I also apologise for rambling on a bit.

Any input is greatly appreciated.

---

### Post by Pard68 on 2011-07-07
Did you try running Blender in GNOME on 11.04? Just go to the login screen and at the bottom select "Ubuntu Classic". I've run Blender in 11.04 without a single problem (I just don't use Unity).

As for the email problem. Why don't you just redo it? It takes like five minutes tops.

---

### Post by verymadpip on 2011-07-07
Hi Pard68.
Yeah, I tried.  It was still a bit freaky.  I think that's why I decided to go back to 10.10 IRCC.  I'd be willing to try it again.  I've nothing to lose at this point so I can do fresh installs 'all day long' so to speak.

When you say redo the email, could you clarify for me a bit please (dope on a rampage here :)).  If you mean retrieve everything again that's do-able.  I'm not sure if I've set it up to keep *sent *items on the server (I use Hotmail).  I'd rather not lose all of them.

Thanks for the reply.

---

### Post by Pard68 on 2011-07-07
Ah I see your email issue then. Have you updated your mail client? It could be that it isn't up to date. It shouldn't be a problem with 10.10 vs 11.04 since the program is the issue not the OS. Could you give me the exact error?

Let me throw Blender back on here and play with it a little. Tell you what I find. It could be messy for me too and I never noticed since I don't use Blender (tried it but decided it was not meant for architects! Back to Chief Architect for me...).

EDIT

[http://ubuntuforums.org/showthread.php?t=1743996](http://ubuntuforums.org/showthread.php?t=1743996)

Appears there is a new version of Blender. Maybe that will run better on 11.04? It's Blender v. 57b

Do you have all the dependencies for Blender?

```
sudo apt-get install subversion build-essential gettext \  libxi-dev libsndfile1-dev \  libpng12-dev libfftw3-dev \  libopenexr-dev libopenjpeg-dev \  libopenal-dev libalut-dev libvorbis-dev \  libglu1-mesa-dev libsdl1.2-dev libfreetype6-dev \  libtiff4-dev libsamplerate0-dev libavdevice-dev \  libavformat-dev libavutil-dev libavcodec-dev libjack-dev \  libswscale-dev libx264-dev libmp3lame-dev python3.2-dev
```

I'll also look into the mail issue as that seems like the quickest solution.

---

### Post by verymadpip on 2011-07-07
Ah, I'm not actually near that box at the moment (not until around 6.30-7pm).

Anyway, the error as I recall was 10.10 Evolution telling me that the backup file I made in 11.04 evolution was **not a valid file to restore from**.
(I also think it's the application & not the OS).

I can get the specific error for you later if that will be more helpful, I expect it would be......

I try use Blender to make models of abstract geometric sculpture that I'm thinking about making.  I don't use it to its full potential, nevertheless it's quite a useful tool for me.  I suppose I could live without it & just start drawing again :p

---

### Post by verymadpip on 2011-07-07
Thanks Pard68, ".49b doesn'treally work in any Natty desktop so I'll try the .57

The error message for Evolution is:

```
Invalid Evolution backup file.
Please select a valid backup to restore
```

I'm going to try the newer Blender in a few minutes.

I appreciate your time by the way, so thanks again.

---

### Post by verymadpip on 2011-07-07
Well, it looks as though new Blender works quite well with 11.04.

I've also been able to restore from my Evolution backup file.

All is well in my world :D

Thanks for the help Pard68.

This community ***rocks***!!!

Oops, I should add that I didn't need any extra dependencies.  Blender 2.58a worked straight out of the box.

---

### Post by Pard68 on 2011-07-07
Glad to hear it.

---

### Post by johnaaronrose on 2011-08-09
verymadpip,

Could you tell me how you managed to restore from your Evolution backup file?

---

### Post by MarjaE on 2011-10-20
> **johnaaronrose said:**
> verymadpip,

Could you tell me how you managed to restore from your Evolution backup file?

I'd also like to know, since I can't restore from mine.

---

