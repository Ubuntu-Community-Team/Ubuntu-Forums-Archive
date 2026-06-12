---
title: "Linux jukebox- software recommendations?"
date: 2006-05-03
forum: General Help
---

### Post by chris_andrew on 2006-05-03
Hi,

I have an old PC:  4GB, 128 Megs, P400.  I would like to convert it into a jukebox for MP3/ ogg's.

My preferred distro's are Debian based.

Can anybody suggest a way to build such a jukebox.  The box will be connected to the internet. The PC will only be used for music, so installing a whole general distro seems wasteful. It will also have access to a monitor, should it require one (PC is connected via a hub to my regular PC's/ SPARC boxes).

Any ideas?  

Many thanks,

Chris.

---

### Post by wylfing on 2006-05-03
Actually, regular old Debian is a good choice for this. Are you thinking of a music server where you listen to the songs at a separate desktop, or will this box actually be playing the music?

---

### Post by Keith_Beef on 2006-05-03
I did this yesterday.

Once I'd got WEP working on my Ubuntu Breezy box (an old HP vectra into which I stuck a NetGear wg311v3 card), I moved the box from the basement to the living room, and exported the /Music directory to be NFS mounted on the Mandriva box in the basement (loud AMD machine).

I connected the audio output to the aux input of the stereo, copied all my ripped CDs to the Ubuntu box and started up Beatbox. And it works, strraight off.

Then SWMBO came home, and saw this baige box with a monitor sitting under the stereo and CD rack.

Not happy. "I don't want to have to do informatiks just to listen to music!" ](*,) 

So it looks like she's back to swapping CDs by hand when she wants to listen to different music.

Now, if it had been a black and silver box, with a small LCD display in the front panel, or a 7" LCD touch screen, that would have been different. ;)

Beef.

No, no, no. Not "Beatbox". **Rhythmbox!**

---

### Post by chris_andrew on 2006-05-03
The computers are all in the same room, so it doesn't really matter.  I guess I will probably plug my speakers into the sound card, and just do it that way.  It could be useful to be able to control it through another computer, though.

If I did a minimal Sarge install for example, could you recommend any software?  KDE have a jukebox app, but it has always looked a bit bloaty.

Thanks,

Chris.

---

### Post by Ramses de Norre on 2006-05-03
Do you mean amarok? That's the best music player around for me. It has a pretty good user interface and an easy to maintain music library, just what you're looking for I think.

---

### Post by chris_andrew on 2006-05-03
Amarok could be useful.  Perhaps a basic debian install, plus amarok and dependencies.

---

### Post by bluenova on 2006-05-03
I've been using amarok ever since I moved to linux, I love it! And if you set it up with a mysql database it runs super fast.

---

### Post by Ramses de Norre on 2006-05-03
How do you do that? Sounds interesting..

---

### Post by wylfing on 2006-05-03
[QUOTE=chris_andrew]I guess I will probably plug my speakers into the sound card, and just do it that way. It could be useful to be able to control it through another computer, though...Amarok could be useful. Perhaps a basic debian install, plus amarok and dependencies.[/QUOTE]

This may be a pretty easy solution to do what you're thinking. Get just enough X and KDE installed to make AmaroK run. Then ssh -X into the jukebox computer and launch AmaroK from there. It will show up on *your* desktop but you'll be controlling the music on the jukebox.

Of course, you could also use the command line to control the jukebox's music playing behavior too, like mpg321 and oggplay and stuff like that. Although even with 4 GiB you probably have plenty of space, so why not run AmaroK over ssh and make things easier on yourself.

---

### Post by chris_andrew on 2006-05-04
ssh -X, now that sounds cool.

Will give it a try.  Would the sound come out of the original box, or somehow through the ssh -X session?

Cheers,

Chris.

---

### Post by purdy hate machine on 2006-05-04
I have a similar setup in my living room which is used for both music and movies. I didn’t want an ugly beige tower taking up space in the living room so I opted for a [Shuttle PC]("http://eu.shuttle.com/en/Desktopdefault.aspx/tabid-3/") which comes with 8 channel surround audio and TV out so there was no need for a separate monitor. I’m running Mepis on the box, music is handled by Amarok and movies by Kaffine.

---

### Post by chris_andrew on 2006-05-04
Will check your link out.

Cheers,

Chris.

---

### Post by wylfing on 2006-05-04
[QUOTE=chris_andrew]ssh -X, now that sounds cool.

Will give it a try.  Would the sound come out of the original box, or somehow through the ssh -X session?
[/QUOTE]

The sound would be coming out of the jukebox computer.

If you want the sound to come out of *your* computer, then you're talking about having a music server. In that case, try running mt-daapd on the jukebox. That'll serve up iTunes-like shared music for everyone on the network to tune into.

---

### Post by bluenova on 2006-05-05
[QUOTE=Ramses de Norre]How do you do that? Sounds interesting..[/QUOTE]
You just need to setup a new mysql database, and (as long as you have the latest amarok) in the amarok options you can set mysql instead of sqlite and it will ask for the db name, password etc.

---

