---
title: "MP3 files will not play"
date: 2010-06-28
forum: General Help
---

### Post by MrNickDanger on 2010-06-28
I'm pretty new to linux and my friend helped me learn the basics but neither of us can figure out why we cannot get mp3s to play. Any help would be greatly appreciated.
so here's what I got

Compaq CQ60 laptop
4gb of ram
AMD Athlon Dual-Core QL-62
250gb Disk space

Ubuntu
Release 10.04(lucid)
Kernel Linux 2.632-22-generic
GNOME 2.30.0

Everything works fine except I can't play my mp3s. I've tried medibuntu ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)), I installed Gstreamer extra plugins, Ubuntu Restriced Extras, Libtwolam0 MPEG Audio layer 2 encoding library,  I've tried different media players, amarok, rhythmbox, vlc, and exaile and still nothing.

Any suggestion?

---

### Post by mick222 on 2010-06-28
Can you play other types of media like a cd or ogg vorbis file?
In software sources make sure all the boxes are ticked except for source code then reinstall restricted extras .

---

### Post by MrNickDanger on 2010-06-28
It does play cds and I don't have any ogg Vorbis files.
I checked software sources and everything was already checked except source code. Then I reinstalled Ubuntu Restriced Extras. Still nothing.

---

### Post by mick222 on 2010-06-28
Strange check out this thread your sound might just be muted but lots of help here.[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by MrNickDanger on 2010-06-28
would it mutes the mp3 files specifically? Because I have sound with cds and movies and basically everything else.

---

### Post by TheStroj on 2010-06-28
In your Home folder, there's an Example directory where you will find all kinds of files, there are also ogv and oga files there.

Do these:

1. Reboot computer and first thing you do is to run different mp3 files in more different players.

2. Tell us if there is no sound from videos or other music files (ogg, wma, wav...) from different players with different files.

3. Tell us exactly what happens when you run mp3 file: is there only no sound or it gets stuck at 0:00 or maybe jumping from 0:00 to 0:01.

4. Try playing online videos / music and telling us what happens.

Have fun :D

---

### Post by chris5 on 2010-06-28
You won't be able to play mp3 files 'out of the box'. You need to download the codecs separately. 
 
Hope this helps

---

### Post by TheStroj on 2010-06-28
> **chris5 said:**
> You won't be able to play mp3 files 'out of the box'. You need to download the codecs separately. 
 
Hope this helps

Read his first post again.

---

### Post by MrNickDanger on 2010-06-28
I know they won't work out of box and need the codecs, Believe me I know. haha

okay so I Rebooted my computer and played a few different mp3s on 3 different players
1. rhythmbox just says "not playing" and doesn't even acknowledgment them in my library under my music folder
2. Exaile says "Could not determine type of stream." 
3. VLC media player stays at 0:00 flashes the name of the song and immediately stops without playing anything 

online videos such as youtube and google play fine, I also have no trouble playing music on pandora and last.fm

---

### Post by TheStroj on 2010-06-28
> **MrNickDanger said:**
> I know they won't work out of box and need the codecs, Believe me I know. haha

okay so I Rebooted my computer and played a few different mp3s on 3 different players
1. rhythmbox just says "not playing" and doesn't even acknowledgment them in my library under my music folder
2. Exaile says "Could not determine type of stream." 
3. VLC media player stays at 0:00 flashes the name of the song and immediately stops without playing anything 

online videos such as youtube and google play fine, I also have no trouble playing music on pandora and last.fm

I know this might sound stupid, but try opening them in Totem (I know its not really a music player but I had some mp3 files which would only play with Totem from unknown reason).

Since I'm not really an expert in such things I would recommend that you run file in debug mode with some music player (in this case will be used Totem) and post the output. Debug mode can be really usefull because it will say everything it does.

Terminal --> run this:
```
totem --debug file.mp3
```

Hope you find your answer in this :)

---

### Post by MrNickDanger on 2010-06-28
> **TheStroj said:**
> I know this might sound stupid, but try opening them in Totem (I know its not really a music player but I had some mp3 files which would only play with Totem from unknown reason).

Since I'm not really an expert in such things I would recommend that you run file in debug mode with some music player (in this case will be used Totem) and post the output. Debug mode can be really usefull because it will say everything it does.

Terminal --> run this:
```
totem --debug file.mp3
```Hope you find your answer in this :)


nickdanger@deathbot3000:~$ totem --debug /home/nickdanger/Music 06 Linoleum.mp3
(totem:1963): Totem-DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
(totem:1963): Totem-DEBUG: Setting initial properties
(totem:1963): Totem-DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
(totem:1963): Totem-DEBUG: Received SaveComplete message in state save-yourself-done
(totem:1963): Totem-DEBUG: Init of Python module
(totem:1963): Totem-DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
(totem:1963): Totem-DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
(totem:1963): Totem-DEBUG: Creating Python plugin instance
(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): 01 White Crosses.mp3 (null) (null)

(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): 02 Hostile Takeover.mp3 (null) (null)

(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): 06 Linoleum.mp3 (null) (null)

(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): 11 Antennas 1.mp3 (null) (null)

(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): 06 (null) (null)

(totem:1963): Totem-DEBUG: totem_playlist_add_one_mrl (): Linoleum.mp3 (null) (null)

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(979): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind

---

### Post by Smart Viking on 2010-06-28
Have you tried different mp3 files?

You could always see if you could be able to play them from the command line with these commands:

Install mpg321
```
sudo apt-get install mpg321
```

Then play a song
```
mpg321 song.mp3 # eventually replace song.mp3 with /path/to/song.mp3
```

I hope this helps. :)

---

### Post by MCVenom on 2010-06-28
OP, if you aren't able to solve your problem here I suggest you look at Linux Mint. It's Ubuntu based and MP3s should play out of the box.

Good luck :P

---

### Post by Smart Viking on 2010-06-28
Hey dude, you files have spaces in them! (ouch)

Take away the spaces in a song, then try to play them, and by the way, for "totem --debug" to work, you will have to do this(because the files have spaces):

```
totem --debug "/home/nickdanger/Music 06 Linoleum.mp3"
```

---

### Post by MrNickDanger on 2010-06-28
> **Smart Viking said:**
> Hey dude, you files have spaces in them! (ouch)

Take away the spaces in a song, then try to play them, and by the way, for "totem --debug" to work, you will have to do this(because the files have spaces):

```
totem --debug "/home/nickdanger/Music 06 Linoleum.mp3"
```

No such file "/home/nickdanger/Music 06 Linoleum.mp3"

seemed to find it fine without the quotations

---

### Post by MCVenom on 2010-06-28
> **Smart Viking said:**
> Hey dude, you files have spaces in them! (ouch)

Take away the spaces in a song, then try to play them, and by the way, for "totem --debug" to work, you will have to do this(because the files have spaces):

```
totem --debug "/home/nickdanger/Music 06 Linoleum.mp3"
```

Actually, I think the slash after the Music directory is missing too, so it'd be this for the proper command:
```
totem --debug "/home/nickdanger/Music/06 Linoleum.mp3"
```

---

### Post by MrNickDanger on 2010-06-28
> **BlackOtaku said:**
> Actually, I think the slash after the Music directory is missing too, so it'd be this for the proper command:
```
totem --debug "/home/nickdanger/Music/06 Linoleum.mp3"
```
nickdanger@deathbot3000:~$ totem --debug "/home/nickdanger/Music/06 Linoleum.mp3"
(totem:2260): Totem-DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
(totem:2260): Totem-DEBUG: Setting initial properties
(totem:2260): Totem-DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
(totem:2260): Totem-DEBUG: Received SaveComplete message in state save-yourself-done
(totem:2260): Totem-DEBUG: Init of Python module
(totem:2260): Totem-DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
(totem:2260): Totem-DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
(totem:2260): Totem-DEBUG: Creating Python plugin instance
(totem:2260): Totem-DEBUG: totem_playlist_add_one_mrl (): 06 Linoleum.mp3 (null) (null)

** Message: Error: Resource not found.
gstfilesrc.c(1055): gst_file_src_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstFileSrc:source:
No such file "/home/nickdanger/Music/06 Linoleum.mp3"

(totem:2260): Totem-DEBUG: Finalizing Python plugin instance
nickdanger@deathbot3000:~$

---

### Post by Smart Viking on 2010-06-28
> **BlackOtaku said:**
> Actually, I think the slash after the Music directory is missing too, so it'd be this for the proper command:
```
totem --debug "/home/nickdanger/Music/06 Linoleum.mp3"
```

Ah yes my mistake, i copied without looking at the directory tree :)

@MrNickDanger: Nopez, when you didnt have the quotations, the terminal thought you have giving it one full path and two relative paths, since it had spaces in it. ;)

---

### Post by MrNickDanger on 2010-06-28
> **Smart Viking said:**
> Ah yes my mistake, i copied without looking at the directory tree :)

@MrNickDanger: Nopez, when you didnt have the quotations, the terminal thought you have giving it one full path and two relative paths, since it had spaces in it. ;)

nickdanger@deathbot3000:~$  totem --debug "/home/nickdanger/Music/06_Linoleum.mp3"
(totem:2301): Totem-DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
(totem:2301): Totem-DEBUG: Setting initial properties
(totem:2301): Totem-DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
(totem:2301): Totem-DEBUG: Received SaveComplete message in state save-yourself-done
(totem:2301): Totem-DEBUG: Init of Python module
(totem:2301): Totem-DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
(totem:2301): Totem-DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
(totem:2301): Totem-DEBUG: Creating Python plugin instance
(totem:2301): Totem-DEBUG: totem_playlist_add_one_mrl (): 06_Linoleum.mp3 (null) (null)

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(979): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind

(totem:2301): Totem-DEBUG: Finalizing Python plugin instance
nickdanger@deathbot3000:~$ 



okay I think I got it right and took away the spaces. Still getting an error >:(

---

### Post by MrNickDanger on 2010-06-28
So is it about that time to burn my laptop as a sacrifice to the Linux Gods?

---

### Post by Smart Viking on 2010-06-28
Out of curiosity, does this play?: [http://smartviking.com/viking/sheep.mp3](http://smartviking.com/viking/sheep.mp3) :)

---

### Post by MCVenom on 2010-06-28
> **MrNickDanger said:**
> So is it about that time to burn my laptop as a sacrifice to the Linux Gods?
No, just try Mint, I guarantee it'll work under it :P

---

### Post by MrNickDanger on 2010-06-28
> **Smart Viking said:**
> Out of curiosity, does this play?: [http://smartviking.com/viking/sheep.mp3](http://smartviking.com/viking/sheep.mp3) :)


yes

---

### Post by Smart Viking on 2010-06-28
> **MrNickDanger said:**
> yes

Thats pretty weird since it is an mp3 file. Then i does not think it i your system that can't play mp3, rather those specific mp3 files that are corrupted.(unless you have tried other mp3 files, and those didn't work either) :)

---

### Post by MrNickDanger on 2010-06-28
> **Smart Viking said:**
> Thats pretty weird since it is an mp3 file. Then i does not think it i your system that can't play mp3, rather those specific mp3 files that are corrupted.(unless you have tried other mp3 files, and those didn't work either) :)
I have about 4 different mp3 files on my computer. I didn't bother putting all 50gb of music I have on here if they aren't going to play. All of the files I've tried so far have not played. They worked fine on my mp3 player(zune, haha I know), and on my previous OS Windows Vista.

---

### Post by MrNickDanger on 2010-06-28
> **Smart Viking said:**
> Thats pretty weird since it is an mp3 file. Then i does not think it i your system that can't play mp3, rather those specific mp3 files that are corrupted.(unless you have tried other mp3 files, and those didn't work either) :)

I'm going to try to download some new mp3s and see what happens, just to see if there was something wrong when they transfered from my thumb drive.

---

### Post by MrNickDanger on 2010-06-28
omfg, it was my thumb drive. The mp3s that I just got work fine. Thank you all for your help. I feel stupid.

---

### Post by TheStroj on 2010-06-29
Sometimes a simple solution is the best solution ;)

---

