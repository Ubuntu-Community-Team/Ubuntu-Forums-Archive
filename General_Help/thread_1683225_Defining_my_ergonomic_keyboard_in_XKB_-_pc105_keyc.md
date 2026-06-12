---
title: "Defining my ergonomic keyboard in XKB - pc105 keycodes?"
date: 2011-02-07
forum: General Help
---

### Post by DreymaR on 2011-02-07
Hello! I'm new here, so please bear with me if I'm doing anything wrong. :)
 
I've just moved to Ubuntu and so far I'm loving it. But I can't get the keyboard layout I'm using quite right:
- I use a pc105 keyboard (aka ISO or "European")
- I move the ZXCVB keys to the left, and the displaced <LSGT> key back where the B key was
- Then, I move all alpha group keys on the right hand one step to the right and the displaced keys back to the middle.
- Together, this constitutes the AngleWideErgo mod which gives a better left-hand wrist angle, better hand separation and shorter distance to the Enter and Backspace keys. I love it!
 
Proselytizing aside: So I want these keys to move but it's not just a Symbols thing. You can type QWERTY with this, or Colemak (which I use) or what-have-you; the Ergo mod is on a lower level. I move the physical key caps around and I want it to be the same for all chosen layouts. I'm ready to compromise the expected logic between symbolic key names and actual placement to achieve this (so that, e.g., the <AB01> key isn't in it's old position anymore - that's my point!).
 
So I changed the Geometry component of XKB, adding a pc(pc105wide) board by adding entries to the pc geometry file, rules/xorg.lst, rules/base.xml as well as rules/evdev.xml and selected that. I hope that's right?
 
Managed to change the keyboard image, yay! But not the codes themselves. Next one out should be Keycodes then I suppose?!
 
Now to the actual problem: I can't find the pc105 board keycodes to change!!! I want to add a pc105wide set of codes (preferably by including the ordinary pc105 and then changing only what I want to change!), but where do I start? There's the evdev keycodes, and the xfree86 ones, and pc105 is found in digital_vndr and sgi_vndr/indy at least. But I have no idea which of these codes I should make changes to.
 
What I'd like to do once I know where to put it, is something like this (based on code found in the xfree86 file):
xkb_keycodes "pc105wide" {
<AB01> = 94
<AB02> = 52
<AB03> = 53
<AB04> = 54
<AB05> = 55
<LSGT> = 56
augment "somefileidontknowthenameofyet(pc105)"
...
 
Where is the "default" pc105 board defined? Which keycodes is XKB using for my selected "Generic 105-key (Intl) PC" keyboard? I wish there were a "Generic" directory somewhere...

---

### Post by VCoolio on 2011-02-07
I really don't have much of a clue about what you're trying to do, but if you run 'xev' and then press the key you need info about, does that help?

---

### Post by DreymaR on 2011-02-07
Thanks for replying!

No, xev will tell me that I pressed a key with for instance keycode 94 (keysym 0x2d, minus). What it doesn't tell me (I think) is how the system arrived at this conclusion! It did provide a little info however: My <LSGT> key has keycode 94, and the ZXCVB keys have 52-56 respectively. So I'm using a board defined like the xfree96 and evdev codes, and nothing like the SGI or Digital ones. That's something!

Still, I need to know which keycodes to change and how. Should I just add my xkb_keycodes "pc105wide" entry to the bottom of the xfree86 file, or what? And why can't I find a "pc105" entry anywhere in the xfree86 keycodes or anywhere else that makes sense to me? Where exactly is my "pc105" aka "Generic 105-key (Intl) PC" keycodes specified?

---

### Post by DreymaR on 2011-02-09
Right - I've been in the thinking box!  :)

If I make an entry in the keycodes/xfree86 file named "pc105wide", I still need a link to that from the keyboard model I've chosen.

I'll probably have to add a line in the keycodes.dir file like this:
-------- -------- xfree86(pc105wide) 
(Or is that generated automagically?)

However, now I'm looking to get a new line inside the /usr/share/X11/xkb/rules/base file, 
under "! model  =  keycodes" that says "pc105wide        =    xfree86(pc105wide) ", right?

That file states that I shouldn't be editing it manually as it's generated from *.part files, and when I made the keyboard definitions I did indeed get them into the file by editing the base.xml file and watch the magic happen. But I don't see any editable .xml or .lst or for that matter .anything files that let me set a link between the keyboard model and its keycodes?!

So there's my dilemma, still.

---

### Post by DreymaR on 2011-02-11
Yay! It's working now! Turns out I'd written "xfree98" in a couple of places where there should've been a "xfree86".

Still feeling bad about manually editing the base and evdev rules files, but at least I now have a workable solution.

---

