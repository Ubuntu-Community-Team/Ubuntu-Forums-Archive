---
title: "Firefox 3.5.4 Search not working"
date: 2009-11-01
forum: General Help
---

### Post by American on 2009-11-01
Upgraded today and FF 3.5.4's search box isn't working. The drop down gives me a full selection of search engines but when I enter data and hit enter or the search icon...nada.

Anyone else having this problem? Solution?

---

### Post by lovinglinux on 2009-11-01
Do you have problems with bookmarks or the address bar?

If yes, then see **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

If not, then try **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*].

---

### Post by American on 2009-11-01
Neither does a thing for me. I've also noticed that Shredder/TB3 will not open FF from links in emails again now.... that was another impossible problem to fix at one point.

Thought I fixed the url issue with Shredder.... was showing:

/usr/lib/firefox-3.0.9/firefox.sh

and changed to:

/usr/lib/firefox-3.5.4/firefox.sh

in the config: network.protocol-handler.app.http and network.protocol-handler.app.https

But that didn't work either.

Even tried /usr/lib/firefox-3.5.4/firefox  but no luck there either.

---

### Post by American on 2009-11-02
What is odd is that I fired up TB 2.0 and it's http config points to /usr/bin/firefox and it works like a charm....but not in Shredder.

---

### Post by American on 2009-11-06
No one else having search problems?

---

### Post by lovinglinux on 2009-11-06
> **American said:**
> No one else having search problems?

Create a new Firefox profile and see if it works. You can do that through the profile manager:

```
firefox -P
```

---

### Post by SlugSlug on 2009-11-10
in the search box click the little arrow and manage / add search engine...

---

### Post by American on 2009-11-10
What's crazy is that is just started working today. Still at 3.5.4...no explanation... there have a been a variety of updates including kernel updates but nothing to FF. Wish I knew what did it but I'm just glad it's working.

Now if I could just get hyperlinks to work in TB.

---

### Post by SlugSlug on 2009-11-10
in TB settings is there a reference to browser?  something like I have in amsn..
i set mine to 
firefox $url

---

