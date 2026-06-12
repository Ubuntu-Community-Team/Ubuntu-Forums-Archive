---
title: "GTK slugginess"
date: 2006-03-03
forum: General Help
---

### Post by Flupke on 2006-03-03
Hi there,

I experience long repaint times on just every program that uses GTK (mozilla, evolution, even simple ones like vim-gtk).
What I mean by slow is when the app has to repaint all of it's client area, say when you switch from one window to another, and the windows where perfectly overlapping (I use [ion window manager](http://modeemi.cs.tut.fi/~tuomov/ion/) so it just happens all the time), it takes sometimes as long as a second for the window to repaint entirely.
Remember the windows 3.1 days when graphic cards had no 2D acceleration ? You could see the applications parts redraw one by one, first the menu bar, then the buttons, then the contents ... That's what I'm experiencing.

The frustrating part is that my system is kind of high end (athlon 64 3500+, GeForce 7800 GTX PCIE, 2Gb ram) :mrgreen: 

I can tell the problem is bound to GTK, because I had the opportunity to try kvim in front of vim-gtk, and kvim was repainting about 10 times faster (well maybe not 10 times, but the difference was really noticeable). Unfortunately not all the applications I use have Qt variants (not to say that kvim is just not finished (no proper unicode support), and not maintained anymore :'( )

I tried to tweak my X graphic configuration (playing with nvidia's proprietary driver acceleration options, switching to opensource nv/vesa driver) ; the applications response time vary a little, but basically GTK programs stay slow.
This was tested on breezy and dapper.

I browsed the net but just discovered that lots of people experience the same problem, any ideas guys ? :)

[edit] : some precisions about my config, I use a wide screen (1920x1200) and saw this [thread](https://bugs.freedesktop.org/show_bug.cgi?id=4320) that seems to talk of the same bug. I will try to read it (it's kind of long :O) and keep you informed.

---

### Post by jdong on 2006-03-03
There's also the issue of Breezy switching to Cairo a bit too soon; as now, it just simply slows things down more than anything else, giving Breezy the illusion of being slow while just the GUI redraw is slow (which is bad enough). Dapper feels much much better, so sit tight I guess :)

---

### Post by Flupke on 2006-03-04
Yes Dapper feels much better in terms of UI responsiveness (in fact that's the reason why I chose to keep using it instead of Breezy :p).

Also reading the [discussion](https://bugs.freedesktop.org/show_bug.cgi?id=4320) about the bug I mentioned (which seems to not affect my installation by the way), I realised how complicated writing Cairo must be, and things will certainly get better and better :)

I'm stilll investigating and found that this [page](http://lambcutlet.org/) may expose a Cairo or GTK performance issue, as konqueror renders it much faster than firefox on Ubuntu, but not on windows (tested with firefox 1.5.0.1, and latest Dapper packages). Does it make sense ?

---

### Post by jdong on 2006-03-04
It's still GTK/Cairo related. Cairo is an investment in the future.

Having hardware X acceleration will help too (xgl/aiglx in the future)

---

### Post by towsonu2003 on 2006-03-04
hmmm, I think this is what I may be experiencing as well. I wanted to post because mine started in time and got a little worse with time as well. how can I diagnose if this is truly related to gtk, or something else (what my suspicions initially were either corrupted video driver / installation or corrupted OS, like in windows)?

---

### Post by jdong on 2006-03-04
Install KDE, contrast the performance of KDE apps versus GTK apps when windows are dragged, alt+tabbed, workspace switch, minimized, etc.

---

### Post by ComplexNumber on 2006-03-04
[quote=towsonu2003]hmmm, I think this is what I may be experiencing as well. I wanted to post because mine started in time and got a little worse with time as well. how can I diagnose if this is truly related to gtk, or something else (what my suspicions initially were either corrupted video driver / installation or corrupted OS, like in windows)?[/quote]
what are the main processes running on your system when its slow (ie run 'top')

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=ComplexNumber]what are the main processes running on your system when its slow (ie run 'top')[/QUOTE]
answer: the ones that are processing something (I know it's a weird answer). common programs are firefox (load digg.com in two+ tabs), gnu r (do graphics in tk interface <-Rcmdr), qemu (load web page in internet explorer) etc. use ~70-100% cpu when I'm doing some process in one of them. 

The common issue is, they are "drawing" stuff on the desktop... 

installing kde will be a far fetch with a dial up. xfce4 (smaller download of xubuntu-desktop) has some sluggishness as well, would that point to something? fluxbox (compiled from source) seems to be fine, although I need more time with it. let me know if comparing firefox in gnome vs. firefox in xfce4 vs. firefox in fluxbox would tell me anything as per diagnosis of cairo / gtk problems -thanks. 

oh wait, you said "kde applications". So konqueror vs. firefox --safe-mode will help me diagnose? (still a big download)

---

### Post by ComplexNumber on 2006-03-06
are you sure the problem isn't firefox? apparently, the resource-hogging nature of firefox is well known and is a 'feature' rather than a bug. i think it is probably due to this rather than gtk itself. have a read of this:
[http://www.theinquirer.net/?article=29707]("http://www.theinquirer.net/?article=29707")

is firefox present during the times when the slowness in other apps occurs?

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=ComplexNumber]are you sure the problem isn't firefox? apparently, the resource-hogging nature of firefox is well known and is a 'feature' rather than a bug. i think it is probably due to this rather than gtk itself. have a read of this:
[http://www.theinquirer.net/?article=29707]("http://www.theinquirer.net/?article=29707")

is firefox present during the times when the slowness in other apps occurs?[/QUOTE]
I am familiar with that Windows-like feature (read: bug). But it is more of a RAM issue than cpu, and I have plenty of free RAM (usually 650MB out of 1GB, no swap usage). 

Which one of the following would be the preferable way to go to diagnose if this is gtk:
a. compare firefox performance in gnome and xfce4 / fluxbox
or
b. compare konqueror (or another browser except dillo??) and firefox in gnome?
or both?

thanks :)

---

### Post by ComplexNumber on 2006-03-06
> But it is more of a RAM issue than cpu they are linked. if its a RAM issue, it becomes a cpu issue. if it uses more RAM, the cpu has to work harder.

i would say doing both a and b will give you some clues.

---

### Post by jdong on 2006-03-06
No, I'm fairly confident that this is related to the whole GTK+/Pango slowness that Breezy has.

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=jdong]No, I'm fairly confident that this is related to the whole GTK+/Pango slowness that Breezy has.[/QUOTE]
No as in: trying firefox in xfce4 and /or fluxbox will not give any meaningful results? Being ignorant about gtk, if so, I guess gtk is used in both environments regardless? 

well, than let's see dapper and compare it to suse in april. 

more ignorance: can I compile firefox not to use gtk but something else? I tried it compiling from source without success here: [http://ubuntuforums.org/showthread.php?t=140342](http://ubuntuforums.org/showthread.php?t=140342)

again, I'm clueless :) (in all issues mentioned here)

---

### Post by ComplexNumber on 2006-03-06
>  I guess gtk is used in both environments regardless? it is.

> 
can I compile firefox not to use gtk but something else? yes. you could try it with wxwidgets.

---

### Post by towsonu2003 on 2006-03-06
let's try that one... (not with wxwidgets but qt: wxwidgets not included as an option).

---

### Post by Flupke on 2006-03-06
I tried to compare mozilla and [mozilla-qt](http://www.mozilla.org/ports/qtmozilla/) side by side, and - at least on my system, I can really feel a difference (yes, I disabled fonts antialiasing, since mozilla-qt (qt2) does not support it :p)

I would say that qt is better, for the moment, at caching rendered parts of the interface : for example when you switch from a desktop to another, you see qt windows contents instantly, while gtk ones suffer from the "redraw part by part" symptom.

This could also mean that qt draws surfaces and text faster than gtk, but I believe this is a cache matter (I don't think that qt and gtk use completely different rendering paths on my (accelerated) X server, because both suck when using vesa driver :)).

Anyway this gave me the opportunity to discover how kde evolved, and I must say that I'm impressed =)

---

### Post by ComplexNumber on 2006-03-06
[quote=Flupke]I tried to compare mozilla and [mozilla-qt]("http://www.mozilla.org/ports/qtmozilla/") side by side, and - at least on my system, I can really feel a difference (yes, I disabled fonts antialiasing, since mozilla-qt (qt2) does not support it :p)

I would say that qt is better, for the moment, at caching rendered parts of the interface : for example when you switch from a desktop to another, you see qt windows contents instantly, while gtk ones suffer from the "redraw part by part" symptom.

This could also mean that qt draws surfaces and text faster than gtk, but I believe this is a cache matter (I don't think that qt and gtk use completely different rendering paths on my (accelerated) X server, because both suck when using vesa driver :)).

Anyway this gave me the opportunity to discover how kde evolved, and I must say that I'm impressed =)[/quote]
because gtk is in the 'changeover stage' betwen non-cairo and cairo, i have heard that gtk isn't anywhere near as fast as it should be. apparently, with cairo, it will be significantly faster

---

### Post by towsonu2003 on 2006-03-06
stupid mozilla and their bugs: [https://bugzilla.mozilla.org/show_bug.cgi?id=178987](https://bugzilla.mozilla.org/show_bug.cgi?id=178987) no qt for anything except mozilla-qt I guess. I also can't believe I'm hang on a stpd browser... grrr.... will try xlib... (all -dev are installed)

Nope - couldn't compile. I just too newbie for that crap I guess... let me know if someone manages to compile this thing withouth gtk / gtk2 -thanks...

---

### Post by hoggbottom59 on 2006-03-24
Has anyone tried changing an priorities using the System Monitor to see if giving the X Window process a higher priority helps?

I'm not sure which process it is or if you have to start changing the run-time levels or whatever at start up.

I think in Windows the GUI is set at a much higher priority than other things to give the illusion that it is smooth because any changes to the GUI in Windows cause the CPU usage to go right up.

Leon.

---

