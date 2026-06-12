---
title: "What should I do next time I get video problem???"
date: 2010-08-14
forum: General Help
---

### Post by oxf on 2010-08-14
OK this not so much a "how do I fix.." question since I cant provide enough info at this stage, but rather what info should I provide next time I encounter it. 

This is what's going on: Occasionally (but not too often) I get either the screen freezing up, or going grey for  a few seconds while the CPU ramps up. I believe the problem might be related to video mem or drivers. Watching embedded videos such as youtube seems to sometimes cause it. 

Also yesterday I was on a site where you could click and compare before/after photos. After a few goes of this the browser (FF3.6) shut down (happened several times) followed by loss of mouse control and then finally I lost all my desktop icons, toolbar and panel leaving me only with the background theme.

So next time any of this happens what should I do to diagnose/collect info to post back here fro help? I presume something out of terminal assuming I can access it.

Many thanks..

---

### Post by kiridude on 2010-08-14
I had a similar problem a few months ago and it turned out to be firefox. This was before the new release had been added to the repos. I solved the issue by downloading and installing the latest version from the mozilla site. Also make sure you have the latest flash from adobe.

---

### Post by oxf on 2010-08-14
> **kiridude said:**
> I had a similar problem a few months ago and it turned out to be firefox. This was before the new release had been added to the repos. I solved the issue by downloading and installing the latest version from the mozilla site. Also make sure you have the latest flash from adobe.

OK thanks. Now I come to think about it, it's only been happening since I installed Lucid and have the FF version thats packaged with it by default. I dont remember it happening like this before. I'll check adobe but pretty sure am up to date on that

---

### Post by oxf on 2010-08-23
OK an update  and some observations.

This only seems to happen when Firefox if running.

Certain websites seems to set this problem off, however, it seems once it starts it tends keep happening even if I've navigated away from that site. Often the only remedy is to reboot

Sometimes (but again not always) I get the error msg " a script is causing FF to run slowly"

There also seems to be a some correlation with "plugin container" causing CPU usage to go way up.

I'm thinking Adobe Flash but am open to ideas.????

---

### Post by PRC09 on 2010-08-23
The plugin container problem in Firefox seems to be happening in both Ubuntu and Windows from what I have read.There is a partial work around posted below but instead of just flash crashing,Firefox itself crashes so not really much improvement.....


[http://support.mozilla.com/en-US/questions/713600?#threadId719044](http://support.mozilla.com/en-US/questions/713600?#threadId719044)

---

### Post by oxf on 2010-08-24
> **PRC09 said:**
> The plugin container problem in Firefox seems to be happening in both Ubuntu and Windows from what I have read.There is a partial work around posted below but instead of just flash crashing,Firefox itself crashes so not really much improvement.....


[http://support.mozilla.com/en-US/questions/713600?#threadId719044](http://support.mozilla.com/en-US/questions/713600?#threadId719044)

OK Thanks! Thats interesting. will take me a while to read through it all.

Yesterday it happened again several times, the last time real bad and could do absolutely nothing with the PC so crashed the system. After which I couldn't boot/mount file system including in recovery mode. Booted from the Live CD and ran fsck. This revealed a pile of inode errors/blocks all of which were fixed. Also error relating to one website and macromedia which it deleted. 

After all this it booted up fine and fast and I havn't had the problem since. So I'm watching it to see if/when it starts happening again!

---

