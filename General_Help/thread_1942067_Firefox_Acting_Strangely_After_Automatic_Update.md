---
title: "Firefox Acting Strangely After Automatic Update"
date: 2012-03-16
forum: General Help
---

### Post by gpeck157 on 2012-03-16
Hi all,
After an automatic update last night, my Firefox started acting strangely. When I launch it, my Bookmarks Toolbar is missing. When I go to View> Toolbars my Bookmarks Toolbar is checked. When I uncheck it and go back to my Homepage then go back and recheck it, they suddenly appear. 
Also, when I type a web address in the Address Bar, such as [http://www.google.com](http://www.google.com) and hit enter (or press the "go to" arrow), nothing happens. If I go to a bookmark, it will take me there. I'm baffled.
Thanks

---

### Post by imachavel on 2012-03-16
here is your best option imho. Go to software sources, find firefox in the repositories it should be installed. Now uninstalled it, reinstall it. Or download google chrome for debian kernel and it should work the same in ubuntu.

---

### Post by lovinglinux on 2012-03-20
What version of Ubuntu and Firefox you are using?

Looks like you have a corrupted bookmark database. Close Firefox, open your Firefox profile folder under ~/.mozilla/firefox/xxxxx.default locate the file *places.sqlite* and rename it to *places.sqlite.bak* or something else. 

Start Firefox, open the Bookmark Manager, click "Import and Backup >>> Restore" and select the latest entry. This will restore your bookmarks. If everything goes well, then you can delete the old *places.sqlite* file.

---

### Post by gpeck157 on 2012-03-26
Thank you for your suggestion.

---

### Post by gpeck157 on 2012-03-26
Thank you for your suggestion. My software repository was linked to an experimental version of Firefox. (I don't remember which one at this point.) I deselected that entry, completely uninstalled Firefox and deleted my .mozilla folder also. Then I rebooted and installed the correct Firefox, rebooted again and voila it was all back to normal. (I saved my bookmarks as an html file prior to doing all of this so they weren't lost.) 

When I uninstalled Firefox I did so from the command line, and accepted the second solution to unresoved dependencies. That, in combination with using the correct version of Firefox, is what I think did the trick.

Thanks again to both of you who responded. I do appreciate the suggestions.

---

