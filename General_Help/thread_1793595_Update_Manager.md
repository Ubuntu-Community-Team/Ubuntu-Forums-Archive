---
title: "Update Manager"
date: 2011-06-29
forum: General Help
---

### Post by carmenat250 on 2011-06-29
I'm not that regular in going into update manager to look for new security updates and so a good amount of time can pass before I check for updates, which means when I do update, there are usually several that need to be downloaded.

Hopefully this is not a stupid question, but does that leave my computer vulnerable.  On Windows, I would say yes, but everyone says Ubuntu is so secure and that's why I'm asking.

---

### Post by nomko on 2011-06-29
I won't say vulnerable but it will eventually leave you with an out-of-dated system. You will miss some important updates.

---

### Post by amjjawad on 2011-06-29
> **carmenat250 said:**
> I'm not that regular in going into update manager to look for new security updates and so a good amount of time can pass before I check for updates, which means when I do update, there are usually several that need to be downloaded.

Hopefully this is not a stupid question, but does that leave my computer vulnerable.  On Windows, I would say yes, but everyone says Ubuntu is so secure and that's why I'm asking.

Didn't understand your point but Update Manager always shows a POP-UP Window/Message with the latest updates. You either go through them or just download. For me, I take a quick look and install.

Ubuntu handles the Updates MUCH better than Windows if you ask me.
With Windows, I feel like the Updates will never stop and it just make me feel bad (not going to say sick).

---

### Post by donato roque on 2011-06-30
My Update Manager set up:
 
 - daily

 - download and install security updates without confirmation

This way with a not so regular update check on my part only application updates are left for my consideration. 

If you still want to make sure if an important security update was accomplished, you can use the log file viewer and open /var/log/dpkg.log 

Or just start the gnome-terminal type: tail -F /var/log/dpkg.log

---

### Post by carmenat250 on 2011-06-30
> **donato roque said:**
> My Update Manager set up:
 
 - daily

 - download and install security updates without confirmation

This way with a not so regular update check on my part only application updates are left for my consideration. 

If you still want to make sure if an important security update was accomplished, you can use the log file viewer and open /var/log/dpkg.log 

Or just start the gnome-terminal type: tail -F /var/log/dpkg.log

I didn't know there were settings associated with this feature.  I just checked mine and they are the defaults and the same as what you've listed above.

I'm not sure why I don't get the prompts to do updates then?  I usually run my Ubuntu using a desktop user account.  Would this prevent the updates from popping up due to a lack of authority?

---

