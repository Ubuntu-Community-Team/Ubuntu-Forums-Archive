---
title: "music server and station"
date: 2010-02-05
forum: General Help
---

### Post by woutervddn on 2010-02-05
hey all,

I'm currently building a Music Station/Server that enables my girlfriend and I to control what music is playing on the central computer (with audio system attached).
So the setup has to be on a way that she can control the music at the same time as I am doing it.

I first thought of XBMC but with the html controls I wasn't able to add songs to the play queue and cycling all songs wasn't easy either.
So I figured we could use VNC to access the xbmc but apparently VNC dislikes it when I click inside XBMC, it just isn't responding to it. (and image transfer is reaaaaaallly slow).
So back to zero I tried Elisa and Moovida (still like elisa more than moovida, don't know why) but same story here. It seems that VNC won't let me click on full screen applications.
An other thing about moovida is that you can't make a queue. 
So apparently I'll have to find a program with tons off options (so exclude 90% off all media centers) that looks nice and has a front end that is capable of beeing controlled via a web browser or via VNC.
So I think it has to be something like winamp for windoze but with a nice and smooth front end.
any ideas?

Other question, the station has to be able to share the optical drives with the other computers in the network because my girlfriends laptop refuses to accept any purple colored dvd.
For that reason it would be nice if the rest off the OS was able to be controlled to (with vnc), but which distro should I use? Ubuntu, Kubuntu, Xubuntu,.. Other,..

Any ideas welcome..

Wouter Vandenneucker

---

### Post by nothingspecial on 2010-02-05
Have a look at squeezebox server.

---

### Post by woutervddn on 2010-02-05
sounds intresting, I'm going to test it later on (when I'm @ school, my download rate shows I've only got 2% left :p)

---

### Post by woutervddn on 2010-02-05
so, I just installed squeezebox server but I can't find it anywhere.. how do I use it now? and can I control the computer on which it is installed from other computers in the network?

---

### Post by nothingspecial on 2010-02-05
It should run on boot.

To configure it, on your main computer in your web browser type in tha address box [http://localhost:9000/](http://localhost:9000/).

Now you need a player. Vlc works well, they have their own called softsqueeze, or there is one that runs in the backgroung called squeezeslave. There`s plenty of tutorials on the web.

To control it from your other computers in your browser ipaddressofyourmainpc:9000

for example 192.168.2.3:9000

---

### Post by nothingspecial on 2010-02-05
As I`ve just done it myself I`ll make it easy for you - On the computer that you want to play the music on and has squeezebox server installed.

```
mkdir ~/bin
``````


cd bin
``````


wget http://sourceforge.net/projects/softsqueeze/files/squeezeslave/squeezeslave-0.9.95/squeezeslave-0.9-95-lnx24.tar.gz/download
```

```
tar -xvf squeezeslave-0.9-95-lnx24.tar.gz 
```
```

chmod +x ~/bin/squeezeslave-lnx24 
```
```
 squeezeslave-lnx24
```

Now if you open the web interface as described above, there should be a player listed in the right hand window of the home page. That is your music playing computer.

The only thing I`m unsure of is wether you have to specify an ip address for your server, because I have just done this on a remote box.

Have fun;)

---

### Post by woutervddn on 2010-02-05
owkeej, now I went to the server and indeed, it was running.
But I'm wondering, If I access this on an other computer, where is the music playing then? on the pc that has the server installed or on the other one?

EDIT:
If I just put a media player on the pc that has the server installed and put the stream.mp3 on this will be the only one playing the music. Unless I put the stream.mp3 on an other computer. Is that correct?

---

### Post by nothingspecial on 2010-02-05
See post above.

You must have squeezebox server and squeezeslave installed on the big pc you want to play the music from.

Do not remove  squeezeslave-lnx24 from ~/bin as this is the program playing the music.

Typing  squeezeslave-lnx24 starts it.

You can install  squeezeslave-lnx24 on both your laptops and play the music on them remotely aswell.

Oh and did I mention there`s about 10 billion radio stations to listen to aswell.

---

### Post by nothingspecial on 2010-02-05
We seem to be getting our posting mixed up. I`ve never done it the stream.mp3 way. The way I`ve posted above will work.

---

### Post by woutervddn on 2010-02-05
Well, I just installed it. And now it's rebooting.
I'll give it a shot right a way ;)

seems to do everything exactly like I want it ^^

thx

---

### Post by nothingspecial on 2010-02-05
Better start saving up.

[http://www.logitechsqueezebox.com/products/overview.html](http://www.logitechsqueezebox.com/products/overview.html)

---

### Post by woutervddn on 2010-02-05
the program works fantasticly,
There's only one (big) but about it.
It's so damn small, it takes 20 seconds before it reacts. Can this have anything to do wih LAME? I havn't installed the LAME encoder but I'm doing it as soon as I'm home.. 
Do you experience problems with it?

Kind greetings

Wouter

PS: Thx for the link :p It might explain much xD

---

### Post by nothingspecial on 2010-02-05
How did you install squeezebox server?

---

### Post by woutervddn on 2010-02-05
I downloaded it from mysqueezebox.com/download.

Why?

---

### Post by nothingspecial on 2010-02-05
Last time I downloaded it you used to have to do a

```
sudo apt-get install -f
```

after installing it, but that was a long time ago.

Do you have alot of .m4as (the itunes mp3 format)?

---

### Post by woutervddn on 2010-02-05
no I  don', I don't use itunes for some reason it allways crashes..

but everything works now (only accessing over lan doesn't work, I still have to open up the 9000 port), I just tested it with an adhoc.

I have the server running on pc1 and vlc player on pc1 plays [http://localhost:9000/stream.mp3](http://localhost:9000/stream.mp3)

In pc2 I go to "http://10. ...:9000" I select a song, press play.

14 seconds later pc1 starts to play the song..

Is this normal? I've got 192kbps bitrate and used the fasted lame encoder..why does it take so long?

Do you have the same problem?

Wouter

---

### Post by nothingspecial on 2010-02-05
I`m not using vlc, I`m using squeezeslave. I`ve given you some copy and paste commands to install it earlier in this thread. It works instantly.

---

