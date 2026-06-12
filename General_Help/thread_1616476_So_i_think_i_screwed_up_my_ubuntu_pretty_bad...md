---
title: "So i think i screwed up my ubuntu pretty bad.."
date: 2010-11-08
forum: General Help
---

### Post by static_hf on 2010-11-08
Hey forum,

I did a big mess today... I installed Lampp on my system few months ago, but for some reasons it wasn't functioning as i was expecting.
So i wanted to unistall it and install a fresh copy of it. Sadly, my friend told me to do :

sudo apt-get remove lamp-server^   

It unistalled almost anything i had on my ubuntu! I thought it wouldn't be so hard to fix it with an update command or fix command.
But it didn't do anything! So i reboot my system and once again i got the annoying message saying "Ubuntu did not detect your graphic card, screen and input devices. please configure them manually".

I run ubuntu on an asus g1sn so i had installed nvidia driver on it... 
My next step was reinstalling my nvidia driver in hope of fixing the problem.

I did it but sadly, im still getting the same error.

Now im planning to update from 10.04 to 10.10 in hope of fixing the problem... do you have any other solutions that might help me?

Briefly, this is what i've done so far:
1- Unistalled Lamp and around 100 packages with the command mentioned... *facepalm*
2- Tried update command
3- Tried fix command
4- Tried renistalling Nvidia driver
5- I'm screwed...

Sorry for the headache,
statichf

---

### Post by P4man on 2010-11-08
try

```
sudo apt-get install ubuntu-desktop
```

---

