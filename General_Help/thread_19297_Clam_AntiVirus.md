---
title: "Clam AntiVirus"
date: 2005-03-11
forum: General Help
---

### Post by ohman11 on 2005-03-11
I installed this with Synaptic and I cant figure out how to run it. I want to update it also....any ideas?

---

### Post by Slapdash on 2005-03-11
try this ( Its just a guess btw )

press CNTRL + F2 ( opens up the run command )
Type Clamav or clam or clam-av

See if you get anything....

---

### Post by nocturn on 2005-03-11
Clam is console bosed, to open a CLI (terminal).

I think the command is clamscan.

There are some GUI frontends for it, you can check freshmeat.net or google if you like.

---

### Post by ohman11 on 2005-03-11
[QUOTE=nocturn]Clam is console bosed, to open a CLI (terminal).

I think the command is clamscan.

There are some GUI frontends for it, you can check freshmeat.net or google if you like.[/QUOTE]

clamscan did it but it just scanned the Home dir. I will look around and see if I can find out how to make it scan the whole drive. Thanks!

---

### Post by nocturn on 2005-03-11
[QUOTE=ohman11]clamscan did it but it just scanned the Home dir. I will look around and see if I can find out how to make it scan the whole drive. Thanks![/QUOTE]

clamscan takes as parameter the location to scan.  I think -r tells it to recurse, so
```

clamscan -r /

```

should scan your entire system.

---

### Post by jsgotangco on 2005-03-11
*clamscan* is the command to start scanning.

*freshclam* is the comman to update your AV patterns. You can set freshclam as a daemon process to update everyday.

---

### Post by Ozitraveller on 2005-03-12
[QUOTE=jsgotangco]*clamscan* is the command to start scanning.

*freshclam* is the comman to update your AV patterns. You can set freshclam as a daemon process to update everyday.[/QUOTE]

I've been using Vet for windows, and am used to it keeping itself up-to-date. How do you get ClamAv to keep itself up-up-date?

I found these on the ClamAV site:

 Debian

    * The Debian package is maintained by Stephen Gran. ClamAV has been officially included in the Debian distribution starting from the sarge release. Run apt-cache search clamav to find the name of the packages available for installation. Unofficial packages for woody and sarge are available. They are usually more recent than official ones. Add the following lines to your /etc/apt/sources.list:

      stable/woody (i386):
      deb [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) woody main
      deb-src [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) woody main
      testing/sarge (i386):
      deb [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) sarge main
      deb-src [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) sarge main
      Feel free to search for clamav on [http://www.apt-get.org](http://www.apt-get.org) too.

Is this recommended or should I wait for the respositories to be updated?

I've finally got my sources.list updated, and install the latest version of ClamAV. Yeah!!

Is there a worthwhile frontend for CmalAV?

---

### Post by picturesqueweb on 2005-03-13
I run the following at the command line

clamscan -r --bell --mbox -i /

This gives me a list of only files that contain viruses, makes a noise when one is found and scans everything. At least I assume it will make a noise....I'm not willing to try it out if you know what I mean.

---

### Post by jdodson on 2005-03-14
do not post questions to the how to section.  please check forum area rules before posting.

---

