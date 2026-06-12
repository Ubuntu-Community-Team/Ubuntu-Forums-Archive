---
title: "Ubuntu Tweak causing many problems"
date: 2012-05-25
forum: General Help
---

### Post by schilkyl on 2012-05-25
Oh happy day. I am yet again in conflict with my own arrogance and quick fleeting fingers. Simply put here is my problem:

I installed Ubuntu Tweak to remove the boot sound (12.04) because ive used tweak before and it seemed to be the easiest method at hand at the time. I also happened to run the Janitor feature while using tweak and used it to clear EVERYTHING. I chose all the options and now I know i was at fault. 

Upon reboot, Ubuntu had a hard time of actually logging in. It hung after pressing enter (after entering my password) and I had to restart multiple times before it would actually log me in. When I finally got logged in I was greeted with almost nothing. I chose to install gnome-panel because I still love it so. But I had a bottom bar and no top bar. All my desktop icons still were present. I could run shorcuts and call up command prompt to load programs that I might use. Unity though, is missing. I have attempted to run unity --reset but nothing was actually accomplished. 

All in all, everything still seems to work fine but I dont really have an interface for my computer to use it. All files that I need are still intact. 

My question: Is there a way I can re-install 12.04 over the top of the current installation basically to replace the core files that I need, and then I can just run update from there to catch up to where I need to be? 
Or: Is there a better method to restore my computer to its former glory before the unholy point and click of Ubuntu Tweak.

Let me know anything else ya need to know. 
Thanks

---

### Post by Haneef Mubarak on 2012-05-25
Have you installed anything else (that didn't come with Ubuntu) after you installed or updated your system?

---

### Post by wilee-nilee on 2012-05-25
> **schilkyl said:**
> Oh happy day. I am yet again in conflict with my own arrogance and quick fleeting fingers. Simply put here is my problem:

I installed Ubuntu Tweak to remove the boot sound (12.04) because ive used tweak before and it seemed to be the easiest method at hand at the time. I also happened to run the Janitor feature while using tweak and used it to clear EVERYTHING. I chose all the options and now I know i was at fault. 

Upon reboot, Ubuntu had a hard time of actually logging in. It hung after pressing enter (after entering my password) and I had to restart multiple times before it would actually log me in. When I finally got logged in I was greeted with almost nothing. I chose to install gnome-panel because I still love it so. But I had a bottom bar and no top bar. All my desktop icons still were present. I could run shorcuts and call up command prompt to load programs that I might use. Unity though, is missing. I have attempted to run unity --reset but nothing was actually accomplished. 

All in all, everything still seems to work fine but I dont really have an interface for my computer to use it. All files that I need are still intact. 

My question: Is there a way I can re-install 12.04 over the top of the current installation basically to replace the core files that I need, and then I can just run update from there to catch up to where I need to be? 
Or: Is there a better method to restore my computer to its former glory before the unholy point and click of Ubuntu Tweak.

Let me know anything else ya need to know. 
Thanks

Not a very solid cause and effect with ubuntu-tweak, I doubt that caused the problems. The janitor there unless you added additional stuff would not cause this.

---

### Post by schilkyl on 2012-05-25
> **Haneef Mubarak said:**
> Have you installed anything else (that didn't come with Ubuntu) after you installed or updated your system?

Ive installed multiple programs that I use every day. Ubuntu is my daily driver. Ive been using it for a long time now and only recently run into this problem. (Just after running tweak and restarting)

> **wilee-nilee said:**
> Not a very solid cause and effect with ubuntu-tweak, I doubt that caused the problems. The janitor there unless you added additional stuff would not cause this.

I literally logged on and decided I wanted to finally get rid of the boot sound. I remembered tweak from previous use and quick installed it. I changed the setting and then ran janitor set to clear everything it possibly could. I reboot after that and wham bam thank you mam, here I am now..

---

### Post by W29 on 2012-10-03
I had the exact same problem. I installed Ubuntu Tweak and a lot of things got ****** up. The only thing I did was changing the login background and I used the janitor.
I wasn't able to log in anymore (it logged out immediately). I even had to remove my account. My home dir was encrypted, so I couldn't recover anything (lucky for me, I had a backup of 2 weeks old). Now I'm working with a new account. But still some problems persist. I cannot update anymore or open the software center.
Every time I've opened Ubuntu Tweak, it ***** up my /var/lib/apt/lists and I have to remove the contents of this folder.

My advise is: DO NOT INSTALL Ubuntu Tweak.

---

