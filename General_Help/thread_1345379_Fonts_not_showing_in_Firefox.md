---
title: "Fonts not showing in Firefox"
date: 2009-12-04
forum: General Help
---

### Post by ricardisimo on 2009-12-04
I don't know if this has anything to do with my problem, but I moved all of my fonts out of /home/sectre/.fonts and into /usr/share/fonts/Custom. Now I have certain webpages (like this one right here, as you can see in the attached screenshot) that are not showing text at all.

Obviously, I'll gladly move all of the fonts back if there's no other way around it, but it seems odd that I can't make the fonts system-wide. By the way, I would have done a search for this problem, but... you see my problem, hopefully. Thanks in advance for any help anyone can give.

---

### Post by ricardisimo on 2009-12-04
So, two things:
[LIST=1]
[*]I moved all of the fonts (thousands of them) back to .fonts in my home folder;
[*]Boot was freezing, so I'm running 2.6.31-14 instead of ...15.
[/LIST]
One of the other of these has resolved the problem, and now text on web pages is rendering just fine. Any clue as to which is the most likely cause of the fix? Thanks.

---

### Post by youngheart80 on 2009-12-14
well, I stumbled across your question after a similar incident.  I had recently moved a lot of fonts over into the /usr/share/fonts folder and suddenly, I didn't have pages rendering.  However, I also noticed that certain system fonts were not showing either.  That's what prompted me to look in there.  There were a couple of .fon extensions and some other that I knew ubuntu wouldn't use so I deleted them and magically, everything was restored.  Then I did the search that found your question.

Perhaps a bug of some kind?  If you have fonts that aren't ttf perhaps it throws ubuntu for a bit of a loop?

---

