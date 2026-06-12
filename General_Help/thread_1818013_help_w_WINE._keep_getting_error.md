---
title: "help w/ WINE. keep getting error"
date: 2011-08-04
forum: General Help
---

### Post by CleveRuse on 2011-08-04
I need help installing programs w/ wine. No matter wut app I attempt to install, I receive an error that the particular ".exe has encountered a serious problem" and nothing will install. Specifically, I'd like to run 'M10 Editor' in 'M10 Tools' but i'll settle for just getting anything to run at the moment. I also tried installing the PhotoShop, Safari, MSPaint..... that I found in WineTricks. All result in the same error. All of those, I just used the 'install application' option in WineTricks, but for the 'm10 editor.exe', and also 'xUltimates d9pc.exe', I'm placing in 'common files' in C_drive/program_files, then choosing to open w/ Wine's program loader. I just don't know wut Im doing wrong.

Obviously I just wanna run some Windows apps. I don't care how. I don't know anything bout Virtual Boxes or if that's the same as dual-booting Windows, so I'd love some insight on wut commonly works best. I plan to, eventually dual boot, but I'm on a netbook type laptop so I'd need to configure a copy of Windows to boot from flash and I don't have a large enough flash stick (only have a 1G) and i don't have another comp. w/ a cd drive, which I think I need

Maybe ill just go get my 16G microSD from my Ex and go to the library and use their computer. I just wanna theme my android, lol!;) Thnx in advance guys

Oh yeah, how do i end WineTricks? It said, I think, to type "winetricks -optout" to end. Where? In my gnome terminal? In Windows terminal? Where's that at? I don't even remember how in reg Windows, cept I had a short cut. Does WINE have a start menu? Confused....

---

### Post by zero2xiii on 2011-08-04
Wow thats confusing? :confused:

But oka let us see now:

First of all, how is wine installed? What version of wine is installed?

Second, please post the exact error message (or a screen shot if the text is not highlightable).


Then. Virtualisation. Its really easy, just donwload and install something like virtual box, then install windows inside it, its pretty easy to figure out, and use GOOGLE!.... There are awsome tutorials out there to get you going like a pro in no time at all. The setup is very very easy, usage is just as easy. its not as powerfull as VMware, but its fine for your usage.

Please give above information so we can follow on further :)

Edit:
I just wondered, is it the INSTALLER that is crashing, (eg installshield wizard) cause thats a very famillier appereance... There are a few ways around this, such as extracting the cab files (need cab extract and 7zip)... or install the application inside a windows environment then copy the working install (from programfiles under windows) to your linux box,

Oh and yes, wine does have a menu, its under Applications > Wine > Programs.

Another thing, is the executable bit set on all the files requierd by the installer? RIght click, properties, the permissions tab...

---

