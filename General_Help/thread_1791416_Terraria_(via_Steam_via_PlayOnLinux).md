---
title: "Terraria (via Steam via PlayOnLinux)"
date: 2011-06-26
forum: General Help
---

### Post by Fyrius on 2011-06-26
Briefly: I'm using Steam via PlayOnLinux, and I bought a legal copy of Terraria this aftenoon, but can't get it to play, at all. 
I know there are walkthroughs for this. My problem seems to be atypical. 

I've been [here](http://www.terrariaonline.com/threads/does-terraria-work-with-ubuntu.11853/#post-182163) and I've been [here](http://www.steamgamesonlinux.com/terraria/) and I've been [here](http://tom-geiger.de/?p=151), and I've done everything they said including the non-overlapping things, and done them all successfully as far as I can tell. 
[SIZE="1"](I upgraded to Wine 1.3.21, installed mono 2.10 and 2.8, installed .NET Framework 4, installed XNA 4, copied the files I was told to copy from those folders to the Terraria folder, installed DirectX 9, all that stuff.)[/SIZE] 
Still, it's not working. 

Meanwhile, if I circumvent Steam and go to the folder where my Terraria files have been downloaded to and run Terraria.exe through Wine, I get a parsing error message - exactly what the walkthroughs I've linked to predicted, so that's good - but when I continue as I'm told I should, it tells me to launch it via Steam instead. So I'm guessing the game itself has been fixed by now, I just can't access it. 

If I do launch it via Steam, I get a window saying "Preparing to launch Terraria..." for a split second, and then it goes away and nothing else happens. 

All my other Steam games (Thief III, Half-Life 2, episodes 1 and 2, Team Fortress 2, Portal) work properly, or at least launch properly. It's limited to this game. 

I've repeatedly exited and restarted Steam, no dice. I've rebooted altogether, no dice. I've deleted the game and reinstalled it, no dice. 

I'm using Ubuntu 10.04 LTS. 
My Wine is set to pretend it's Windows XP. 

Tl;dr: Having followed other Linux gurus' advice, Steam still refuses to start up this game.
[SIZE="1"](Help us, Ubuntu Forums. You're my only hope.)[/SIZE]

---

### Post by Fyrius on 2011-06-27
Um. Guys? Any ideas at all? 

Do excuse me for self-bumping, but I was sort of serious about that last sentence. If not even you guys can figure this out, I don't know what else I could do short of giving up. 
And that would make me very sad.

---

### Post by NinjaWizard on 2011-06-27
I'm playing Terraria on Ubuntu 10.04 and it works fine, except for the occasional crash during saving.

All I did was to upgrade wine and follow the instructions here:
[http://tom-geiger.de/?p=163](http://tom-geiger.de/?p=163)
I actually skipped steps 5-8. (This article is newer than the article you linked to, just in case you haven't seen it).

I don't really have any other suggestions, since this worked for me.

Good luck!

---

### Post by Fyrius on 2011-07-01
Thanks for the input. :)
I'll try it.

---

### Post by Fyrius on 2011-07-01
> **NinjaWizard said:**
> All I did was to upgrade wine and follow the instructions here:
[http://tom-geiger.de/?p=163](http://tom-geiger.de/?p=163)
I actually skipped steps 5-8. (This article is newer than the article you linked to, just in case you haven't seen it).

I did everything it says there that I hadn't already done when following the other walkthroughs - that is to say, I installed *xact* and *xinput*. (The rest overlapped.)

Still no luck. 

So unless somehow the order in which I install all these things is really important (could that be it?), I still have no idea what I'm doing wrong.

---

### Post by Fyrius on 2011-07-01
I finally figured it out. 
I had to reinstall Steam on Wine for it, and then follow the instructions. But it works now. 

So, long story short, for those who come after: the solution is not to use PlayOnLinux, I suppose.

---

