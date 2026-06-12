---
title: "What should I use to RIP??"
date: 2011-01-29
forum: General Help
---

### Post by NertSkull on 2011-01-29
So I don't know what the best program to rip CDs is.

GRIP is dead.  I've built it myself and got it working, but without it being supported I'm not sure I really want to use it, or that its even working 100% right.

Rubyripper was almost impossible to get installed on my 10.10 64-bit.  But I did get it.  But it is amazingly slow.  Even from the command line it takes 2-2.5 hours to rip one CD (and my computer is only 4 months old).

And I don't know of any others that support FLAC and secure ripping.  I am trying to archive some of my CDs and I don't know what to use.  

Anyone have advice.  K3b doesn't seem to cut it for me.  I wasn't impressed with Soundjuicer's quality.  So for now I've been just using EAC on my laptop with Win7 until I can find something that is just as good as EAC for ubuntu.

Any ideas what that would be?

---

### Post by AlphaLexman on 2011-01-29
I loved Grip too, :( I tried rubyripper and ripperx, eventually just trusted the command line, and abcde.

[Here]("http://www.andrews-corner.org/abcde.html") is an excellent guide to set up your config file for abcde.

---

### Post by HermanAB on 2011-01-29
Nothing wrong with Grip.  It works. It doesn't have any serious bugs.  So why would anyone not use it?

---

### Post by AlphaLexman on 2011-01-29
> **HermanAB said:**
> So why would anyone not use it?
It hasn't been available in the repo's since 9.04. Unless you compile it yourself and solve the dependency hello.

---

### Post by shantiq on 2011-01-29
fastest and simple


```
 sudo apt-get install sound-juicer

```     then go applications/sound and video/sound juicer


if quality is really your main concern use [rubyripper ]("http://linuxappfinder.com/package/rubyripper") which is the closest to EAC linux has got so far
you can of course also use EAC under wine 

Both of these programs rip twice and compare the 2 files to make sure rip is perfect

                               ====================================

but **command-line** is maybe more fun  ===> [**here**]("http://ubuntuforums.org/showpost.php?p=10292500&postcount=5")

---

### Post by Noah0504 on 2011-01-29
I still use Sound Juicer.  Not sure if it's hated for a specific reason, but it always works well for me!

---

### Post by Swagman on 2011-01-29
Another Sound Juicer user here.

Why do people hate it ?

---

### Post by Noah0504 on 2011-01-29
> **Swagman said:**
> Another Sound Juicer user here.

Why do people hate it ?
I don't know that they do.  Haha.  If I had to guess, it would probably be how it actually rips the CD.  I think it has to do with the Sound Juicer rip not being "secure."

---

### Post by oldos2er on 2011-01-29
I use grip. It's been a long time since I looked at sound-juicer, but as I recall it didn't offer all the options that grip does.

---

### Post by uRock on 2011-01-29
I use Brasero to rip images and Sound Juicer to rip tunes. I have never had a problem with Sound Juicer.

---

### Post by NertSkull on 2011-01-31
Yeah I'm not anti-sound juicer for regular ripping.  I've used it before and it seems ok.

It was more that for archival purposes it doesn't seem to quite do the trick.

For now I've installed grip and I'm using that.  Although I've found nothing that claims its as good as EAC or rubbyripper.  But rubyripper is just unbearably slow.  And I can't get EAC to work under wine despite multiple people getting it to work.

So I guess grip it is for me.  All in all it works pretty well, and it claims its using cdparanoia.  So quality should be half decent.

Thanks all though for the input.

Oh, and grip wasn't too bad to install.  The "dependency hello" was easily solved with 2 minutes of googling, and all is now well.

---

### Post by dontbugmee on 2011-02-17
i tried sound juicer on 11.04, and it's a click factory [-X, also someone reported this as a bug like 3moths ago or so, but still does it for me, 

tried rubbyripper and i like it, but it's way too slow, i think for one track it rips it 4 times and compares it twice, 
i wish there was a way to just rip it twice and compare it once, that's good enough for me , or even just rip it once speed mode

---

### Post by stchman on 2011-02-17
It's not Sound Juicer's fault that your resulting MP3s are not the best sounding.  I have made a page that allows you to rip your CD using LAME in Sound Juicer.  You will have to install Sound Juicer.

```
sudo apt-get install sound-juicer
```


[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Hope this helps.

---

### Post by uRock on 2011-02-17
I have never had a problem with Sound Juicer. Having issues while using Natty might have nothing to do with Sound Juicer. Could be kernel related or a million other things. It is going to have bugs, that is why it is still in Alpha testing.

---

### Post by dontbugmee on 2011-02-17
> **stchman said:**
> It's not Sound Juicer's fault that your resulting MP3s are not the best sounding.  I have made a page that allows you to rip your CD using LAME in Sound Juicer.  You will have to install Sound Juicer.

Hope this helps.

i encoded with flac at highest quality, ill check out the link, thanks

---

### Post by dontbugmee on 2011-02-18
i found out that there is some kind of bug in ruby that makes rubyripper really slow in gui mode, but it works nice and fast in cli mode, good quality rips too

---

### Post by hugmenot on 2011-02-19
The latest project for secure ripping is morituri. But that has no GUI and it gave me an error last time I tried to use it on natty.

---

### Post by cascade9 on 2011-02-19
> **NertSkull said:**
> For now I've installed grip and I'm using that. Although I've found nothing that claims its as good as EAC or rubbyripper. But rubyripper is just unbearably slow.

That is fixable, you need to install ruby 1.9.2, see mc4mans post (#174) on this thread- 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10408621](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10408621)

> **hugmenot said:**
> The latest project for secure ripping is morituri. But that has no GUI and it gave me an error last time I tried to use it on natty.

I'll keep an eye on morituri (though the name is awful IMO, Latin for "those who are about to die"). It seems to just be using CDparanoia with a few extra bit and pieces, rubyripper uses a different secure ripping algorithm.

---

### Post by lykeion on 2011-02-19
Here's a review of some CD rippers incl. a few I hadn't heard about before like Asunder and Audex: [http://www.tomshardware.com/reviews/ubuntu-linux-audio-software,2856-8.html](http://www.tomshardware.com/reviews/ubuntu-linux-audio-software,2856-8.html)

---

### Post by hugmenot on 2011-02-19
> **cascade9 said:**
> I'll keep an eye on morituri (though the name is awful IMO, Latin for "those who are about to die"). It seems to just be using CDparanoia with a few extra bit and pieces, rubyripper uses a different secure ripping algorithm.

You are mistaken. Rubyrip is based on cdparanoia like almost any other linux ripper. And rubyripper only does the read&verify cycle, where you hope that reading twice will notify you of glitch problems. But that presupposes that you can defeat the cache.

Check here and feel educated:
[https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip#Comparison](https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip#Comparison)

---

### Post by cascade9 on 2011-02-19
> **hugmenot said:**
> You are mistaken. Rubyrip is based on cdparanoia like almost any other linux ripper. And rubyripper only does the read&verify cycle, where you hope that reading twice will notify you of glitch problems. But that presupposes that you can defeat the cache.

Check here and feel educated:
[https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip#Comparison](https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip#Comparison)

You are mistaken. Rubyripper uses a 2-pass rip, but its not using CDparanoias ripping algorithm, its got its own. 

Check here and feel educated- 
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

---

### Post by hugmenot on 2011-02-19
Check again. It uses cdparanoia to rip. And it rips twice using cdparanoia. And then it compares those rips. That is the "secure algorithm" that it uses. 

If your drive caches audio data then those comparisons don’t work. The drive will just return the same data from it’s cache. Now rubyripper uses cdparanoia’s cache circumvention to flush the cache.

Do you have anything else to add?

---

### Post by cascade9 on 2011-02-19
Errr...yeah, it uses CDparanoia to rip, but its in -Z mode 

> [FONT=Verdana, Arial, Helvetica][SIZE=3][COLOR=#002b8b]-Z --disable-paranoia
	      Disable  all  data  verification and correction features. When
	      using -Z, cdparanoia reads data exactly as would cdda2wav with
	      an  overlap  setting  of zero.	[/COLOR][/SIZE][/FONT]

[http://xiph.org/paranoia/manual.html](http://xiph.org/paranoia/manual.html)

Its not using the 'standard' CDparanoia ripping algorithm, its got its own. Which is what I was said originally. ;) 

Sure, AFAIK its still using the CDparanoia 'disable cache' but as far as I know that works just fine. Though I could be wrong on that, IIRC there was some talk about rubyripping getting a different disable cache than the CDparanoia version, I dont know if that ever happened.

---

