---
title: "java 6.17"
date: 2010-04-18
forum: General Help
---

### Post by shipinomore on 2010-04-18
this is my first day on Ubuntu and have done some other linux os's
I am a somewhat newbie at 71.
I like the wine app and trying to get several programs to work. one is for Bayer my diabetes software. the special requirement is Java 6.17 and I did install or run the software but it depends on that version of Java
should I convert the rpm to .deb ???
One other is Quicken Deluxe and it runs until you try to open the data file and it dies there and does not display anything?
I am searching and looking for answers on my own. but need a push in the right direction.
thank you 
Larry

---

### Post by john newbuntu on 2010-04-19
Take a look at wineHQ, which lists the softwares that run successfully on wine at: 
[http://appdb.winehq.org/](http://appdb.winehq.org/)
The browse by apps on the left will point you to a form where you can enter the name and see if it is suppoted in wine.  I did not fine the Bayer software, but did find quicken deluxe.  It probably needs a few extra libraries.  But re-confirm this anyway.

Also, the site:
[http://www.bayerdiabetes.com/sections/ourproducts/software.aspx](http://www.bayerdiabetes.com/sections/ourproducts/software.aspx)
says it is only supported on windows so you would not find a linux version of it as you may already know.

The other option is to install virtualbox (free) in Ubuntu and then install windows in virtual box.  This way, you can run all your win apps within virtualbox.

Good luck.

---

