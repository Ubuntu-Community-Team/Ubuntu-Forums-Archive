---
title: "remove residual config packages/files from the command line"
date: 2009-09-04
forum: General Help
---

### Post by pythonscript on 2009-09-04
In synaptic, there's an option in the package manager to mark residual config files/packages for complete removal, and I'm wondering how to do this from the command line. I ran 

```
sudo deborphan | xargs sudo apt-get purge -y
sudo apt-get autoremove -y
sudo apt-get clean
``` but some packages still show up in synaptic, so clearly, these commands aren't removing everything. My main laptop runs a command line ubuntu interface with icewm on top, so I primarily use the command line, and I'd like to know how to remove residual config packages from the command line. Maybe something using dpkg -l to search for packages labeled "rc?" Thanks!

---

### Post by sahabcse on 2009-09-04
Hi

For complete removal

sudo apt-get purge packagename


more [info]("http://ubuntulinux.co.in/package-installation-over-command-propmpt.php")

---

### Post by pythonscript on 2009-09-04
I know about apt-get purge, but what if I don't remember what the packages are? When I looked in synaptic in gnome, there were packages from a while back that still had config files left all over my system, so is there a way from the command line to run purge for all packages that have already been installed? Thanks!

---

### Post by sahabcse on 2009-09-04
this may be help

[http://www.debian-administration.org/article/An_introduction_to_Debian_packages](http://www.debian-administration.org/article/An_introduction_to_Debian_packages).

---

### Post by pythonscript on 2009-09-04
Let me rephrase my question... How can I use "dpkg -l" or "dpkg-query" so it will only show the output of packages labeled as "rc?" (As opposed to those labeled "ii" etc). Thanks!

---

### Post by unutbu on 2009-09-04
Maybe this will do?
```
dpkg-query -W -f='${Package}\t${Status}\n' | awk '/deinstall/{print $1}'
```

---

### Post by oldos2er on 2009-09-04
The CLI equivalent of Synaptic is aptitude. Run **sudo aptitude** in a terminal. More info here: [http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)
It's a few years old, but the commands are still the same.

---

### Post by pythonscript on 2009-09-04
> **unutbu said:**
> Maybe this will do?
```
dpkg-query -W -f='${Package}\t${Status}\n' | awk '/deinstall/{print $1}'
```

Thank you! I really appreciate the help!

---

### Post by geirha on 2009-09-04
```
aptitude search '~c'
``` will show you uninstalled packages that still have configuration around. With the -F option you can have it only print the package name (%p)
```
aptitude -F %p search '~c'
```
See the aptitude readme for more; /usr/share/doc/aptitude/README

---

### Post by pythonscript on 2009-09-04
To save space in on my laptop, I've actually uninstalled aptitude... because I tend to use apt-get. Once I get back to my apartment, I'll check to see if similar commands apply. Thanks for the help!

---

### Post by oldos2er on 2009-09-04
> **pythonscript said:**
> To save space in on my laptop, I've actually uninstalled aptitude... 

 Ouch. apt-get is not a stand-alone program like aptitude is.

---

### Post by pythonscript on 2009-09-04
> Ouch. apt-get is not a stand-alone program like aptitude is.

Is it possible to completely remove apt-get and simply use aptitude, instead? Are they both equally powerful? Out of curiosity, why does canonical include both by default in ubuntu?

---

### Post by oldos2er on 2009-09-04
> **pythonscript said:**
> Is it possible to completely remove apt-get and simply use aptitude, instead? Are they both equally powerful? Out of curiosity, why does canonical include both by default in ubuntu?

 I'm not a dev, so I can't really answer your questions, sorry.

 My opinion as a home desktop user is that aptitude is more powerful than apt-get, but I am certainly not all-knowledgable about the subject.

---

### Post by pythonscript on 2009-09-05
That's settled, then. Thanks for the help everyone!

---

### Post by afrodeity on 2010-10-29
This is interesting, although there is probably a safer method out there.

[http://www.johnlewis.ie/remove-residual-config-files-in-ubuntu-a-one-liner/](http://www.johnlewis.ie/remove-residual-config-files-in-ubuntu-a-one-liner/)

---

