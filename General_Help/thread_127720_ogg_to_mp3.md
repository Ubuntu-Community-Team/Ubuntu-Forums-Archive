---
title: "ogg to mp3"
date: 2006-02-09
forum: General Help
---

### Post by Simian on 2006-02-09
I'm looking for a application that converts ogg to mp3. I was hoping someone could recomend one. :-k 

I did look on the wiki and i've searched this forum.

Tahnks in advance :)

---

### Post by kwaanens on 2006-02-09
Package: soundconverter

- Ketil

---

### Post by Simian on 2006-02-09
[QUOTE=kwaanens]Package: soundconverter

- Ketil[/QUOTE]

Thanks. I have that but I can't enable MP3. I guess that's the real question I should have been asking. Do you know how I can enable it?

---

### Post by The Mekon on 2006-02-09
You probably need to install the mp3 codecs.  This is explained inthe Wiki at this [link]("https://wiki.ubuntu.com/RestrictedFormats").

---

### Post by kwaanens on 2006-02-09
You need gstreamer0.8-lame
Then restart soundconverter

- Ketil

---

### Post by Simian on 2006-02-10
Thanks again for your advice Kwaanens and The Mekon. I'll give it a go this evening.

---

### Post by handy on 2006-02-10
I think that if you use Automatix, one of the options that it will install for you is lots of codecs.

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

I've installed this on 64bit & 32bit, no problems! :mrgreen:

---

### Post by frodon on 2006-02-10
[QUOTE=Simian]I'm looking for a application that converts ogg to mp3. I was hoping someone could recomend one. :-k 

I did look on the wiki and i've searched this forum.

Tahnks in advance :)[/QUOTE]I use this script, really easy to use and powerful : [http://ubuntuforums.org/showthread.php?t=82806](http://ubuntuforums.org/showthread.php?t=82806)

---

### Post by robenroute on 2006-02-10
You could also try gnormalize. Have a look on gnomefiles.org

Rob

---

### Post by Simian on 2006-02-10
handy: I will look at automatix too. I assume that you can choose which features are enabled on it right? A lot of them I wouldn't want.

frodon: Thanks that script looks good.

robenroute: I've read about gnormalize but it isn't in the repos.

---

### Post by Simian on 2006-02-10
Automatix did the trick ;)

---

### Post by kwaanens on 2006-02-10
[QUOTE=handy]I think that if you use Automatix, one of the options that it will install for you is lots of codecs.

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

I've installed this on 64bit & 32bit, no problems! :mrgreen:[/QUOTE]

Automatix screwed up my installation on Hoary, I remember. And the Breezy-version did a couple of annoying stuff as well. Remember: Automatix is just a package that can do a lot of different stuff, but that stuff is possible to get to work without Autoamtix too. Just check the how-tos for the individual changes you want to make.

Saying this, because a lot of people answer "use Automatix" to virtually every question asked. It *can* be a trap. So be aware. If you want to learn about your stuff, manually configuring stuff is sometimes better.

- Ketil

---

### Post by handy on 2006-02-10
Yes, it is totaly up to the user what they select to install.

I just updated Automatix last night, It now installs Firefox 1.5, painlessly, amongst a few other new options.

I think Automatix is such a great timesaver.

---

### Post by kwaanens on 2006-02-10
[QUOTE=handy]Yes, it is totaly up to the user what they select to install.[/QUOTE]

That's sorta my point.
It's easy to fall into the belief that "wow, I could need all this". That's often not true, and the same goes here as everywhere else: the more stuff you try to change, the more potential you have to screw something up.

[QUOTE=handy]I think Automatix is such a great timesaver.[/QUOTE]

I agree, but use it cautiously! (As all other pieces of software that prompts a password.)

- Ketil

---

### Post by handy on 2006-02-10
[QUOTE=kwaanens]Automatix screwed up my installation on Hoary, I remember. And the Breezy-version did a couple of annoying stuff as well. Remember: Automatix is just a package that can do a lot of different stuff, but that stuff is possible to get to work without Autoamtix too. Just check the how-tos for the individual changes you want to make.

Saying this, because a lot of people answer "use Automatix" to virtually every question asked. It *can* be a trap. So be aware. If you want to learn about your stuff, manually configuring stuff is sometimes better.

- Ketil[/QUOTE]


Hi Ketil,

I can only call it as I see it, from my experience Automatix is faultless!  

I know there are so many variables in the computer world, just all the possible hardware configurations alone, is mind boggling!  Let alone drivers, software, users, electrical power fluctuations & magnetic fields...

Automatix, has surely matured as it heads through version 5.4.1.

Many of us noobs, have so much to learn at the beginning with linux, we welcome something like Automatix, which takes some of the strain off both our brain, & our time.  Some users also, don't want to know anymore than what it takes to get the job done!

I think that the Ubuntu community, as expressed in the forum, in combination with Automatix, are 2 of the most powerfull things that will keep new users with Ubuntu.

Many people in the forum will prescribe Automatix, because they are so happy with what it has done for them.  It is unfortunate that you were one of the few that have had unpleasant experiences.

---

### Post by handy on 2006-02-10
[QUOTE=kwaanens]That's sorta my point.
It's easy to fall into the belief that "wow, I could need all this". That's often not true, and the same goes here as everywhere else: the more stuff you try to change, the more potential you have to screw something up.[/QUOTE]

When we have something new, ie. Ubuntu, some of us may want to see what **ALL** these things are, & for free too!!:-D   I do agree, it *can* be seen as an immature attitude, **BUT** freedom of choice is such a wonderful thing to express! :KS & trying lots of things can be great fun!

Yes, the more we change in an operating system the more possibilities for disaster.  

**Keep your data backed up.**

---

### Post by kwaanens on 2006-02-10
I've now been using Linux for about 2 years. I learned a lot of things through and through, because I didn't have stuff like Automatix, only newsgroups, forums and so on.

That helped me a lot in understanding the fundamental ways lots of Linux systems work.

I just think that it (sometimes) is a more profound way of helping someone to explain what to manually do, instead of getting them to use Automatix. Sorta, keeping in tune with the "give a man a fish, and he'll eat for a day. teach a man how, and he'll eat for a life time"-philosophy.

But, hey, that's just my opinion!

- ketil

---

### Post by handy on 2006-02-11
Good, I agree :KS  

Some days **/** people are better for fishing than others.  If today you feel like fishing?  Go Fish.  If you don't, on the other hand, 'cause it's raining or you hate gutting them, it sure is nice to have the fish shop next door! :KS

---

### Post by sugarland2k on 2007-12-22
Thanks for the advise on soundconverter !  I store my music files as ogg's but my trucks CD player only plays WMA's and MP3 ;(  

I do have a SanDisk Sansa e250 music box and I have RockBox loaded on it and it works great, I can even play Doom on the tiny screen!  Ogg and Open Source rules!  

Thanks to all - Keep learning!
Billy:)

---

