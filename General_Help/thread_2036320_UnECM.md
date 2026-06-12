---
title: "UnECM"
date: 2012-08-01
forum: General Help
---

### Post by Kodeine on 2012-08-01
Salutations!

So I have some ECM compressed files and I'm wanting to uncompress them. After googling it appears I must install the ecm package (available from the repos) and use the unecm tool to do so. However after installing the package it says that command can't be found? I've went to the ECM website where it's available in a command line utility pack for all operating systems under the sun. Mac, Windows and even DOS. But not Linux. I did use the dos version with dosbox but surely there is a native linux build of ECM?

---

### Post by Kodeine on 2012-08-02
Bumpzies!

---

### Post by mr_luksom on 2012-09-22
Hi,

I have just come across the same problem. You need to compile unecm yourself, there is something wrong with the package.

1. First download the source for 'Command Line Tools' from here: [http://www.neillcorlett.com/ecm/](http://www.neillcorlett.com/ecm/)

2. Then you want to uncompress the archive, and find a file in the src directory called ecm.c, and compile using this command:

```
 gcc ecm.c 
```

If this command doesn't work, you will need to install build-essentials (try elsewhere on this forum).

3. Move the compile executable a.out to to the /usr/bin directory:

```
 sudo cp ~/'Wherever you unzipped it'/cmdpack-1.03-src/src/a.out /usr/bin/unecm 
```

Then you can use it.

---

