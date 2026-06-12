---
title: "Frong End GUI for lame?"
date: 2006-06-02
forum: General Help
---

### Post by russianbandit on 2006-06-02
Is there an app or some kind of GUI front end for lame?
I really don't want to type in the console each time i want to convert an album from a VBR to 192kbps. I'm looking for something that kind of acts like iTunes for converting mp3s.

---

### Post by mustang on 2006-06-02
Perhaps a script would help?

[http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/n/nautilus-script-manager/nautilus-script-manager_0.0.5-0ubuntu3_all.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/n/nautilus-script-manager/nautilus-script-manager_0.0.5-0ubuntu3_all.deb)
[http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb)

```
nautilus-script-manager enable ConvertAudioFile
```

---

### Post by givré on 2006-06-02
You also have soundconverter :
```
sudo apt-get install soundconverter gstreamer0.8-lame gstreamer0.8-plugins gstreamer0.8-plugins-multiverse
```

---

### Post by mjm115 on 2006-06-02
Both KAudioCreator (Kubuntu) and SoundJuicer (Gnome) can be used as a front-end for lame, although they are both closer to CDex than iTunes.

---

### Post by russianbandit on 2006-06-02
Does SoundJuicer convert albums that are not on a CD but are on a harddrive?

---

### Post by meng on 2006-06-02
Soundjuicer (and possibly KAudioCreator, but I have no personal experience with it) will require you to create and edit a profile (i.e. gstreamer pipeline) for encoding mp3 at 192 kbps, but it's relatively easy to do this.

---

### Post by givré on 2006-06-02
[QUOTE=russianbandit]Does SoundJuicer convert albums that are not on a CD but are on a harddrive?[/QUOTE]

It's not done for that

---

### Post by russianbandit on 2006-06-02
[QUOTE=givré]It's not done for that[/QUOTE]

What's not done for that?
What I need is, say I have an album sitting on my harddrive in VBR, but I want to covert it to 192kbps withought using the console. Will soundjuicer or some other app work for me?

---

### Post by stimpsonjcat on 2006-06-02
did you try soundconverter or the nautilus script mentioned above? if so, why don't they work for you?

---

### Post by givré on 2006-06-02
For that the best app. is soundconverter (has i say before ;) )
you should try it.

N.B : you should install it like that to have mp3 tag enable :
```
sudo apt-get install soundconverter gstreamer0.8-lame gstreamer0.8-plugins gstreamer0.8-plugins-multiverse
```

---

### Post by givré on 2006-06-02
Here the website if you want some screenshot:
[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)
he is quite simple but he do the job, and quite fast

---

### Post by russianbandit on 2006-06-02
Thanks, I will try the soundconverter.
One thing that I noticed, you say to get all of these gstreamer-0.8 plugind, I thought that Dapper only used gstreamer-0.10 stuff now.
Am I wrong here?

---

### Post by givré on 2006-06-02
The thing is soundconverter only work with gstreamer0.8 for the moment.
You could install the two version without problem, it's safe and will not affect your other sound application

---

