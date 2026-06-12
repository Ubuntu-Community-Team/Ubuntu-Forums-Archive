---
title: "Firefox unable to get to non authenticated sites"
date: 2010-02-24
forum: General Help
---

### Post by Nonno Bassotto on 2010-02-24
I'm using Firefox 3.5.8 on Ubuntu 9.10. It seems it has gone crazy when visiting a site with a broken authentication.

Previously I could see a message warning that there were problems and asking if I wanted to continue understading the risk. Now it seems that this page is broken: I get an XML error saying

```

Errore interpretazione XML: entità non definita
Indirizzo: jar:file:///usr/lib/firefox-3.5.8/chrome/browser.jar!/content/browser/certerror/aboutCertError.xhtml
Linea numero 59, colonna 12:    <title>&certerror.pagetitle;</title>
-----------^

```

This happens for example visiting [this page]("https://tqft.net/hg/Grothendieck/"). So have they broken their own message page? Do you experience the same error?

---

### Post by Nonno Bassotto on 2010-02-24
I cannot reproduce this anymore, so I guess it is solved :confused:

---

### Post by derekh4 on 2011-03-04
I still get this error on Firefox 3.6.13 running Ubuntu 10.04 so I would disagree that it is "solved".

---

### Post by knoxg on 2011-03-14
Also seeing this behaviour in Firefox 3.6.14 on Ubuntu 10.10 (including security updates to 2011-03-14)

---

