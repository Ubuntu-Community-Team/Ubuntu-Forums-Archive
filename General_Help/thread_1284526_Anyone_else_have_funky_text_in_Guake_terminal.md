---
title: "Anyone else have funky text in Guake terminal?"
date: 2009-10-06
forum: General Help
---

### Post by lukeiamyourfather on 2009-10-06
My system is running Ubuntu 9.04 and its up to date. I'd love to use the Guake terminal emulator but it has funky kerning of the text in the terminal. It seems to happen regardless of what application is running in the terminal and regardless of the font settings. Does anyone have the same issue, or could you install Guake and see? See attached image for an example of the funky text. Cheers!

---

### Post by fcuk112 on 2009-10-06
i use guake and i don't get this problem.  no idea what the issue is though...

---

### Post by sisco311 on 2009-10-06
try to change the fonts in *guake-prefs* -> Appearance tab.

---

### Post by lukeiamyourfather on 2009-10-06
> **sisco311 said:**
> try to change the fonts in *guake-prefs* -> Appearance tab.

Thanks for the idea! Though changing font doesn't solve the problem. Its like the kerning per character is incorrect and happens on all fonts and all applications in the terminal, and even when there's no application running in the terminal. Other terminal emulators work just fine so it doesn't seem to be a font problem, but rather a Guake problem. 

Its good to know at least one other person is running Guake successfully but not sure how to troubleshoot it on my system. Cheers!

---

### Post by lukeiamyourfather on 2009-10-06
I forgot to mention it in the first post but its 64-bit Ubuntu 9.04 if that might make a difference. Cheers!

---

### Post by lovinglinux on 2009-10-06
I had this problem with Guake too, so I started to use [tilda](apt:tilda), which is much better imo.

---

### Post by fcuk112 on 2009-10-06
you can also try yakuake, though to be honest i still prefer guake though, hope you can resolve the issue.

---

### Post by lukeiamyourfather on 2009-10-06
> **lovinglinux said:**
> I had this problem with Guake too, so I started to use [tilda](apt:tilda), which is much better imo.

Yeah, that's probably what I'll do. I started using both recently but was not really satisfied with Tilda because it doesn't have shortcuts for things like a new tab and won't run in 100% width for some reason (1024 pixel width screen on a laptop so I like to use all I can get). I also like the looks of Guake better but that's a subjective thing.

I'll leave the status of the thread as unresolved for a few days to see if anybody has a solution (because its over my head!), and if nothing comes up I'll change it resolved by using Tilda. Cheers!

---

### Post by dmflad on 2009-10-09
Had funky text until I changed my font in the Guake prefs. I switched it to use Bitstream Vera Mono, 10pt(my pref'd font everywhere). Can't remember if I had to log out then in for change or if it just worked after change.

Been running Guake for few days and really like it but today it is acting badly when I have more than one tab open. It acts like only the most recent tab is the only tab and all tabs show same info.  Example: I open tab1 and ssh to server1 and run ls -l. Results appear, all okay. Now I open tab2, ssh to a server2 and run du -cks|sort -rn|head -11 and results show up okay in tab2. Now I click back on tab1 and I see same info I just got on tab2 until I close tab2.

Only change since yesterday is Ubuntu sent out some updates (don't remember what for) so I'm thinking Ubuntu update changed something Guake presumed.

---

### Post by sillyfofilly on 2009-10-22
I had the funky text as well, but I solved it by changing the font from the default Sans to Monospace. (See attached screenshots)

[https://bugs.launchpad.net/debian/+source/guake/+bug/277252]("https://bugs.launchpad.net/debian/+source/guake/+bug/277252") says that Guake 0.4.0 (which will be in Karmic) has Monospace as the default

---

