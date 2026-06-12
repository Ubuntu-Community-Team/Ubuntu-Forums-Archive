---
title: "AisleRiot Solitaire crash"
date: 2006-06-17
forum: General Help
---

### Post by Martian on 2006-06-17
Just recently, AisleRiot Solitaire has started 'crashing' when I try to select a new game (sometimes...).

Here's what comes up in the terminal:
```
Backtrace:
In /usr/share/sol-games/sol.scm:
 480: 0* (if (defined? (quote card-guardian)) (letrec (# #) (catch # # ...)) ...)
 481: 1  (while (card-guardian))
In unknown file:
   ...
   ?: 2  [catch break #<procedure #f ()> #<procedure #f v>]
   ?: 3* [#<procedure #f ()>]
   ?: 4* [continue]
   ?: 5  (or (not (card-guardian)) (begin (begin) (continue)))
   ?: 6  (begin (begin) (continue))
   ?: 7* (begin)

<unnamed port>: In procedure begin in expression (begin):
<unnamed port>: missing or extra expression
```

I have done some further 'testing' using the terminal.  Some variations cause AisleRiot to crash when trying to switch to and/or from them, bringing up the same message as above.  Some variations seem 'safe' enough for the most part, such as FreeCell... Still, while I can switch from FreeCell to Jumbo without a crash, switching back to FreeCell from Jumbo crashes AisleRiot.  Some variations, such as Klondike and Elevator, seem to be practically guaranteed crashers when either switching to or from them.

Anyone else having a similar problem?  I'm just trying to determine if a reinstall is in order or if recent updates have 'broken' something (I'm using Dapper Drake with all the latest updates).

---

### Post by mikaw on 2006-06-17
Aisleriot crashes here when I try change to different game. Default Klondike have been working ok.

Machine is IBM ThinkPad A31p and all the patches that system have been suggesting have been installed.

---

### Post by Computeruser on 2006-06-17
Agree - I just tried it and Klondike is the only one that works.

---

### Post by Martian on 2006-06-17
Did either of you try loading up AisleRiot using the "FreeCell Solitaire" link in the Games menu?

You can also start AisleRiot using the terminal command:
```
/usr/games/sol
```
The above command will have the same effect as clicking on "AisleRiot Solitaire" in the Games menu.

A specific variation can be loaded up using the terminal.  For example, if you want Helsinki, you can use the command:
```
/usr/games/sol --variation helsinki
```

If nothing else, you can use the terminal to start up whatever solitaire game you wish to play... The names of all the variations can be found in the /usr/share/sol-games/ directory (all the .scm files).  I've attached a text file with all the variation names, just in case anyone has difficulty finding the directory...

---

### Post by Computeruser on 2006-06-18
I didn't bother (I don't need it). We are reporting a (small) bug - that's all.

---

### Post by Martian on 2006-06-19
Yep.

---

### Post by SuperJETT on 2006-06-28
Same problem here.

I just reinstalled Dapper 4-5 days ago and this behavior popped up where on the previous install it worked fine.  

The terminal start works fine, but my wife doesn't like it.

---

### Post by eagle101 on 2006-07-03
It worked when I first installed 6.06, but I just did about 70Meg worth of updates gtk libs, qt libs, kernel, you name it -  and it quit working.  I uninstalled it with ubuntu-desktop and reinstalled it & it didn't help :-| 

Sorry, no advice.  Just in the same boat also.  I'd really like this game working right also.

---

### Post by eagle101 on 2006-07-03
I saw this on a few other threads with no solution, besides using the command line to start each game.  I have no idea about scheme (which the sol.scm file seems to be), so can't help there.  
Regards - Dave

Dapper Drake, most recent updates 7/03/06

Aisleriot version 2.14.2

Crash data:

Backtrace:
In /usr/share/sol-games/sol.scm:
 480: 0* (if (defined? (quote card-guardian)) (letrec (# #) (catch # # ...)) ...)
 481: 1  (while (card-guardian))
In unknown file:
   ...
   ?: 2  [catch break #<procedure #f ()> #<procedure #f v>]
   ?: 3* [#<procedure #f ()>]
   ?: 4* [continue]
   ?: 5  (or (not (card-guardian)) (begin (begin) (continue)))
   ?: 6  (begin (begin) (continue))
   ?: 7* (begin)

<unnamed port>: In procedure begin in expression (begin):
<unnamed port>: missing or extra expression



Reading another thread someone suggested the .conf file might be corrupt.
I tried deleting %gconf.xml from :~/.gconf/apps/aisleriot$  :~/.gconf/apps/aisleriot/rules, but it reappears with my old preferences. 

It doesn't look corrupt anyway:

<?xml version="1.0"?>
<gconf>
        <entry name="statistics" mtime="1151917551" type="list" ltype="string">
                <li type="string">
                        <stringvalue>Golf</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>7</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>Klondike</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>1</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>0</stringvalue>
                </li>
        </entry>
        <entry name="height" mtime="1151952499" type="int" value="590">
        </entry>
        <entry name="width" mtime="1151952499" type="int" value="595">
        </entry>
        <entry name="card_style" mtime="1151952499" type="string">
                <stringvalue>bonded.png</stringvalue>
        </entry>
        <entry name="game_file" mtime="1151952499" type="string">
                <stringvalue>golf.scm</stringvalue>
        </entry>
        <entry name="show_toolbar" mtime="1151952499" type="bool" value="true">
        </entry>

---

### Post by ccnelson on 2006-07-11
This problem is only affecting my Dapper system where I installed a new 
hard drive and then installed the OS from scratch.  My Breezy box, and my Dapper box that was upgraded from Breezy have no problems with Solitaire.  My laptop (IBM T23) which does show the problem, didn't before I replaced the
HD and was running a system that was upgraded from Breezy.

So, no solutions here, but maybe this information will give someone some ideas.

---

### Post by eagle101 on 2006-07-12
> **ccnelson said:**
> This problem is only affecting my Dapper system where I installed a new 
hard drive and then installed the OS from scratch.  My Breezy box, and my Dapper box that was upgraded from Breezy have no problems with Solitaire.  My laptop (IBM T23) which does show the problem, didn't before I replaced the
HD and was running a system that was upgraded from Breezy.

So, no solutions here, but maybe this information will give someone some ideas.

It's probably something to do with Breezy->Dapper libs/interpreter(s)?  I really didn't test the game much before applying dozens of megs of updates.  The bug may have actually been there before the updates.  No help here either.

I hope the Jonathan Blandford will look into it.  It's the best game for Ubuntu by far. :D

---

### Post by tschaboo on 2006-07-18
I have the same problem. Did anyone file a bug-report at launchpad?

---

### Post by kwisatz on 2006-08-07
I have the same problem on my Dapper. When I try to change game on 
Aisleriot:
Backtrace:
In /usr/share/sol-games/sol.scm:
 480: 0* (if (defined? (quote card-guardian)) (letrec (# #) (catch # # ...)) ...)
 481: 1  (while (card-guardian))
In unknown file:
   ...
   ?: 2  [catch break #<procedure #f ()> #<procedure #f v>]
   ?: 3* [#<procedure #f ()>]
   ?: 4* [continue]
   ?: 5  (or (not (card-guardian)) (begin (begin) (continue)))
   ?: 6  (begin (begin) (continue))
   ?: 7* (begin)

<unnamed port>: In procedure begin in expression (begin):
<unnamed port>: missing or extra expression

UPDATE: with the last update Aisleriot now works...!

---

### Post by tschaboo on 2006-08-07
You're right, synaptic installed a gnome-games update a few days ago and since then everything work's fine.

---

### Post by eagle101 on 2006-08-10
Yes!  Works now.

---

### Post by Squee22 on 2007-03-06
crashes on load

> Memory status: size: 19898368 vsize: 0 resident: 19898368 share: 0 rss: 7671808 rss_rlim: 0
CPU usage: start_time: 1173169581 rtime: 0 utime: 7 stime: 0 cutime:6 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/aisleriot'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226085760 (LWP 18627)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb78c8a2e in __waitpid_nocancel () from /lib/libpthread.so.0
#0  0xb78c8a2e in __waitpid_nocancel () from /lib/libpthread.so.0
#1  0xb7f191b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#2  <signal handler called>
#3  0xb7913781 in scm_c_define_gsubr_with_generic ()
   from /usr/lib/libguile.so.12
#4  0x080d3e08 in ?? ()
#5  0xbfa0bc88 in ?? ()
#6  0xb792100a in scm_init_numbers () from /usr/lib/libguile.so.12

Thread 1 (Thread -1226085760 (LWP 18627)):
#0  0xb78c8a2e in __waitpid_nocancel () from /lib/libpthread.so.0
No symbol table info available.
#1  0xb7f191b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0xb7913781 in scm_c_define_gsubr_with_generic ()
   from /usr/lib/libguile.so.12
No symbol table info available.
#4  0x080d3e08 in ?? ()
No symbol table info available.
#5  0xbfa0bc88 in ?? ()
No symbol table info available.
#6  0xb792100a in scm_init_numbers () from /usr/lib/libguile.so.12
No symbol table info available.
#0  0xb78c8a2e in __waitpid_nocancel () from /lib/libpthread.so.0


---

