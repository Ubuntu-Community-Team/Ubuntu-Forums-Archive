---
title: "Importing settings/profile in Chrome"
date: 2009-11-12
forum: General Help
---

### Post by DJJoeJoe on 2009-11-12
I love Chrome, it was my joy when I was running windows and switching recently to ubuntu I'm wondering exactly how to import at least my bookmarks and general settings into the dev build I currently am running now.

I've saved my userdata folder```
C:\Documents and Settings\\Local Settings\Application Data\Google\Chrome
``` which contained everything from the previous windows installation of chrome, and I honestly don't know where to begin to either simply move the folder to where it is in ubuntu or any other tricks I'll need to import the data if the file structure is different.

I'm assuming that all I need right now is just the location to place/import the userdata folder to get my settings intact.

Thanks in advance, I can provide more info if needed and all that.

PS: Loving the Ubuntu experience so far, packages are genius if a bit of a learning curve.

---

### Post by DJJoeJoe on 2009-11-12
Looks like I'm smarter then I thought, and it's easier then I thought too.

For those interested you can simply copy/paste the userdata folder to:

```
/home/<user>/.config/google-chrome
```

It seems I'll need to place the history in the main folder rather then in 'Default' for it to grab it, but all my bookmarks work fine as is so far.

EDIT: I'm unsure how to change the prefix of this thread to 'solved' for which it should now be switched to. :)

---

### Post by Riot@ct on 2010-03-25
How I make a new user profile?

---

### Post by idrinkwhisky on 2010-06-02
if you want to make a new profile you can do the following:

use your explorer to go to:

.config/google-chrome

then create a new folder. Call it "ABC" (or whatever).

then you can right-click your panel and select "add to panel".
Now select "custom application launcher".

in the field "name" fill in "chrome ABC"
command fill in:

google-chrome --user-data-dir=/home/USER/.config/google-chrome/ABC

note where it says USER you should fill in your username
where it says ABC fill in whatever you picked.

(i read bout this procedure somewhere on the web a while ago, can't remember what site it was).

---

### Post by fragos on 2010-06-02
Chrome has an excellent synchronization feature that dose bookmarks, themes and settings. I know the bookmarks are stored in a folder in Google Docs. I don't know for sure but I'd sure try syncing Windows Chrome and Linux Chrome to the same Google account. It works well between Ubuntu systems even when one is a new clean install.

---

