---
title: "Firefox Process Takes Forever to end"
date: 2010-01-14
forum: General Help
---

### Post by acetylyne on 2010-01-14
Hello Everyone, I'm having a problem with my Firefox.

I'm running 9.1 and Firefox 3.5.7 with a few addons (better privacy, ghostery, cookieculler, adblock, personas)  on a HP 8710p laptop with 4gb of ram.

I use it to browse the internet at work, and I have it up for about 8-9 hours every day, during the course of the day I will open and close tons of tabs.  At the end of the day when I'm getting ready to leave, I close out of firefox, and it takes one of my duo core processors all the way to 100% and sit at the top of my processes in my Conky for 5-10 minutes before it finally closes.  I've been googling for a couple days and have yet to come up with anything, any help would be greatly appreciated.

thanks!

---

### Post by chrismb on 2010-01-15
I've just started getting the same problem with Firefox 3.5.7 and Ubuntu 9.10. The only add-ons we have in common are Ghostery and Adblock, so you could try disabling either of them.

I just kill the process manually in the terminal:

ps -u YOUR_USERNAME

followed by

kill FIREFOX_PROCESS_ID

---

### Post by Rodney9 on 2010-01-15
Ghostery seems to be the problem , see here [http://ubuntuforums.org/showthread.php?t=1375930&page=3](http://ubuntuforums.org/showthread.php?t=1375930&page=3) 
I removed it and that fixed my problem which was the same as acetylyne's

Rodney

---

### Post by acetylyne on 2010-01-16
Thanks for the Tip Rodney, I'll try that out and let you know.  Interestingly enough they mention it's a problem in XP as well, which I can't verify since I rarely boot into my XP partition, but it's not a problem for me in Windows 7.

---

