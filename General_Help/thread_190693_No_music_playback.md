---
title: "No music playback"
date: 2006-06-06
forum: General Help
---

### Post by elin on 2006-06-06
I cannot play music at all with Ubuntu Dapper. Rhythmbox fails to play everything including the file "ubuntu Sax.ogg" in the Examples folder using the Live CD. Whatever it is, it makes me crazy. Somebody experiencing the same problem?

---

### Post by givré on 2006-06-06
Do you have an error?
Is your sound card detected (do you have sound at startup ?)

---

### Post by ifokkema on 2006-06-06
[QUOTE=elin]I cannot play music at all with Ubuntu Dapper. Rhythmbox fails to play everything including the file "ubuntu Sax.ogg" in the Examples folder using the Live CD. Whatever it is, it makes me crazy. Somebody experiencing the same problem?[/QUOTE]

I think this will solve your problem:
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

This should allow rhythmbox to play mp3's.

Edit: I've been pointed at: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Ivo

---

### Post by sharperguy on 2006-06-06
Ubuntu can play ogg files with no extra libaries at all, so I doubt this is the problem

---

### Post by elin on 2006-06-06
Well, I have no problem with the sound card (Aureal Audio) and I hear sound on startup. Furthermore, I have already followed the instructions on the Wiki and all needed gstreamer plugins for mp3 are installed.

Well, just to be sure, here is exactly what I do:

Applications > Sound & Video > Rhythmbox Music Player > Music > Import File > ubuntu Sax.ogg (in the home, then Examples folder) > Double click in the Rhythmbox window > Player starts, then stops immediately, showing "Not Playing".

Reinstalled Ubuntu three times from clean, formatted hard disk, same error. ](*,) 

Thankful for your replies, hopefully more replies will come in :grin:

---

### Post by cleentrax on 2006-06-06
Does Dapper play the login, or opening sound?

What happens when you hover the pointer over an ogg file? (It should preview the file).

---

### Post by elin on 2006-06-06
Would like to add that I tried to play a CD in Rhythmbox - same result though. This makes me crazy, so I installed VLC - no problem! Everything worked just fine. Same computer, same files, same everything.

Now I could live with the ugly :rolleyes: interface of VLC to play a single file every other year, but it is horrible to use VLC all the time. Please - is there any other music player to use, since Rhythmbox has proven to be allergic to my speakers?

---

### Post by givré on 2006-06-06
and do you have sound with totem (same engine but other apps)

---

### Post by givré on 2006-06-06
If you want the best audio player ever, try amarok, far better than anything you tried :KS

---

### Post by ifokkema on 2006-06-06
[QUOTE=elin]Would like to add that I tried to play a CD in Rhythmbox - same result though. This makes me crazy, so I installed VLC - no problem! Everything worked just fine. Same computer, same files, same everything.

Now I could live with the ugly :rolleyes: interface of VLC to play a single file every other year, but it is horrible to use VLC all the time. Please - is there any other music player to use, since Rhythmbox has proven to be allergic to my speakers?[/QUOTE]

Now I may be far off (wouldn't be the first time :)) - could this be caused by Rhythmbox trying to access the sound card through alsa while esd is running?

Just a check - what if you kill the esd process and try again? This will not be a fix, but it may determine the problem if my theory is correct.

---

### Post by elin on 2006-06-06
I see you are using Kubuntu - is amaroK going to install on Ubuntu Dapper (without installing the whole massive download times of KDE)?

---

### Post by givré on 2006-06-06
I'm not running kubuntu at the moment, it's the theme of the forum you see at the left (in blue it's far better :cool: )
So of course you will not have to install lots of kde stuff, and it's work perfectly in gnome.
If you prefer some GTK apps, you could try banshee (never try, but appear to be quite good)

Make your choise, there is lots and lots audio player in linux world :wink:

---

### Post by elin on 2006-06-06
Well, I installed amarok, great program, but it does not play mp3:s either. OGG works fine so it must be something with my computer. Do I have to install the gstreamer plugin again or does amarok come with its own mp3 engine?

It is nearly midnight here in Europe, so thank you all and good night.

If it wasn't Linux I would reformat the hard drive in ten red seconds and revert to Windows. But certainly it is a pity that Ubuntu would come with a music player that just supports OGG. Does not make any good first impression, not at all.

---

### Post by givré on 2006-06-06
No it's because it use xine and not gestreammer.
You should return there [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) :wink:

---

### Post by givré on 2006-06-06
To be simple, just do 
```
sudo apt-get install libxine-extracodecs
```
And you can go

---

