---
title: "Have Google Chrome prompt for profile"
date: 2010-12-17
forum: General Help
---

### Post by MSPdwalt on 2010-12-17
Rumor has it that one of my favorite web services del.icio.us may be getting the ax from Yahoo.  The firefox delicious extension was the only reason I hadn't switched to Chrome. (Couldn't find a Chrome extension I liked)

Now I've [migrated my bookmarks]("http://www.ampercent.com/delicious-shutting-down-export-delicious-bookmarks-migrate-google/7600/") to Google Bookmarks, found a nice Google Bookmarks Chrome extension, and  made the switch.

Where I run into problems is my workplace uses Google Apps for email.  So I have 2 Google accounts my personal Gmail account and my work account.  I'd like to separate the 2 when using chrome which I've found is fairly straight forward.  You create a separate [chrome profile]("http://techspalace.blogspot.com/2010/02/multiple-profile-in-google-chrome-in.html") and then have to create a separate launcher for your new profile.

I would like to script something to prompt me to choose a profile, then launch chrome using said profile.

I'm pretty weak with my bash scripting and have never even attempted a nautilus script.

Any suggestions?

-DW

---

### Post by tgalati4 on 2010-12-17
Does the chrome command take any commandline parameters?  If so, then you could create two desktop launchers.  Each would have the work or personal profile commandline flag (if such a flag exists).  If chrome is already running in one profile and you try to launch in another profile, I'm not sure what would happen.

---

### Post by MSPdwalt on 2010-12-17
> **tgalati4 said:**
> Does the chrome command take any commandline parameters?  If so, then you could create two desktop launchers.  Each would have the work or personal profile commandline flag (if such a flag exists).  If chrome is already running in one profile and you try to launch in another profile, I'm not sure what would happen.
Yes Chrome does have command-line functionality (follow the profile link in my original post)  What they suggest is what you suggest, create multiple launchers.

I would rather create a single launcher to execute some kind of script that asks me which profile I want to use, then executes the appropriate chrome command based on my response.  That way I don't end up accidentally logged into the wrong account.

---

### Post by MSPdwalt on 2012-03-10
This was resolved by Google implementing it's multiple sign on feature and delicious being bought instead of axed.

---

