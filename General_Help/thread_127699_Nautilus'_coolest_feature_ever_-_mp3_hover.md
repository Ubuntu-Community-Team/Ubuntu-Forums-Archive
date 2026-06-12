---
title: "Nautilus' coolest feature ever - mp3 hover"
date: 2006-02-09
forum: General Help
---

### Post by z_diver on 2006-02-09
In nautilus I can hover over any mp3 file and hear the song play.  It's AWSOME.  I can check out a folder full of mp3s in 15 seconds flat.

This just started working out of the blue on my desktop today although it's still not working on my laptop.  Anyone know how to fix it there?

---

### Post by cdhotfire on 2006-02-09
Open up Home folder or any other.  Click "Edit -> Preferences". Now click the "Preview" tab, go down to "Sound Files", select either "Always" if you want it to preview sounds on different harddrives or "Local Files Only" if you want it only to preview on your main harddrive, usually your Home folder.

Good luck. :)

---

### Post by z_diver on 2006-02-09
Nope, that didn't do it.  I have 4 ubuntu machines and of those it only works on my desktop.  I noticed that Ubuntu had some updates today and one was for alsa but that still didn't do the trick.

I don't mind if these features take some setting up but I sort of do mind when they are undocumented.  Am I volunteering?  Sure.  How do I start?

---

### Post by z_diver on 2006-02-09
Well, I'm still not sure what it was but it works after installing Automatix on one of the laptops.  I selected the various free and non free codecs plus most of the music players he lists in 5.4-1 and now I can hover and hear music.  

So once again Automatix comes to the rescue.:KS   Damn handy.  He's got a lot of stuff available in there.

---

### Post by sabredog on 2006-02-09
I discovered this feature last week. What a handy thing to have, a nice integration of multimedia into a desktop.

Well done, Ubuntu and Automatix!

cheers

---

### Post by xmastree on 2006-02-09
It's werid though, if you **don't** know about it, and are listening to music at the time...

---

### Post by nik on 2006-02-09
Well, I would like to know how it's done, without automatix... So please post if you figure out what happened :)

---

### Post by Stormbringer on 2006-02-09
@nik: Got it to work by typing the following magic words in a terminal (the info is hidden somewhere in the wiki):

```

sudo apt-get install mpg321

```

If the MP3 hover doesn't work straight ahead, log out and back in.

Storm.

---

### Post by z_diver on 2006-04-09
[QUOTE=Stormbringer]

sudo apt-get install mpg321

If the MP3 hover doesn't work straight ahead, log out and back in.

Storm.[/QUOTE]
YES INDEED.  Worked for me on my new Dapper install.  Seeing that Gnome has the feature built in and mpg321 is all of what, 34 kB, seems like it should be default in Dapper!!!

I'm heading to malone now.

---

### Post by trent dillman on 2006-04-09
Yes, this is such a sweet feature. Especially when your Windows friends are around. :-P

---

### Post by bionnaki on 2006-04-09
kde does this as well with konqueror

---

### Post by z_diver on 2006-04-09
Seeing how it will work in both Gnome and KDE, I filed a bug report to add mpg321 to the Dapper Drake release by default.  If you want to see it also, let them know on Launchpad.

[https://launchpad.net/distros/ubuntu/+source/mpg321/+bug/38828](https://launchpad.net/distros/ubuntu/+source/mpg321/+bug/38828)

---

### Post by Hairy_Palms on 2006-04-09
id guess its not default due to it being an mp3 thing, and no mp3 codecs are installed by default so it wouldnt work "out of the box" so to speak.

---

### Post by Ziggurat on 2006-04-27
It does not work with .ogg files (at least for me) and that seems really strange being ogg and open format and mp3 not.

Maybe i have to install a little ogg player i dont know about??

---

### Post by krusbjorn on 2006-04-27
[QUOTE=Ziggurat]It does not work with .ogg files (at least for me) and that seems really strange being ogg and open format and mp3 not.

Maybe i have to install a little ogg player i dont know about??[/QUOTE]

Works here. I dont know which package is needed, but i would guess vorbis-tools,  some libvorbis*- or libogg*-package or gstreamer0.8-vorbis.

Anyone know how to get it working in list view? Only works in icon view right now.

---

### Post by ronmarley1 on 2006-04-27
[QUOTE=Ziggurat]It does not work with .ogg files (at least for me) and that seems really strange being ogg and open format and mp3 not.

Maybe i have to install a little ogg player i dont know about??[/QUOTE]
Works for me also...
rg

---

### Post by thesm on 2006-04-27
[QUOTE=xmastree]It's werid though, if you **don't** know about it, and are listening to music at the time...[/QUOTE]

Yeah, I thought I was going crazy until I realised what it was.  Very nifty  feature.

---

### Post by Shay Stephens on 2006-04-27
[QUOTE=Stormbringer]@nik: Got it to work by typing the following magic words in a terminal (the info is hidden somewhere in the wiki):

```

sudo apt-get install mpg321

```

If the MP3 hover doesn't work straight ahead, log out and back in.

Storm.[/QUOTE]

Thank you!!!  That worked for me without having to log out.

---

### Post by sinkxdie on 2006-04-27
Haha, I had a windows friend around, showed him this, and he was instantly begging me to install Linux onto his computer. :D

---

### Post by djsroknrol on 2006-04-27
That is the nicest little feature yet...thanks guys !!....

---

