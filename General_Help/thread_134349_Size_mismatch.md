---
title: "Size mismatch"
date: 2006-02-21
forum: General Help
---

### Post by glave on 2006-02-21
How many people are having size mismatch errors right now? I've been trying to insall python-dev all day, and each time I search the forums, and I'm finding more and more very recent posts about other people having problems.

Is there a possible problem with the repositories?

---

### Post by Strike&gt;&gt; on 2006-02-21
yeah, happened to me too, had to do with installing libs that where needed for ati driver:

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base 

and it gave me miss match errors, but that was because i replace my sources.list with another one, recommended by the site, but as soon as i replaced the list with my own  sources.list(thank god i saved it), and it installed the files, without an error!

Strange indeed.

this was the site:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by glave on 2006-02-21
Mine isn't quite so happy of an ending. I changed my sources to the original listed in the wiki, and still no luck. I've done clean, update, upgrade, etc...

---

### Post by loafula on 2006-02-21
i'm having the same problem on x86_64.. size mismatch errors when updating my packages.  anyone out there got ideas?

---

### Post by Connollyir on 2006-02-21
Its strange..... only the KDE apps seem to be having issues for me...... I can download and install a ton of other stuff but nothing from Kdesktop. Bad timing since  I've been trying to install the Kdesktop all day long.

-Ian

---

### Post by az_human on 2006-02-21
I was having the size mismatch problem trying to download php4-ldap earlier.

---

### Post by Connollyir on 2006-02-21
Well I'm pretty sure this is a problem with the repository servers that we are just going to have to wait till they fix it. I wonder if they were updating and something broke? At any rate, just stating the obvious.

-Ian

---

### Post by Dougga on 2007-04-14
I've installed and reinstalled Ubuntu over the past month with two different versions  from several different repositories.  

Very much like Microsoft error reporting, I think the "size mismatch" error is too common to be related to broken repositories.  Unless most every repository on earth is broken - which would put the viability of Ubuntu in doubt altogether.

I'm beginning to suspect that there is a protocol problem with the apt-get functionality.  

In assessing Ubuntu as a platform, I'd have to say it's not ready for prime time (the datacenter) based upon the quality of this most critical feature.  This is still a toy for the enthusiast-engineer.  I'll still run it for fun, but I'd be curious to know how many engineers are willing to stake their reputations on it.

What do you all think?
:guitar:

---

