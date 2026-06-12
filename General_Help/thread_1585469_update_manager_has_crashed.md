---
title: "update manager has crashed"
date: 2010-09-30
forum: General Help
---

### Post by percyhahn on 2010-09-30
i tried to load update manager, but a red circle with a line through it appeared next to my wireless signal bit, with the following code

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

  then a grey shap appears next to it, saying report it to ubuntu, but when i press ok, it says it cant find the error to report. i upgraded to ubuntu 10.10 the other day just for the record

   ps sorry if in wrong section, im new here :p

---

### Post by robsoles on 2010-09-30
What do you get if you try to update via terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

If that runs through with non-critical errors then try to open update manager again and let us know result.

---

### Post by percyhahn on 2010-10-01
when i typed in terminal sudo apt-get update, it did it, i think, this come up at the end though.
  W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

   when i typed sudo apt-get upgrade, this come up

   peter@peter-laptop:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$ 

   the red error sign at the top of the screen is there permanently now from when i switch on. im not worried about it or anything, but it will probably need sorting.
   when trying to run update manager, it still wont load up.

---

### Post by Soul-Sing on 2010-10-01
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by percyhahn on 2010-10-01
when i paste that in, or type it in myself, it doesnt do anything


peter@peter-laptop:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
peter@peter-laptop:~$

---

### Post by sikander3786 on 2010-10-01
> **percyhahn said:**
> when i paste that in, or type it in myself, it doesnt do anything


peter@peter-laptop:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
peter@peter-laptop:~$
Did you try sudo apt-get update after that command?

---

### Post by percyhahn on 2010-10-01
> **sikander3786 said:**
> Did you try sudo apt-get update after that command?

  that might help! sorry!
   i typed in after, but still no joy. terminal cam back with this, after alot of updates
Fetched 12.7MB in 23s (545kB/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Soul-Sing on 2010-10-01
> W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz](http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz) 404 Not Found

no broken -apt/dpkg, but a server error from an added PPA

---

### Post by sikander3786 on 2010-10-01
> **leoquant said:**
> no broken -apt/dpkg, but a server error from an added PPA
Yes. Go to System > Administration > Software Sources, Other SOftware tab and deselect the offending ppas and again try to update. It should work this time.

---

### Post by percyhahn on 2010-10-02
iv had a look in system>software sources, and everywhere else i can on ubuntu, but i cant sem to find software sources. 
    can it be booted from terminal?

---

### Post by percyhahn on 2010-10-02
looking at the url's it couldnt find, they were both from xbmc. i tired installing xbmc the other day, and was partially successful, but it couldnt then install xbmc main file itself fr some reason, so i left it. could that cause this problem?
 [http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz")  404  Not Found

  [http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz")  404  Not Found

---

### Post by robsoles on 2010-10-02
> **percyhahn said:**
> looking at the url's it couldnt find, they were both from xbmc. i tired installing xbmc the other day, and was partially successful, but it couldnt then install xbmc main file itself fr some reason, so i left it. could that cause this problem?
 [http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz")  404  Not Found

  [http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz")  404  Not Found

Yes.

> **percyhahn said:**
> iv had a look in system>software sources,  and everywhere else i can on ubuntu, but i cant sem to find software  sources. 
    can it be booted from terminal?

'System'->'Adminstration'->'Software Sources' should have it, other wise```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
``` should open it.

---

### Post by percyhahn on 2010-10-02
SOLVED
   thanks for your help everyone :)

---

