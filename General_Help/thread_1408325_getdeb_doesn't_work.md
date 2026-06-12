---
title: "getdeb doesn't work"
date: 2010-02-16
forum: General Help
---

### Post by Objekt on 2010-02-16
I would like to install some of the apps at getdeb.net ([http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)), for example, Acetone ISO ([http://www.getdeb.net/updates/Ubuntu/9.10/?q=acetone](http://www.getdeb.net/updates/Ubuntu/9.10/?q=acetone)).

However, I can't make it work.  I tried to follow their instructions here but when clicking their "Install this now" links, Firefox pops up an error dialog with the message, ```
Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program.
```

I do have the apturl package installed, pretty sure it was in there (Ubuntu 9.10 64-bit) by default.  Likewise firefox-support-gnome and firefox-3.5-gnome-support packages.

FWIW, I installed Firefox using Ubuntuzilla and am using version 3.6.  In searching for fixes, I found references to people getting this error when using versions of Firefox not installed from the default repositories.  However, I also found instructions for manually adding the apt protocol to Firefox in the about:config page, which I did.  Still can't use the getdeb install links.

---

### Post by Jackzor on 2010-02-16
Google Chrome works perfect :P

---

### Post by Objekt on 2010-02-16
Not a solution, as I was asking about Firefox.

Chrome doesn't work either, FWIW.  While I get a little farther than with Firefox, I still get an error dialog titled "APT simple frontend" with the message "Invalid package name."

I was finally able to install Acetone ISO by simply doing it at the command line:
```
sudo apt-get install acetoneiso
```

But I would really like to have the "Install this now" links work.

---

### Post by bowens44 on 2010-02-16
> **Objekt said:**
> Not a solution, as I was asking about Firefox.

Chrome doesn't work either, FWIW.  While I get a little farther than with Firefox, I still get an error dialog titled "APT simple frontend" with the message "Invalid package name."

I was finally able to install Acetone ISO by simply doing it at the command line:
```
sudo apt-get install acetoneiso
```

But I would really like to have the "Install this now" links work.

Do you have apt-url (or maybe it's apturl) installed?

---

### Post by Objekt on 2010-02-16
> **Objekt said:**
> 
I do have the apturl package installed, pretty sure it was in there (Ubuntu 9.10 64-bit) by default.  Likewise firefox-support-gnome and firefox-3.5-gnome-support packages.

Obligatory text to avoid the "short message" filter.

---

### Post by Swagman on 2010-02-16
did you install the key ?

---

### Post by Objekt on 2010-02-16
Yes.  At least twice.  I manually added the getdeb repository to my software sources and added their key.  I also ran their downloadable .deb package.  Clearly something is missing, but I don't know what it could be.

---

### Post by Swagman on 2010-02-16
Do you have noScript blocking it ?

---

### Post by howefield on 2010-02-16
Is this specific to the getdeb website or is it a global issue you have with all debs you download from other sites ?

---

### Post by Objekt on 2010-02-16
> **howefield said:**
> Is this specific to the getdeb website or is it a global issue you have with all debs you download from other sites ?

Seems to be specific to getdeb.  Downloaded .deb files do work.

---

### Post by howefield on 2010-02-16
> **Objekt said:**
> Seems to be specific to getdeb.  Downloaded .deb files do work.

So maybe it's not your problem ?

---

### Post by vnt87 on 2010-03-17
This thread is a bit old, but I ran into the same problem (apt protocol not recognized by Firefox). I followed the instruction for FF3 here and it seems to work now:

[https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)

---

### Post by Objekt on 2010-03-18
I followed those instructions a while ago, but it still doesn't work.  I get the "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program." alert.

---

### Post by didizingo on 2010-03-26
> I followed those instructions a while ago, but it still doesn't work. I get the "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program." alert.Hi Objekt.
Try to install this package: "firefox-3.5-gnome-support", as it's said in this link: [http://getsatisfaction.com/allmyapps/topics/protocol_apt_and_firefox_3_5](http://getsatisfaction.com/allmyapps/topics/protocol_apt_and_firefox_3_5)

And, "Don't forget to enable 'Remember my choice' and validate."

It worked for me (though I use kubuntu 9.10).
Good luck!

---

### Post by Objekt on 2010-03-27
I've had that package installed for a while.  getdeb still doesn't work.

This is ridiculous.  I'm going to either file a Bugzilla report (I can't believe there isn't one already about this!), or switch browsers, or perhaps both.  I've stuck with Firefox for a long time because of all the nifty add-ons, but maybe it's time to switch.  I can't even open downloaded files or the containing folder from the "Downloads" window.  Too many simple things that SHOULD work are broken.

---

### Post by mealstrom on 2010-04-28
You should install getdep first.

---

### Post by Objekt on 2010-05-03
> **mealstrom said:**
> You should install getdep first.

Can't.  It's not in the repositories and no one offers a .deb package.

---

### Post by mealstrom on 2010-06-06
> **Objekt said:**
> Can't.  It's not in the repositories and no one offers a .deb package.
wget -q -O - [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
sudo sh -c 'echo "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'

---

### Post by Objekt on 2010-06-06
> **mealstrom said:**
> wget -q -O - [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
sudo sh -c 'echo "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'

Sigh.  As I suspected, you meant getde**b**, not getde**p**.  But there is a package called "getdep," which is indeed not in the repositories - and apparently, not relevant to this discussion.

I ran the command you suggest long ago.  The getdeb website seems to be down now, so I can't tell whether it's fixed yet.

---

