---
title: "*some* MP3s shared on Ubunut PC have duration of 0:00 on Windows XP PC"
date: 2009-07-11
forum: General Help
---

### Post by HiImTye on 2009-07-11
ok. here's the scenario
    I am filesharing my mp3s so that I can listen to them on the Windows XP computer that is on my network. all of the mp3s work on the Ubuntu PC but half or more of the mp3s display a duration of 0:00 and an empty tag on the Windows XP computer. I have done two things which I found on another thread, days ago, of which I have lost the link. the first is to re-set the system time format on the Windows XP computer (in regional settings). the second is I manually built all the 'tags' using EasyTag (the thread I found suggested another windows program but all the files are on the Ubuntu PC).

any ideas how to fix it?

---

### Post by lisati on 2009-07-11
Don't panic! You're not alone in noticing an "incorrect" duration for the MP3 files. 

A search of the forums reveals a number of threads that touch on this topic: [http://ubuntuforums.org/tags.php?tag=length](http://ubuntuforums.org/tags.php?tag=length)

Seomthing else to be aware of (which might not be relevant to your siuation) is that some MP3 files that can be downloaded using P2P software come with nasty surprises in the form of [malware]("http://en.wikipedia.org/wiki/Malware").

---

### Post by HiImTye on 2009-07-12
some of the files showing incorrect duration are ones that were ripped locally and I always approach every file with a 'hacker mindset' - old habits die hard lol

I wouldnt have posted if I didnt take as many steps as I could think of (including searching) before posting.

I know, you're used to lay-mans trying to finger stuff out but I'm not a layman at all. a bit new to Linux (about a year or so) but not new to computing at an advanced level at all.

---

### Post by lisati on 2009-07-13
> **HiImTye said:**
> some of the files showing incorrect duration are ones that were ripped locally and I always approach every file with a 'hacker mindset' - old habits die hard lol

I wouldnt have posted if I didnt take as many steps as I could think of (including searching) before posting.

I know, you're used to lay-mans trying to finger stuff out but I'm not a layman at all. a bit new to Linux (about a year or so) but not new to computing at an advanced level at all.

So the other threads on the forum didn't help?:guitar:

---

### Post by HiImTye on 2009-07-13
no, the ones linked ^ up there were about incorrect duration *within* Ubuntu, not correct length in Ubuntu and incorrect length in Windoze XP. The one thread I found offsite I tried both 'fixes' (mentioned in my first post) but neither corrected the issue.

---

### Post by HiImTye on 2009-08-23
so I did fix my problem (I did a couple weeks ago and forgot to post the solution). It turns out that I needed to enable both 'Read' and 'Execute' permissions for all of the files. Only some had 'execute' permissions and so only they were able to show the proper duration.

to do so, I used nautilus.

[LIST=1]
[*]right click on the folder containing all of my MP3s (neatly organized in sub-folders)
[*]select the 'permissions' tab
[*]ensure that both 'read' and 'execute' are enabled for 'group' and 'everyone else' for both folders and files
[*]click 'close'
[*]viola!
[/LIST]
hope this helps someone else!

---

