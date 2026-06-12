---
title: "Chromium is totally broken"
date: 2011-08-13
forum: General Help
---

### Post by StartedTheFire on 2011-08-13
A few weeks ago I ran chromium as root for some reason. After that, running it normally would result in it not being able to read preferences or use any extensions. That was really annoying so I made a script to run chromium as root. So I just would click on that, alt+t, and enter my password. But I wanted to find a real solution so I asked my friend and he said it's probably the permissions of my ~/.config/chromium-browser folder. I looked at it and tried to change the permissions but ended up just deciding to delete the folder.

When I launched the browser it just made a new folder and the permissions issue was solved. But then lots of things weren't working (I think it all has to do with flash because flash was definitely not working at all.) I couldn't comment on facebook statuses because enter just made a new line, and the menu bars and mouseover stuff on that site wasn't working at all. 

I have since tried to completely remove Chromium and I can't! I have removed everything via synaptic, opened nautilus as root and searched for chromium, removed it via the app store- EVERYTHING that looks like it has anything to do with chromium is GONE. And yet whenever I reinstall it, it still somehow saves my passwords and it still doesn't act like a clean install.

TL;DR- I am trying to completely reinstall chromium but it's impossible. It stays totally screwed up even after as complete a reinstallation as I can do. Flash refuses to work because it's supposed to "just work" with the browser which means little to no documentation on what to do if it actually DOESN'T work.

---

### Post by flipper T on 2011-08-13
flash is supposed to "just work" with chrome, not chromium.

have you tried installing chrome as an alternative to chromium ?

ps they are very similar

---

### Post by MG&amp;TL on 2011-08-13
Quick and nasty fix, but is there a reason why you can't do a reinstall of your OS?

Alternatively, use Firefox. Or use Opera, although I think they are free but not open-source.

---

### Post by StartedTheFire on 2011-08-13
Yeah I might end up just doing that. It wouldn't be the first time I've reinstalled my OS to do something dumb and it won't be the last.

And I just don't like google. I feel more like a super leet haxxor when I use chromium.

---

### Post by flipper T on 2011-08-13
i'm getting really old

---

### Post by niko123456 on 2011-08-13
did you try using Chromium to clear all the browsing data?

what happens if you try and view Facebook in a stealth/pr0n mode (ctrl shift + n)?

---

### Post by StartedTheFire on 2011-08-14
It actually all works perfectly in incognito. I was totally not expecting that! Thanks! I suppose it must be an extension somewhere that's disabled in incognito....

---

### Post by StartedTheFire on 2011-08-14
All I had to do was clear all my browsing data and now everything works! Thanks for the suggestion about incognito, it got me on the right path.

---

