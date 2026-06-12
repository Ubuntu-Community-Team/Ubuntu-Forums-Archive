---
title: "latest applications"
date: 2009-09-04
forum: General Help
---

### Post by Knowle on 2009-09-04
Is there a way to get Ubuntu to always have up to date applications?

Such as always having the latest version of Pidgin, Firefox, OpenOffice, Empathy, VirutalBox, ect. ...

I get the latest version of VB everytime it comes out by uninstalling/reinstalling the .deb file posted on their site. Firefox already updated to the latest(3.5.4pre, unbranded) on Ubuntu 9.04 were as Pidgin(2.5.5) still hasn't updated to 2.6.1 and its been over a week since that release came out. OO.org is out of date as well.

 I guess I just don't understand how the release schedules work. Why is Firefox able to update(unbranded) to the latest version through a regular software update yet applications like Pidgin and OO.org don't?

---

### Post by fluffman86 on 2009-09-04
Ubuntu takes pride in having stable release software and not changing it for 6 months.  They fell that a major update every 6 months is often enough, and yet necessary to test new versions of software to ensure it's stable.

If you want always up-to-date software, you can usually find a PPA of individual packages.  

Here's how to install Pidgin's PPA:
[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

And how to install the OpenOffice.org PPA:
[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

More can be found by googling "APPNAME PPA" and this will help keep everything up-to-date.

---

### Post by Vaphell on 2009-09-04
there are 3rd party repos, so called PPA
i use few of these myself - for pidgin and firefox 3.5/3.6a/3.7a

firefox
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
pidgin:
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

add lines listed there to the sources.list file or via System->Administration->App sources

---

### Post by Knowle on 2009-09-04
I sorta understand how PPAs work, I currently have the Firefox(minefield/trunk) PPA added. I thought PPAs were the latest developer build(s) though? I'm sorry I know I wasn't very clear. I'd like up to date applications... but stable ones. Like the example I gave before with Pidgin.

I don't really understand why Firefox updated from the 3.0.x build to the 3.5.x yet Pidgin doesn't do the same. Unless I did something wrong when I added the PPA a few weeks ago? I mean I have the 3.5.x build and then I also have the 3.6pre/Namoroka that I get off the PPA.  :/

---

### Post by Vaphell on 2009-09-04
it's because there is that thing called feature freeze. To ensure stability apps are are locked when new Ubuntu version is about to be released and only bugfixes are allowed later for that distro. If you get Pidgin 2.5 by default you'll never see 2.6 in official repos, unless you upgrade when new flavor of ubuntu comes out.

if you want to be updated, you have to use PPAs or find .deb files with newer versions somewhere on the internet... or install from newest sources.

---

