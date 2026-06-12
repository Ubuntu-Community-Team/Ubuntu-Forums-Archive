---
title: "Tomboy sync options greyed out"
date: 2011-10-18
forum: General Help
---

### Post by freesitebuilder on 2011-10-18
I'm running 10.10, and I want to set my Tomboy notes to sync to my Dropbox folder - but all the options on Edit > Prefs > Sync tab are greyed out. I've got the Note Dir Watcher enabled, and all the add-ins under the Sync section, but that's made no difference.

---

### Post by duanedesign on 2011-10-18
To resolve this you have to edit the server field for Tomboy Web. After authenticating in the browser it tells you to go back to the Preferences window and press Save. Go back to the Preferences and remove the trailing slash '/' from the server address. It will read https:one.ubuntu.com/notes/ and change it to https:one.ubuntu.com/notes . You can add the trailing slash back if you want. The important thing is the field is edited.

NOTE: I have seen some fixes using the edge server. http//edge.one.ubuntu.com/notes . I do not recommend using the edge server. It is used for testing and updated hourly.

---

### Post by freesitebuilder on 2011-10-19
That's the problem - it's greyed out. The only clickable item on that tab is the advanced button, and the "automatically sync" checkbox.

---

### Post by dyess002 on 2011-10-19
Same problem here also.

---

### Post by freesitebuilder on 2011-10-19
I'm wondering if removing UbuntuOne (which hasn't worked for me since 2009!) will give me the options.

---

### Post by practic on 2011-11-29
Did you folks try the "Clear" button, located to the right of the "Advanced" button?

---

### Post by dyess002 on 2011-12-05
This is what my Ubuntu One looks like.

---

### Post by practic on 2011-12-05
Hmm...

I thought the original question was about using Tomboy sync with Dropbox. Somehow it got turned into a UbuntuOne question...?

Anyway, my UbuntuOne control panel looks very different...are you sure you're not using an out-dated version?

---

### Post by dyess002 on 2011-12-05
> **practic said:**
> Hmm...

I thought the original question was about using Tomboy sync with Dropbox. Somehow it got turned into a UbuntuOne question...?

Anyway, my UbuntuOne control panel looks very different...are you sure you're not using an out-dated version?


Sorry about that I should have paid attention before I wrote.  I am using the repositories in Backtrack5 Lucid I believe. I can't find a way to check the version of Ubuntu one. I got the Ubuntu One site to let me add my computer but when I click ADD the web page shows not available check your connection stuff.  I sure would like to get to work in Backtrack.

---

