---
title: "How do I make links in Liferea and Thunderbird open in the background in Firefox?"
date: 2012-06-08
forum: General Help
---

### Post by Rytron on 2012-06-08
Hi.

How do I make links in Liferea and Thunderbird open in the background (I want to open certain links in Firefox but continue to work in Liferea/Thunderbird in the meantime) in Firefox? They used to until recently. I could make the windows stay on top but this would have to be done every time I re-open Liferea and Thunderbird which is a nuisance.

---

### Post by chupnik on 2012-09-02
I have the exact same issue.
I found the following way by setting CCSM(Compiz Config Settings Manager).

In CCSM, under General Options, set Auto-raise=Very high and Delay=500. All new windows will open in the background!

But there is a small disadvantage. Some dialog box is also open applications in the background.
Maybe if you play around with the settings and CCSM can solve it.

---

### Post by Zill on 2012-09-02
Rytron/chupnik:
[LIST=1]
[*]Enter "about:config" into the Firefox address bar
[*]Type "diverted" into the search box
[*]Double-click on the entry "browser.tabs.loadDivertedInBackground"
[*]This should now have changed the value from "false" to "true"
[*]Job done!
[/LIST]

---

### Post by Rytron on 2012-09-02
> **Zill said:**
> Rytron/chupnik:
[LIST=1]
[*]Enter "about:config" into the Firefox address bar
[*]Type "diverted" into the search box
[*]Double-click on the entry "browser.tabs.loadDivertedInBackground"
[*]This should now have changed the value from "false" to "true"
[*]Job done!
[/LIST]

Sweet! Thank you Zill. ;)

---

### Post by Chainy on 2012-11-16
Yes, thank you Zill. Your method works perfectly.

---

