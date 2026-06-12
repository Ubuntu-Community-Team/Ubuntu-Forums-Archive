---
title: "Firefox won't start"
date: 2010-09-11
forum: General Help
---

### Post by beacon on 2010-09-11
I have used firefox in various versions for years, and this is the first time I have had problems. I was attempting to install several add-ons, and after that firefox would seem to be loading, but after an interval, stopped without anything appearing.

I have read through all the threads until I am bleary-eyed and have tried many suggestions. (Perhaps trying so many messed me up even more.)

I thought I could completely remove everything connected to Firefox and begin again. But even after complete removals, done according to some of the helpful posts, there were still items in usr/lib, including firefox, firefox-3.6.9, and firefox addons. I can't find a way of purging those. 

I then followed another suggestion and went to the Mozilla site and downloaded 3.6.9 once again. No joy. So I returned to the site and downloaded the beta version 4. It worked, and I got all the preferences established and began to install addons. No problem until I added x,scripts after which I restarted firefox and I was back to square one. Nothing happened.

I know there are lots of posts on this type of problem, but I can't find a solution. If anyone can suggest how to get back to a usable Firefox I would be grateful.

---

### Post by sikander3786 on 2010-09-11
Are you able to start firefox in safe mode

```

firefox -safe-mode

```

If it does, you should be able to uninstall the problematic add ons. Before typing the command, make sure no instance of firefox is running other wise it might not work.

---

### Post by WorMzy on 2010-09-11
You should have no need to uninstall Firefox. Just remove the .mozilla folder from your home folder, that's where all your settings relating to Fx are stored.

Since the folder is a hidden folder, you will probably need to press Ctrl+H in nautilus to show it.

---

### Post by beacon on 2010-09-11
Thank you sikander and wormzy. I have tried to use safe mode and get the message that Firefox is already running and that I must close it. However, I can no see any evidence that it is running. I haven't yet followed the suggestion of wormzy but will soon and post the outcome.

---

### Post by sikander3786 on 2010-09-12
Run this command before starting firefox in safe mode. It will kill all instances of firefox.

```

ps axjf | grep firefox

```

---

### Post by beacon on 2010-09-12
I'm still having problems. Thank you again Sikander. I might be missing something, but I failed. I typed the code you suggested. I then went to firefox in safe mode, and version 4 opened. When I went to usr/lib, it still contained firefox, firefox 3.6.9 and firefox addons. Should they still be there?

I haven't had the courage yet to try add ons.

---

### Post by sikander3786 on 2010-09-12
You said in your first post "No problem until I added x,scripts after which I restarted firefox and I was back to square one. Nothing happened." So start in safe mode, try to uninstall x,scripts and then start in normal mode to see if it worked.

---

### Post by beacon on 2010-09-12
Thanks once more. I have followed all the suggestions in this thread. I don't know what worked, but I suddenly find that Firefox 3.6.9 appears once again. ( I don't know what happened to FF4, which I installed yesterday.) Anyway, for the moment the problem seems to have been solved, even though there is a mystery about how.

I appreciate all the help.

---

