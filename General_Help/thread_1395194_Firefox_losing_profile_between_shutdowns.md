---
title: "Firefox losing profile between shutdowns"
date: 2010-01-31
forum: General Help
---

### Post by xaegis on 2010-01-31
I'm running Ubuntu 9.10 (x64) and Firefox.
Every time I restart firefox (even within the same session) it deletes my profile and dumps all the content of the ".mozilla" folders, mostly .sqlite and preference files into my home folder. It then presents me with a prompt that says I should create a new profile and says that the default location is unavailable.


```
Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520005 (NS_ERROR_FILE_DESTINATION_NOT_DIR) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520005 (NS_ERROR_FILE_DESTINATION_NOT_DIR)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]
```
Does anyone have any Idea what could be happening here and how do I solve this problem?

---

### Post by lovinglinux on 2010-02-01
Try [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

Also check if the settings on the first table [from here]("http://kb.mozillazine.org/About:config_entries#Profile.") are with default values.

---

### Post by oldfred on 2010-02-01
Are you running it as root not as your user? You should have correct permissions for your default profile and directory. Are you redirecting you profile to another directory (I do but had to make sure permissions were correct)?

[http://kb.mozillazine.org/Category:Issues_%28Firefox%29](http://kb.mozillazine.org/Category:Issues_%28Firefox%29)

---

