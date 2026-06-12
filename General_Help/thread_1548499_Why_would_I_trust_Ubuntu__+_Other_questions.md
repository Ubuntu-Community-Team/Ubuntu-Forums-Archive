---
title: "Why would I trust Ubuntu ? + Other questions"
date: 2010-08-08
forum: General Help
---

### Post by i3MS on 2010-08-08
Hello Dear members,

**Introduction**
I'm a new member here ;) thought not a new linuxER,
ubuntu 7.04 was my first linux distribution to try, that was in 2007.
I've been downloading other linux distributions (ubuntu newer versions included) and decided that i SHOULD give it Yet another try :p!

**Intro No#2:**
I humbly count myself as a professional, I'm a developer,
My developing history:
vb6 -> vb.net -> C# -> C++
php -> Asp.net

I'm interested in wxWidgets, Qt, Mono(a little because i somehow hate GTK).

SO now i'm requesting help right??, please make your answers full strength!

**Getting into topic:**

But.....
Being a Microsoft Fan :KS for several years, I can find moving to Linux is quite hard to be honest, i will miss my favourite windows only programs (see below under 'what prevents me...)

Also i've had [COLOR=Red]VERY BAD[/COLOR] experience with Ubuntu 9.10, maybe because i wasn't good enough ? maybe, but i think i encountered bugs ?
(MOST importantly, poing/bug No#1 & #3.

[LIST=1]
[*]Kernel Error or something after updating Kernel THROUGH the "noob-friendly" update window, Why is that? why there weren't any warnings about a possible crash?
[*]iwl4965 drivers or something iirc kept my wireless blinking all the time, I had to modify some files to turn that off, which has wasted my time, (I know ubuntu not to blame but just mentioning that as a Bad experience)
[*]Ubuntu CRASHES network thing after changing the Appearance multiple times, WOW this isn't stable as advertised
[*]Installing nvidia drivers was a pain in the ";)"  process, just as point 2, mentioning something not ubuntu related which was a bad experience.
[/LIST]
 
**My Reasons Behind this move**

[LIST=1]
[*]I want to make cross-platform programs (learn more about linux stuff)
[*]I want a little change in UI, speed(if there any), the way i do things
[*]I don't want to install the bugging AVG/Avira which slows down your computer to hell, I don't want to download viruses, I don't want to care about registry
[*]I don't want to pay anymore for software, I want free programs (i've been using free software for years now like jDownloader, VirtualBox, VLC, Pidgin, Code::Blocks, FIREFOX !!...etc
[*]I DONT PLAY GAMES ON MY LAPTOP lol :D
[/LIST]

**What Prevents Me from Doing that! ([COLOR=Red]The Real Questions in this topic[/COLOR])**

[LIST=1]
[*]There is no Comodo Firewall (THE ONLY firewall i trust, no matter how many 'good' ones out there I feel like there is something missing if comodo wasn't here. [SIZE=4][COLOR=Blue]SO...[/COLOR][/SIZE]
[*][COLOR=Blue]WHY would i trust Ubuntu?, there is no powerful firewall like my trusty comodo on it, SO i can't be sure no one is downloading my files secretly or if there are some 1337 hax out there to get controlled ( Yeah yeah i know i know, teh linux iz secure, but how should i persuade myself to believe that?[/COLOR]
[*][COLOR=Blue][COLOR=Black]THERE is NO VisualStudio :(:(, I know about mono but its not as well powerful as VS with other plugins like devexpress CodeRush, no refactor and no 
[/COLOR][/COLOR]
[*][COLOR=Blue][COLOR=Black]DO you really trust burning programs quality, burning verifications? nothing beats the windows-only IMGBurn.[/COLOR][/COLOR]
[/LIST]
I'm paranoid, i don't want others to see my files (thats my right also i guess), even on MS-Windows, I only trust comodo as I stated above, I have a lot of text login files,
ALSO being a linux beginner I may not secure it the way it should be or i may enable some screw-up option or two.

**Finally**

[LIST=1]
[*]I'm not here to troll and prove that linux/ubuntu is stupid, it is NOT,  but just posting my opinions, because i'm really serious about a change  as my previous reasons stated.
[*]I've searched and couldn't find some at all, and even if something existed i think my post would be totally different
[*]Please read it carefully, i put some effort in it and don't want to re-post them again.
[/LIST]

Thanks for reading!
-i3MS

---

### Post by dino99 on 2010-08-08
good thread :p

i think you have already answered to your question ;)

transitional is not an easy time even for devs, need to let behind old automatism, ...

by the way, in my old time i was a Comodo fan to when using windoz (a bunch of years back now) but you might consider UFW (iptable) and iplist (ipblock or moblock) to deal whith huge blacklist, very powerfull, the best i know for sure.

---

### Post by bobnutfield on 2010-08-08
> My Reasons Behind this move
I want to make cross-platform programs (learn more about linux stuff)
I want a little change in UI, speed(if there any), the way i do things
I don't want to install the bugging AVG/Avira which slows down your computer to hell, I don't want to download viruses, I don't want to care about registry
I don't want to pay anymore for software, I want free programs (i've been using free software for years now like jDownloader, VirtualBox, VLC, Pidgin, Code::Blocks, FIREFOX !!...etc
I DONT PLAY GAMES ON MY LAPTOP lol

You list many of the reasons I switched to Linux many years ago.  I still keep a Windows installation on one of my laptops for my wife to use and, up until the release of Lucid, for iTunes.

But it appears to me you are approaching this with a "Windows state of mind", and that will doom you to frustration and failure if you REALLY want to switch.  Linux is not Windows.  As a developer, I am sure you are aware that the file structure differences alone separate the two like night and day.  The only similarity, in my opinion is that they are both operating systems.  I quickly grew to like the way Linux handled files, and now hardware support is BETTER than Windows.  If you doubt that, try installing a copy of Windows on a newly formatted laptop.  You will spend hours (if not days) hunting down drivers for all the hardware.  In most cases, it's all already there on a new Linux installation.  And, while I understand that there are some proprietary drivers that outperform the equivalent open source driver, it is already included nonetheless and the hardware "just works" with little or no configuration needed for most people.  It wasn't always that way, but it is now.    

It's my opinion based on my own experience, but if you approach a switch to Linux (any Linux) with a view to making it "work like Windows", you will find it a hard road to follow.

---

### Post by Quackers on 2010-08-08
If it's any help to you I have iwl4965 working fine. I also have nvidia driver for 8600M GT working fine too (after downloading the proprietary drivers via System > Administration > Hardware Drivers.
I'm using Lucid Lynx and am really quite impressed with how it's working. I haven't used Vista for over a week :-)

---

### Post by HPD2 on 2010-08-08
Linux security =/= Windows security. A firewall in Linux isn't 100% required and if your behind a router you likely don't need one.

Ubuntu does in fact  have a great firewall, UFW. UFW is a tool used to configure IP tables. IP tables is the real firewall and can be configured with out UFW. UFW makes interacting with IP tables a bit more simple, UFW also has a GUI interface GUFW.

As far as trusting a burning program, the Ubuntu built in program, Brasero, works just fine. I have used it to burn just about everything just fine.

*As far as the Nvidia drivers go just go to System>Hardware Drivers, then select the driver you want to use. Let it install and your done.

*Also read [Linux is Not Windows.]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by jomo56 on 2010-08-08
K3b is also a good burning program.

---

### Post by QIII on 2010-08-08
With regard to your experience with 9.10, *NO OS* is perfect, no upgrade is perfect and people *DO *encounter problems.  You know full well that there are Windows forums aplenty.  Windows users run into neither more nor fewer problems with installations and upgrades.  You will find Windows bashers here, unfortunately.  The fact is that sometimes people encounter problems installing or upgrading Ubuntu or any other Linux distro.  Drivers for particular pieces of hardware can be problematic in any OS.

Fear of switching from Comodo to another firewall solution will hold you back.  There is risk in everything you do.  If you chose to be held hostage by the fear of that which is new to you, then you lose the opportunity to explore.  The security models of the two OSes are completely different.   You won't have Comodo, but you will have other solutions.

No.  There is no Visual Studio.  That is primarily due to the fact that there is no need for it, since .NET applications do not run natively in Linux.  Aside from things like Mono, there is no use for Visual Studio.  This is Linux, not Windows.  Mono can create applications that give you the libraries needed to run .NET applications in Linux, but a .NET application would not otherwise run natively in Linux.  Again, Linux is not Windows.  You are traveling from your country of birth to a foreign one.  It will not be entirely the same.  The language and customs will be different.

As to whether something or another (such as a burning application) cannot be beat, there are many opinions.  It may very well be that in your experience your choice of software has been the best for you.  It may not have been the best for others, even Windows users.  Such things are largely matters of opinion.

The great thing for you is that you do not have to step into the void with no more than a prayer and leave your world behind forever.  You have the option to dual boot (subject covered often, and we can point you in the right direction) and try Ubuntu (or any Linux distro) to your heart's content while maintaining the security of Windows.  Wubi is another option (installing Ubuntu inside Windows as if it were, to Windows' mind, just another application).  I have no experience with Wubi, but its intent is to provide an opportunity to "kick the tires" without a great deal of effort.  Since Wubi installs create a loop device, Ubuntu can be fat, dumb and happy while it believes it is really running on its own partition.

The thing I must stress is that if you are trying to reassure yourself that you can find "Windows-likeness" in Ubuntu you will be disappointed.  If you think in terms of "Windows alternative" and expect to encounter a steep learning curve (which you would encounter as a native English speaker learning Swahili), you are more likely to enjoy the experience.

Here's how the process has worked for many people, in phases.

1.  Try Linux (dual boot, say) and maintain Windows as the primary OS.

2.  Experiment with Linux (I'd recommend trying several distros, not just Ubuntu).

3.  Become comfortable with Linux.  

4.  Do more and more with Linux.

5.  Do less and less with Windows.

6.  Move to Linux as a primary OS.

7.  Give over entirely to a world without walls and fences, finding no further need for Windows and Gates.

(As a note:  If you really want to keep Visual Studio, do as I have done:  I run Windows in a virtual machine from Linux.  I still have clients who use Windows.)

---

### Post by i3MS on 2010-08-08
Hello again,
thanks for the responses so far!

Right Now, i'm Uninstalling software using Control Panel to make sure i  backup all of my programs/licenses and setups, because I think its not a  good idea to continue this discussion without installing ubuntu first  :-)

> **bobnutfield said:**
> You list many of the reasons I switched to Linux many years ago.

I'm kind of happy and sad to see that i'm not the only one who is "complaining" about these .

> **bobnutfield]The only similarity, in my opinion is that they are  both operating systems.  I quickly grew to like the way Linux handled  files, and now hardware support is BETTER than Windows.  If you doubt  that, try installing a copy of Windows on a newly formatted laptop.  You  will spend hours (if not days) hunting down drivers for all the  hardware.  In most cases, it's all already there on a new Linux  installation.  And, while I understand that there are some proprietary  drivers that outperform the equivalent open source driver, it is already  included nonetheless and the hardware "just works" with little or no  configuration needed for most people.  It wasn't always that way, but it  is now.    [/quote]

Yeah, anyway drivers aren't a problem for me, i'm using a supported PC,  ubuntu worked quite nicely on it in one of my failed linux tests.
I think i will sacrifice some features but i'll be positive, I hope i won't need that!

[quote=bobnutfield]It's my opinion based on my own experience, but if  you approach a switch to Linux (any Linux) with a view to making it  "work like Windows", you will find it a hard road to follow.[/quote]Yes,  i suffer from this problem probably 
I need a windowsified-Ubuntu which is a bit 'stupid' because i'm here for a change!

[QUOTE=Quackers said:**
> If it's any help to you I have iwl4965 working  fine. I also have nvidia driver for 8600M GT working fine too (after  downloading the proprietary drivers via System > Administration >  Hardware Drivers.
I'm using Lucid Lynx and am really quite impressed with how it's working. 

thank you, i will try that, i hope the blinking "issue" is fixed with iwl4965.
(if its not, i will modify *that file *no problem)

> I haven't used Vista for over a week lol, IMO you should have dropped Vista since ages, it just sucks ;--)

> **HPD2 said:**
> Linux security =/= Windows security. A firewall in  Linux isn't 100% required and if your behind a router you likely don't  need one.

let me be more specific,
i use comodo because it notifies me of every home call made by programs,  some that really disgusts me, i don't know how to trust ubuntu or any  other linux program :(,
i know its from a trusted publisher maybe but...hmm i guess i will get used to that?
or are linux packages tested and verified and any change will get appropriate attention ?

> **HPD2]As far as trusting a burning program, the Ubuntu built in  program, Brasero, works just fine. I have used it to burn just about  everything just fine.

*As far as the Nvidia drivers go just go to System>Hardware Drivers,  then select the driver you want to use. Let it install and your done.

*Also read [Linux is Not Windows.]("http://linux.oneandoneis2.org/LNW.htm")[/quote]

About the burning program, i think i will make a test copy and will do a quality scan in one of the windows pcs in my home.
but i like IMGBurn because it notifies you of every small error!, if you  want a perfect 1:1  burn with detailed logs and what is the dvd burner  is doing atm, i  assure you imgBurn has plenty of those features for  paranoid people.

About nvidia, ok i will see, iirc i've done that before, not sure why i got into trouble :p

about the last link, looks interesting, will put some reading into it, i think it will solve a lot of my 'upcoming' questions.

[QUOTE=dino99 said:**
> by the way, in my old time i was a Comodo fan to   when using windoz (a bunch of years back now) but you might consider UFW   (iptable) and iplist (ipblock or moblock) to deal whith huge  blacklist,  very powerfull, the best i know for sure.

> **HPD2]Ubuntu does in fact  have a great firewall, UFW. UFW is a   tool used to configure IP tables. IP tables is the real firewall and can   be configured with out UFW. UFW makes interacting with IP tables a bit   more simple, UFW also has a GUI interface GUFW.[/quote]

Since i don't know what you are talking about, i'm installing ubuntu as we speak.
but its good for all that text-editing activities (i suppose) to have a GUI, i like GUIs more.

[QUOTE=jomo56]K3b is also a good burning program.     [/QUOTE]

Noted, thank you, will see it.

[QUOTE=QIII]no upgrade is perfect and people *DO *encounter  problems.   You know full well that there are Windows forums aplenty.   Windows  users run into neither more nor fewer problems with  installations and  upgrades.  You will find Windows bashers here,  unfortunately.  The fact  is that sometimes people encounter problems  installing or upgrading  Ubuntu or any other Linux distro.  Drivers for  particular pieces of  hardware can be problematic in any OS.[/QUOTE]No upgrade is perfect?  yes, but imo installing a service pack on windows is faultless (or lets say has a 1.0%  fail rate), maybe because updating 'linux kernel' is different..

It makes me somehow sad because when I tried 9.10 and listened to  windows-bashers I was really thinking of a paradise and utopia but 9.10  crushed me back to windows :-)


>  ...... You won't have Comodo, but you will have other  solutions....I hope so!

> No.  There is no Visual Studio.  That is primarily due to the  fact that  there is no need for it, since .NET applications do not run  natively in  Linux.  Aside from things like Mono, there is no use for  Visual Studio.   This is Linux, not Windows.  Mono can create  applications that give you  the libraries needed to run .NET  applications in Linux, but a .NET  application would not otherwise run  natively in Linux.  Again, Linux is  not Windows.  You are traveling  from your country of birth to a foreign  one.  It will not be entirely  the same.  The language and customs will  be different.I'm sorry  if i sounded vague,
I wanted a VisualStudio or a VisualStudio-Like and power equal IDE for linux,
which is the price of movement to linux for 'betraying microsoft :p'.

i think eclipse is nice, i will try it (more deeply) but still i won't feel home.

>  As to whether something or another (such as a burning  application)  cannot be beat, there are many opinions.  It may very well  be that in  your experience your choice of software has been the best  for you.  It  may not have been the best for others, even Windows users.   Such things  are largely matters of opinion.IMGBurn notifies  you of every small error!, if you want a perfect 1:1 burn with detailed  logs and what is the dvd burner is doing atm, i assure you imgBurn has  plenty of those features for paranoid people.

> The great thing for you is that you do not have to step into the  void  with no more than a prayer and leave your world behind forever.   You  have the option to dual boot (subject covered often, and we can  point  you in the right direction) and try Ubuntu (or any Linux distro)  to your  heart's content while maintaining the security of Windows.   Wubi is  another option (installing Ubuntu inside Windows as if it were,  to  Windows' mind, just another application).  I have no experience  with  Wubi, but its intent is to provide an opportunity to "kick the  tires"  without a great deal of effort.My paranoid-o-meter  doesn't allow that, I don't trust that for my files,
1 OS on 1 Computer - my 'principle' of installing Oses  said:**
>  The thing I must stress is that if you are trying to reassure  yourself  that you can find "Windows-likeness" in Ubuntu you will be  disappointed.   If you think in terms of "Windows alternative" and  expect to encounter  a steep learning curve (which you would encounter  as a native English  speaker learning Swahili), you are more likely to  enjoy the experience.     I don't mind learning something new,  in fact linux-knowledge is must when it comes to companies, you don't  want to miss a job/project opportunity because you don't know how to  "sudo" ;--)
and thats another reason of this(my) move..


> 1.  Try Linux (dual boot, say) and maintain Windows as the primary OS.

2.  Experiment with Linux (I'd recommend trying several distros, not just Ubuntu).

3.  Become comfortable with Linux.  

4.  Do more and more with Linux.

5.  Do less and less with Windows.

6.  Move to Linux as a primary OS.

7.  Give over entirely to a world without walls and fences, finding no  further need for Windows and Gates.good points, i've actually   did a lot of them (in a not so-perfect way) except point No** 4 & 5** which are the most important ones 

> (As a note:  If you really want to keep Visual Studio, do as I  have  done:  I run Windows in a virtual machine from Linux. ** I still have  clients **who use Windows.)     Its crystal reports AND MSSQL because a lot of them don't trust non-MS products, am i right?? ;)
I think i will do the same.


I'll be back, thanks again @all :--D

---

### Post by QIII on 2010-08-08
"I wanted a VisualStudio or a VisualStudio-Like and power equal IDE for linux ..."

Netbeans is very full-featured for many languages (I use it for C++, Java and Python).  It has some very nice tools that I don't have in Visual Studio.

"Its crystal reports AND MSSQL because a lot of them don't trust non-MS products, am i right??".

Not really.  It's simply that they specify .NET and run Windows enterprises.

---

### Post by i3MS on 2010-08-08
Hi, thanks for the fast response,

> **QIII said:**
> Netbeans is very full-featured for many languages (I use it for C++, Java and Python).  It has some very nice tools that I don't have in Visual Studio.

i'll see how would NB perform *when* using it for C++.

btw I'm currently thinking of trying eclipse C++ and code::blocks(for wxWidgets framework) and the Qt framework.

---

### Post by giddyup306 on 2010-08-08
This is a great post on what some people encounter switching to Linux.  Part of the reason why Linux is so "hard" is because people have been using Windows for so long, and they are used to doing stuff the Windows way.  I'm 26, so I've been using Windows for 20 years (I remember Windows 3.1).

[http://ubuntuforums.org/showthread.php?t=58017&highlight=intentioned+troll](http://ubuntuforums.org/showthread.php?t=58017&highlight=intentioned+troll)

As far as programming goes, I like Eclipse (unless it crashes).  You don't need a firewall because unlike windows, Ubuntu doesn't open unnecessary ports.  If you want a firewall you can install ufw/gfuw.  If you are really worried about someone hacking into your Linux machine, don't keep any personal information on there. It's like having a nice car.  If someone wants to steal it bad enough they're going to get it.  You just have to make it as inconvenient as possible.  Plus most people that are going to hack into something would opt for an unsecure Windows machine. Unless the hacker is a masochist.    I personally erase my hard drive all the time.  It's virtually impossible to get a virus on Linux.  There have only been one or two in Linux history and they only affected a specific distro that ended up getting patches.  If you want your Linux secure (like I do) you can look into SELinux, ghostery, no script, Moblock/Moblocquer, and any of the other security things that are available.

---

### Post by i3MS on 2010-08-08
> **giddyup306 said:**
> This is a great post on what some people encounter switching to Linux.  Part of the reason why Linux is so "hard" is because people have been using Windows for so long, and they are used to doing stuff the Windows way.  I'm 26, so I've been using Windows for 20 years (I remember Windows 3.1).

[http://ubuntuforums.org/showthread.php?t=58017&highlight=intentioned+troll](http://ubuntuforums.org/showthread.php?t=58017&highlight=intentioned+troll)

that thread describes trolls nicely if you ask me :p
The example the thread author mentioned is basically EQUAL to what happened to me,
i've read it fully and can now understand why i ran into those "problems".

I'll continue tomorrow, i'm going to get some sleep now,
will format tomorrow.

> As far as programming goes, I like Eclipse (unless it crashes).will see, i think it would either eclipse or Netbeans.

> You don't need a firewall because unlike windows, Ubuntu doesn't open unnecessary ports.  If you want a firewall you can install ufw/gfuw.  If you are really worried about someone hacking into your Linux machine, don't keep any personal information on there. It's like having a nice car.  If someone wants to steal it bad enough they're going to get it.  You just have to make it as inconvenient as possible.  Plus most people that are going to hack into something would opt for an unsecure Windows machine. Unless the hacker is a masochist.    I personally erase my hard drive all the time.  It's virtually impossible to get a virus on Linux.  There have only been one or two in Linux history and they only affected a specific distro that ended up getting patches. I got the part about the ufw/gfuw from this post and previous ones, looks like a good solution,
however i don't find the idea of separating my files a good one :(.
what about chmod?

> If you want your Linux secure (like I do) you can look into SELinux,  ghostery, no script, Moblock/Moblocquer, and any of the other security  things that are available.I'll see what are these tomorrow,
good night

and thanks all.

---

