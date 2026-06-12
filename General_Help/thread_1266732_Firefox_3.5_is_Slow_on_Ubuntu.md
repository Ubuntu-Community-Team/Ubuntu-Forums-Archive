---
title: "Firefox 3.5 is Slow on Ubuntu"
date: 2009-09-15
forum: General Help
---

### Post by Yanatsu on 2009-09-15
It runs better on Windows, which I really hate to say. When I have multiple tabs open and loading, it just gets slow and laggy. I'm using the binaries provided by Mozilla on their website, if anyone was wondering, since the FF3.5 in the repositories is from the beta (last I checked).
My computer's got 1GB of RAM and a dual core 1.73GHz processor, so it shouldn't be doing this. I can have 20+ tabs open in Windows, no issue. Yet with Linux...

---

### Post by hibliss on 2009-09-15
The official final version is in the repos, and works fine for me. I am on 3.5.2.

If you think it runs slow, try Epiphany, it is much faster.

---

### Post by Yanatsu on 2009-09-15
I'm on 3.5.3, but sure, I'll test the one in the repos. What's the command?

---

### Post by sgosnell on 2009-09-15
sudo apt-get install firefox

The one in the repository is 3.5.3, the same as on the Mozilla website.  Works great for me.

---

### Post by oboedad55 on 2009-09-15
> **sgosnell said:**
> sudo apt-get install firefox

The one in the repository is 3.5.3, the same as on the Mozilla website.  Works great for me.

I just installed it from the repo and I've got 3.5.2. What gives?

---

### Post by sgosnell on 2009-09-15
I don't know.  I installed from the repository, just checked About, and it says 3.5.3.  After the install and restart of Firefox, it opened the Mozilla site that said I had the latest version of Firefox.  That's about all I can say.

BTW, to the OP:  Can you tell my why you would want to open 20+ tabs at the same time?  That boggles my mind, but then maybe it's just easily boggled.

---

### Post by relay_man on 2009-09-15
I think this is a bug, but I'm not sure yet.
You've got Intel processor and graphics?

Whenever this happens, could you open terminal and  run the command "top"  and list the 3 processes with the most memory and processor useage?

---

### Post by lovinglinux on 2009-09-15
The correct command is:

```
sudo apt-get install firefox-3.5
```

To optimize Firefox, read [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

.

---

### Post by Yanatsu on 2009-09-15
> **sgosnell said:**
> I don't know.  I installed from the repository, just checked About, and it says 3.5.3.  After the install and restart of Firefox, it opened the Mozilla site that said I had the latest version of Firefox.  That's about all I can say.

BTW, to the OP:  Can you tell my why you would want to open 20+ tabs at the same time?  That boggles my mind, but then maybe it's just easily boggled.
When I'm reading news, I click all the articles that interest me until the articles get to ones I've read already. Some days, I have a lot of tabs open. And it lags when I'm loading three, and that's a reasonable number, no?

And thank you, LovingLinux. I knew the command to get FF3, but wasn't sure how the version number was written in apt.

EDIT: So, speed problem fixed. But why does it still use the Minefield logo...? And why does the version in the repos work better? It's an older version, even.

---

