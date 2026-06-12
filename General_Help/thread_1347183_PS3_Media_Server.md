---
title: "PS3 Media Server"
date: 2009-12-05
forum: General Help
---

### Post by Nixie Pixel on 2009-12-05
Is there a web configuration available for PS3 Media Server? I have it installed on a headless Ubuntu Server (8.10), and I'm having real problems configuring it. I would love to be able to connect to the server via a web browser and configure it, if possible.

Barring that, what is a simple way to have it rescan content directories from the terminal via ssh? (If that is possible...) I added a video file to one of the watched directories and it has not automatically added it (or at least my XBox 360 can't see it yet).

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
XBMC watches my samba shares and adds everything automatically... in fact it downloads the movie posters and actor's pictures and all kinds of fun stuff with music too. Not sure how to do what you're asking though.

---

### Post by Nixie Pixel on 2009-12-05
> **Sin@Sin-Sacrifice said:**
> XBMC watches my samba shares and adds everything automatically... in fact it downloads the movie posters and actor's pictures and all kinds of fun stuff with music too. Not sure how to do what you're asking though.
Hmm, interesting. I'm getting tired of switching to different media servers - twonky, fuppes, ushare, media tomb, now ps3 media server. I just want one that I can set up and run, which will watch my samba shares and stream to my XBox 360 without a lot of extra work.

I can set up XBMC on a headless server, and let it run without a lot of extra work? 

Will it transcode .mkv files for my XBox 360? (not a necessity)

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
It was pretty easy for me to setup. All GUI. In the videos section of XBMC just add the folders and set the options and leave it go. I just went back to it from mythtv because of the new found x64 support and even though it's considered beta I haven't had a single glitch. Not sure about the mkv files but the program was originally made to run an xbox media client/server. [http://xbmc.org/](http://xbmc.org/)

---

### Post by Nixie Pixel on 2009-12-05
Hmm, well as it is a headless server (i.e. no monitor) I would have to run the install via ssh, and then connect to some sort of web interface - can you configure and manage mythtv/xbmc via a web browser from another machine?

Thanks!

---

### Post by renkinjutsu on 2009-12-05
If you're talking about [this]("http://ps3mediaserver.blogspot.com/"). Then there's a way to configure it using the command line, and the settings are also saved in a text file so you won't have to specify all the parameters everytime you start it. There's a user maintained documentation of all the options in the [forum]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=254") .. I use pms myself, and new videos are available on my PS3 as soon as i put it in the directory, so there shouldn't be a problem at all.

If you're too lazy to learn to use the command line interface, you can probably fire up PMS in a graphical environment and tweak it to your liking, save the configuration, then copy the configuration file over to your headless server.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
I'm sure you can. Just did a locate of *xbmc*.conf and *xbmc*.list and there were a lot of results so it might not be quite as easy. I found [this]("http://blog.xbmc.org/forum/showthread.php?t=55282") but it looks like it installs as a bootable server. Might shed some light though. I've changed a few of the configuration files but because of the extensive GUI I never really had to. I guess I wasn't much help considering you were looking for a non-GUI method... sorry.

---

### Post by Nixie Pixel on 2009-12-06
> **renkinjutsu said:**
> If you're too lazy to learn to use the command line interface, you can probably fire up PMS in a graphical environment and tweak it to your liking, save the configuration, then copy the configuration file over to your headless server.
Well, it isn't so much laziness as it is lack of time. This stuff is a hobby for me, but it is sometimes time-prohibitive.

That's the beauty and the drawback to having so many different options to do what you want to do. When you look at a computer as a tool rather than a tinker-toy, sometimes linux can be frustrating. This is one area I'm finding frustrating and rewarding at the same time...

I'll look into the config options for PMS since my server has no head and I can't seem to figure out either VNC or NX (another frustration... ](*,)), and I'll see if MythTV (since I do need x64 support) can also do what I'd like, headlessly :P

---

### Post by zaphod777 on 2009-12-06
Here is a post in the PS3 media server forums on this

[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4547](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4547)

---

### Post by renkinjutsu on 2009-12-06
> **Nixie Pixel said:**
> Well, it isn't so much laziness as it is lack of time. This stuff is a hobby for me, but it is sometimes time-prohibitive.

That's the beauty and the drawback to having so many different options to do what you want to do. When you look at a computer as a tool rather than a tinker-toy, sometimes linux can be frustrating. This is one area I'm finding frustrating and rewarding at the same time...

I'll look into the config options for PMS since my server has no head and I can't seem to figure out either VNC or NX (another frustration... ](*,)), and I'll see if MythTV (since I do need x64 support) can also do what I'd like, headlessly :P

if you're trying to pull graphics from your headless server (i'm assuming it has X properly installed), i say forget about VNC and NX. You've already got SSH!

for X forwarding, start ssh with the -X option, and you'll be able to start gui applications from the terminal and have the window open up on the ssh client machine!

---

### Post by Nixie Pixel on 2009-12-06
> **renkinjutsu said:**
> if you're trying to pull graphics from your headless server (i'm assuming it has X properly installed), i say forget about VNC and NX. You've already got SSH!

for X forwarding, start ssh with the -X option, and you'll be able to start gui applications from the terminal and have the window open up on the ssh client machine!
I have tried that, I still have problems trying to start a session:

```
nixie@lion:~$ sudo gnome-session
[sudo] password for nixie: 
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.

** (gnome-session:2854): WARNING **: Cannot open display:
```
But I suppose that is a discussion for another thread...

---

### Post by renkinjutsu on 2009-12-06
why are you trying to start a gnome-session? And as root?
I've never actually done that before :p maybe i'll try that.
But, what i usually do is type in *program &* and the window pops right out.

Also, if you really want to start a gnome-session, try it without sudo, because the root account probably has no configuration for GNOME at all.. all the files are in your own ~/ directory. If gnome-session doesn't work, try ```
gnome-panel &
nautilus &
```
That's a huuge part of gnome already

but what i'd do, would be '. /path/to/PMS &' to open up the program instead of a whole session.

edit: Also, if loggin is successful, with the -X option, then 'echo $DISPLAY' should spit out 'localhost:10.0'

---

### Post by Nixie Pixel on 2009-12-06
Heh, sorry, I don't know anything at all about X forwarding, I was just doing what someone suggested I do in this situation. I'll try the command you gave me and see what happens...

Ok, here are the results. No idea if it worked or not (but I don't have the PMS config util popping up on my local machine...).

```
nixie@lion:~/pms-linux-1.10.5$ -bash: ./PMS.sh: Permission denied

[1]+  Exit 126                ./PMS.sh
nixie@lion:~/pms-linux-1.10.5$ sudo ./PMS.sh &
[1] 16204
nixie@lion:~/pms-linux-1.10.5$ 
```

---

### Post by renkinjutsu on 2009-12-07
hm.. permission denied error. Try making that file executable ```
chmod +x ./PMS.sh
```
and try again. I remember having to do that myself when i set up pms

---

