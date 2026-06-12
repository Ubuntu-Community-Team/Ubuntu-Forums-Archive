---
title: "Sound recorder problem"
date: 2011-11-23
forum: General Help
---

### Post by 13im6b on 2011-11-23
Hi guys, i install today lubuntu and i have problems trying to install the sound recorder

sudo apt-get install sound-recorder doesnt work and gnome-sound-recorder either

can any tell me the specific package name please? i cant find this in the Synaptic



(sorry if u have a problem understanding, my english sucks)

---

### Post by Rex Bouwense on 2011-11-23
Welcome to the Forums.  I'm not sure what you are wanting to install.  Do you want to install a program that will allow you to record something?  Do you want video or just audio?  Cheese will allow you to record the audio and video from your web cam and mic.  Are you wanting to edit audio?  A little more information would be advantageous toward someone providing meaningful assistance.  And don't feel bad about your English.  It is fine.

By the way there is a bug in the install of the guvcview, which is the default web cam program, which turns it off as soon as capture video is pressed.

---

### Post by pretty_whistle on 2011-11-23
> **13im6b said:**
> Hi guys, i install today lubuntu and i have problems trying to install the sound recorder

sudo apt-get install sound-recorder doesnt work and gnome-sound-recorder either

can any tell me the specific package name please? i cant find this in the Synaptic



(sorry if u have a problem understanding, my english sucks)
I thought "sound recorder" is its name.

I wished I could recall how I did it but I was able to install it.

---

### Post by oldtimer7777 on 2011-11-23
> **pretty_whistle said:**
> I thought "sound recorder" is its name.

I wished I could recall how I did it but I was able to install it.

Well if you had Gnome installed before, it should be there..  Wierd..

Try this:

```
**sudo apt-add-repository ppa:osmoma/audio-recorder**
** sudo apt-get update && sudo apt-get install audio-recorder**
```

---

