---
title: "Installing Java (errors)"
date: 2009-09-20
forum: General Help
---

### Post by ARom on 2009-09-20
I tried to install Java with:

sudo apt-get install sun-java6-jdk

Everything went fine until the terminal popped back up with a blue page with what looked like a terms of conditions notice, the only problem is that I couldn't click ok. I tried clicking ok at the bottom and enter repeatedly, but the screen just stayed the same, all it let me do was scroll.

Eventually I closed the terminal and I don't think it is installed properly.

Now when I try to re-install I get:
[B]
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"[/B]

How do I install Java 6 properly now?

Java command is still not found in the terminal.

---

### Post by ARom on 2009-09-20
How do I fix the broken package: 

sun-java6-jre
Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)

Synaptic Package Manager won't let me remove it, I get an error:
[B]
E: sun-java6-jre: Package is in a very bad inconsistent state - you should
[/B]

---

### Post by ARom on 2009-09-20
ok, this worked to get me to the configuring sun-java6.bin page again:

> Open System &#8594; Administration &#8594; Software sources &#8594; [ Tab Ubuntu software ]
enable "Software restricted by copyright or legal issue ( multiverse )"
Close and confirm the repository reload.

Then open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:

sudo aptitude update
sudo apt-get upgrade
sudo aptitude install sun-java6-jre sun-java6-plugin



Now if only it'll let me accept...

---

### Post by ibuclaw on 2009-09-20
> **ARom said:**
> How do I fix the broken package: 

sun-java6-jre
Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)

Synaptic Package Manager won't let me remove it, I get an error:
[B]
E: sun-java6-jre: Package is in a very bad inconsistent state - you should
[/B]

To fix:
```
sudo apt-get install -f
```

If it continues with the installation, and you are prompted to accept the license again, press** TAB **to switch from scrollbar to command box then **ENTER** to continue.

Regards
Iain

---

### Post by ARom on 2009-09-20
Tab + enter to accept

---

