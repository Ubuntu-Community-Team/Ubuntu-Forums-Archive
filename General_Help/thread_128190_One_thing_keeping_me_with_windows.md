---
title: "One thing keeping me with windows"
date: 2006-02-10
forum: General Help
---

### Post by psilo357 on 2006-02-10
easy dvd backup, i cannot for the life of me get ANY of the utilities for linux to work, ive set up a bunch of other programs and whatnot, but the backup programs simply will not work.  In windows i used dvddecrypter and dvdshrink to do the backups....and they worked and still work great for me.  Ive tried k9copy, xdvdshrink, and wine with dvddecrypter and shrink for windows, and nothing....If there is a simple guide for setting these programs up and have them actually work that would be great, or any other help you guys could offer.

thanks 

peace

ps...if i can get this to work, windows will have only one use to me, and that is games.

---

### Post by Zelut on 2006-02-10
I use xdvdshrink (from the repositories) and it works just fine.  I don't use the GUI but I don't think that would matter much.  What errors are you getting?  Does it not work at all?  Only burn coasters?

---

### Post by cdhotfire on 2006-02-10
Very easy.

Lets grab the tools.
```

$ sudo apt-get install mkisofs gnomebaker

```

Okay we are ready.

Lets start by making a folder at "Home" and calling it "dvd".  Now we go to "Computer" and go into the dvd drive and copy the "AUDIO_TS" and "VIDEO_TS" over to the new folder we made called "dvd".

Now you do:
```

$ mkisofs -dvd-video -o dvd.iso dvd/

```

Now it should create a dvd.iso.

Open up Gnomebaker and press "Burn DVD Image", select your newly made dvd.iso, and let the burning start. :)

Hope this works for you, good luck.

---

### Post by akiro.yamamoto on 2006-02-11
I use the wine 0.93 ( .deb package from winehq.com) version with DVD Decrypter and DVD Shrink with no problems.
For DVD Decrypter use "winecfg" and just specify Win NT. That's all the real configuration you have to do.

---

### Post by ohman11 on 2006-02-12
[QUOTE=cdhotfire]Very easy.

Lets grab the tools.
```

$ sudo apt-get install mkisofs gnomebaker

```

Okay we are ready.

Lets start by making a folder at "Home" and calling it "dvd".  Now we go to "Computer" and go into the dvd drive and copy the "AUDIO_TS" and "VIDEO_TS" over to the new folder we made called "dvd".

Now you do:
```

$ mkisofs -dvd-video -o dvd.iso dvd/

```

Now it should create a dvd.iso.

Open up Gnomebaker and press "Burn DVD Image", select your newly made dvd.iso, and let the burning start. :)

Hope this works for you, good luck.[/QUOTE]


I get his error

INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.

---

### Post by cdhotfire on 2006-02-12
Try
```

$ sudo apt-get install dvdauthor
$ dvdauthor -o dvd -T

```

This makes new INFO files. Do this before mkisofs.

---

### Post by handy on 2006-02-12
I use DVDshrink under Wine, no probs, same speed for me as xp.

I then burn with NeroLINUX, easy as can be.

One caveat, don't install Internet Explorer with Wine.  Somehow it messes up DVDshrink's display!!!??

---

### Post by Cathbard on 2006-02-12
If you like Nero you might want ot have a look at k3b. It comes with kde normally but I run it fine on Gnome. It gives a really cool gui burner interface that is very easy to use. You can get it from the Ubuntu repositories. It will want to install some kde components too; they won't hurt your gnome desktop.

I have burnt things that my brother (who is a windows nut) hasn't been able to and he has a plethora of windows burning tools. The coasters at my house are cd's labelled "Windows Coaster V1.0" and "Windows Coaster V1.1" for the dvd's.
I don't have any "Linux Coasters"
After watching me copy "uncopyable" discs on Linux, my brother decided to take a copy of Ubuntu home with him. (An aside: My 60 yr old mother uses Kanotix already because of the virus /spyware issue with winblows and she loves it. It makes me laugh when people say linux is too hard, what they usually mean is they are too lazy to learn it.)
Don't give up on Linux, cd/dvd burning is actually one of it's strong points.

---

### Post by handy on 2006-02-13
Thanks for that Cathbard!

On your recomendation I'll check out k3b.  

I installed nero 'cause it was relatively cheap & easy, after using the demo to  burn 6 or so of my DVD's, which all turned out - no coasters.

My attitude is, to use whatever is easiest, at this early stage of my Ubuntu career, with the desire to use OpenSource software wherever possible.  Eventually I'm sure that OpenSource will be all that I use, with perhaps the exceptional game or two...:mrgreen:

---

### Post by blackant on 2006-02-13
If only I can get my canon IP6000D printer to work without purchasing the driver.

Guess I can't go totally without windows for support for hardwares. :(

---

### Post by Cathbard on 2006-02-15
[QUOTE=blackant]If only I can get my canon IP6000D printer to work without purchasing the driver.

Guess I can't go totally without windows for support for hardwares. :([/QUOTE]

Have you tried the BJC6000 driver supplied with Ubuntu (or maybe one of the other BJC's perhaps)? I have read people having success with pixmas that way.
Worth a try anyway.

---

