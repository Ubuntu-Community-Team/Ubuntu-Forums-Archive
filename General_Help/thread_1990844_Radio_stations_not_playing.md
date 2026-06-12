---
title: "Radio stations not playing"
date: 2012-05-29
forum: General Help
---

### Post by Yumi on 2012-05-29
I used to listen to my hometown radio station on Banshee. Since the update to 12.04 neighter Rhythmbox nor Banshee are playing radio.

Music files play ok. But selecting my radio station, press play and in a fraction of a second it returns to "not playing". The URL is ok as before. Rhythmbox then displays a red stop sign in front of the radio station entry.

Suggestions where to look please?

Michael

---

### Post by VE6EFR on 2012-05-29
What is the URL of the station that you are trying to listen to? I can try it here and see if it works for me.

Also, are any other stations working for you? Here are two that that my wife and I run that work fine in Banshee. If you want give it a try and see if it works on your system. Just click on Media, then Add Station. The following you would enter in the stream URL field:

Edmonton Fire Department - [http://s6.voscast.com:7792/](http://s6.voscast.com:7792/)
Edmonton EMS - [http://s6.voscast.com:7794/](http://s6.voscast.com:7794/)

Station website - [www.edmontonfireradio.com](www.edmontonfireradio.com)

The EMS stream is a lot more active than fire, but I wanted to list both just in case one wasn't working for you.

---

### Post by sammiev on 2012-05-30
Please leave us the addie to the radio station you wish so we can test it. :)

---

### Post by Yumi on 2012-05-30
The speciffic station I want to listen to is a Bavarian forest joodeling one with the URL: [http://login.streamplus.de/player.php?spt=4877](http://login.streamplus.de/player.php?spt=4877). But the same happens on all the preset stations like [http://vu.wsum.wisc.edu/wsumlive.m3u](http://vu.wsum.wisc.edu/wsumlive.m3u).

VE6EFR I tried the stations you mentioned, same thing. I think it is not the station and not the internet, it must be something within my computer, speciffic ubuntu.

Michael

---

### Post by jim_24601 on 2012-05-30
What format are the files that you can play in? You will need MP3 support to play most Internet radio stations, which I believe you have to install separately due to licensing issues.

---

### Post by Yumi on 2012-05-30
Well, they are mp3 files which are playing when stored on the computer.

Googled for "ubuntu 12.04 install mp3 support" and it indeed mentions something in "10 things to do after upgrading to 12.04". But would you believe it, all this sites are blocked here in China! Everything with blog in the URL or wordpress and god knows what - blocked.

Michael

---

### Post by sammiev on 2012-05-30
I can listen to the first one with my default programs like Real Player and VLC but the second address did not work for me.

---

### Post by sgage on 2012-05-30
> **Yumi said:**
> The speciffic station I want to listen to is a Bavarian forest joodeling one with the URL: [http://login.streamplus.de/player.php?spt=4877](http://login.streamplus.de/player.php?spt=4877). But the same happens on all the preset stations like [http://vu.wsum.wisc.edu/wsumlive.m3u](http://vu.wsum.wisc.edu/wsumlive.m3u).

VE6EFR I tried the stations you mentioned, same thing. I think it is not the station and not the internet, it must be something within my computer, speciffic ubuntu.

Michael

Working fine here - I must say that's a snappy "Zweanaika Polka" they've got going!

I have had no problem with a wide variety of Internet radio streams. You might try installing ubuntu-restricted-extras - that might provide some missing codec or the other.

[Edit: I'm using Rhythmbox.]

---

### Post by Yumi on 2012-05-31
Thanks, but I wish to listen to that polka to.

Ubuntu-restricted-extras are installed.

I thought maybe this URL's are also blocked in China. But this is not the case.

Michael

---

