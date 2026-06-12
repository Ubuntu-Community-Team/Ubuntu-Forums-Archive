---
title: "Software installs - Confused"
date: 2012-01-03
forum: General Help
---

### Post by meshman333 on 2012-01-03
I'm new to Ubuntu and it's baffling me. It seems anything I install on it just disappears. Case in point (Ubuntu 11), I need to install OpenOffice. I go to openoffice.org and baffled by the massive grid of download packages. I try one for Debian since that seems to be the only selection that makes sense and I end up with a bunch of DEB files. Confused as to what I'm supposed to do with these, I go into the Unbuntu Software Centre and search for it. I install it. No problem.
 
Where is it? There's no program groups, no icons and if I search using Dash it finds absolutely nothing for "Open", "OpenOffice". etc.
 
What am I missing?
Thanks!

---

### Post by snowpine on 2012-01-03
OpenOffice has been renamed LibreOffice. It should be under your Applications, Office menu. :)

---

### Post by t0p on 2012-01-03
When using Ubuntu, you don't use the Windows way to install software.  You don't need to go to websites to download apps to install.  Just go to **Applications > Ubuntu Software Center** (or whatever it's called nowadays) and install apps from there.  Much simpler.

---

### Post by meshman333 on 2012-01-03
> **snowpine said:**
> OpenOffice has been renamed LibreOffice. It should be under your Applications, Office menu. :)
 
Oh fer...
 
Thanks!

---

### Post by t0p on 2012-01-03
Or, as snowpine pointed out, you've already got a whole heap of apps already installed. Look in the **Applications** menu.  Names may be unfamiliar, but the functionality of various Windows apps will be available right there.  And if not, check out the Ubuntu Software Center (or whatever it's called nowadays - I'm still using Ubuntu 10.04, and I believe a lot has changed since then).

---

### Post by meshman333 on 2012-01-03
"OpenOffice has been renamed LibreOffice."
 
Actually, now that I look around I'm not so sure.  LibreOffice is an entirely different site and appears to be a different product.  However when I look at the details for the installed OpenOffice I have it says:
 
"This is a transitional package, replacing the OpenOffice.org packaging with the LibreOffice packaging."
 
Followed by comments asking my original question, claiming it's broken, etc.  So does anybody know what this is all about?  Is it OpenOffice using LibreOffice icons?  If LibreOffice is OpenOffice renamed, shouldn't this be plastered all over openoffice.org?  I'm just confused because I require OpenOffice specifically.
 
Thanks for all the replies...

---

### Post by spacecheck on 2012-01-03
> **snowpine said:**
> OpenOffice has been renamed LibreOffice. It should be under your Applications, Office menu. :)

Actually, OpenOffice wasn't "renamed", but had been acquired by Oracle. Fearing it would no longer be open source, LibreOffice was created as an open source fork based on the code availble at the time and was subsequently developed separately. Since then, Oracle has donated OpenOffice to the Apache Software Foundation, so it will also remain open source (apparently). Canonicl (Ubuntu) chose to go with LibreOffice before Oracle decided to give it away.

The Software Center (just looked) does not offer OpenOffice, but only a transitional package to migrate past Ubuntu dists with Oo.org to LibreOffice.

*.deb files, including those from oo.org and other locations, can indeed be installed via diverse package managers, but these packages are not maintained (updated/upgraded) by Canonical for bug fixes or security updates, etc., as are the Canonical-maintained packages.

Also, such external packages may have different dependencies and dependents, which could result in additional files being required, or conflicts being created.

Good luck!

---

