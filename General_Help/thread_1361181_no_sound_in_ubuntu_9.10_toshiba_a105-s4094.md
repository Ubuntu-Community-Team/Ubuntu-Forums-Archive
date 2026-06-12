---
title: "no sound in ubuntu 9.10 toshiba a105-s4094"
date: 2009-12-21
forum: General Help
---

### Post by ultragamer on 2009-12-21
I am using a Toshiba Satellite A105-S4094 which I just installed Ubuntu 9.10 on. When I was running from the live cd, I had sound. Now, after the installation, I don't have any sound. In the sound preferences, the only output option is "Dummy Output". The volume is all the way up in both Ubuntu and on the laptop. Help!!

---

### Post by itang sanjana on 2009-12-21
From the terminal, run the command
```
aplay -l
```
If you see something like "no soundcard found", Ubuntu is not recognizing your sound card for playback. Further reading: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by LuisGMarine on 2009-12-21
To begin, we are going to make a backup copy of your current */etc/modprobe.d/alsa-base*.  So go ahead and fire up a terminal and type in the following command followed by <enter> and of course type in your root password when it prompts you to:

```
sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf_bak
```

Next, open it up to edit the file with your favorite text editor, for this example I'm going to use the text word editor , Gedit.

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Once the file is open look for a line that might look *similar* to this:

```
options snd-hda-intel 
```

Now all you need to do is make that line look like this, keep in mind if you don't have that line, just add the line below to the bottom of the file:
```

options snd-hda-intel model=toshiba
```


Save the file and quit, and then restart your PC.

[SIZE="2"]*Note:  You can restart the sound module, but I don't know how to do it off the top of my head, so lets just play it safe and restart ;)*[/SIZE]

Let me know how it goes.

**I pulled this info from a very old post.  Here is the thread in general.  You are more than welcome to dig it to see if you can maybe find a solution if the one I provided doesn't work.  Good Luck

[http://ubuntuforums.org/showthread.php?t=845331&page=3]("http://ubuntuforums.org/showthread.php?t=845331&page=3")

---

### Post by ultragamer on 2009-12-22
I ran all of the commands that both of you told me to run. Still, no sound. I still only have dummy output as an option.

---

### Post by lividup on 2010-03-25
I am having the same problem with my toshiba a105 4284. I've tried a multitude of solutions from the threads but to no avail. When I install what should be the proper driver with ndis... I get a hardware not present error with the hardware present in the box below. aplay -l says no soundcards found. What gives? I think toshibas are pieces of crap. My Gateway laptop was 100 % funcional with kubuntu 9.10 but this toshiba, Giant fonts, no wifi, no sound what a turd. Help me if you can. I'm not afraid of the terminal but I am no expert for sure.

---

