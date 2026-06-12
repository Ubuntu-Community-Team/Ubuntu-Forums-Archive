---
title: "Distorted Sound when plug in Audio Jack"
date: 2010-03-15
forum: General Help
---

### Post by kthxbai2u on 2010-03-15
I am running Karmic (9.10) on an MSI U120 Wind. I dislike netbook-remix but that is beside the point.

Last night I made the biggest mistake of my life which is causing a loss of still counting hours. I decided to do an update, due to having enough bandwidth, and security updates to download.

So it finished, and I went to sleep.

This morning I went to plug in my speakers to the audio jack so I can listen to music loud, and it was all distorted. I changed al 8 or 9 volume controls and nothing. I unplugged the wire from the audio jack, and the sound is perfect on my netbook's speakers.

I have tried different wires, speakers, editing config files, removing and purging related packages, and nothing works...

I have been google-ing for hours and everyone seems to have the same problem, but all of the supposed fixes do not work for me...

Here is a pastebin of my Alsa info : [http://pastebin.ca/1841579]("http://pastebin.ca/1841579")

I fear switching back to winblowz... It wont happen. I wont let it... I need everyone's help badly...

---

### Post by kthxbai2u on 2010-03-15
Ok I would delete this thread now, but that gets rid of useful information...

I am not sure what it was causing this problem...

The only thing I can suggest to anyone experiencing these problems:

```
sudo apt-get install kdm kubuntu-desktop
sudo apt-get remove --purge kdm kubuntu-desktop
```

I don't know why or how, but that solved my problem... Although after doing that and rebooting I got a kernel panic something about not syncing with VFS I cant remember exactly...

So to get from there back in, I just selected a previous kernel...

I am going to reboot though and select the first one to see if it boots now... I may have to change the root(8,1) in grub to root(0,0) to get it to boot but meh...

I GOT MY SOUND BACK :D

thanks even though I solved my own problem (so crudely)

---

