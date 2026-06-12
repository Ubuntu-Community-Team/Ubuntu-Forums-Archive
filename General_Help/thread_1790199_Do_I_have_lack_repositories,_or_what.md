---
title: "Do I have lack repositories, or what?"
date: 2011-06-24
forum: General Help
---

### Post by Aisaka_Tiger on 2011-06-24
Please excuse how surely ignorant and annoying I am. Ubuntu has become the "Linux for everyone", including idiots like me, and I'm certainly one of those ignorant types about computers. So this may come out of left field and stupid, and even embarrassing to exist on the forums.

Long story short, I built a new computer, and used Wubi to make a dual-boot with Linux and Windows 7 both available. Since I finally wanted to try Linux(actually I had tried it once before on an old laptop, but this was my first desktop experience).

At first I tried Kubuntu. But I was having problems so I uninstalled Kubuntu and installed Xubuntu. Things have been going mostly pretty good, but there's still the same old problems which some google searches don't seem to fix, at least not quickly.

I still don't understand how on earth I can get Wine to play the games I want. Which is a topic for another time. All of the times I try to search "Wine tutorial" or "Wine configuration" it does little, and most things talk about PlayOnLinux or Winetricks or the like. But there's a limited amount I've been able to do with that. 

And onto the other problem, a lot of the programs for Linux I've been trying to find that should be there in the Synaptic Manager, aren't there in the search, they were worse, much worse in Kubuntu, but they're not great here, either. It seems to be a repository problem. But I don't know how to update that or whatever. I had to find a off-site that gave me a long Terminal command to put Dolphin the emulator, in the repositories, I don't remember what it was, but it finally worked. It's not listed in my "other software" as ppa.launchpad.net/glennric/dolphin-emu/ubuntu natty . And I again can't remember what that Terminal command was for the life of me. But I don't know how else I would have gotten it to show up on Package Manager without doing that. It certainly wasn't there before. And I had everything on "other software" listed, checked. Canonical Partners, Independent, all of them.

And I'm still having problems because of this sort of thing. Now that I've gotten Dolphin to work, albeit at a lower framerate than in Windows 7, I also can't get many files from PlayDeb.net to work. I tried getting pcsxr from there, but Ubuntu Software Center says "Not Found. There isn't a software package called "Pcxsr" in your current software sources". So the solution would seem to be, get more and better ones. But aside from checking all of the boxes and reloading/updating normally, I don't have a clue how. I had to search for that Dolphin-emu repository, and that was a single repository.

I don't understand why my repositories always seem so... limited. They're pretty limited in this. And they had almost nothing available in Kubuntu. That was a long and drawn out way to say something simple, new, and idiotic, and I'm sorry if I'm saying something embarrassingly dumb on your forums. And making you read a lot just do to so. I would use the "absolute beginner" section like the beginner fool that I am, but it appears that section is only an archive now.

Um, if you want to know my specifications. I'm using a AM3 X2 Callisto CPU, an HD 4870 GPU... and that's pretty much the most you need to know about my hardware, right? I should have the best ATI Drivers, since it asked me if I wanted to update as soon as I first booted up Xubuntu and I said yes and installed them. If you want the technical aspects, my Catalyst Control Center says this:

BIOS: 
Date 03/02/09
Version 0
Part Number 113-SBJ2G11-00R-00
Memory:
Type DDR5
Clock 900 MHz
Size 1024 MB
Bandwidth 115.2 Gbyte/s 
BUS:
Graphics Capability PCI Express 2.0
Maximum Setting x16
Core Clock 750 MHz
Software: 
Driver Packaging Version 8.84.6-110324a-116088C-ATI
2D Driver Version 8.84.60
Catalyst Control Center Version 2.13
Rand R Version 1.3
Open GL:
Open GL Provider ATI Technologies Inc.
Open GL Renderer ATI Radeon 4800 Series
Open GL Version 3.31.10665 Compatibility Profile Context

For some screenshots:

Catalyst information:
[http://img.imgland.net/KCGxMtuv2.png](http://img.imgland.net/KCGxMtuv2.png)

Ubuntu Software Center and the results of trying to get Dolphin in it:
[http://img04.imgland.net/M7w8fTR4W.png](http://img04.imgland.net/M7w8fTR4W.png)
It is checked under "all software", instead of just "Canonical Maintained Software".

A screenshot of my "other software".
[http://img.imgland.net/bsaFNfiveV.png](http://img.imgland.net/bsaFNfiveV.png)

The result of clicking "install this now" on the pcsxr page of PlayDeb.net.
[http://img04.imgland.net/zGGevx8mUq.png](http://img04.imgland.net/zGGevx8mUq.png)

And that is pretty much the gist of things. Sorry for being such an idiot. I know Linux is DIY. But I've having a bit of a hard time figuring out of of the DIY aspects. I've been able to do most of what I want to do on Linux that I can do in Windows to a fair degree, torrent things, watch things, browse the internet, listen to music and have it scrobbled on Last.fm, use messenger, and that's pretty much it.

To bring things all to one, it'd be nice to be able to play Doujin/Indie games without problem on Wine, and emulate PlayStation and PlayStation 2 games just like I'm used to doing on Windows 7. So far one of the only Indie games I've been able to get to work is Eversion, which had no problems in Wine. Recettear, not so well. Even though I installed Steam in PlayonLinux. I seem to have some rather limited choices on some of these things, without a lot of searching. And I'm plain worn out/stumped.

Thanks to anyone who cares to spend the time reading my incredibly uneducated and foolish post.

---

### Post by silex89 on 2011-06-24
Man, don treat yourself like crap!, we are pleased to help you :), you're trying to learn things out!, that's very valuable, everything takes its time, it's just a matter of little patience and everything goes well :)


Your problem is really easy to resolve, just open up a terminal and type

```
sudo apt-get update
```

That should give you the whole list of libraries and apps out there.


Best luck :)

---

### Post by haqking on 2011-06-24
update your repos

sudo apt-get update

then see what happens

edit: ninja'd by above ;-)

---

### Post by SunnyRabbiera on 2011-06-24
Unfortunately for your Wine inquiries, well there isn't much to do about it as wine is not perfect, there are many windows apps that simply wont install in it and this includes many games.
Gaming is a MAJOR weakness in linux and to be honest the best way to game on your PC is to dualboot with windows no iffs, ands or buts about it.
Keep in mind Wine is reverse engineered software so it can only cover so much in the windows programming library.

As for your repository issue, what are you trying to install?

---

### Post by haqking on 2011-06-24
as for the PCSXR from playdeb.

if you folow the link the website specifically for it you can get it there.

[http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)

and choose your version

---

### Post by Aisaka_Tiger on 2011-06-24
> **SunnyRabbiera said:**
> As for your repository issue, what are you trying to install?
Hopefully a working PlayStation emulator. And maybe even someday PCSX2. I've spent countless hours using ePSXe and PCSX2 in Windows. Especially nice would be using it under Pete's OpenGL1 and OpenGL2. Games look really nice in those.

In this case, it seems PlayDeb.net had one, but not ePSXe. Pcsxr, it was.
[http://www.playdeb.net/software/pcsxr](http://www.playdeb.net/software/pcsxr)

I just went to Terminal and put that in, but it didn't seem to work. In fact, I've tried that many times under Kubuntu and Xubuntu both, and neither seemed to work. And in this case pcsxr does not seem to even still be available. Perhaps I need to reboot?
> **haqking said:**
> as for the PCSXR from playdeb.

if you folow the link the website specifically for it you can get it there.

[http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)

and choose your version
That's fantastic, thank you very much!

Oh, darn me though for accidentally not paying attention when looking for a deb file and clicking [386.deb]("http://pcsxr.codeplex.com/releases/view/50048#DownloadId=140537")  when I'm running AMD64 obviously. Gave me a "Wrong architecture 'i386'"  sign even when I went back in and clicked on the AMD64 option. But it  seems to have installed anyway.

I hope this works, thank you! I wonder why PlayDeb.net didn't work?

Anyway, I'm going to try to get this emulator to work now. I'll come back and post my results soon!

---

### Post by haqking on 2011-06-24
> **Aisaka_Tiger said:**
> Hopefully a working PlayStation emulator. And maybe even someday PCSX2. I've spent countless hours using ePSXe and PCSX2 in Windows. Especially nice would be using it under Pete's OpenGL1 and OpenGL2. Games look really nice in those.

In this case, it seems PlayDeb.net had one, but not ePSXe. Pcsxr, it was.
[http://www.playdeb.net/software/pcsxr](http://www.playdeb.net/software/pcsxr)

I just went to Terminal and put that in, but it didn't seem to work. In fact, I've tried that many times under Kubuntu and Xubuntu both, and neither seemed to work. And in this case pcsxr does not seem to even still be available. Perhaps I need to reboot?

the deb and binaries in .tar on the site link i posted above ^

---

### Post by SunnyRabbiera on 2011-06-24
Fair warning: ps1 emulation on linux is a little shaky, at least in my experience

---

### Post by Aisaka_Tiger on 2011-06-24
Woah, it works. Thanks for the heads up. That makes one more think I can do in Linux without having to rely on Windows.

It doesn't look great, but pcsxr is working. I think I'll go in and configure the graphics to see if I can get it looking on part to Pete's OpenGL1 without downloading something.

That's kind of disappointing that it appears there will be many things I like to do, that I can't easily do in Linux, since I'm a huge gamer. But otherwise I'm having a great time.:KS

Sorry, that part about Wine was probably off topic, too. I made this thread about programs I've had a hard time getting in the Synaptic. I'll know to make a thread about Wine in the Wine section when I ask about that. Sorry.

**Edit:** Oh yes, this looks very nice. I just turned the graphical settings on the plug-in all the way up and set it to 720p windowed. And this looks equally nice to Windows. Suberb. One less thing for me to feel the need to boot into Windows for. And it's **free**. Thank you all so much, this has been a great help.

And just to give proof of accomplishment, my first screenshot of emulating the PlayStation One in Linux!
[http://img03.imgland.net/LPfxPF4es.jpg](http://img03.imgland.net/LPfxPF4es.jpg)
Feels great. As one more world of opportunities for gaming in Linux has opened up for me.

---

