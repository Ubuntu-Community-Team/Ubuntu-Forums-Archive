---
title: "Replay terminal commands?"
date: 2009-11-13
forum: General Help
---

### Post by MaindotC on 2009-11-13
I was reading up on Kevin Mitnick on the site takedown.com and I see they have (or had) sessions of Mitnick's commands saved that can be replayed.  I found a [youtube video](http://www.youtube.com/watch?v=69rei214eDE) that shows the commands being entered.  How do you reply your terminal/bash entries like that?

---

### Post by fluffman86 on 2009-11-13
It essentially looked like a video capture program to me.  You can get one in the repositories.

---

### Post by MaindotC on 2009-11-13
Yes I'm sure Mitnick was using Hypercam at the time he hacked into DEC...

---

### Post by MaindotC on 2009-11-13
bump

---

### Post by falconindy on 2009-11-13
If you read the description of the video, the claim of how the log was produced is right there:
> In the course of tracking the attacker(kevin), a great deal of network traffic was captured by a specially modified version of tcpdump (here's information on the legality of the acquisition of this evidence), and then a program written by Tsutomu was used to produce playable logs.

---

### Post by MaindotC on 2009-11-13
Yes I read that, but I was hoping there would be some application available that did it automatically.  I can understand at the time Mitnick was being monitored, they probably did need "a specially modified version of tcpdump", but that 10+ years ago. No one knows of anything like that that has already been developed?

---

### Post by fluffman86 on 2009-11-13
I guess I'm just failing to see what exactly you need.

If you want someone to see a recording of everything you did...like a video...then video capture is probably the way to go.

If you want someone to be able to reproduce your commands, then take a look at ~/.bash_history

If you want someone to see everything you did as text, then in gnome-terminal you can go to edit, select all, then ctrl+shift+c to copy and paste it where ever you want.

edit: and if you want someone to view your terminal as you are using it, like VNC or Remote Desktop but for terminal only, then check out [https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/Byobu](https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/Byobu)

---

### Post by MaindotC on 2009-11-13
I don't NEED to do anything! I just wondered if I could do it now without using a "specially modified version of tcpdump". I appreciate your remarks and I will take them into consideration but I just wondered how it would be done - say for example if I was a web developer of the site Takedown.com and someone asked me "hey, is there any way you can show his terminal commands in real-time?"  I'm not a dev and I'll prolly never be asked that question, but I was just curious how you would do it.

---

