---
title: "apt-get won't recognise openoffice"
date: 2009-07-27
forum: General Help
---

### Post by geekpie on 2009-07-27
I am trying to install openoffice.org on intrepid.

I have added the following line to my sources.list as instructed in numerous places:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

I then ran apt-get update.  No errors.

I then ran sudo apt-get install openoffice

but got 

E: Couldn't find package openoffice

Thanks for any advice.

---

### Post by t4thfavor on 2009-07-27
type
```

sudo apt-get install openoffice 

```
then hit tab tab to see the list of pachages with openofice in the name, I bet your just typing it incorrectly.

---

### Post by geekpie on 2009-07-27
no completion is done when I hit tab.  The cursor doesn't move.

---

### Post by t4thfavor on 2009-07-27
```

sudo apt-get install openoffice.org
Display all 555 possibilities? (y or n)

```

I got lots of em, perhaps you mistyped the repo? 

Note: I did not enable that third party repo, this is just what is in the standard jaunty repos.

---

### Post by geekpie on 2009-07-27
I don't think openoffice is in the standard intrepid repos.

My 
/etc/apt/sources.list.d/openoffice.sources.list 
has the following single line:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

which seems to be a good URL:  it works in a browser.

When I run sudo apt-get update

I don't see any mention of this repo though.

---

### Post by t4thfavor on 2009-07-27
Have you seen this thread

[http://ubuntuforums.org/showthread.php?t=945174](http://ubuntuforums.org/showthread.php?t=945174)

They also mention backports.

---

### Post by geekpie on 2009-07-28
Thanks for all your advice t4thfavor.

I finally got it to install.  I did 2 things;  not sure if the first was necessary.

1.  added 
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

to /etc/apt/sources.list.d/openoffice.sources.list

but not sure why I would need to tell apt-get where the source files are?

2.  entered sudo apt-get install openoffice.org 
instead of 
sudo apt-get install openoffice
but why wasn't tab autocomplete doing this for me?

any retrospective advice very welcome.

---

