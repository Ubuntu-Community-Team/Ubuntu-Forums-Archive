---
title: "Howto: Disabling firefox crash restore"
date: 2010-03-01
forum: General Help
---

### Post by sandyd on 2010-03-01
I found many people were complaning about the fact that firefox does "session restore" after shutting down with firefox still on.

I recently was browsing around the mozilla wiki, and I found a article about it.

Although this will also cause you to be unable to restore your sessions after a crash, it fixes the "session restore" issue.

so, go to "about:config" in the firefox address bar.
click through the warning.
search for the value  [browser.sessionstore.resume_from_crash]("http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash")

double click on it to set it to false. 

that should fix the session restore problems.

---

