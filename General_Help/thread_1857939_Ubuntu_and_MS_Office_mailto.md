---
title: "Ubuntu and MS Office mailto:"
date: 2011-10-11
forum: General Help
---

### Post by YankeeFan on 2011-10-11
Greetings all,
I'm running Ubuntu 11.04.  When on a webpage (FireFox), if I click on a mailto: link, my system wants to open up Evolution.  I want it to open Outlook, which I have installed via CrossOver software.

I wrote a shell script to fire up Outlook for me.  In FireFox's preferences I pointed the mailto: trigger to fire my shell script.  It works.

My problem is this. Office starts up, but no mailto: window opens automatically.  I'm hoping someone knows what I need to add to my script to get the email window for the mailto: link to open when I click on the link.

Shell Script Code (wrapped in php tags for formatting - sorry)
[PHP]#!/bin/sh
#########################################################################################
#  script to help launch outlook when clicking on a mailto: link from browsers          #
#########################################################################################

"/home/jdc44/.cxoffice/Microsoft Office 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/Microsoft+Office+Outlook+2007"[/PHP]

Thanks for any tips or tricks!
Still a "YankeeFan"

---

