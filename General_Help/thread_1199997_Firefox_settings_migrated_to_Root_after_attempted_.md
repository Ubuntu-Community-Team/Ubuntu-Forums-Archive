---
title: "Firefox settings migrated to Root after attempted upgrade"
date: 2009-06-29
forum: General Help
---

### Post by dogeatery on 2009-06-29
I wanted to try the Firefox 3.5 RC and, as you know, to use the "Help > Check for updates" option, one must be running the browser as root. So I did "sudo firefox" and ran the function, restarted the program and: 

1) it didn't upgrade to 3.5 (no biggie, I guess I can just be patient and wait for it to show up in the repositories) 

**2) The real problem:** All of my bookmarks, cache, cookies, Awesome Bar no longer work unless I run FF as root.  Obviously, I don't want to be online as root user 100% of the time. I did a quick check and in my /home/.mozilla folder, everything is still in its proper place, yet the program isn't finding it. I tried making a new /.firefox folder and copy/pasted everything into it but this also didn't work. 

I've posted this at  Firefox forums and received little help -- I already checked with the profile manager and found this was not the cause of the problem.  Any suggestions?

Edit:  In case it matters, I'm running Linux Mint Elyssa

---

### Post by Celauran on 2009-06-29
Did you check the ownership of ~/.mozilla and its subdirectories? Might just need a chown -R.

---

### Post by CatKiller on 2009-06-29
That's why you use gksudo rather than sudo for graphical applications.

++ on the plan to check the permissions on your Firefox profile folder.

---

### Post by dogeatery on 2009-06-29
**Action:**  Checked ownership, and though it said I am the owner of ~/.mozilla, I went ahead and ran the chown -R command.

**Result:**  Problem persists.

Thanks for the suggestion, though, Celauran

---

### Post by dogeatery on 2009-06-29
> **CatKiller said:**
> That's why you use gksudo rather than sudo for graphical applications.

++ on the plan to check the permissions on your Firefox profile folder.

Sorry I didn't see your post immediately.  I wasn't aware there was a difference.  What does gksudo do?  Is it more secure while I'm dealing with this problem?

---

### Post by CatKiller on 2009-06-29
> **dogeatery said:**
> I wasn't aware there was a difference.  What does gksudo do?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dogeatery on 2009-06-29
> **CatKiller said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I read this post and now am of the opinion that I did exactly what this post says not to do and the result was exactly what the post said might happen.  How can I return the root configuration to my user configuration?

Also, thanks for the enlightening post, I've been using sudo for years in very similar situations and you probably just saved me lots of headaches down the road.

---

### Post by Celauran on 2009-06-29
> **dogeatery said:**
> How can I return the root configuration to my user configuration?
If chown didn't do the trick, you could try moving your ~/.mozilla to ~/.mozilla.bak and start a new instance of Firefox. This should create a new ~/.mozilla for you. Now it's just a matter of copying ~/.mozilla.bak/firefox/gibberish/* to ~/.mozilla/firefox/moreGibberish

---

### Post by dogeatery on 2009-06-29
> **Celauran said:**
> If chown didn't do the trick, you could try moving your ~/.mozilla to ~/.mozilla.bak and start a new instance of Firefox. This should create a new ~/.mozilla for you. Now it's just a matter of copying ~/.mozilla.bak/firefox/gibberish/* to ~/.mozilla/firefox/moreGibberish

**Action:  **moved ~/.mozilla to ~/.mozilla.bak.  Opened a new instance of firefox and copied ~/.mozilla.bak/firefox/oxu01orc to ~/.mozilla/firefox/oxu01orc.default

**Result:  **Problem persists

Is there something corrupted in my gibberish file?

---

### Post by CatKiller on 2009-06-29
> **dogeatery said:**
> copied ~/.mozilla.bak/firefox/oxu01orc to ~/.mozilla/firefox/oxu01orc.default

I think you need to be a bit more fine-grained about it. You know that **something** is broken in there. You need to isolate what that is, and restore as much as you can from your old profile without breaking the new one. One step at a time.

---

### Post by Celauran on 2009-06-29
> **dogeatery said:**
> **Action:  **moved ~/.mozilla to ~/.mozilla.bak.  Opened a new instance of firefox and copied ~/.mozilla.bak/firefox/oxu01orc to ~/.mozilla/firefox/oxu01orc.default

**Result:  **Problem persists

Is there something corrupted in my gibberish file?

I meant do the same thing one directory down; ~/.mozilla/firefox/oxublahblah/*

Could well be that something is corrputed, though. gksu, run Firefox, and export bookmarks should at least rescue those. Settings/saved passwords are another story.

---

### Post by lovinglinux on 2009-06-29
> **Celauran said:**
> If chown didn't do the trick, you could try moving your ~/.mozilla to ~/.mozilla.bak and start a new instance of Firefox. This should create a new ~/.mozilla for you. Now it's just a matter of copying ~/.mozilla.bak/firefox/gibberish/* to ~/.mozilla/firefox/moreGibberish

I don't know why everyone recommends moving or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications stores their profiles (Thunderbird, Sunbird, etc), so deleting this folder will delete their settings too.

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to delete a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla. Nevertheless, deleting an entire profile is usually unnecessary and must be avoided, since just a few profile files are the usual culprits, otherwise you will delete all Firefox settings, extensions, themes, bookmarks and so on.

> **dogeatery said:**
> **Action:  **moved ~/.mozilla to ~/.mozilla.bak.  Opened a new instance of firefox and copied ~/.mozilla.bak/firefox/oxu01orc to ~/.mozilla/firefox/oxu01orc.default

**Result:  **Problem persists

Is there something corrupted in my gibberish file?

If you move ~/.mozilla.bak/firefox/oxu01orc.default to ~/.mozilla/firefox/oxu01orc.default you are essentially copying the corrupted files back to your profile, so it won't fix it.

The problem with bookmarks and the Awesome Bar are usually caused by a corrupted *places.sqlite* file inside the profile. In your case, the problem is probably due to permissions, since you ran Firefox with sudo. You could try to simply delete the file *places.sqlite*. This will reset your bookmarks and fix the problem with the Awesome bar. Then you can restore a bookmark backup through the Bookmark organizer.

If this doesn't solve all your problems, then close Firefox, delete ~/.mozilla/firefox and start Firefox again so it can create new profile files. Don't copy anything from the old profile backup. First check if everything works with the clean profile. Then you can copy essential files from the ~/.mozilla.bak/firefox/oxu01orc.default one by one. But check each file ownership before copying. 

If you tell me which things you want to preserve from the old profile, like extensions, cookies, settings and so on, I can tell you which files you need to copy.

---

### Post by dogeatery on 2009-06-29
**Action:** ```
sudo chown -R <user>:<user> ~/.mozilla
```  (where <user> is your username)

**Result:**  Problem solved!  All previous settings were restored to Firefox when I opened the application as a normal Ubuntu user.   [IMG]http://forums.mozillazine.org/images/smilies/icon_mrgreen.gif[/IMG] 

**Moral of the Story:**  Use gksudo instead of sudo when running graphical apps like Firefox from the console.

lovinglinux: Was about to go with your solution but I was given the above in the Mozillazine forums.   Posting it here for the community, as it's apparently a Linux/Ubuntu issue more than a strictly Firefox issue.

Thanks to everyone for their quick and helpful responses!

---

### Post by lovinglinux on 2009-06-29
> **dogeatery said:**
> **Action:** ```
sudo chown -R <user>:<user> ~/.mozilla
```  (where <user> is your username)

**Result:**  Problem solved!  All previous settings were restored to Firefox when I opened the application as a normal Ubuntu user.   [IMG]http://forums.mozillazine.org/images/smilies/icon_mrgreen.gif[/IMG] 

**Moral of the Story:**  Use gksudo instead of sudo when running graphical apps like Firefox from the console.

lovinglinux: Was about to go with your solution but I was given the above in the Mozillazine forums.   Posting it here for the community, as it's apparently a Linux/Ubuntu issue more than a strictly Firefox issue.

Thanks to everyone for their quick and helpful responses!

Fortunately it was just a permission issue and not file corruption. Nevertheless, I wouldn't recommend running Firefox with sudo or gksudo in the future.

---

### Post by dogeatery on 2009-06-29
> **lovinglinux said:**
> Fortunately it was just a permission issue and not file corruption. Nevertheless, I wouldn't recommend running Firefox with sudo or gksudo in the future.

Yeah, I plan on avoiding it.  If I'd known 3.5 was supposed to come out tomorrow I never would even have bothered with it.

---

### Post by lovinglinux on 2009-06-29
> **dogeatery said:**
> Yeah, I plan on avoiding it.  If I'd known 3.5 was supposed to come out tomorrow I never would even have bothered with it.

Firefox 3.5 final probably won't be available in Jaunty repositories, only in Karmic Koala. The version available today is still beta, not even RC.

---

