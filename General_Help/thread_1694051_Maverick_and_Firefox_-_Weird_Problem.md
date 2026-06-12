---
title: "Maverick and Firefox - Weird Problem"
date: 2011-02-23
forum: General Help
---

### Post by crh0831 on 2011-02-23
I've learned to never say "that's impossible" because of problems like this one.

Today, I installed Ubuntu 10.10 on a Dell Optiplex 330 for a non-profit organization.  Installation was uneventful and I thought everything was fine.  Upon having the user test-drive the machine she reported "I can't get into my Yahoo mail!" Hmm...  ok, let me have a look.

I'll be damned.  She's right.

Here's the relevant info:
Maverick clean install.  All updates applied.
Firefox 3.6.13
GnomeXP theme (to make the transition to linux easier :) )

Here's what happens:

[LIST]
[*]Firefox will load [http://yahoo.com](http://yahoo.com) just fine.  Upon clicking "sign in" the throbber just spins and spins.  Never loads the page.  I tried viewing the source of the page and it seems OK, but it never renders on-screen in the browser.
[*]Firefox will not load [http://www.facebook.com](http://www.facebook.com).  Same symptoms as above.  Firefox ***will*** however load [http://www.facebook.com/home.php](http://www.facebook.com/home.php) and allow me to login.
[*]Firefox loads these pages just fine:  [http://hotmail.com](http://hotmail.com),  [http://gmail.com](http://gmail.com),  [http://aol.com](http://aol.com)
[/LIST]

Here's what I've tried with no results:

[LIST]
[*]Firefox in safe mode
[*]removed icedtea6 and installed Sun's Java
[*]flushed cookies and history
[*]tried accessing sites in "privacy mode"
[/LIST]

I'm stumped.

Here's a few more tidbits:

[LIST]
[*]Google Chrome has the same problem with the same sites.
[*]Elinks, Midori and Opera load the problem pages just fine.
[*]Firefox 3.6.13 on Lucid Lynx works fine on the problem sites.
[/LIST]

My thoughts:

[LIST]
[*]javascript?
[*]Not a browser, but a Maverick-specific problem (seeing as everything's ok under Lucid)?
[/LIST]

Has anybody run into such a quandary?  I'm working on the machine until I get this licked.  Any help or advice is much appreciated.

---

### Post by blakep2 on 2011-02-23
Yahoo is a piece of junk anyway switch to gmail.
But if there is no other option...
Have you been able to sign in ever?
If so try clearing cache.

---

### Post by crh0831 on 2011-02-24
I haven't had a chance to prove this, but after some more forum searching I found another thread that describes my problem pretty well: [http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506)

Could it be the MTU setting on eth0?  I know that my problems must exist on more than just facebook and yahoo, but I have yet to find another website on which the browser just hangs.  The above mentioned thread sounds suspiciously like the problem I'm having.

In any event, unless someone has something to contribute, I'll update this thread once I try to MTU setting hypothesis.

---

### Post by dcymbal on 2011-02-25
I started having the same exact problems a day ago, only the big difference is I have existing 9.04 and 10.10 installations (9.04 is x86, 10.10 is amd64) that were working perfectly well.

Same problem using either Firefox or Chrome.  Tried clearing the caches, etc. to no success.

The 10.10 is my day-to-day system and gets updates automatically applied so I thought maybe a recent update did something.  However, the 9.04 box hadn't been booted for a month and it is having the same exact problem with no recent updates.  For me, yahoo and facebook are the 2 problematic websites, every other site I tried behaves normally.  These boxes are dual-boot windows and I don't have problems with yahoo/facebook with these boxes if I boot into Windows.  As a test, I installed VirtualBox on the 10.10 system and hosted Windows XP and 7 as a guest.  Running as guests, these now have the same problems with yahoo/facebook, so the problem certainly appears to be related to the underlying network and are not browser specific.  Could it be some additional factor like some change with my ISP causing issues (I have Verizon FiOS and of course they were NO help)?  I have thinking about bringing one of the boxes into work and seeing if the problem continues on a different network.

---

### Post by dcymbal on 2011-02-26
Well the thread crh0831 mentioned about MTU size solved the problem for me.  I noticed that the Windows boxes were using 1492 and Ubuntu 1500.  I dropped my Ubuntu boxes down to 1492 and yahoo and facebook immediately behaved as expected.

Very weird.  I am assuming that Ubuntu has always used 1500 since my older, not-recently-updated system always was set to this.  Does this effectively mean that something somewhere in the path from my systems to yahoo and facebook changed to start dropping 1500 byte packets, or perhaps something changed on yahoo and facebook where more than 1492 byte packets started being utilized?

---

### Post by crh0831 on 2011-03-16
Sorry for being so irresponsible.  I meant to post my results long ago.  My problem was indeed the MTU setting.  I fought and fought with the settings on each of the machines until I was struck by a blinding lash of the obvious - the problem was on the router, not the individual machines.  DUH!  Once I changed the MTU to 1492 on the router everything was cool...

Problem / thread solved.

Thanks everybody.

---

