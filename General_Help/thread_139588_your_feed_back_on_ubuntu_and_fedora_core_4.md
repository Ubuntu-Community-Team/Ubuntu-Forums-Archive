---
title: "your feed back on ubuntu and fedora core 4"
date: 2006-03-04
forum: General Help
---

### Post by njzillest on 2006-03-04
whats your feedback on ubuntu and fedora core 4?

i have both and im not sure what to switch to...


i dont want to hear what your friend thinks.. i want to know what **you** think...

you may include what the differences are.. do what ever you wont..
..just plz...
dont post about one or the other distro if you have never used it...




thanx

---

### Post by taurus on 2006-03-04
Instead of wanting to hear what others have to say about Ubuntu and FC, why don't you install Ubuntu, play with it for a couple of weeks.  Then install FC; play with it a couple of weeks, and then make up your mind to see which one you should use...  Since it is Ubuntu's forum, people here will tell you that Ubuntu is more newbie friendly and you only have to download one CD instead of four CDs like in FC!!!

---

### Post by darkmaze on 2006-03-04
with fedora there is no central repo. & its minimal out of the box. seems like a learner distro. ubuntu seems like a transitional to me. for people coming in from the   windows  hell. but check them both

---

### Post by simoncoul on 2006-03-04
I used fedora for a few days but it was complicated to install things and was very hard to find information about oh to to it.  With ubuntu it comes with alot of stuff and u just look on this forum for information, if u don't find it post it and within a few hours usually u will have your answer.   I think the community of ubuntu is what really makes it better then most distos.

---

### Post by ComplexNumber on 2006-03-04
[quote=simoncoul]I used fedora for a few days but it was complicated to install things and was very hard to find information about oh to to it.  With ubuntu it comes with alot of stuff and u just look on this forum for information, if u don't find it post it and within a few hours usually u will have your answer.   I think the community of ubuntu is what really makes it better then most distos.[/quote] i would have to disagree on all these points. FC is a lot easier to install than ubuntu and has one of the easiest (but not the best) installers of any distro and is FAR from complicated. 
ubuntu doesn't come with a lot of stuff - it is one of the most minimal of all distro's. there is under 630MB on the supplied CD whereas fedora core 4 comes with several gigobytes.
looking at both the ubuntu forum and the fedora forum at this present time, we can compare the activity between the forums:
ubuntu forum - 238 members and 800 guests (total = 1038 )
fedora forum - 278 members and 4517 guests (total = 4795)
now ask yourself, which has the most active community?



[B]
njzillest
[/B]neither is better. i don't really have a preference because i like them both but in different ways....ok, perhaps i like fedora more because of the much greater range of applications supplied by default (my linux box has no internet connection), the nicer look and feel of it, and because i find rpm's to be easier to deal with the debian packages. ubuntu is VERY minimal to say the least whereas fedora includes almost everything. i like the bluecurve/clearlooks combination just slightly more than the ubuntu's human default theme.

---

### Post by njzillest on 2006-03-04
i do have both installed on my computer.. i have been using ubuntu for about 4 months.. pretty easy to use... i just installed fedora (now i have a tri boot)


so far i have noticed:
FEDORAS INSTALL IS ALOT EASIER THAN UBUNTUS 
Fedora has more than ubuntu (for servers and development... also you can choose to install 3 diffferent differrent desktop enviroments (including gnome and kde)

Fedora has a larger community

the draw backs for me going straight to fedora is the fact i dont know the commands

it took me a while to learn how to install everything on ubuntu.. and also ubuntu comes pre configigured with the 2200 ipw... 

I heard the YUM is very simular to the apt-get..


how differrent is fedora cores commands from those of ubuntu? is it better to learn both.. so i will have a basic knowlege on most linux distros (debian based and red hat based)

---

### Post by ComplexNumber on 2006-03-04
>  how differrent is fedora cores commands from those of ubuntu? what do you mean by 'commands'? are you referring to the  bash shell on the command line? in that case, they're the same. on the command line for installing programs, ubuntu uses deb and fedora uses rpm, and each use a different syntax.
i don't bother with yum on fedora - i used synaptic (its a gui program).

---

### Post by taurus on 2006-03-04
I am not sure what you mean with fedora core commands?  If you are using bash, then commands are exactly identical whether you use Fedora Core, Ubuntu, Gentoo, Slackware, or other linux distros.  The only difference is that Fedora Core uses yum (yumex--GUI) to install/upgrade things while Ubuntu uses apt-get (synaptic--GUI) to accomplish the same task.  So, it's up to individual's taste.  Personally, I think you should go with Gentoo so you can learn more about the ins & outs of your OS!!!  But if you just want to install and have a minimum interaction with it, then go with FC, Ubuntu, or SUSE...

---

### Post by njzillest on 2006-03-04
what do you mean the "ins and outs?"


whats the difference between debain and redhat..?? if the commands are the exact same?


i tried doing "iwconfig and ifconfig" with redhat and it was an invalid syntax.

what other operating system do you recomend for ethical hacking and programming? (java, python, and c++)

---

### Post by arctic on 2006-03-04
Most of my machines run with Fedora, only two of my systems run with Ubuntu. Both systems are good. But my main machines will remain Fedora-boxes. I will try to sum up my thoughts:

Fedoras strenghts:
- It has a very easy to use and flexible installer (GUI). You can decide from the start what you want to do. Set up a server, set up a geeky developers box, setup a desktop-workstation, set up a multimedia box. It is way more flexible in this respect than Ubuntu... but then, you will download a "whopping" four CDs unless you decide to do a FTP-installation.
- Fedora is rock-stable. It never died on me. Why? Well, I guess because the bugtesting is awesome. Many users use Fedora for runing their servers, not without a reason. Ubuntu is also very stable but has more glitches here and there imho.
- There are more configuration tools (e.g. system-services, LVM, ...) in FC than in Ubuntu. Thus administration is not overly complicated, unless you want to dig deeper into Fedoras stomach. Then you will use the CLI, just like in Slackware and other purist distros. Fedora is somewhere between the nerd and the newcomer distros. It is more demanding than Ubuntu imho, alo because of SELinux.
- Yum has imho one advantage to apt-get. It will automatically switch servers once they are peppered with too much traffic and it automatically synchronizes to the mirrors, thus verifying that the packages are 100% okay. Of course this makes yum a little bit slower than apt-get (the syncing function can be turned off in FC, then both managers are similar in speed), but this extra bit of security is very nice if you have e.g. a mission critical server running.
- The documentation for Fedora is way better. At Red Hats site, you can download tons of PDF-documents that explain everything from tip to toe. From newcomer-stuff to admins and developers.
- Bigger community with imho deeper knowledge (due to the fact that many admins use Red Hat and/or Fedora).
- If you want to become a serious admin, Red Hat / fedora is usually the way to go. RHCE is one of the most sought after certifications.

Ubuntus strenghts:
- Less tweaking for certain tasks (e.g. laptop-extra keys) necessary
- One CD-download is very nice if you have e.g. dial-up connection (not everyone has broadband).
- The desktop is well designed for newcomers and reduces some of the fear that many people have when they hear "linux".
- Good solution if you want a simple desktop for most "every-day" tasks, like surfing, writing, mailing.

"Bad" on both systems: Multimedia support if you want to use non-free stuff. Both systems do not support MP3 or WMA by default. But both can be tweaked with a few clicks and will equally support all the stuff, so the multimedia-thing some people mention is nonsense.

These are my VERY OWN impressions.

PS: In fedora, you run root commands e.g with
/sbin/iwconfig

the /sbin part is necessary for many commands. Another security feature...

---

### Post by arctic on 2006-03-04
The difference between Debian and Redhat is 1.) the package-manager and 2.) the system-layout. Debian stores some files in different places than rpm-based distros and also names them differently in some cases.

---

### Post by njzillest on 2006-03-04
well im fairly new to linux... ive been on ubuntu for 4 months now.. and i have been trieng to program... (c/++, java, and python)

what do you think is better for a n00b l1k3 me? 
also whats better for my ethical hacking? (im guessing fedora)

i knoticed that ubuntu is easier on the n00bs when it comes to networking (ie the preconfigured ipw 2200 driver for the intel 2200 b/g wireless adapter) 

i want to use fedora but its hard to configure my adapter with it :( 

what would you recomend more for my programming and ethical hacking??

---

### Post by arctic on 2006-03-04
About ipw 2200, check this thread [http://www.fedoraforum.org/forum/showthread.php?t=59470&highlight=ipw+2200](http://www.fedoraforum.org/forum/showthread.php?t=59470&highlight=ipw+2200)

For programming, I'd say: use fedora. But after all, it's your personal choice. ;)

---

### Post by ComplexNumber on 2006-03-04
[quote=njzillest]well im fairly new to linux... ive been on ubuntu for 4 months now.. and i have been trieng to program... (c/++, java, and python)

what do you think is better for a n00b l1k3 me? 
also whats better for my ethical hacking? (im guessing fedora)

i knoticed that ubuntu is easier on the n00bs when it comes to networking (ie the preconfigured ipw 2200 driver for the intel 2200 b/g wireless adapter) 

i want to use fedora but its hard to configure my adapter with it :( 

what would you recomend more for my programming and ethical hacking??[/quote] for the absolute newbie, i would say ubuntu. after a few months or so, fedora is best. fedora has a lot more to offer. for developement, definitely fedora. fedora is amongst the best for developement IMO.

---

### Post by taurus on 2006-03-04
[QUOTE=njzillest]
i tried doing "iwconfig and ifconfig" with redhat and it was an invalid syntax.[/QUOTE]
Because /sbin is not in your path!!!  :rolleyes:

---

### Post by njzillest on 2006-03-04
wow guyz.. thanx alot..

i have another question about ubuntu and linux in general..



i was reading an ethical hacking book.. and it said to use a "unix shell" my ISP does not support unix shells, but i heard i could get free unix shells... 


is that possiable? also if i can.. do i have to use Free BSD? or can i just use fedora core/ubuntu?

---

### Post by njzillest on 2006-03-04
also is it possiable to Ndiswrapper on fedora to locate and use the ubuntus ipw2200 adapter settings?

---

### Post by njzillest on 2006-03-16
ok i have decided to stay with ubuntu then later one go on to fedora..









i fear change though 

is there any good haxing distro that can be installed to the HD (i dont know if i can install KNoppix std to the HD)


is phlak any good?


(im a white hat hacker-------------- all legit :) )

---

### Post by Steve1961 on 2006-03-16
I have ubuntu and FC4 installed and IMHO there's not a huge amount to choose between them.  Despite trying many many distros over the past year these have stayed on my disks throughout my experimentation.  apt-get is great in ubuntu, but yum works really well in Fedora and basically does the same job.  Both have great community support, are stable, have regular release cycles, and lots of repositories full of software.  FC4 tends to send more updates down the line than Ubuntu, including regular kernel updates to the latest version, but these have never broken my system so I tend to see this as a strength.  Ubuntu installs faster and can be configured faster, but there's not that much in it.  Bottom line?  Both are excellent so it's down to personal preference.

Compare either of these distros to something like Slackware and you'll see that they're more similar than different.  Not that I have anything against Slackware - I also have this installed and it's amazingly fast and stable and a great platform for learning how to configure a system from scratch or running a server, especially if you have older hardware.  Also a great development platform because it keeps things simple.

---

### Post by njzillest on 2006-03-22
ive also heard feedback on Free BSD and Net BSD. 


i dotn know much about them, but i heard it sdefferent from Debian and Red Hat.

i think its used more for servers though

---

