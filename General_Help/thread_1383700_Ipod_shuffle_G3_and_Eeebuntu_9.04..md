---
title: "Ipod shuffle G3 and Eeebuntu 9.04."
date: 2010-01-17
forum: General Help
---

### Post by dchurch24 on 2010-01-17
Hi all,

For Christmas I bought my daughter an Eeepc. I ditched the standard Xandros install and installed eeebuntu and now it's a usable machine once again.

However, her mother bought her a 3g ipod shuffle to go with it (without seeing if it would work in (x)buntu.

It turns out the 3g ipod shuffle doesn't work in Ubuntu yet - or at least that is what I am discovering.

I have tried Rhythmbox - my personall favourite - but although the device is listed, I can do nothing with it. I tried gtkpod, but it just keeps throwing errors at me. I'll fix one, then another comes up. I read the docs on the gtkpod site, and despite the front page claiming that it supports generations 1 through 5, it then goes on elsewhere to say that G3 and G4 or not supported.

I read on pages here that Amarok was the way to go, but it seems the package installation is broken for 9.04. I've tried to upgrade the machine to 9.10, but with a 2gb ssd internal card as a hdd there is not enough room left to install it.

So, my question is: How can I get this ipod shuffle working so that my daughter can easily transfer music to it?

If this is not yet possible, does anyone know of or have the spec for the ipod internal db and I'll write a version and post it up somewhere for others to use.

---

### Post by warfacegod on 2010-01-17
I suggest gtkpod. It can be found in Synaptic.

---

### Post by dchurch24 on 2010-01-17
Hi, thanks for the reply, but I already tried gtkpod, but it just kept throwing error after error at me. After eading the wiki on the gtkpod site, it turns out that g3 and 4 shuffles are not supported for some reason.

I've tried banshee too, but it's a similar story to Rhythmbox sadly.

I'm starting to think that the 3g shuffle is not supported in Ubuntu.

---

### Post by warfacegod on 2010-01-17
As far as I know the only iPod that doesn't play nice with 'buntu is the Touch.

---

### Post by warfacegod on 2010-01-17
Read this:

[http://ubuntuforums.org/showthread.php?t=1382355]("http://ubuntuforums.org/showthread.php?t=1382355")

---

### Post by dchurch24 on 2010-01-17
Hi, thanks for the link. I've followed most of the steps in the posts, but now I am getting 'unmet dependencies' when installing some of the packages mentioned.

I think I'll just throw it away and buy an iRiver or something a bit less proprietry, if it were my choice it wouldn't have been an ipod at all - I've never been a fan even way back when I used Windows. That iTunes software was so processor hungry it was dreadful. That more-or-less put me off Apple for life (well that and OS9 ;-))

Thanks anyway.

---

### Post by warfacegod on 2010-01-17
> **dchurch24 said:**
> Hi, thanks for the link. I've followed most of the steps in the posts, but now I am getting 'unmet dependencies' when installing some of the packages mentioned.

I think I'll just throw it away and buy an iRiver or something a bit less proprietry, if it were my choice it wouldn't have been an ipod at all - I've never been a fan even way back when I used Windows. That iTunes software was so processor hungry it was dreadful. That more-or-less put me off Apple for life (well that and OS9 ;-))

Thanks anyway.

Another solution would be to run Windows as a Virtual Machine so that iTunes can be used. I personally consider that to be a serious hassle for what is in essence a glorified mp3 player.

My wife asks me occasionally what the difference is between an iPod and an mp3 player. I stopped answering last year.

---

### Post by dchurch24 on 2010-01-17
Hi. i had considered the vm route. i run winxp and win7 in vms as i have to test my website and associated software in as many environments as i can. 

the problem is my daughter is seven years old and simply wants to take her music with her where she goes. installing a vm on an eeepc would probably not happen in any case (900mhz with 2gb hdd) and she is used to linux now, so would be hard work for her.

i may have a stab at writing a little app to simply copy music to it and update the db, so she can simply click a button to do it.

i noticed that amarok has been written in c# mono, so i may have a look at that approach.

---

### Post by warfacegod on 2010-01-17
> **dchurch24 said:**
> Hi. i had considered the vm route. i run winxp and win7 in vms as i have to test my website and associated software in as many environments as i can. 

the problem is my daughter is seven years old and simply wants to take her music with her where she goes. installing a vm on an eeepc would probably not happen in any case (900mhz with 2gb hdd) and she is used to linux now, so would be hard work for her.

i may have a stab at writing a little app to simply copy music to it and update the db, so she can simply click a button to do it.

i noticed that amarok has been written in c# mono, so i may have a look at that approach.

I use Amarok 1.4 and presumably has good iPod support. I don't own one so can't say. I have also *tried* to use Amarok 2.2 several times and it is absolutely awful. Although, for a seven year old, it probably wouldn't matter.

I commend you for giving your child a Linux machine and allowing her the option of learning to use a computer instead of resigning her to the fate of having the computer use her. Too often parents simply hand their children Windows machines and I translate that as "Here's a useless piece of junk kid, now sign your soul on the dotted line that says EULA and join the multitudes.

---

### Post by dchurch24 on 2010-01-18
Ha - too true!

I did think about having Windows on there for the simple reason that the kids use it at school, however one day I witnessed a lesson in which all 20 odd of them had laptops with XP on. By the time the teacher managed to get the software up and running the kids had lost interest and the lesson was all but over.

That was the clincher for me and Eeebuntu went on the machine that night.

The fact that my old school has now become a "Microsoft Academy" (seriously, it's the first in the country) bears heavily on my soul as well. If it was MacDonalds that sponsored the school, the parents would be up in arms. Personally I don't see the difference in one big American company brainwashing my kids over another, but that's a different story!

By the time these kids leave school and are struggling with Windows 27 or whatever it will be, at least my daughters will realise that there is another side to the coin. 

Back to the original thread though, I'm going to take her iPod into work and use one of the Windows machines there to reset the device (I believe this can be done using iTunes, but I've never used it so I don't know for sure - only what I've read), and try again.

At the moment, all she uses the laptop for is amsn (to talk to me) and TuxMath and TuxType and some maths website that they use at her school. It would be great if she learned that it could be used for fun as well as learning.

---

### Post by warfacegod on 2010-01-18
I suspect that by the time Windows 27 comes around Microsoft will be crumbling around its own ears. Like watching the Fall of the Roman Empire in fast forward.

Your bring it to work idea rings true to me.

I have Gcompris, Childsplay, and Tuxpaint installed on my laptop for my daughters. They're 5 & 6 and they love those programs. Childsplay and Gcompris are both educational based game suites. They learn math, spelling, logic, physics, geometry, pattern recognition,typing, etc. And all on a computer that doesn't have an invisible chain around their necks. Tuxpaint?, well it's obvious why they like that one!

---

### Post by warfacegod on 2010-01-18
Come on kids it's time to go to MurderKing Acadamy where you can get your daily lesson in conformity and oppression! Oh wait. They already have that. It called the U.S. Public School System. (Great now I'm going to get another infraction for more political discussions.)

---

### Post by dchurch24 on 2010-01-18
Ha ha - that made me laugh. It's the same here (UK) though!

Still, at least some kids will have an idea of diversity when it comes to computing!

Not seen 'Childsplay' but I'm about to ;-)

---

### Post by dchurch24 on 2010-01-18
Incidently, I've rebuilt the ipod shuffle on a colleagues PC and gtkpod seemed, at first to recognise it. I moved a song to the device, and get the dreaded "Please use itunes to synch music" message.

I plugged it in again and it then moaned that the directory structure was wrong and do I want gtkpod to create it. I said Yes, and now the story is exactly the same.

So....I retried Rhythmbox, but I get the same message.

I have tried on my laptop running 9.10 (the eeepc is 9.04) and I get the exact same things happening.

Is it known that the G3 shuffle doesn't work, or is it just me? 

I don't understand why the ipod has to be different. Years ago I had a Diamond Rio; I simply copied mp3's to it and I could play them - completely OS independent.

My GF has an Ipod Nano, and this was almost as troublesome as this one. Ironically, I tried to use hers with iTunes on an old Windows box I had and it simply wouldn't work. I plugged it into Debian and copied files to it and it works fine.

---

### Post by dchurch24 on 2010-01-18
Ok, after a few more hours faffing about trying to get an overhyped and overpriced MP3 player working - i.e. The iPod 3G Shuffle, I have to concede that it just isn't going to work.

I post this here to hopefully prevent others from going through the same pain.

1.) Rhythmbox - will list the device, but that is all.
2.) gtkpod - simply will not work.
3.) Amarok - package is broken in 9.04 so I don't know.
4.) gnupod - looks like it works when using gnupod_addsong etc... but when you plug in the headphones: "please use itunes to synch music ...blah..."
5.) using the shuffle_db hack seems to work. Alas, when headphones are plugged in: "Please use itunes etc...."
6.) attempting to install YamiPod fails. It's looking for libstdc++.so.5 when it should be looking for libstdc++.so.6. So that's a no-go as well (despite them wanting 19.95 for their efforts). Install so.5 and then it continues...all the way to an error message: "error: not mhod 51,1" which is really descriptive and points me in the right direction to start fixing it...Not!

...as far as I could tell, when it did have music on it, there's no way to skip to the next song. You simple have to listen to every song on it in sequence. FFS! A Sony Walkman from 25 years ago had a FastForward button!!

So, the trick is.....to not buy an iPod Shuffle if you are using Linux, sadly.

I'm sure, one day some clever person will come along and fix these issues, but for now, buy an iRiver or something else.

---

### Post by Floola on 2010-03-14
Floola 5.5 now supports shuffle3G.

Visit [http://www.floola.com](http://www.floola.com)

---

### Post by dchurch24 on 2010-04-12
Ooops - only just seen this.

Thank you, I will give that a go next time I get hold of her ipod.

---

