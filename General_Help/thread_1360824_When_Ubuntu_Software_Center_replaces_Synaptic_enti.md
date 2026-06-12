---
title: "When Ubuntu Software Center replaces Synaptic entirely..."
date: 2009-12-21
forum: General Help
---

### Post by bolucpap on 2009-12-21
I was reading the roadmap for Ubuntu Software Center and what I got from the gist of it is that in the future it will replace Synaptic entirely. However, at the moment there are many packages that are not in USC, but can only be searched for/added through Synaptic. (For example, angband is in the repositories, but not present in the Games section of USC) What will become of these packages? Also, there are many supplementary packages that are not applications per se, but need to be added/managed to customize the behavior of other applications (for example, different mono libraries are needed to compile different .NET framework executables when working with monodevelop). Is there a plan to radically expand the scope of USC to address those issues?

Thanks in advance, 
Boluc

---

### Post by philinux on 2009-12-21
Interesting. I'm testing lucid and synaptic is still there for now.
[http://en.wikipedia.org/wiki/Ubuntu_Software_Center](http://en.wikipedia.org/wiki/Ubuntu_Software_Center)

October 2009 - Ubuntu 9.10 Karmic Koala
    Introduce a new simple interface for locating, installing, and removing software, with better security based on PolicyKit instead of gksudo.[3]

April 2010 - Ubuntu 10.04 Lucid Lynx LTS
    The Software Center will replace Synaptic, Software Sources, Gdebi, and possibly the Update Manager. This will include finding, installing, and uninstalling non-graphical software such as utilities, fonts and database software. A system will be included using Launchpad to allow interactive software ratings and reviews.[3]

October 2010 - Ubuntu 10.10
    Integration of the ratings and review system from Launchpad into the Software Store, including the ability to purchase software.[3]

April 2011 - Ubuntu 11.04
    Improve sharing and tracking of software within the Store, to allow lists of installed software by parameters such as license, cost, or maintenance timetable. Allow users to find software by seeing what their friends have installed and also downloading a package once for deployment on several computers. There will also be a history feature that will indicate past software installations, removals and purchases, which will allow specific changes to be undone. At this stage the application should allow finding and installing specialized packages, including fonts and screensavers.[3]

---

### Post by Yellow Pasque on 2009-12-21
I was under the impression that Synaptic would still be easily installable. If not, I'm sure someone will grab the source and put it in his PPA ;)

---

### Post by synapsys on 2009-12-21
Everything is available via the command line (aptitude/apt-get)

---

### Post by bolucpap on 2009-12-21
Synapsis: Yes, that's true but synaptic offers a GUI to search for keywords in package descriptions, lets you sort them according to status/source, etc. All of which is probably possible using apt-get and aptitude once you learn the necessary command options/switches, but a GUI is much more intuitive for me. 

So, from what I gather the current (Karmic) USC is a pale shadow of what it's planned to be in Lucid?

---

### Post by feistybill on 2010-02-05
> **Temüjin said:**
> I was under the impression that Synaptic would still be easily installable. If not, I'm sure someone will grab the source and put it in his PPA ;)

I hope so. I'm starting to hate all these Windowzian innovations...

Quote from [https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)
"Be prepared to enter a new world.. in which you may feel as needing a Ph.D. in physics merely to install new applications or updates."
Just because you have to use 2 very simple interfaces like synaptic and update-manager? WTF, did these people expect something like Vista or maybe the Playstation load/save interface? What about a giant "click me to update" button on the desktop then? :-s

---

