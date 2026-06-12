---
title: "update manager"
date: 2011-07-14
forum: General Help
---

### Post by nick_:D on 2011-07-14
hello i need some help with my update manger i think i messt it up by downloading a old software source from ubuntu software center because i dint have software sources in administration so i seen the 2 in ubuntu software center so i downloaded it now my update don't work or sptynaic don't work either and i get errors for both.

here is the error 

could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 50 in source list /etc/apt/sources.list (dist parse)'

plz help me =[

---

### Post by nick_:D on 2011-07-15
bump. ](*,)

---

### Post by 3rdalbum on 2011-07-15
There's a line in the file "/etc/apt/sources.list" that is incorrect. It's line 50 of this file. If you have recently modified this file, reverse the modifications you've made and then run 'sudo apt-get update'.

Open the /etc/apt/sources.list file like so:

```
gksudo gedit /etc/apt/sources.list
```

And remove whatever it is at line 50 that is wrong; it's usually the thing that looks out of place and not like the other lines.

---

### Post by nick_:D on 2011-07-15
E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
this error is from synaptic manger 
how do i fix this the code you sent me i looked and see what i could added and see what i added still doing the same thing 48 instead of 50

---

### Post by alphacrucis2 on 2011-07-15
> **nick_:D said:**
> E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
this error is from synaptic manger 
how do i fix this the code you sent me i looked and see what i could added and see what i added still doing the same thing 48 instead of 50

Paste the output of:

```
cat /etc/apt/sources.list
```

---

### Post by sikander3786 on 2011-07-15
Posting the outputs as requested above and troubleshooting the problem step-by-step would be better.

But for a faster approach, you can just genenrate a new sources.list and replace your existing one to get rid of those errors as there might be more than 1 of those malformed entries in your sources.list. Take a look here:

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

---

### Post by raja.genupula on 2011-07-15
how deleting all these sources and placing new sources sounds ?

             try this 


sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

---

### Post by nick_:D on 2011-07-15
omg! thank you! guys for the help works now =D :popcorn:

---

