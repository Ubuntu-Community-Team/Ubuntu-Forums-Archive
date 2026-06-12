---
title: "how to check installed versions of apps from command line"
date: 2010-09-08
forum: General Help
---

### Post by shanep-server on 2010-09-08
Like i'm curious what version of wine i have installed...

What are my current ati drivers installed...

If wine isn't 1.2 or 1.3 how do i update it from command line?

really any insight into this process would help its not absolutely critical to know but i've been looking around and haven't found information that really helps me. If someones kind enough to try and clue me in on this i would be greatly appreciative.

Or some references to good articles to become a command line guru would be cool as well. Maybe something you found useful.:p

---

### Post by dirghrabadia on 2010-09-08
In the terminal:
```

*application* -version

```

---

### Post by shanep-server on 2010-09-08
:~$ wine -version
wine: cannot find L"C:\\windows\\system32\\-version.exe"

:~$ ati - version
No command 'ati' found, did you mean:

etc...

---

### Post by garvinrick4 on 2010-09-08
[LIST]
[*]```
sudo dpkg --get-selections > 	installedsoftware
```
[*]```
aptitude show wine
```
[/LIST]
First piece of code will give you copy of all your installed packages in Places to Home folder
in their true package name.

Second piece of code
Will show you what it is, where it is and version installed or if not installed.

---

### Post by shanep-server on 2010-09-08
shane@Lucid:~$ aptitude show wine
Package: wine
State: installed
Automatically installed: no
Version: 1.1.42-0ubuntu4
Priority: optional
Section: universe/otherosfs
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 65.5k
Depends: wine1.2
Provided by: wine1.2
Description: Microsoft Windows Compatibility Layer (dummy package)
 This package is to ease upgrades for users of earlier Wine packages. It can be
 safely removed.
Homepage: [http://www.winehq.org/](http://www.winehq.org/)

Version: 1.1.42-0ubuntu4 - does that mean i'm running 1.1.42 wine?

Down farther it says Depends: wine1.2 and Provided by: wine1.2

How would i upgrade to wine 1.2 or 1.3 from terminal?

---

### Post by Achilles124 on 2010-09-08
[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

Read the page

---

### Post by shanep-server on 2010-09-08
thank you :)

---

### Post by garvinrick4 on 2010-09-08
> **shanep-server said:**
> thank you :) In due time the ubuntu repositories do get the next upgrade of packages. The aptitude show (package) does
show what repository it is in. But as the gentlemen said in previous you can go to source and get the next version or a ppa for your repository. I seem to like to let Ubuntu do their thing and then get normal upgrades in their due time. Every one has their own preferences and it is nice to have that option.

---

### Post by inameiname on 2010-09-08
I prefer 'sudo apt-cache policy'.

sudo apt-cache policy tvtime
[sudo] password for me: 
tvtime:
  Installed: 1.0.2-6.1ubuntu1
  Candidate: 1.0.2-6.1ubuntu1
  Version table:
 *** 1.0.2-6.1ubuntu1 0
        100 /var/lib/dpkg/status
     1.0.2-5ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages

---

