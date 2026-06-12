---
title: "Thunderbird address book in ubuntu openoffice"
date: 2009-11-27
forum: General Help
---

### Post by GiganticDays on 2009-11-27
I'm running Ubuntu 9.10 and OOO 3.10 Ubuntu version, and almost, almost finished migrating from Windows completely.
One problem still nags though, and that's the inability to import the Thunderbird address book into OOO.
I initially tried to use Evolution, for which there is support, but found it unstable and buggy. So I returned to TB which I find fits my needs perfectly.

I've trawled the web looking for a workaround and tried installing OOO 3.1 from the openoffice.org site. It seemed to work OK and I successfully imported the TB address book. However calc just wouldn't work at all; it crashed on startup every time.
So I went back to the Ubuntu OOO 3.1 and, at the moment, am putting up with not having my address book integrated.

Are there any solutions out there for this?

PS I tried exporting the AB from TB as a csv file and importing that way but the fields got wrongly mapped and loads of records vanished altogether.

---

### Post by el cameleon on 2009-12-04
Maybe due to that bug: [         **Bug 519398**]("https://bugzilla.mozilla.org/show_bug.cgi?id=519398") -               Address book export of fields with embedded double-quote characters is invalid

You should check if you have this kind of character in your address book.

---

