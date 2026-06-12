---
title: "firefox save tabs on exit in 9.10 karmic"
date: 2010-02-17
forum: General Help
---

### Post by InspiredIndividual on 2010-02-17
Is it possible in Ubuntu 9.10 Karmic, Firefox 9.5, to save your tabs on exit while not saving your browsing history? This used to be possible in 9.04, same Firefox version, but I haven't managed to do so after upgrading to 9.10.

I read some earlier thread dealing with Ubuntu 8.10 ([http://ubuntuforums.org/showthread.php?t=919952](http://ubuntuforums.org/showthread.php?t=919952), now closed) in which it was stated that combining 'tab restoring' and 'no browsing history' was not possible altogether. Actually, it was. Exiting the browser by clicking the 'x' or closing the last tab did not work, but File -> Quit or Ctrl + Q did the job perfectly.

Does anyone have an idea to help me out?

---

### Post by ajgreeny on 2010-02-17
Use **Tab Mix Plus** add-on and you can do what you want, but only if you use the option to use the add-ons own session restore rather than firefox own version.  You set that up in the TMP preferences.

---

### Post by lidex on 2010-02-17
There is an option in the "Bookmarks" menu to "Bookmark all tabs..." - or by right-clicking on a tab for that matter. Not an option for you?

---

### Post by InspiredIndividual on 2010-02-17
I'll look into Tab Mix Plus. I was aware of the possibility to bookmark all tabs, but I consider it imperfect. It is much easier if everything is done automatically.

Generally, I would prefer to get the previous behavior back within the main Firefox itself, because more addons do mean more bloat. That being said, I think I'll use Tab Mix Plus if I do not find an alternative. Thanks very much for the suggestions.

---

### Post by lovinglinux on 2010-02-17
You could write a script to copy the file *sessionstore.js* to another folder before closing Firefox and copying it back before starting Firefox. That is the file that stores information about opened tabs. It gets deleted when you choose to delete the history, although it does not contain the history info itself, which is stored in the database file *places.sqlite*.

---

### Post by zbirdman777 on 2010-02-17
I think the cause of the problem is that when you first run firefox and exit with tabs open it asks you to save tabs and quit, or quit without saving, and there's a checkbox that says don't show me this message again.

I bet you hit the checkbox and clicked save and quit so now the prompt won't come up again.

I don't know if this will work for sure but go to Edit > Preferences (in Firefox) go to Tabs and check the box that says warn me when closing multiple tabs.

That will probably bring up the prompt and when it does click "quit without saving" and check the box.

I'm not sure what Firefox 9.5 is though.

---

### Post by lovinglinux on 2010-02-17
> **zbirdman777 said:**
> I think the cause of the problem is that when you first run firefox and exit with tabs open it asks you to save tabs and quit, or quit without saving, and there's a checkbox that says don't show me this message again.

I bet you hit the checkbox and clicked save and quit so now the prompt won't come up again.

I don't know if this will work for sure but go to Edit > Preferences (in Firefox) go to Tabs and check the box that says warn me when closing multiple tabs.

That will probably bring up the prompt and when it does click "quit without saving" and check the box.

I'm not sure what Firefox 9.5 is though.

That is not the same problem. The problem is that when you choose to delete the browser history, Firefox automatically deletes the file *sessionstore.js*, which stores the information about running tabs. So, unless you don't delete the history, the information about opened tabs also gets deleted, no matter if you properly setup Firefox as you suggested.

---

### Post by InspiredIndividual on 2010-02-18
> **lovinglinux said:**
> That is not the same problem. The problem is that when you choose to delete the browser history, Firefox automatically deletes the file *sessionstore.js*, which stores the information about running tabs. So, unless you don't delete the history, the information about opened tabs also gets deleted, no matter if you properly setup Firefox as you suggested.

I agree that this is most probably the prefered behavior by Mozilla. The funny thing is, it was not completely working like this previously. I guess that I managed to take profit from a minor bug while it hadn't been resolved yet.

> **lovinglinux said:**
> You could write a script to copy the file *sessionstore.js* to another folder before closing Firefox and copying it back before starting Firefox. That is the file that stores information about opened tabs. It gets deleted when you choose to delete the history, although it does not contain the history info itself, which is stored in the database file *places.sqlite*.

I am afraid that I do not know precisely how to implement this. I can probably write the script. However, I've got no clue how to automatically run it before Firefox closes, nor how to execute the second part of the script to move *sessionstore.js* back to its original location after Firefox has closed.

---

