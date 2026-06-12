---
title: "My pc freezes for a about half a min, right after I log in"
date: 2012-02-14
forum: General Help
---

### Post by Evanfox on 2012-02-14
Hi everyone,

I noticed that my pc freezes for a while right after I enter the DE (I use xubuntu btw), for no particular reason. This lasts only half a min or so and everything goes back to normal after that. 
What can I do to fix this??

Thanks in advance
Cheers! :-)

---

### Post by Toz on 2012-02-14
What version of xubuntu are you using? 
Is there anything in your ~/.xsession-errors file that might show whats holding it up?
What applications are you autostarting?

One possible fix that might help is to clear the sessions cache (saved sessions). Open a terminal window and type in this command:
```
rm -rf ~/.cache/sessions
```
...this command will delete the folder that holds the information about your saved sessions - in effect clearing out the saved session information. Saved sessions is a functionality of xfce that basically saves information about running programs (only the programs, not the data) so that when you log in the next time it can restore (restart) those applications for you. There may be some redundant or problematic entries there that might be delaying your startup.

---

### Post by Evanfox on 2012-02-15
Hi, thanks for your reply!
I just had to uninstall a program and now everything is back to normal.
:-)

---

