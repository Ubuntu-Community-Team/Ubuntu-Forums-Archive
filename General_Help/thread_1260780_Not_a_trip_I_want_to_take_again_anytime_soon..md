---
title: "Not a trip I want to take again anytime soon."
date: 2009-09-08
forum: General Help
---

### Post by Silvernail on 2009-09-08
That was a hoot. Not a trip I want to take again anytime soon.

I have a new computer that I installed Hardy Heron on last  week.
Last night I went to a terminal and typed in: gwenview
Back comes this message that it is not installed and tells me to use apt-get.

So I do.  sudo apt-get -y install gwenview

During installation I see this line scroll by.
Suggested packages:
Blah Blah
Recommended packages;
Blah Blah

So when finished with gwenview,
 I scroll up and copy those 2 lines and use apt-get to install them.
A little later I go back to see how things are going. Across the screen are rows and rows of the message: Removine such'n'such program. Investigation show that 102 programs were deleted. Firefox, Teminal, some part of login, I could inter name and password but that was as far as it went. To say the least my system was severally crippled.

Luckally, nothing important was lost. I spent all this morning reinstalling 8.04.

Is this a known issue? Anyone got a system they are willing to kill to see if this was an isolated case? Who to report this to?

---

### Post by Johnny B on 2009-09-08
what were the 2 packages that you installed?

aparently this dosent affect jaunty
i had nothing unusual happen when:
sudo apt-get install gwenview
...
The following extra packages will be installed:
  libkipi6
The following NEW packages will be installed:
  gwenview libkipi6

---

### Post by Silvernail on 2009-09-08
These were not automatically installed with 'gwenview'. There were 2 lines in the stuff that scrolls across the screen.

One was "Suggested Packages" and a list of apps.
The other was "Recommended Packages" and a list of apps.

I had to do another 'apt-get install'.
Here are the offending lines:
```
t
Suggested packages:
  gwenview-i18n fam perl-suid nas libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
Recommended packages:
  kdegraphics-kfile-plugins kipi-plugins libarts1-akode exiv2

```

---

