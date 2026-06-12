---
title: "use of IE on Ubuntu computer"
date: 2011-02-13
forum: General Help
---

### Post by wpshooter on 2011-02-13
I need to be able to use IE on my home based Ubuntu computer so I can get to and use the Prosystem Global FX tax program which will ONLY work with IE.

Is there a version of IE 6.0 or greater that I can safely install on Ubuntu computer and will not interfere with my use of Firefox for other applications, etc. ?

Thanks.

---

### Post by An Sanct on 2011-02-13
Wine actually has a "Wine Internet Explorer", but I would recommend that you set up a virtual machine, that will be 100% IE

Also it is able to run the original IE -> [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

---

### Post by An Sanct on 2011-02-13
A quick installation guide can be found [here]("http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html").

---

### Post by Frogs Hair on 2011-02-13
This works for some users with Firefox . [https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/)

---

### Post by wpshooter on 2011-02-14
> **An Sanct said:**
> Wine actually has a "Wine Internet Explorer", but I would recommend that you set up a virtual machine, that will be 100% IE

Also it is able to run the original IE -> [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

Am I correct in assuming that this means that I would have to have the legal rights to a M/S windows O/S in order to run Windows from within the Ubuntu O/S ?

Which I don't have and if I did, why would I not just install M/S on a/the computer and then run Prosystem from the M/S windows/IE computer ?

Thanks.

---

### Post by wpshooter on 2011-02-14
> **An Sanct said:**
> A quick installation guide can be found [here]("http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html").

I tried this and it worked fine until I got to the point of trying to open the Prosystem Global FX tax program from within IE and then it would NOT work because it was then trying to do the needed setup of the Global workstation FX components and could not do so because it was looking for a M/S windows based hard drive layout to do the workstation install to, which of course, it did not have because just installing IE with WINE does not create a M/S hard drive layout.

Thanks.

---

### Post by wpshooter on 2011-02-14
> **Frogs Hair said:**
> This works for some users with Firefox . [https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/)

Have not yet actually tried this one but again I have serious doubts that this will work because again just because Prosystem might be fooled into thinking that the browser is IE, there is still no M/S based drive layout in which it's workstation Global workstation components to be installed to, i.e. no C:drive.

Thanks.

---

### Post by lisati on 2011-02-14
> **wpshooter said:**
> Have not yet actually tried this one but again I have serious doubts that this will work because again just because Prosystem might be fooled into thinking that the browser is IE, there is still no M/S based drive layout in which it's workstation Global workstation components to be installed to, i.e. no C:drive.

Thanks.

My $0.02 worth is based on my having had a website online for about a year.

For everyday browsing, it shouldn't make one iota of difference to the people hosting the web site how the OS a browser is running on organizes its file system, labels its disk drives, or what sort of hoops the system has to jump through to display properly formatted web pages.

---

### Post by wpshooter on 2011-02-14
> **lisati said:**
> My $0.02 worth is based on my having had a website online for about a year.

For everyday browsing, it shouldn't make one iota of difference to the people hosting the web site how the OS a browser is running on organizes its file system, labels its disk drives, or what sort of hoops the system has to jump through to display properly formatted web pages.

So are you saying that you think there is still a possibility that this IE add-on might be sufficient to allow me to open and run the Prosystem Global FX tax program on my strictly Ubuntu based O/S computer ?

Thanks.

---

### Post by sydbat on 2011-02-14
> **wpshooter said:**
> So are you saying that you think there is still a possibility that this IE add-on might be sufficient to allow me to open and run the Prosystem Global FX tax program on my strictly Ubuntu based O/S computer ?

Thanks.Only way to find out is to try it.

But I think what lisati was getting at is - any website that requires a specific OS and it's associated file system structure to be able to run, is likely not one you want to have anything to do with...as in, the reason it "needs" a specific file system structure is so it can install malware that much easier...

Of course, you are talking about a tax program, which will require you to enter specific personal and financial details. That it also "requires" Windows to run from their website makes me suspicious. I do my taxes online with Ubuntu and have no problem with the company I deal with, because their system is properly set up to be OS agnostic.

Maybe you should look into another company / software to do your taxes online?

---

### Post by Mark Phelps on 2011-02-14
Unfortunately, some of these online tax tools, especially the FREE ones do, in fact, require an actual Windows install running IE in order to work.  We saw this come up last Spring -- with the attendant outrage from lots of folks -- and it looks like it's going to happen again.

Not much you can do other than choose a different tax prep provider.

---

### Post by 3Miro on 2011-02-14
Wine doesn't require windows licence, but wine IE doesn't run very well (compared to the rest of wine).

Virtual Box requires a windows licence, but it will run IE.

Wine emulates a HDD layout on your system (in .wine/drive_c becomes c: then the you have c:\windows c:\Program Files ... )

From a technical stand-point, there is no need for a tax program  to require specific OS or HDD layout. I would definitely be suspicious.

For taxes, I like to go to a real CEO, it costs me about 100 dollars (it may be more on other places), but I get a person to yell at when things go wrong. That's one solution. Another solution is to find a friend with windows and ask them to borrow their machine for an hour or two (or however long it takes).

---

### Post by wpshooter on 2011-02-15
> **3Miro said:**
> Wine doesn't require windows licence, but wine IE doesn't run very well (compared to the rest of wine).

Virtual Box requires a windows licence, but it will run IE.

Wine emulates a HDD layout on your system (in .wine/drive_c becomes c: then the you have c:\windows c:\Program Files ... )

From a technical stand-point, there is no need for a tax program  to require specific OS or HDD layout. I would definitely be suspicious.

For taxes, I like to go to a real CEO, it costs me about 100 dollars (it may be more on other places), but I get a person to yell at when things go wrong. That's one solution. Another solution is to find a friend with windows and ask them to borrow their machine for an hour or two (or however long it takes).

Prosystem Global FX is a "professional" quality tax preparation software application not just some $100 fly-by-night tax software.  Prosystem is what many (if not most) major CPA firms in this country use to prepare client tax returns.  I am not talking about a tax software that would be used to prepare just my own personal tax return.

See this link.

[http://www.cchgroup.com/webapp/wcs/stores/servlet/category_ProSystem-fx-Suite-Solutions_10151_-1_10053_50005702_10151_N_Y?cm_guid=1-_-100000000000001158385-_-5573361017&cm_mmc=Google+CorpSystem-_-ProSystem+Branded_Branded+Terms-_-BROAD-_-prosystem+fx]("http://www.cchgroup.com/webapp/wcs/stores/servlet/category_ProSystem-fx-Suite-Solutions_10151_-1_10053_50005702_10151_N_Y?cm_guid=1-_-100000000000001158385-_-5573361017&cm_mmc=Google+CorpSystem-_-ProSystem+Branded_Branded+Terms-_-BROAD-_-prosystem+fx")

Thanks.

---

