---
title: "Ubuntu Software Center: Failed to download package file"
date: 2011-11-22
forum: General Help
---

### Post by Cfoobs on 2011-11-22
Hi,

I'm new to Ubuntu and I've just started using version 11.10 (64bit). Everything is working great so far, except whenever I use the Ubuntu Software Centre, whatever I try to download and install it says "Failed to download package file" and that I should check my internet connection (which is fine).

Some help with this would be much appreciated.

---

### Post by jerrrys on 2011-11-24
try this.  open a terminal and enter:

sudo apt-get update

then try the software center, also watch for error messages

---

### Post by Cfoobs on 2011-11-24
I did what you said and it works fine now. Thanks very much for the help. :)

---

### Post by sirvinniei on 2011-11-24
> **Cfoobs said:**
> I did what you said and it works fine now. Thanks very much for the help. :)
please mark a thread as solved when it&#347; solved, that gives others a bigeer chance to get their problems solved

---

### Post by torontopronto on 2011-11-24
Hi I'm relatively new to the Ubuntu Forum.  I followed the post of that was given here to get my webcam to work on skype.  Yep I was impressed, my webcam works on skype and all is well.

BUT !!! Now I cannot open the Ubuntu Software Centre.

I ran a the command: sudo apt-get update
and my terminal responded with:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of source could not be read.

Can someone please help...!!!:(

---

### Post by mutley89 on 2011-11-25
> **torontopronto said:**
> Hi I'm relatively new to the Ubuntu Forum.  I followed the post of that was given here to get my webcam to work on skype.  Yep I was impressed, my webcam works on skype and all is well.

BUT !!! Now I cannot open the Ubuntu Software Centre.

I ran a the command: sudo apt-get update
and my terminal responded with:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of source could not be read.

Can someone please help...!!!:(

Post /etc/apt/sources.list, so that we can see what the error is.

---

### Post by jerrrys on 2011-11-25
> **Cfoobs said:**
> I did what you said and it works fine now. Thanks very much for the help. :)

your welcome

@torontopronto:  open a terminal and enter

sudo gedit /etc/apt/sources.list

and please post

---

### Post by oldtimer7777 on 2011-11-25
New users should always use a walkthrough or guide when they first start using Ubuntu like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It helps get everything just right and gives you a good idea how everything works too..

> **torontopronto said:**
> Hi I'm relatively new to the Ubuntu Forum.  I followed the post of that was given here to get my webcam to work on skype.  Yep I was impressed, my webcam works on skype and all is well.

BUT !!! Now I cannot open the Ubuntu Software Centre.

I ran a the command: sudo apt-get update
and my terminal responded with:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of source could not be read.

Can someone please help...!!!:(

---

### Post by Omegabyte on 2011-11-30
I am having the same problem with my Software Center.  It keeps saying "**Failed to dowload package files**. Check your internet connection" and I know my internet connection is good, I'm using it right now. 
When I type "apt-get update" into terminal it prints:

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any help?

---

### Post by mutley89 on 2011-11-30
Run apt-get as root:
```

sudo apt-get update

```

---

