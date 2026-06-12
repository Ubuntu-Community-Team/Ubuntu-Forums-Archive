---
title: "wma(windows media audio decoder) problem"
date: 2010-12-17
forum: General Help
---

### Post by U_buntu on 2010-12-17
I cant seem to run wma audio files as well as some videos. Says I need the windows media audio decoder plug in. But when I do the search option it gives me it finds nothing. And I cant find any info on the net. I am running 9.10

---

### Post by carverj on 2010-12-17
Have you installed the restricted extras?
[http://www.jonathanmoeller.com/screed/?p=1674](http://www.jonathanmoeller.com/screed/?p=1674)

---

### Post by amsterdamharu on 2010-12-17
Ubuntu is 100% open source. Windows media is not, this means that if a program wants to encode or decode Windows media it has to ask Microsoft for permission to do so. At any moment the holder of the software patent can decide to sue the software creator or change it's policies and demand money, they can even sue you for using the software with patented parts for using it.
Luckily Software patents are only recognized in the US and Japan so you can add the codecs for mp3, wma and others using the following instructions:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Remember you can copy and paste commands from your browser into your terminal.

---

### Post by amsterdamharu on 2010-12-17
After you've added medibuntu to your software repositories you can install the codecs in the following way:

```
sudo apt-get install non-free-codecs
```

---

### Post by U_buntu on 2010-12-18
i have done both and still nothing

---

### Post by amsterdamharu on 2010-12-18
What file are you trying to view and what program do you use?

What is the output of the following command?

```
dpkg-query -W | grep w32codec
```

---

### Post by U_buntu on 2010-12-18
w32codecs    20071007-0medibuntu5

thats the output and I'm using windows movie payer

---

### Post by amsterdamharu on 2010-12-18
I've lost you, you are installing codecs for Ubuntu for Ubuntu software but trying to watch something in wine (that emulates windows and is a different system within Ubuntu)?

If the file is local just use VLC to watch it I am sure it'll play just fine. If it's online streaming then install the VLC plugin for firefox:

```
sudo apt-get install vlc mozilla-plugin-vlc
```

---

### Post by U_buntu on 2010-12-19
Oh sorry no, I'm just watching it through the movie player. Wasn't trying to bring wine in on it lol. But actually a reboot helped some what (don't know why the heck I didnt do that earlier). The music is playing just fine now. So thank you ever one for your help. Can't seem to get the videos to play though. Its only one so I deal. Was more interested in getting my music going. So again thank you guys.

---

### Post by amsterdamharu on 2010-12-19
Could you try and run that movie in vlc?
You can start it by pressing alt + f2
Before opening it could you choose "view" -> "messsage windows" -> set verbosity to 2 -> go back to vlc window and open the media with file -> open file/url ...

Can you post the output of the message window so we might be able to see what's the problem?

---

