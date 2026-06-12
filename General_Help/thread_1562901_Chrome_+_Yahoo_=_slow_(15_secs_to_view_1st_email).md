---
title: "Chrome + Yahoo = slow (15 secs to view 1st email)"
date: 2010-08-28
forum: General Help
---

### Post by aeronutt on 2010-08-28
Using Chrome, when I first view yahoo mail in a tab, and select an email, it takes 10-15 secs for the message to show up in the view pain. (It takes this long anytime I go check a yahoo email message for the first time in a tab, so it's not only after first login.) Selecting other emails after that in that tab, all is ok. Doing the same thing in Firefox shows no problems (message loads in <  1 sec). I haven't noticed anything else exceptionally slow using Chrome. Also, switching to Yahoo classic email fixes the problem.

Some additional info:

Chrome version: 6.0.472.36 beta
Ubuntu 9.10

about : plugins in chrome shows:
Shockwave Flash 10.1 r82
Java(TM) Plug-in 1.6.0_20
(plus some other plugins)

Any ideas?

---

### Post by SedukiDude on 2010-08-28
Hey Aeronutt, I didn't use to have a problem with chromium opening my Yahoo Mail until recently. It is when I check my first incoming message and it takes about 10 seconds for it to appear. All other new incoming mail opens instantly. It was after I reset my router I started getting the message, **Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found**. I got this message for every site I tried to open. I eventually deleted Chromium and reinstalled it and it worked. Since then I noticed the slowness in Yahoo Mail. My other mail accounts work fine and I have found no other issues as of yet. After I got Chromium working I decided to setup Epiphany Web Browser as a backup because I may uninstall Chromium again and reinstall it. Hey, I think I will check Epiphany and see if Yahoo is slow through that web browser. BRB.

Wow, what a difference in speed using Epiphany...that opened my Yahoo Mail fast. I recommend you set up Epiphany or another browser while you uninstall/reinstall Chromium. I prefer Chromium as my primary browser so I am not going to give up on it. It worked great before.

---

### Post by aeronutt on 2010-08-28
I hate to say it, but I'm glad someone else is having the exact same problem :)

I'll probably use Firefox, and uninstall/reinstall chrome and see what happens. Good idea, thanks!

---

### Post by coolman98 on 2010-08-28
wow that is very weird just use firefox

---

### Post by aeronutt on 2010-08-28
Overall, I like chrome, but it seems to just not be quite 100% stable yet. It's faster than Firefox on most pages.

---

### Post by SedukiDude on 2010-08-28
Let me know how it works out!

---

### Post by aeronutt on 2010-09-12
I finally got around to uninstalling chrome, cleaning up a few things, and reinstalling the stable version.  It fixed the 'slow to read first yahoo email' problem!

Now, here's my concern.

Upon first launching the newly loaded chrome, I got an odd pop-up. It said an extension was asking for access, and that if i didn't explicitly ask to run this extension, I should hit the 'do nothing' button. So of course I did.  The extension it was asking to give permission to was something like:

cjaluflkdjfioulkjdlkjfuf/background.html

or something like that. Bascially, a long string of random alpha characters, then the word background...etc. (Is there a log file I can view to get the actual details of this?)

**Could this have been something 'bad' running in the background of my previous chrome load?**

---

### Post by SedukiDude on 2010-09-14
No it is nothing like that. Background.html is a code for setting the background picture or texture of a web page. It is harmless. Glad to hear the slowness of Yahoo cleared up for you. Mine is still slow on the first open email but I really have had not much time to work on it. Hey, how come you haven't up graded your version of Ubuntu?

---

### Post by aeronutt on 2010-09-14
Thanks, that makes sense on the background.html.  

Everything is working fine for me with 9.10, so I'm taking my time to upgrade. I have 10.04 loaded on another partition and all seems to work on my computer, so I'll get around to it soon.

---

### Post by aeronutt on 2010-09-15
Well, the slowness problem is back. First view on an email, and it takes 14 seconds or so to come up. Close the tab, reopen tab and click yahoo mail, click on email, and slow...14 sec to view email.

I've made no changes to chrome, loaded no new s/w, have no idea why the problem is back.

About ready to uninstall chrome and go back to firefox as my primary browser.

---

### Post by mskullcap on 2010-09-29
Same problem for me... on Ubuntu AND WinXP.  So I **excluded** AdBlock from blocking ads for yahoo.com and now email works fast as it should now.  Do you happen to have AdBlock installed?

---

### Post by mastablasta on 2010-09-29
14 second for webmail (and only first one). i wonder what you guys would say if you ever used 14.4 Kb dial up conneciton.

---

### Post by aeronutt on 2010-09-29
> **mskullcap said:**
> Same problem for me... on Ubuntu AND WinXP.  So I **excluded** AdBlock from blocking ads for yahoo.com and now email works fast as it should now.  Do you happen to have AdBlock installed?

BINGO!!!!  Yep, made that change, and first email loads within a second or less most times now. Awesome. **Thanks**!!!!!!!!!!

I'll wait a few days and see if this holds, and will then mark solved.

---

### Post by aeronutt on 2010-09-29
> **mastablasta said:**
> 14 second for webmail (and only first one). i wonder what you guys would say if you ever used 14.4 Kb dial up conneciton.

I pay $$$/month so I don't have to use dial-up. :)

---

