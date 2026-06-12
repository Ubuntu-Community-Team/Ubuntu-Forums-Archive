---
title: "Strange keyboard issue"
date: 2010-07-24
forum: General Help
---

### Post by ed-koala on 2010-07-24
I recently upgraded to the latest kernel - 2.6.32-24 I believe - and all is well, except when I rebooted to the new kernel my Function keys would not work at reboot.  I was unable to hit F-1 as I needed to continue.  Escape and other keys worked fine.

I had to plug in a different keyboard to get past my boot screen.  All keys are working fine now, including the F keys.  So it isn't a dead keyboard.

Any ideas what might be the problem here?  This has never happened before, so the upgrade and resulting problem seem to be related, but how can that be when I hadn't gotten to the OS?

edit:  Actually, my F keys do not seem to be working since the kernel upgrade.  Any ideas how to fix this?

---

### Post by ed-koala on 2010-07-24
Hmmm, most curious.  Pressing F1 brings up a black info area with a light bulb and the words Power Information.  Obviously my keyboard works (not correctly) but none of the other F keys seem to do anything.

I've tested F9 and F10 by enabling water effects in Compiz but the key combos do not work.

Really need some help figuring this one out.  What happened to my F keys?

---

### Post by ubunterooster on 2010-07-24
Is the problem the same on both keyboards?

---

### Post by ed-koala on 2010-07-24
No.  An old Compaq keyboard I had lying around works normally.

I'm at a loss to figure out why my F keys are gone/acting funny.  I can't imagine it's Ubuntu as I can't use F1 to get past the Bios screen, before any OS is loaded.  But pressing F1 in Ubuntu does bring up that power info area, so it IS doing something, just not what it should.

Oh, booting into the previous kernel has no effect, so all I can figure is this keyboard is dying a very weird death.

---

### Post by floopy1962 on 2010-09-25
Hi i have very strange issue... i believe is not from my keyboard... i have this keyboard from long time.
The Problem is that when i type for example "e" i get "¤" when i type "-" i get "\" when i type "4" i get "$" everything is a mess... :confused:
My language switcher i gone and when i use xfce switcher with xfce panel my language's i gone i don't have "bulgarian traditional phonetic" any more in keyboard preferences don't have bulgarian to :( what is going on... also my arrows doesn't work in text entryes, i have to select text with the mouse.
sorry for bad english... is hard to write with "ctrl+c" and "ctrl+v" thanks god that the backspace is working :D pls help 
... So i think i found my problem but i don't know how to fix it :)
i upgrade to maverick (this is not solve my problem) 
the probrem is that my default keyboard layouts just disappear... 
for english-us i have only "US 105-key keyboard (with windows keys)" witch looks like this:
[IMG]http://i52.tinypic.com/2s804tv.png[/IMG]
and for bulgarian have only "Bulgarian Keymap" :
[IMG]http://i53.tinypic.com/2hyf67r.png[/IMG]
but i want this:
[IMG]http://i56.tinypic.com/2j4ocih.png[/IMG]
where are "united state" layouts and "bulgaria, bulgarian phonetic, bulgarian phonetic traditional" ...
why they disappear, how can i bring them back pls help :(
and something else... when i go to init 3 or 4 the keyboard work normal with normal layout when start X again 105-key...

---

### Post by floopy1962 on 2010-09-26
pls... do i have to reinstall whole system for this :confused:
ok i solve tha half of the problem... i just delete the "/usr/share/xmodmap/" folder and the keyboard working ok now :P
now i got little problem again :(
i'm from bulgarian and now i don't have bulgarian... i don't have any langs 
can i download from somewhere keymaps...
thanks :P ...

---

