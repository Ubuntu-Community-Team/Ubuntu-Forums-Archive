---
title: "newbie question"
date: 2005-03-03
forum: General Help
---

### Post by easy123 on 2005-03-03
um, can someone help me? I am new to this linux stuff, i have no clue how it works. Anyways, i have some win32 applications but they cannot install. Do i need to install some extra components? I have the 4.10 version of the Ubuntu.

---

### Post by BillyD on 2005-03-03
[QUOTE=easy123]um, can someone help me? I am new to this linux stuff, i have no clue how it works. Anyways, i have some win32 applications but they cannot install. Do i need to install some extra components? I have the 4.10 version of the Ubuntu.[/QUOTE]
 I am a newbie too and I believe the answer to this question is that you cannot run win32 applications in Linux.  However, I could be wrong.

---

### Post by lordofkhemenu on 2005-03-03
[QUOTE=easy123]um, can someone help me? I am new to this linux stuff, i have no clue how it works. Anyways, i have some win32 applications but they cannot install. Do i need to install some extra components? I have the 4.10 version of the Ubuntu.[/QUOTE]
Start [Linux for newbies]("http://www.linuxhelp.net/newbies/") and [this excellent series of articles]("http://www.northernjourney.com/opensource/newbies/") for the Linux newcomer. After that, hit [the Ubuntu Guide]("http://www.ubuntuguide.org").
You can run some Windows programs on Linux, but not all. Why? Not the same Operating System. You need an an emulator, like Wine, or Crossover Office...but then **W**ine **I**s **N**ot an **E**mulator.
[google.com/linux](www.google.com/linux) is your friend.

---

### Post by easy123 on 2005-03-03
thx, just one quick question before i hit the pages; can i install things like screensavers and other stuff?

---

### Post by jsgotangco on 2005-03-03
If you mean your windows screensavers, no. It has its own screensaver engine but the stock screensavers are really good in my opinion.

Codeweavers' CrossOver Office can run SOME major applications like MS Office, Photoshop and Dreamweaver which they officially support.

[www.codeweavers.com](www.codeweavers.com)

For games, you might want to check out Cedega by Transgaming Technologies. Cedega supports major Windows games in Linux.

[www.transgaming.com](www.transgaming.com)

These add-on applications actually originated from the WINE project:

[www.winehq.com](www.winehq.com)

But to really appreciate Linux in general, try looking for applications and compare it with  its Windows counterparts.

---

### Post by Jad on 2005-03-03
The most important question
Why you need to install some win32 applications under linux ? 
check this table of equivalents windows software in linux
[http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml](http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml)

---

### Post by easy123 on 2005-03-04
where can i get Wine, and how do i install it? I downloaded the source files, but dont have a clue about what the readme files talking about... #-o

---

### Post by bored2k on 2005-03-04
[QUOTE=easy123]where can i get Wine, and how do i install it? I downloaded the source files, but dont have a clue about what the readme files talking about... #-o[/QUOTE]

Oh boy... lol

U can not expect to install all ur redmond apps so this would just become a skinned xp _ _ _ . we all hated not having our apps with us , but a little search will help u.

open synaptic [not saying where it is cuz ur a clicker from xp u should know :P] clic search , names and descriptions, and search "music organizer", "emulator"  "torrent" or whatever .


in linuxquestions.org there is a good what u would lik in nix from xp thread with all the equivalency .

watch out installing redmond apps, u might see this in ubuntu:
[IMG]http://www.erben.com/Images/DeleteWindows.gif[/IMG]

---

### Post by easy123 on 2005-03-04
:confused:

---

### Post by DirtDawg on 2005-03-04
Poor Easy is confused. Don't worry Easy, we've all been there. My guess is you probably have no idea what any of us are talking about (What the hell does WINE mean!?). Well we all have various amounts of experience so we take a lot of this terminology for granted (of course, I'm not speaking for everyone here). For example, I've been using Linux for about 2 years and I understand about 40 to 60% of what people are talking about in these forums(A lot better than two years ago when I understood about 2-5% of what was going on).

Here's a hint: Read read read read read. Linux users are notoriously friendly when it comes to helping newbies, but you'll need to do some research on your own. Check out the links from previous responses, browse this forum and linuxquestions.org, Google newbie Linux guides, and remember to _play_ and _experiment_ with your new Linux. 

This may sound like a lot of work, but it's really not. Give yourself some time and have patience.  It really pays off, ask anyone here. 

Peace

---

### Post by DirtDawg on 2005-03-04
[QUOTE=Jad]The most important question
Why you need to install some win32 applications under linux ? 
check this table of equivalents windows software in linux
[http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml](http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml)[/QUOTE]

By the way, sweet link. Thanks Jad.

---

### Post by HungSquirrel on 2005-03-04
Edit: before following these instructions, [enable universe](http://ubuntuforums.org/showthread.php?t=179&highlight=universe).

To install wine, open up Synaptic.  It's in the Computer menu.  It will ask you for your password.  Then, click Search.  Enter 'wine'.  When the results display, mark the following for installation: wine, winesetuptk, and wine-utils.  Click Apply.  They are now installed.

To set up wine, press Alt+F2 to bring up the Run Application dialog, type in *winesetup*.

To run a program under wine, open up a terminal and enter *wine programname.exe* .  I recommend you learn how to use the Linux command line if you are not already familiar with it.




HOWEVER, instead of doing all that, as someone else recommended, try the Linux equivalents of Windows applications first, if they exist.  Most are just as good as the non-free Windows programs they replace.  Some are much better!

---

### Post by poofyhairguy on 2005-03-04
[QUOTE=jsgotangco]
Codeweavers' CrossOver Office can run SOME major applications like MS Office, Photoshop and Dreamweaver which they officially support.

[www.codeweavers.com](www.codeweavers.com)[/QUOTE]

I vote for Crossover. It works like a Windows user would expect.

---

### Post by easy123 on 2005-03-04
[QUOTE=HungSquirrel]Edit: before following these instructions, [enable universe](http://ubuntuforums.org/showthread.php?t=179&highlight=universe).

To install wine, open up Synaptic.  It's in the Computer menu.  It will ask you for your password.  Then, click Search.  Enter 'wine'.  When the results display, mark the following for installation: wine, winesetuptk, and wine-utils.  Click Apply.  They are now installed.

To set up wine, press Alt+F2 to bring up the Run Application dialog, type in *winesetup*.

To run a program under wine, open up a terminal and enter *wine programname.exe* .  I recommend you learn how to use the Linux command line if you are not already familiar with it.




HOWEVER, instead of doing all that, as someone else recommended, try the Linux equivalents of Windows applications first, if they exist.  Most are just as good as the non-free Windows programs they replace.  Some are much better![/QUOTE]

that requires internet access, right?

---

### Post by HungSquirrel on 2005-03-04
Sure does.  :)

---

### Post by easy123 on 2005-03-04
but the computer that i installed linux doesnt have internet access, is there another place to get it?

---

### Post by DirtDawg on 2005-03-04
[QUOTE=easy123]but the computer that i installed linux doesnt have internet access, is there another place to get it?[/QUOTE]

I'm not sure it's in here, but I'm not hooked to the net either. This site will be your best friend:

[http://higgs.djpig.de/ubuntu/www/warty/](http://higgs.djpig.de/ubuntu/www/warty/)

---

