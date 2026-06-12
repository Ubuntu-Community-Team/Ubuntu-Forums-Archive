---
title: "Video Editing programs"
date: 2006-03-21
forum: General Help
---

### Post by deadgobby on 2006-03-21
Greetings,
 I got my new cool Leadtek Winfast TV 2000 XP up and running and pleased how simple it was. Now I would like to capture some video and edit it. I installed Kino, but when I go to capture video. It is a blank black screen. What am I doing wrong and how to correct it. Is there better capture/editing programs out there for Linux? Any help would be very nice.

---

### Post by damu on 2006-03-21
Kino seems to be the good choice for video capture. 
Installing the best linux video editing tools on Ubuntu might be a nightmare if, like me , you are not a pro of the command line... :) 

I want to switch to Linux for video editing too. I found it more practical to have dedicated live distros for specific task (video editing and sound production).

Probably the best distro for video editing is [Dynebolic]("http://www.dynebolic.org/")

You just boot from the dynebolic live cd, and here you are with the best video editing softwares for linux : [Cinelerra]("http://heroinewarrior.com/cinelerra.php3")
[jahshaka]("http://www.jahshaka.org/")
[FreeJ]("http://freej.dyne.org/")

I don't think it includes [PiTiVi]("http://pitivi.sourceforge.net/") , which seems to be a project worse monitoring for GPL video editing ...

Dynebolic also includes other tools like Gimp, Blender for 3D render, Ardour as a very professionnal multitrack studio,etc.

As far as Sound production is concerned, I purchased [Studio to go]("http://www.studio-to-go.com/") , which is quite an amazing distros for sound production. Ardour feels rock solid and dead professional compared to Cubase . Synchronised with Rosegarden (midi and audio sequencer) and Hydrogen, you can really produce some top qulity soundtracks. The great thing about Studio to go is that it just works! (it is the only one so far which works straight out of the box with my RME) and it has VST support implemented!
A good free alternative to Studio to go is [musix]("http://www.musix.org.ar/en/index.html")

You might also want to monitor these projects :

[64Studio]("http://64studio.com/wiki")

and off course,

[ubuntustudio.com]("http://ubuntustudio.com") which, even though in early stage, looks very promising.

---

### Post by deadgobby on 2006-03-21
Thanks for the information, I tried Xsane and still get a black sceen. I sees my card still nothing. It like that way with Kino.  Kino says my raw1394 mod needs to be loaded.The dev1394 dev = /dev/ieee1394/dv/host0/PAL/out .The Vtime works just fine. Do you know what may be causing this? I am going to Dynebolic once the ISO DL and burn that. I just not to keen on using a live CD cause live CD's are slow compare to a HD.
Thank you 
Gobby

---

### Post by damu on 2006-03-21
Can't help you with your specific issue on Ubuntu.
With live cd, launching an application is slower, but once the application is launched you shouldn't notice much difference in the speed of the processing.

However, with Dynebolic, you can make an image on your HD.

I forgot to mention [mediainlinux]("http://www.mediainlinux.org/"), distro presented as the swiss knife for multimedia on Linux.

Have fun. :-D

---

### Post by deadgobby on 2006-03-22
Thanks for your help. I tried out dyne and will play with it. At least it sees the TV card.
GObby

---

### Post by deadgobby on 2006-03-22
Oh crap, now it sees it and now it don't. Now I am on a mission of getting this to work. ](*,)  I just may do the daul boot the HD with the linux o/s you mechened. See if that works, if not, try Suse too.

---

### Post by sham69 on 2006-03-26
I think these other fellows are on the wrong track. They are talking about programs that take digital video from a digital video cam or other such source and edit that.
You are talking about recording TV, I believe.
I think the only program I've heard of that will do that, with your card (same as mine) is Myth TV. The install for that looks very frightening for a noob and I haven't even downloaded it. It involves setting up SQL databases, etc.
Check it out, though.
I am still recording TV and editing in Windows for now, as I can't find the tools to record to mpeg (using software encoder, which your card requires) and edit that. If you want to record to .avi, you may have better luck.

---

### Post by RikoW on 2006-03-27
If you want to record TV streams from a card, I can also recommend kaffeine, which is the kde media player. I don't know, though, if your specific card is supported, but if it can be used with mythtv, I assume it should also work with kaffeine.

mythtv is of course a multimedia program on a bigger scale than kaffeine. However, I didn't manage to get it to work (did not try very hard, but it's not an out-of-the-box installation). If you just want to watch tv, record some stream and set timers for recording, kaffeine works great for me.

Cheers,

             Riko

---

