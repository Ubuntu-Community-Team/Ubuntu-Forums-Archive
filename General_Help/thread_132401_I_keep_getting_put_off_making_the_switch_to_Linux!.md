---
title: "I keep getting put off making the switch to Linux!"
date: 2006-02-18
forum: General Help
---

### Post by MattBeard on 2006-02-18
I write cross platform software tools and I have to test them under Linux.

I have my main PC set up as dual boot, originally with SuSE, then with debian-64, now I have installed Ubuntu-64.

Each time I set up a new distro I consider using the Linux boot as the main OS for my machine. However, I always get put off!

Today I got as far as getting quite a lot to work. I have my NTFS Windows partition mounted (as read-only :( ) and I can edit and build my code. I have e-mail access and most of the other little bits I need day to day.

I thought it would be useful to set up wine to allow me to run some of my Windows apps. Big problem... wine doesn't work under the 64-bit versions.  OK, this is fixable... I can use chroot to run it as 32-bit.

While I am setting up this 32-bit environment I thought I would have some music... So I try and play some mp3s... no go!  It seems that for legal reasons Linux distros can't support mp3s or DVDs - and according to what I have read in these forums this is unlikely to ever change!!

Why do I ever bother, I spend less on a copy of Windows every 4 or 5 years than I do on coffee each year - and it always does the things I want it to do.  most of the software I run under Windows is Open Source, and the software I write is Open Source, but I don't think I am ever going to be able to live with an Open Source operating system!

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Ramses de Norre on 2006-02-18
I think you're giving up too soon, about the mp3's: there are codecs available they're just not included on the install disc due to licences. But you can install them when you enable universe/multiverse repo's (enough info on how to do that on the forum).

And maybe you should also look at what the OS's don't do, like windows downloading and installing viruses an adware. You don't have that problem with Linux.
I've installed ubuntu a month ago and since then I've booted windows once, to update my sony mp3 which needs a program that only runs under windows.
I did had to search a lot to get some things running but once they do, they do it at least as good as the windwos apps.
You just need to get used to the new environment and you shouldn't compare everything to windows because it isn't windows.

And I'd advice you to use the 32bit version if you don't want those wine problems (there are more programs that haven't a 64bit version yet). It isn't very much slower, the only reason to use 64bit for me would be if I needed more than 4gig's of ram. Which I don't:)

---

### Post by MattBeard on 2006-02-18
I have to use the 64-bit version because the tools need >4Gb RAM access for some of thier processing.  This is the main reason I need them to run under Linux, because that is one thing it does better than Windows.

From what I have read these "easy to find" add ons that let you play mp3s are not included with the distros because they are not legal.  Am I right here?  If that's true then even suggesting I install them is illegal in this country!

---

### Post by Grey on 2006-02-18
I personally am rather amazed that you can chroot a 32-bit environment, but yet don't seem to realize that MP3 playback is quite easy to come by.  Have you ever used Media Player Classic?  VLC?  LAME?  All of these have free implementations of the MP3 codec.  And MP3 is patent encumbered.

As for your problem, do this:

sudo apt-get install gstreamer0.8-mikmod

And it should work just fine.

---

### Post by torx on 2006-02-18
if you are comfortable with the OS you are on now, why switch? Personally, i believe for normal daily use, windows is a more suitable OS. 

if it aint broke, don't fix it.

---

### Post by az on 2006-02-18
[QUOTE=MattBeard]

Why do I ever bother, I spend less on a copy of Windows every 4 or 5 years than I do on coffee each year - and it always does the things I want it to do.  most of the software I run under Windows is Open Source, and the software I write is Open Source, but I don't think I am ever going to be able to live with an Open Source operating system!

](*,) ](*,) ](*,) ](*,) ](*,)[/QUOTE]

Proprietary software bugs me.  I won't use it.  I consider it my right to know what my computer is doing.  I don't consider software as property.  I own my computer.  I am not subject to the owner of the software.  

If this doesn't compell you to use Ubuntu or any other free-libre software, I don't care.  No one is putting a gun to your head, forcing you to try Ubuntu.

---

### Post by MattBeard on 2006-02-18
> I personally am rather amazed that you can chroot a 32-bit environment, but yet don't seem to realize that MP3 playback is quite easy to come by. Have you ever used Media Player Classic? VLC? LAME? All of these have free implementations of the MP3 codec. And MP3 is patent encumbered.
I have never needed to run any of these because (as you may have figured out by reading my original post) I have found RealPlayer, Windows Media Player and iTunes fine for my requirements.

Buy a new PC with Windows installed, or install windows yourself and you will find that it will play DVDs and mp3s without any need to mess with cryptic commandline installs of stuff that you have to search "expert" forums for.

Indeed, if you find some sort of file that uses a compression that your player doesn't currently support most "grown up" players will search for the codec themselves and allow you to install it "pain free".

---

### Post by MattBeard on 2006-02-18
> I don't consider software as property.
My guess is that there speaks someone that doesn't make his living from writing software.

You often feel more "proprietorial" about something that you have slaved 50-60 hours a week for two and a half years to produce and then find someone copies it because they don't see why they should pay $5 for it!!!

---

### Post by nalmeth on 2006-02-18
> You often feel more "proprietorial" about something that you have slaved 50-60 hours a week for two and a half years to produce and then find someone copies it because they don't see why they should pay $5 for it!!!
So then do open-source developers not bleed and sweat for their software? Or what? Do you think this OS was just thrown together in a day by monkeys?
Also, maybe you should read more into what OSS is about. You'll find the goal is not for it to be free as in beer, but free as in freedom to use, modify and improve the software in anyway that is needed or desired. The free beer part is secondary, and is a nice side-effect

EDIT: also, people will copy your software no matter what consequences they may face. OSS gives them the option to not pirate, but still get great software for free.

---

### Post by GTvulse on 2006-02-18
[QUOTE=MattBeard]
Buy a new PC with Windows installed, or install windows yourself and you will find that it will play DVDs and mp3s without any need to mess with cryptic commandline installs of stuff that you have to search "expert" forums for.
[/QUOTE]

It will play MP3s, yes; the OS publisher has bought a license to the patent holder, in fact it uses an mp3 decoder written by the patent holder itself ([Fraunhofer-Institut für Integrierte Schaltungen (IIS)]("http://www.iis.fraunhofer.de/amm/")). But DVDs? As far as I know that is not true. You **have to buy** extra software or go hunting the internet in search of a free MPEG2 decoder and a DVD CSS decryptor. Those are not included in Windows. In fact that DVD CSS decryptor can put you in legal trouble depending on what country you live in.

Now, you may have bought a computer with bundled software that included the necessary codecs to play DVDs, but that software wasn't free. You paid good money for the licenses, included in the total purchase price you accepted to give to your supplier in exchange for the goods.

---

### Post by Denis on 2006-02-18
[QUOTE=MattBeard]Buy a new PC with Windows installed, or install windows yourself and you will find that it will play DVDs and mp3s without any need to mess with cryptic commandline installs of stuff that you have to search "expert" forums for.[/QUOTE]You are right that this can be a problem for the new user when using Ubuntu. 

But this is not a justified argument against a GNU/Linux system. There are also Linux distributions that do support mp3 and DVD's right after install. 

There is a lot of information about this topic on the forum. The essence is that Ubuntu can't be distributed as a free system, when it includes non-free codecs. 

Now if you do want those codecs you can find all information at the Ubuntu wiki: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
I think this really can't be the only issue that stops you from running Ubuntu Linux as your main OS. If it is, then it shouldn't be that much of a problem to fix that issue.

---

### Post by dreadbrazen on 2006-02-18
I'm confused by this whole thing....

Did you post this thread in order to get help from the people on this forum, or to explain to a whole lot of people who happily use this software every day (including the software that you refuse to take an extra step for)?

I'm sorry, I just don't understand what compells you to post this if you're just going to snap back at everyone who offers you advice.  This forum does not exist to trash others' faith in open source operating systems.  It exists to aid those trying to understand and work with those operating systems.

Personally, I like the idea of open source, right down to the operating level.  Everything on my linux box right now (with the exclusion of Unreal Tournament 2004) is open source.  And given a little reading (which is generally necessary when trying to adapt to a new environment) I was able to solve the problems that you stated within minutes.  

I'm sorry that it takes a little more effort to get a working, more stable environment running, but that effort goes a long way.  I started dabbling in linux in high school, after I had a fairly complete grasp on Windows.  I always wanted to be able to use linux, but my computer knowledge was lacking at the time.  Now, after putting in a lot of time this summer with Ubuntu, I am proud to say that with my linux experience I am much more familiar with my computer and the inner workings of the operating system I love.  Not to mention, I'm proud of the work I've put into my computer and my learning experiences with it.

Really, if you're not willing to put in the time, and you're not willing to accept the help that these people are trying to give you, then what are you doing here?

---

### Post by aysiu on 2006-02-18
Windows won't play DVDs out of the box.
You need PowerDVD or InterVideo WinDVD or some other helper program to install the necessary codecs.

And there are plenty of distributions that come with all sorts of proprietary software ready to go: PCLinuxOS, Mepis, Blag, Linspire...

Ubuntu doesn't come with all of that. It's not a Linux thing. It's a Ubuntu thing.

---

### Post by thespazzz on 2006-02-18
I really hate it when people compare Ubuntu or any linux distro to Windows.


NEWS FLASH: IT IS NOT WINDOWS

If we wanted it to be windows then we would use windows.

Your pissed because it dosen't support MP3?  Blame the people who think propriatary file formats are a good idea. I.E. The developer of that software and your Government.  Its not the OS developers fault that they can get sued if they include it by default.  If you want to install it and take that responsibility yourself then do so, Plenty of other people do.  If you have a problum with Propriatary formats then 1. Don't use them and 2. Write to congress or parlament or whatever.

Whats funny is given your earlier posts you think that propriatary software is fine.  Thats fine but you can't have it both ways.  The people who designed MP3 set fourth rules for governing its use.  Those rules don't allow it to be included in a "Free" OS.

Better yet if you pissed about the non free format, Do what i'm considering doing and convert your MP3 library to Ogg which I belive Ubuntu and most Linux distro's do support out of the box.  Why?  Because its an open source format.

DVD Playback.  Windows XP does not have it by default usualy unless it came preinstalled and the computer manufacturer paid to have a DVD app put on there.  BTW the developers of the DVD Application PAID the DVD folks royalities because, survey says, its a pattented format!

I guess in a less caustic message what i'm simply trying to say is...

Don't shoot the messenger.

---

### Post by az on 2006-02-19
[QUOTE=MattBeard]My guess is that there speaks someone that doesn't make his living from writing software.[/QUOTE]

You're right.  I run a heart-lung machine for a living.


[QUOTE=MattBeard]You often feel more "proprietorial" about something that you have slaved 50-60 hours a week for two and a half years to produce and then find someone copies it because they don't see why they should pay $5 for it!!![/QUOTE]

What do you do?  Write "shareware"?  

Free-libre open source software is bug business.  Look it up.  

Google, Yahoo, IBM, Novell, Most Internet service providers all use and make money from free-libre software, to name a few.

Look here, too:
[http://www.dwheeler.com/oss_fs_why.html](http://www.dwheeler.com/oss_fs_why.html)

A developer who works for a proprietary software publisher does not own the code she writes.  On the other hand, the code that a developer who works for a free-libre software publisher witres still owns her code- it belongs to everybody.  She gets to keep her paycheck, too.

You get to reuse working code and "stand on the shoulders of giants" in with free-libre software.  That's why it goes zoom!  Your 50-60 hours a week for two years can multiply....

---

### Post by purdy hate machine on 2006-02-20
[QUOTE=MattBeard]

While I am setting up this 32-bit environment I thought I would have some music... So I try and play some mp3s... no go!  It seems that for legal reasons Linux distros can't support mp3s or DVDs - and according to what I have read in these forums this is unlikely to ever change!!

Why do I ever bother, I spend less on a copy of Windows every 4 or 5 years than I do on coffee each year - and it always does the things I want it to do.  most of the software I run under Windows is Open Source, and the software I write is Open Source, but I don't think I am ever going to be able to live with an Open Source operating system!
[/QUOTE]

You write your own software… spending 2 minutes of your time installing a handful of codec’s shouldn’t be too much of a grind for you.

---

### Post by torx on 2006-02-20
Personally, i don't think GNU/Linux is ripe enough for mass-consumerism. And honestly, i like it that way. It's one of the few things in life still very priviledged to geeks like us and it sets us apart from the rest. =) However, it is praise-worthy of Microsoft to making computing easy. Microsoft to me is like Adobe Photoshop, easy to use without compromising functionality.

---

### Post by thespazzz on 2006-02-20
[QUOTE=torx]Personally, i don't think GNU/Linux is ripe enough for mass-consumerism. And honestly, i like it that way. It's one of the few things in life still very priviledged to geeks like us and it sets us apart from the rest. =) However, it is praise-worthy of Microsoft to making computing easy. Microsoft to me is like Adobe Photoshop, easy to use without compromising functionality.[/QUOTE]

Buggy software, Security bugs out the wazzoo.  Easily vunerable to system wide spyware and viruses.

Yea.. Perfectly functional.. not :-)

---

### Post by Lord Illidan on 2006-02-20
[quote=thespazzz]Buggy software, Security bugs out the wazzoo.  Easily vunerable to system wide spyware and viruses.

Yea.. Perfectly functional.. not :-)[/quote]

While I agree about the security problems, XP hasn't given me a bluescreen in over 3 months. (Wait, but I haven't used XP for three months :) ).
Joking aside, I don't know about the buggy software. Open Office is definitely more buggy on my Linux box than MS Office on Windows.

---

### Post by mscman on 2006-02-20
The reason why many Linux distrobutions don't support mp3 and DVD playback right out of the box (along with many other media types) is because of the cost of licensing.  Yes, there are some linux distros that support these media types, but you will find that those distros usually have some sort of fees associated with them.  This is because the cost of licensing to include these codecs in your software is phenomenal.  It has been discussed many times to include these codecs in many distros, but the cost issue has caused it to be a no-go.

---

### Post by Lord Illidan on 2006-02-20
[quote=mscman]The reason why many Linux distrobutions don't support mp3 and DVD playback right out of the box (along with many other media types) is because of the cost of licensing.  Yes, there are some linux distros that support these media types, but you will find that those distros usually have some sort of fees associated with them.  This is because the cost of licensing to include these codecs in your software is phenomenal.  It has been discussed many times to include these codecs in many distros, but the cost issue has caused it to be a no-go.[/quote]

There are some free distros like Simply Mepis  and PC Linux OS who include these things out of the box without any regard for the licensing. Hope they don't get into trouble, though.

---

### Post by thespazzz on 2006-02-20
[QUOTE=Lord Illidan]While I agree about the security problems, XP hasn't given me a bluescreen in over 3 months. (Wait, but I haven't used XP for three months :) ).
Joking aside, I don't know about the buggy software. Open Office is definitely more buggy on my Linux box than MS Office on Windows.[/QUOTE]

XP dosen't give me bluescreens granted.  At least not due to a software error (usualy) I have gotten them due to a faulty video card.

Open Office works just fine for me.  Actualy I can't think of anything other than WINE that gives me any trouble on Ubuntu

---

### Post by Lord Illidan on 2006-02-20
[quote=thespazzz]XP dosen't give me bluescreens granted.  At least not due to a software error (usualy) I have gotten them due to a faulty video card.

Open Office works just fine for me.  Actualy I can't think of anything other than WINE that gives me any trouble on Ubuntu[/quote]

I remember getting them blue screens on a previous ATI video card. It would lock up when playing certain games..

I am rechecking Open Office now that I installed Ubuntu, instead of Kubuntu. In Kubuntu, Impress was crashing every time I made a new slide...well, almost.

---

### Post by az on 2006-02-20
[QUOTE=torx]Personally, i don't think GNU/Linux is ripe enough for mass-consumerism. And honestly, i like it that way.   It's one of the few things in life still very priviledged to geeks like us and it sets us apart from the rest. =) 
[/QUOTE]

What are you from 1999?

[QUOTE=torx]However, it is praise-worthy of Microsoft to making computing easy. Microsoft to me is like Adobe Photoshop, easy to use without compromising functionality.[/QUOTE]

Gnome makes computing way easier than the microsoft desktop.  Adobe makes Photoshop, not Microsoft.

It's just a matter of time before the free-libre tools rival phtoshop.  A few years ago, GimpShop didn't even exist...

---

### Post by holomorph on 2006-02-26
I agree about ease of use; I find Ubuntu much easier to use for most of the things I want to do.  I use both windows XP and Ubuntu frequently, but I often feel a bit crippled in XP.

Primarily, what makes my Ubuntu exerience superior to windows is:
1. The OpenBox window manager.
2. Virtual desktops (though I have tweaked all my windows systems with nvidia tools to include virtual desktops)
3. Easy software installation and management (through apt-get or synaptic) and the plethora of free software available.
(4. copy and paste)

I'm sure there are others, but those are my top three as far as usability goes I think (oh yea bash is way more functional than the windows command line).  

There are also various moral, philosophical, and economic reasons I prefer open source software, but that's hard to articulate in brief (and others do it much better than I).  

And yes, there are definately still a few things that are a pain in the *** to make work, but I find these days that they are just different pains than windws, not that there are more of them.

---

