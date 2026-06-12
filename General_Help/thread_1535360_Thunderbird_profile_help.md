---
title: "Thunderbird profile help"
date: 2010-07-20
forum: General Help
---

### Post by caro on 2010-07-20
OK, I screwed up.  I ran an update to Thunderbird by launching Thunderbird from the terminal using 

> sudo thunderbird

and then clicked on Help > Check for updates.

The update ran just fine but doesn't recognize my old profile.  (And of course I didn't back it up first.)

If I look at /home/.thunderbird or /home/.mozilla-thunderbird, I see my default profile and all the mailbox settings and folders with the data in them; however, they are not showing up when I launch Thunderbird.

For good measure, I removed the updated Thunderbird and added it back via Synaptic.  Still no luck.

How can I get Thunderbird to recognize the Mail folder in my profile?

---

### Post by lidex on 2010-07-20
Why would you even contemplate running thunderbird with sudo? OK, never mind.
Right-click on the .thunderbird folder and select properties. Click the permissions tab. Does it look like this screen?

---

### Post by oldfred on 2010-07-20
I think running it as root just creates a new profile for the 'root' user. It now may be the default but your old profile should still be there.

What does profile.ini have in it.

---

### Post by caro on 2010-07-21
> **oldfred said:**
> I think running it as root just creates a new profile for the 'root' user. It now may be the default but your old profile should still be there.

What does profile.ini have in it.

Profile.ini points to the correct profile.

---

### Post by caro on 2010-07-21
> **lidex said:**
> Why would you even contemplate running thunderbird with sudo? OK, never mind.
Right-click on the .thunderbird folder and select properties. Click the permissions tab. Does it look like this screen?

Well, I was messing around (never a smart thing to do) and noticed that if I ran it with sudo it let me check for updates. :(

 No, it looks a little different.  I'm on a different computer now and will have to take a screen shot tomorrow.  

Folder access - create and delete files
File access - blank

Group and others have no access. 

I've reset all my email account settings -- if I can just get my saved emails I'll be happy.  I've resigned myself to the fact that it is hosed.

---

### Post by lidex on 2010-07-21
If the profile is still there you can access it this way. From an Alt+F2 run dialog enter```
 firefox -profilemanager
```

As for file permissions, your username should be owner and group. If it's root try opening nautilus as root and changing it back:
```
gksudo nautilus
```
Then click the button to apply to folder contents as well.

Always use gksudo for gui apps, not sudo.

---

### Post by caro on 2010-07-21
I'll check this when I get home from work.  Thanks.

I made the changes to the profile permissions and no luck.  I can still see the files but TB won't recognize them.  I can look at the code and get the important information I need and will just rebuild the mailboxes.  Thanks for your help.  Lesson learned!

---

