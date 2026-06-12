---
title: "How to remove mail addresses from auto-completion in Evolution?"
date: 2010-12-20
forum: General Help
---

### Post by megandy on 2010-12-20
Hi all,

I'm wondering how to remove some email addresses from the auto-completion list which appears when starting to enter a new mail address into the "to:" field. Since I'm using Evolution for several years now there are a lot of e-mail addresses which are either obsolete or simply incorrect.

Has anyone an idea?

- Andy

---

### Post by tredegar on 2010-12-20
I'm guessing, but I would have expected evolution only to auto-suggest addresses that are in your address book. If this isn't the case then perhaps make it suggest an address that isn't in your address book, and that you do not want, and then run a recursive **grep** for that address in **~/.evolution/*** That should tell you where the addresses are being kept.

---

### Post by megandy on 2010-12-21
Thanks for your suggestion. Indeed I found an additional address book, from my migration to the new version which was queried. I've removed this and old addresses are gone.

Thank you very much!

---

