---
title: "Things that are keeping me from moving to Linux"
date: 2006-04-04
forum: General Help
---

### Post by 3david on 2006-04-04
I've been using Linux on and off for the past 5 years, and I've written a list of things that are keeping me from moving to Linux:

[http://www.ee.bgu.ac.il/~elentok/wiki/LinuxNotYet](http://www.ee.bgu.ac.il/~elentok/wiki/LinuxNotYet)

I would love to hear people's comments about my list, maybe I could get some solutions and finally move to Linux completely.

Thanks,
   David.

---

### Post by aysiu on 2006-04-04
It sounds as if you're a far more advanced user than I am, and you're quite picky (I don't mean that as an insult). Yes, Linux "as is" probably won't suit your needs, and it sounds as if you've tried everything. Sorry.

Firefox 1.5 will be available through the repositories in Dapper.

---

### Post by 3david on 2006-04-04
Yeah, I know, I'm an extreme customizer :-)

---

### Post by karthik085 on 2006-04-04
I have had similar problems like you had too. Linux Desktop is still evolving. 

Alternatives to foobar2000:
Recently, try xmms2. It is still under development, but probably can solve your problems.
Quod Libet - one of the best audio player.
foobar2000: Does it work with wine? Using wine to do might be difficult, but not impossible.

ICD2 IDE: Try Piklab
[http://sourceforge.net/projects/piklab/](http://sourceforge.net/projects/piklab/)

Gstreamer:
Maybe xine, mplayer can help you.

Firefox 1.5 is available in dapper and not id breezy due to backporting issues.

[QUOTE=3david]I've been using Linux on and off for the past 5 years, and I've written a list of things that are keeping me from moving to Linux:

[http://www.ee.bgu.ac.il/~elentok/wiki/LinuxNotYet](http://www.ee.bgu.ac.il/~elentok/wiki/LinuxNotYet)

I would love to hear people's comments about my list, maybe I could get some solutions and finally move to Linux completely.

Thanks,
   David.[/QUOTE]

---

### Post by az on 2006-04-04
"Wine
I haven't tried to install it in about a year, but last time I tried it was a real pain in the *** to install and configure."


sudo apt-get install wine.



"Stuff that don't make sense to me
Why use GStreamer? it's a resource hog, when I play a movie with it, my hard drive works non-stop, but when I use mplayer or vlc it's quiet, no constant disk-access. I've also checked Dapper flight 5, and the gstreamer that comes with it doesn't seem improved hd-usage-wise."

Gstreamer is a free-libre implementation of a lot of codecs.  Why use anything else?  It's a framework for multimedia codecs.  With it you can easily build apllications for movie editing and the like.



"Why can't I update to firefox 1.5.0.1 on Ubuntu 5.10 with a simple "apt-get update firefox" or something?"

Because of the dependencies.  Gnome uses the gecko engine for rendering certain things like their help tool.  Development is on the source level, not the binary level.  Really, this is a minor inconvenience to only a few users and a huge convenience to development.

---

### Post by 3david on 2006-04-04
You ignored the part about GStreamer being inefficient, although I do hope that it will improve, after all it's a rather new project.

You said "Why use anything else?", my answer to that is that it chokes my hard drive, and i really don't like that.

And also, even with the multiverse codecs it still can't play anything useful.

Oh, and why not vlc? as I understand it's codecs are opensource as well (or am I wrong...?), and it's extremely efficient cpu/hd-wise, only problem i have with vlc is the ugly subtitles.

---

### Post by limaunion on 2006-04-04
Check this site for a GNOME equivalent of Amarok:

[http://listengnome.free.fr/](http://listengnome.free.fr/)

and this thread: [http://ubuntuforums.org/showthread.php?t=126080&highlight=gnomebaker](http://ubuntuforums.org/showthread.php?t=126080&highlight=gnomebaker)

---

### Post by hugmenot on 2006-04-04
Six times check. The answer to the first question is *-drum-roll-* Quod Libet¹.

Stop looking for duplicates and embrace equivalents I'd say.

[COLOR="DimGray"]¹Global shortcuts apart from standard multimedia keys need to be done by the window manager. I used echo random album > ~/.quodlibet/control; echo next > ~/.quodlibet/control to add skip to random album for instance.
That makes Play/Pause, Next, Random Album, Show/Hide, Search Library all on my otherwise useless three special keys.[/COLOR]

---

### Post by 3david on 2006-04-04
[QUOTE=hugmenot]Stop looking for duplicates and embrace equivalents I'd say.
[/QUOTE]

I'm not looking for duplicates, I'm looking for equivalents, and not just equivalents, i'm looking for solutions that would be even more than the original, that's why I wrote down the minimal list of features i need.

---

### Post by DJiNN on 2006-04-04
I know what you mean. There are many things that can be done (Right or wrong) in Windows that's just so much easier! .... And yet, in spite of the fact that I have just purchased a Creative Zen Touch which (try as i may) i CANNOT get to work with Gnomad2, i still use Ubuntu Breezy as my main desktop..... & why? Because since i have been using it full time (Which is only the last 4 months) I have actually "USED" my computer so much more than when i had XP in full time use. I get more done, and i really enjoy it.

Sure, there have been, and continue to be, many times when i think "Why not just go back to XP & save yourself the hassle?"...... like the whole Zen Touch thing. If i want to copy tracks onto it. i have to re-boot into windows! But that's not the fault of Linux.... it's Creatives fault for tying itself into ONE OS alone.

Why will i stay with Ubuntu when i resonate so much with what you say & agree also? Because it's driven by people who listen, people who care, people who help, and it's a damn good OS, & it's still in its infancy!! Wow!.... that's so much more than can be said for XP.  Plus the fact that i don't have to spend my time faffing about updating Anti Vir's etc...... 

Everytime Firefox crashes (& it does, EVERY DAY!) i get slightly hacked off..... & then I remind myself that this whole OS is free..... COMPLETELY FREE, and also built on the back of people that WANT to make it better & offer more, and that can only come with time & effort. Linux, & Ubuntu has come so far in such a short space of time,..... it's worth putting up with some of the crap just to be able to be part of a movement that's growing so fast & in such a great way!! Long may it continue! :)

Sorry about the rant...... too much Absynth!! But it had to be said..... Ubuntu ROCKS>....!! Regardless of any flaws that it may have! :)

DJiNN

---

### Post by elamericano on 2006-04-04
[QUOTE=azz]
sudo apt-get install wine.
[/QUOTE]

As if Wine is just going to work after that. Anyway, do I misunderstand that if you get all the other solutions you're looking for that you'll still want to torture yourself with Wine?

---

### Post by wolfee on 2006-04-04
Very well put DJINN!!! I have been using Ubuntu for 3-4 weeks and I have it as my main os on my viao 2.o ghz p4 512 ram machine with NO PROBLEMS!!! Ya I have some issues with tar gz and source file compiling and installing, but like yousaid THE PEOPLE HELP!!! I have had so many people give me links with step by step instructions THAT WORK!!!!! @#$% microshaft!!! I have xp "pro" on my "old" machine 733 mghz 256 ran dell optiplex gx110 only for bible software like esword that just won't work on linux, and maybe 3d max which I don't know yet if that will run on 256 ram 733. It will NEVER SEE THE INTERNET!!! because xp sucks!!! It is the most comprimised operating system EVER!!! Ther are no threats with Ubuntu thats why it's my main os and why I "put up" with it's little quarks!!

---

### Post by Hairback357 on 2006-04-04
I know exactly what your saying. I started using Linux to put on my kids computer. They were always screwing up their computer with viruses and spyware. I loaded Ubuntu on their machine as an experiment. I loaded it on their machine and forgot all about it. Then after a few months I noticed I had never heard from my kids saying the computer was messing up. I would have had to repair their computer 4 or 5 times in that amount of time with XP. That peaked my interest and I then loaded it on my machine to play with. In a short amount of time I decided I was having fun with it. It was a challenge getting everything working. I am still having hardware problems that I could easily fix by just booting XP but for some reason I keep trying to get it working. I have a serious want or need to get away from XP. I really don't like where I see Microsoft going so I need out! 

I to have had many software issues and I think many of us do. Each one of us has software we have been using over the years on XP that we are trying to replace on Linux that we haven't found a solution for. I know that the music management programs are an issue. Amarok is the closest I have found for me. They all still lack key features that seem essential to their functionality. Wireless networking is an area I struggled in. It is tough to get a wireless card going. I just ordered a new card for my laptop to help with this. I am also a big Slingbox user and I have no choice as of now but to boot XP for this. 

On the plus side though. Linux has been much faster for me. It has made my computer feel more responsive. I like some of the programs for specialty stuff for example Tellico. There are several small useful programs you won't find in the XP world. Stability has been great. I personally have never had a system crash. 

The bottom line for me is Linux is a whole lot more work but once you get it to do what it is you want it to it is well worth it. It trucks right along after you fight for it. XP is a non stop baby sitting experience that is a lot easier to make hardware work. 

For me Linux is good for a person who just wants to do basic internet stuff like check email and surf the web. It is robust and little time has to be invested in worrying about security issues. It is also great for the power Linux user who really gets it. The guy who is in the middle will be frustrated quickly and is not likely they will stick it out to learn to become proficient. XP on the other hand is scary to use unless you know what your doing to secure you computer from threats. The average user is going to get infected with who knows what and may never know it. I am personally sticking with Linux and see where it takes me. 

I have been frustrated many times using Linux but I have eventually worked it out so far especially since I can make XP run and rarely find myself at a loss. I tried many flavors of Linux and after many hours of trial and error I have Ubuntu to be the best for me.

---

