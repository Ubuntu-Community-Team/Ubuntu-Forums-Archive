---
title: "Can't update mozilla (ubuntuzilla)"
date: 2009-08-05
forum: General Help
---

### Post by metalmakker on 2009-08-05
I've downloaded ubuntuzilla-4.7.1-0buntu1-i386.deb. Opened it with GDebi, but it stopped because of an error: wrong architecture 'i386'. (translated from Dutch, but it should make sense).
I want my Firefox to be up to date on my laptop, so what to do?

---

### Post by t4ggs on 2009-08-05
open synaptic and search for firefox and install 3.5

---

### Post by nanotube on 2009-08-05
> **metalmakker said:**
> I've downloaded ubuntuzilla-4.7.1-0buntu1-i386.deb. Opened it with GDebi, but it stopped because of an error: wrong architecture 'i386'. (translated from Dutch, but it should make sense).
I want my Firefox to be up to date on my laptop, so what to do?

you downloaded the wrong architecture - get the amd64.deb (when on project summary page, click "view all files" and you'll see it).

that said, there are some problems with plugins when using the mozilla build (a 32bit build) on 64bit systems, so unless you really want the mozilla build, and are willing to take time to manually install some plugins, you're better off going with the firefox PPA repository, or grabbing the beta-version of firefox3.5 from the official repositories.

see [http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion) for alternative methods of getting ff3.5

---

### Post by metalmakker on 2009-08-06
thansk, i'll check it out. Been using Ubuntu for a few days now, so it's still very new to me...

---

### Post by burmanabhay88 on 2009-08-06
> **t4ggs said:**
> open synaptic and search for firefox and install 3.5

i had been facing the same problem. i downloaded the tar.gz and manually installed it. I guess synaptic would have been a better option.

---

### Post by metalmakker on 2009-08-06
Are the plugins you are referring to plugins liike the one that makes Last.fm radio play? Because that isn't working... how do i find out what I need for that?

---

### Post by nanotube on 2009-08-06
> **metalmakker said:**
> Are the plugins you are referring to plugins liike the one that makes Last.fm radio play? Because that isn't working... how do i find out what I need for that?

don't know what the last.fm plugin is... but if it's a plugin rather than an add-on, then yes, that's what i'm referring to. :) 

if it's an addon, then it should be architecture-independent...

---

