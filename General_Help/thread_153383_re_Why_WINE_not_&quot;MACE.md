---
title: "re: Why WINE not &quot;MACE"
date: 2006-03-31
forum: General Help
---

### Post by master5o1 on 2006-03-31
Why does everyone want windows programs? Why not have a MAC Emulator ("MACE"?)

Is there a mac emulator? coz if MAC is a unix based system like Linux...shouldnt it be easier to do than WINE??

---

### Post by Zeroangel on 2006-03-31
[quote=master5o1]Why does everyone want windows programs? Why not have a MAC Emulator ("MACE"?)

Is there a mac emulator? coz if MAC is a unix based system like Linux...shouldnt it be easier to do than WINE??[/quote] 
[COLOR=Sienna]**W**[/COLOR]ine[COLOR=Teal] [COLOR=Sienna]**I**[/COLOR][/COLOR]s [COLOR=Sienna]**N**[/COLOR]ot an [COLOR=Sienna]**E**[/COLOR]mulator (it's a compatibility layer)

---

### Post by frup on 2006-03-31
that doesnt answer his point though. i think its a good idea

---

### Post by Kevinator on 2006-03-31
PearPC comes to mind, but I think this is actually a PPC emulator, and is not intended to run Mac applications without MacOS.

I think the answer to the question of why WINE is so popular is that most non-native software that people want to use on GNU/Linux is Windows software. Also, as Zeroangel said, WINE doesn't do emulation, and therefore doesn't suffer the performance hit of running non-native code (only non-native API calls).

---

### Post by mcmillan on 2006-03-31
I remember coming across a mac emulator once, can't remember the name though. I think it's a bit more complicated since it also has to emulate a different processor. But I do imagine the biggest reason wine is so much more popular is like Kevinator said, more software that people are looking to run seems to be for windows

---

### Post by schwegler on 2006-04-05
Since there is MAc OSX on x86 hardware wouldn't a Mac Compatability layer be easier now?

---

### Post by NeghVar on 2006-04-05
> Since there is MAc OSX on x86 hardware wouldn't a Mac Compatability layer be easier now?

Im not up on apple but is it out yet, and if it is, hasnt it only been out for a short period of time...

---

### Post by terranz on 2006-04-05
running mac programmes on linux would probably make linux more popular than windows for using an ipod.

iCal
iTunes etc

---

### Post by JoeMetal on 2006-04-05
[QUOTE=NeghVar]Im not up on apple but is it out yet, and if it is, hasnt it only been out for a short period of time...[/QUOTE]

The new Macs are now shipping out with Intel chips.  They are also released an alpha version of a program called Boot Camp which will allow users to dual boot windows and os x.  Boot Camp will come with Leopard which will be unveiled in August.  

One reason that there are few (if any) mac emulators is because Macs are fundamentally different that Windows machines.  And since more people switch to Linux from Windows than from Macs, there is not such a big push to emulate their software.

---

### Post by terranz on 2006-04-05
OSX is built on BSD so how different could it be?

---

### Post by Toxicity999 on 2006-04-06
He's talking hardware.. in the past and considerably less now Macs are run on very different pieces of hardware (PPC EFI and all that.) The gap is closign for sure with the new Intels but as of now... *shrug*

---

### Post by MighMoS on 2006-04-06
[QUOTE=terranz]OSX is built on BSD so how different could it be?[/QUOTE]
Very different.  A) Apple changed a lot of things that make many programs that run fine on BSD have issues on OSX.  B) BSD is **not** Linux.  C) Apple programs are not usually written using the same API as BSD, but Cocoa or whatever its called, so *very* different.

And one of the reasons I can think of that there is no Mac emulator is because most Mac programs that I can think of off the top of my head already run on Windows (I.E: iTunes, Photoshop, etc).  As mentioned earlier, PearPC is a full blown emulator, meaning that you actually need a copy of MacOSX to run the programs, whereas WINE Is Not an Emulator, and just translates all the API calls to Linux ones on the fly (no Windows OS needed).

---

