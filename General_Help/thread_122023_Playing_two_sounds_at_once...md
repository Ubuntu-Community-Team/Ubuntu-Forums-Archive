---
title: "Playing two sounds at once.."
date: 2006-01-26
forum: General Help
---

### Post by three_sixteen on 2006-01-26
I can't seem to get my soundcard to output more than one 'channel' of sound at a time.

Like XMMS and mplayer, or XMMS while I play a game.

Do I have the wrong sound drivers installed or is something configured improperly.. or is this normal Linux behaviour?

---

### Post by Stereotypical Rage on 2006-01-26
I've used all Ubuntu versions (Warty, Hoary, Breezy and Dapper) You need to be using the Englighten Sound Daemon (ESD) for Gnome and aRts(KDE), which allow for multiple sounds. (XMMS and GAIM). I can hear XMMS and GAIM at the same time.

Is this what you wanted?

---

### Post by Sutekh on 2006-01-26
Try these HOWTOs/Threads

[Ubuntu Forums - howto multiple sounds at once]("http://www.ubuntuforums.org/showthread.php?t=101125")

[Ubuntu Forums - Have an audigy? Want multiple sounds without ESD? Do this!]("http://www.ubuntuforums.org/showthread.php?t=104388")

[Ubuntu Forums - Happy ALSA, OSS, ESD, with Duplex - Sound Settings]("http://ubuntuforums.org/showthread.php?t=44753") - (check last pages for relevance to Ubuntu 5.10)

---

### Post by three_sixteen on 2006-01-26
[QUOTE=Sutekh]Try these HOWTOs/Threads

[Ubuntu Forums - howto multiple sounds at once]("http://www.ubuntuforums.org/showthread.php?t=101125")

[Ubuntu Forums - Have an audigy? Want multiple sounds without ESD? Do this!]("http://www.ubuntuforums.org/showthread.php?t=104388")

[Ubuntu Forums - Happy ALSA, OSS, ESD, with Duplex - Sound Settings]("http://ubuntuforums.org/showthread.php?t=44753") - (check last pages for relevance to Ubuntu 5.10)[/QUOTE]

I tried these, but I still can't play music while playing games in wine.

I suppose I didn't specifically ask about that though.

---

### Post by TechSonic on 2006-01-27
I've made a post on that audigy one.  SB Live! 24bit doesn't work the same.

---

### Post by Sutekh on 2006-01-27
[QUOTE=TechSonic]I've made a post on that audigy one.  SB Live! 24bit doesn't work the same.[/QUOTE]

Haha, not what I wanted hear.  That's what I've got now, and was gonna look into it this weekend!

---

### Post by JayBachatero on 2006-01-29
[QUOTE=Stereotypical Rage]I've used all Ubuntu versions (Warty, Hoary, Breezy and Dapper) You need to be using the Englighten Sound Daemon (ESD) for Gnome and aRts(KDE), which allow for multiple sounds. (XMMS and GAIM). I can hear XMMS and GAIM at the same time.

Is this what you wanted?[/QUOTE]

I have tried all the tutorials around and I can't get this to work.  This is exactly what I want.  Sound in XMMS ans GAIM.  Thanks in advance.

---

### Post by JayBachatero on 2006-01-30
Ok I seem to have something working.  I'm able to listen to music usint Totem and hear sound from GAIM.  That's an improvement.  I still would like to get XMMS to work.  When I try to open a file I get 
> 
Please check that:
Your sound car is configured properly
You have correct output plugin selected
No other program is blocking the sound card.

---

### Post by Stereotypical Rage on 2006-01-30
GAIM and XMMS configured to use ESD?(eSound)

---

### Post by JayBachatero on 2006-01-30
I have no Idea.  How can I check this?  I'm a total noob when it come to Linux :-\

---

### Post by JayBachatero on 2006-02-18
Well I got this issue solved.  thanks for all the help.

---

