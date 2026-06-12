---
title: "cannot update to firefox 3.6"
date: 2010-07-02
forum: General Help
---

### Post by capo1949 on 2010-07-02
hi
I am using ubuntu karmic, 9.10

I  am trying to update to Firefox 3.6, using the following commands

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update

Exiting firefox closed before final command

graham@graham-laptop:~$ sudo apt-get install firefox-3.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
graham@graham-laptop:~$ 

I find the browser is still 3.5.9

Checking the /etc/bin file there are 2 entries, one being firefox and the other firefox-3.5

Some help would be appreciated****

---

### Post by warfacegod on 2010-07-02
Try:

```
sudo firefox &
```

And have Firefox check for updates under the help menu.

---

### Post by khelben1979 on 2010-07-02
> **warfacegod said:**
> Try:

```
sudo firefox &
```

And have Firefox check for updates under the help menu.

I would not recommend to start the web browser with root permissions.

---

### Post by Rubi1200 on 2010-07-02
> **khelben1979 said:**
> I would not recommend to start the web browser with root permissions.

+1 

and the devs are porting the new FF version to Karmic "soon." Can't you wait a bit?

Just found the link:

[http://ubuntuforums.org/showpost.php?p=9529064&postcount=5](http://ubuntuforums.org/showpost.php?p=9529064&postcount=5)

---

### Post by capo1949 on 2010-07-02
thanks your input both tried
sudo firefox &
 [1] 5905
there was no mention of updates under help menu.

Yes no great rush i can wait a week or so

---

### Post by warfacegod on 2010-07-02
Normally I don't recommend opening browsers as root either but if no real browsing is being done and it's only for a few minutes then the risk is extremely low.

I'd forgotten that ```
sudo firefox &
``` is the preferred way to update through the ubuntuzilla package. At least it was the last time I bothered to used it.

Various versions of 3.6 have been available for Karmic for months. I see no reason to believe that 3.6.6 is going to magically install itself if capo1949 is still on 3.5.

@capo1949 Try going to: System> Admin.> Software Sources> Updates tab> enable Unsupported Updates (Karmic-backports)> click Close> click Reload.

Then run Update Manager.

---

### Post by Oolongtea on 2010-07-02
```
sudo apt-get install firefox-3.6
```

---

### Post by nanotube on 2010-07-02
> **warfacegod said:**
> 
I'd forgotten that ```
sudo firefox &
``` is the preferred way to update through the ubuntuzilla package. At least it was the last time I bothered to used it.


just fyi: it's been a long time since that was the case. ubuntuzilla is now a ppa repo containing mozilla builds. as always, see site for latest details. ;)

---

### Post by capo1949 on 2010-07-02
Solved thx all for your help.
A little aside, I originally updated with agt-get update,
but it was when I run update manager that did the trick,, I thought they were the same?

---

### Post by lovinglinux on 2010-07-02
> **warfacegod said:**
> Try:

```
sudo firefox &
```

And have Firefox check for updates under the help menu.

You should NEVER use sudo with Firefox. If you really want to enable the built in Firefox update, which I do not recommend, then you need to use gksudo instead. When using sudo you lose ownership of ~/.mozilla directory and screw up your Firefox user profile.

> **capo1949 said:**
> thanks your input both tried
sudo firefox &
 [1] 5905
there was no mention of updates under help menu.

Yes no great rush i can wait a week or so

You need to fix your Firefox profile ownership because of that, otherwise Firefox will not work properly. See the first item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

For future reference see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

---

