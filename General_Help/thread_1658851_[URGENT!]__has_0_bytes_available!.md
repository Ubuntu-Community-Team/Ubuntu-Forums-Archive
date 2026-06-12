---
title: "[URGENT!] / has 0 bytes available!"
date: 2011-01-03
forum: General Help
---

### Post by RobinJ1995 on 2011-01-03
I started the installation of a bunch of software and let it run in background while playing a game. When I stopped playing i tried to start my webbrowser (Google Chrome), this didn't work out so well...
I tried Firefox instead, wich (luckily) started. As I tried to run more programs, I found out more of them unexpectedly quit, or even didn't run at all. So I tried a lucky guess with running ```
$ sudo aptitude why-not google-chrome
```. This told me that it could not lock some or another directory, wich I know meant that aptitude was already doing something. Then I remembered that I was still installing a unch of software in background. I opened up the software center/manager and saw it was stuck in a state not much further from where i left it, so I cancelled all tasks. When I looked over at the filesystem tab in the system monitor (I still had it open), and saw that I didn't have any space left! I opened nautilus and saw that I indeed had **0 bytes** space left on my root partition! I tried to remove some stuuf, but it was still stuck a 0 bytes, no matter what I removed, it kept saying that I had 0 bytes space left. I also tried to remove a few packages, but the same thing happens (wich is to say, nothing at all). I still have an instance of nautilus opened, wich is only good, because I was stupid enough to try and remove everything in the /tmp folder, and now it won't start aymore either.
_**[SIZE=5]Please help, because I know out of experience that an Ubuntu installation with a full root partition refuses to boot!![/SIZE]**_

---

