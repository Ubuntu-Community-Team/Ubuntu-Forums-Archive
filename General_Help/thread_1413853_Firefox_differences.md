---
title: "Firefox differences"
date: 2010-02-22
forum: General Help
---

### Post by christia on 2010-02-22
Okay, this is probably a super stupid question:
 
In windows, i used to be able to pres ctrl+e when i was browsing, making it go directly to the search field in the upper right corner. that doesnt seem to work in firefox in ubuntu - how do i make that happen?
 
also, when i click in the url, instead of highlighting it all as it does in firefox for windows, it just places the cursor there, which is annoying me to death. how do i fix that?

---

### Post by nixclusive on 2010-02-22
You can use ctrl-K to goto the search field. Double clicking in the address bar would highlight the whole url. Not sure how you'd go about making it behave like windows.

---

### Post by christia on 2010-02-22
ok, thanks. ctrl+k is fine as well, although ctrl+e is more convenient imo. the doubleclicking is annoying though, but so be it

---

### Post by kaibob on 2010-02-22
> **christia said:**
> also, when i click in the url, instead of highlighting it all as it does in firefox for windows, it just places the cursor there, which is annoying me to death. how do i fix that?

Change the following Firefox about:config setting to true. If you are not familiar with about:config settings, let us know.

browser.urlbar.clickSelectsAll

---

### Post by christia on 2010-02-23
am not familiar, sorry :)

---

### Post by kaibob on 2010-02-23
> **christia said:**
> am not familiar, sorry :)

Load Firefox and enter "about:config" (omit quotes) in the address bar. After "filter" enter "browser.urlbar.clickSelectsAll" (omit quotes). Below that, double-click on browser.urlbar.clickSelectsAll, which should change the "Value" from false to true. Restart Firefox, and you should be good to go.

---

