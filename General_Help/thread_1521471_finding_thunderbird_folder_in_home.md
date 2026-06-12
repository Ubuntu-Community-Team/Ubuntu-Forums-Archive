---
title: "finding thunderbird folder in /home"
date: 2010-06-30
forum: General Help
---

### Post by craig.brisbane on 2010-06-30
Hi, I recently did a fresh upgrade. I am having problems in getting Thunderbird to run. From reading stories on the web I attempted to create the folder ".mozilla-thunderbird" in my /home folder as I could not see the hidden folder.

When creating the folder I get a message that the folder already exists - however I can not see the hidden folder - I see a number of other hidden folders but not this one.

any suggestions on how I can locate this folder??

---

### Post by Vaphell on 2010-06-30
what happens when you enter '~/.mozilla-thunderbird' in the location bar of nautilus? (may require switching to proper mode with ctrl+L)

also you can try running
```
find ~ -name .moz*
```
in terminal

---

### Post by SoFl W on 2010-06-30
I have  "/home/SoFlW/.mozilla-thunderbird" as a linked folder to "/home/SoFlW/.thunderbird"

---

### Post by oldfred on 2010-07-01
the new version of thunderbird moved its default location. It must have added the link to in effect move the data from old version to new.

New version:
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Older version:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

