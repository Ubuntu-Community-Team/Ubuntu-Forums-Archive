---
title: "Help! I messed up my sources list!"
date: 2009-11-08
forum: General Help
---

### Post by Enriquecaribe on 2009-11-08
While trying to install epsxe on ubuntu 9.04 I managed to destroy my app list. Everytime I click on a .deb file I get this message:

**This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.**

After I do what it says, its says "permission denied" in the first code.
When I click on the Synaptic Manager it reads:

[B]E: Malformed line 60 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/B]
And nothing still is fixed. I tried to google some of the lines but no progress. Can someone please help me fix my software sources?

---

### Post by drs305 on 2009-11-08
Open up sources.list for editing and look at line 60. If you don't recognize the error, post the contents:
```

gksu gedit +60 /etc/apt/sources.list

```

This will open up the editor on line 60. All lines in source.list should start with either "deb" or "#", which may help you recognize the error.

You can generate a new sources.list from this link if necessary:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by Enriquecaribe on 2009-11-08
> **drs305 said:**
> Open up sources.list for editing and look at line 60. If you don't recognize the error, post the contents:
```

gksu gedit +60 /etc/apt/sources.list

```

This will open up the editor on line 60. All lines in source.list should start with either "deb" or "#", which may help you recognize the error.

You can generate a new sources.list from this link if necessary:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

Whoa that was fast! THANK YOU SOO MUCH! That code you gave me allowed me to open the list and delete line 60 (which was named "gutsy" at the end of the line. I just deleted the line and every thing worked. THANKS SOO MUCH!! I TRULY APPRECIATE IT!!! A LOT!!!

---

