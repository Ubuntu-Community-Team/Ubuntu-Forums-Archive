---
title: "Can't set swiftweasel as default for nautilus"
date: 2009-08-13
forum: General Help
---

### Post by triplemaya on 2009-08-13
I'm trying to set swiftweasel as the default browser. No problem setting it in preferred applications, but nautilus still uses firefox.
When I do
sudo update-alternatives --config x-www-browser 

I get

There are 2 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/firefox-3.0
*+        2    /usr/bin/epiphany-gecko

Press enter to keep the default[*], or type selection number: 

No mention of swiftweasel, which is not surprising as I have simply unpacked it in a directory. I tried to install it several different times but without success, so in the end I just set my menu to call the app direct. But of course firefox still starts when I click on a file in nautilus.

It's odd because google desktop search and thunderbird both open html files with swiftweasel.


Please could someone tell me how to fix this.

Many thanks in advance.

---

### Post by CatKiller on 2009-08-13
> **triplemaya said:**
> No problem setting it in preferred applications, but nautilus still uses firefox.

What do you mean by "nautilus still uses firefox?" What is it that you're trying to open? Links will open with whatever you've set in Preferred Applications (which in your case should probably be "/path/to/swiftfox %s"), but launchers will run whatever program they have in their Command field, and documents will open in whatever you've set in the Open With for that document type.

---

### Post by triplemaya on 2009-08-13
I click on an html file in nautilus and firefox opens the file.

---

### Post by CatKiller on 2009-08-13
> **triplemaya said:**
> I click on an html file in nautilus and firefox opens the file.

Then right-click on it, select Properties, click the Open With tab and either select swiftfox in the list (if it's there) or click Add and make it open with Swiftfox.

---

### Post by triplemaya on 2009-08-13
Got it. Couldn't find the 'open with' tab for looking! Now I know where it is. Thanks for your help.

---

