---
title: "Help, I'm in Windows Nightmare! :'-("
date: 2010-02-28
forum: General Help
---

### Post by ClarkePeters on 2010-02-28
I abandoned Windows completely over 4 or 5 years ago, but now, within the last couple of months, I'm having all sorts of Window-like nightmares! It makes me so sad because the whole reason I switched was the speed and simplicity of Ubuntu (no lag, screen lockups, or reboots).

I do mostly office stuff but do watch and edit movies sometimes (avidemux, mencoder, ffmpeg), never had problems, lightning fast--everything. My laptop is only a couple years old if that, so I can't imagine I'm having hardware problems (ACER, 1gb DDR, ATI Radeon, Intel(R) Core(TM) Duo CPU  T2450  @ 2.00GHz;  800mhz; L2cache 2048KB; Swap at 3GB usually free or 98%; 160 gig hard drive about 30 gigs free;) 

If I use evince or kpdf, almost everything comes to a stand still; even without that problem, gnome file manager has serious lag, also, switching from one prog to another like from gedit to openoffice or from firefox to whatever, also has very serious lag. I can't do anything with movies without frame freezes or jumpiness. I used to download torrents while I was compiling in avidemux while using open office too -- life used to be so sweet.

How can I 
1) analyze my system to see what the trouble is and fix it, or pare down my ubuntu. (I've already turned off a lot of startup progs)
OR
2) Run hardware diagnaostics (sometimes I wonder if my cpu is overheating)
OR
3)  Should I abandon Ubuntu and go for something like Xubuntu or Lubuntu, or maybe just a pared down Debian system and build up only with essentials?

Sometimes after a reboot, things work okay for a bit, but start to slow down later, sometimes a reboot doesn't help, and occasionally, my computer seems to run okay, like before but not that often (usually just open up a single prog or two).

I almost always have firefox open because of my job, and used to have as many as 20 tabs or more open while also working in open office and gedit simultanesouly (I could never get that kind of performance with Windows) so things used to work really good for me on Ubuntu.

Any advice appreciated. It's 3am here and I have a full day tomorrow but I'll try to check back as soon as possible.

---

### Post by dragonboss on 2010-02-28
Check what programs are hogging ram or cpu in th system monitor in the system>administration menu or from the terminal with top or htop(sudo apt-get install htop)
Firefox uses up quite a bit of RAM too so 20 pages at once with open office is a bit much!

---

### Post by ClarkePeters on 2010-03-01
What I've found out is that my memory, regardless of the number of apps I open, tends to hang around 300+ mb, which I think is good, seems that even with large apps like openoffice and vlc running a movie at the same time, doesn't affect memory too much -- so seems Ubuntu has good memory management. Swap is consistently at 30+ mb.

for processes, the biggest users of memory for the system are deskbar-applet (~30mb), gnome-panel (~30mb), nautilus (~70mb), python (~16mb)

for processes, the biggest users of memory for applications are firefox 3.0.x(~80mb), evince (~25mb),  openoffice (~25mb), gedit (~15mb), and VLC (~25mb);

But like I said, the memory manager (according to resources), keeps the memory usage around 300+mb no matter whats going on. I once got it up to 450mb but I was intentionally opening as much as I could to push the envelope.

CPU
However, the cpu usage jumps to 100% on both CPUs quite frequently, especially when opening any prog for the first time, and even on closing. I suppose that's not totally suprising, but what is surprising is that, especially on opening a prog, the CPUs will both hang at 100% usage for anywhere from 10 to 40 seconds--that's causing some serious lag time, and why I'm getting frustrated working on Ubuntu, the same happens when I'm just switching from one app to another, major lag time--JUST LIKE GOOD OLE WINDOWS! yippee!

Even when not a single app or prog is open, the CPUs run around 30% each, vacillating from say 15 to 45%.

Also, on closing almost any app, I get a lot of "not responding" "force quit" messages.

So, guys/gals, I need some help with the next step. What do I do?

BTW would it be possible that it's not ubuntu but something like my CPUs overheating so they have to work harder?

Any advice or direction appreciated.

---

### Post by houseworkshy on 2010-03-01
Well usually worth cleaning the innards of the box, it could be a temperature thing.  Depending on the enviroment they can get dirty fast, especially around smoking and that makes things hot.  For something which used to work and doesn't anymore that would be the most likely explaination.  The htop advice above is well worth trying.  If that doesn't find any problems see how much your swap file is being used, such things can be altered.

---

### Post by underquark on 2010-03-01
When it next crashes, reboot and go into the BIOS.  See what the CPU temperature readings are and also (if your BIOS supports it) see what your voltages are doing, particularly if your 5V is <4.7 or >5.3.  Overheating and power supply failure are both possible.  Mind you, so is a failing graphics card/chip/memory.

---

### Post by 3rdalbum on 2010-03-01
If your CPUs are working at 30% when they should be idle, then you simply need to use System Monitor to find out exactly which programs are working your CPU so hard, and then kill those programs. Just sort the list of processes by CPU % and the offending programs will pop to the top of the list.

That's all there is to it.

---

