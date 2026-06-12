---
title: "Problem with apt: 'The packa ge lists or status file could not be parsed or opened.'"
date: 2012-05-21
forum: General Help
---

### Post by jmr59 on 2012-05-21
Yesterday I installed 12.04 for a friend. (We've both been using kde on debian for some years, but went for kubuntu as it was easier to install on a MacBook for EFI-related reasons.)

The install worked very well, the only difficulty being that the live CD didn't recognize the wireless card, but after installing from the CD wifi worked without any problems.

After installing I installed aptitude, uncommented some of the repositories from /etc/apt/sources.list, and ran aptitude update and aptitude safe-upgrade.

Since doing this, anything involving aptitude (install or search), apt-get or apt-cache results in the following error-message:

```
E: Lesefehler - read (5: Eingabe-/Ausgabefehler)
E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.
```

(The install's in German; I'm more comfortable seeking help in English.)

I presume the last line of this is a translation of

```
The package lists or status file could not be parsed or opened.
```

-- the only google hit for the German error-message is the translation of aptitude at [http://naesten.dyndns.org:8080/public_html/debian/aptitude/po/de.po]("http://naesten.dyndns.org:8080/public_html/debian/aptitude/po/de.po")

I've found a great many solutions to similar problems that involve deleting the contents of /var/lib/apt/lists/ and running apt-get update. Each time I try this I get the same error.  (I also get it when running apt-get update again for good measure.)

I've ensured that the install CD is not contained within sources.list. I've tried commenting out all but the first repositories from sources.list, with no success. I've also tried regenerating sources.list from [http://repogen.simplylinux.ch/generate.php]("http://repogen.simplylinux.ch/generate.php") and then deleting the contents of /var/lib/apt/lists/ and running apt-get update, but that still results in the same error-message.

Any suggestions? Please let me know if you want me to post the full output of any of the commands mentioned (or indeed of any others).

---

### Post by Zorael on 2012-05-22
I'm not familiar with the error. Have you tried commenting out all your sources (including files in **/etc/apt/sources.list.d/**) and then enabling them one by one?

---

