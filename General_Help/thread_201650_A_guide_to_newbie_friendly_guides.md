---
title: "A guide to newbie friendly guides"
date: 2006-06-22
forum: General Help
---

### Post by Haegin on 2006-06-22
Anybody who has been using these forums for more than a few hours will probably come accross a howto that largely consists of a series of commands to run which should give the desired result. While this is all well and good for most people who are used to Linux often people who are new to Linux get confused and don't know what they are doing often asking (perfectly reasonable) questions such as "where do I enter this?" and "what is a terminal?".

Dapper drake is meant to be the most highly polished release of Ubuntu yet and this should be reflected in the communities guides and howtos. If we want Ubuntu (and Linux in general) to spread we need to make it as accessible as possible to newbies.

To do this we can do many things but I think something that will be very helpful to all newbies is to add a script to your howto that automates the entire process where possible. Tools like zenity make it easy to get user input and bash scripting is not that hard to learn.

Obviously some people don't have the time or the interest to invest in learning how to script and I suggest others who are "in the know" write the automation scripts if possible. Additionally some guides will be much harder to convert into an automated form and may not be possible. The aim is to get as many guides automated as possible so users can just download them and run them.

I am also not suggesting that we replace the original step by step guide. I think the steps are very important to more advanced users (and the curious) who want to know what they are doing rather than just doing it. Also please comment your code. This will help users learn bash scripting for those who want to learn and make it easier for somebody to port when Edgy Eft comes out.

**Links and Stuff**
[LIST]
[*]Zenity - Already installed on Dapper I think - the documentation is in System Help under Applications > Accessories > Zenity
[*][http://linuxcommand.org](http://linuxcommand.org) - A very helpful site with a tutorial on bash scripting
[*]/tmp folder - a great place to store a log of what is happening. If something goes wrong you can just pop up a message to the user telling them to email you the file or to post it on the forums. If it all goes to plan the log will disappear when the tmp folder is emptied.
[/LIST]

**Changelog**
[list]
[*]Added note about not replacing step by step instructions  (Thanks to Edward The Bonobo)
[/list]

---

### Post by Edward The Bonobo on 2006-06-22
Bravo! Bravo!  Seconded!

Can I add something else?  I'm the kind of non-techie who'd (mostly) appreciate just being able to run a script.  However - my aspiration is to learn more.  It would be very useful to have *in addition to the script *a step-by-step guide to what's being done and why.  In short - please remember to comment your code.  Lots and lots of comments.  If in doubt - comment it.

---

### Post by Haegin on 2006-06-22
OK, Just knocked up a quick script for users which will check if zenity is installed and install it if it isn't there then ask for the location of a script to run, ask if it needs root permissions, make it executable and execute it (using gksudo if needed).
I have attached it to this post.

**Install Instructions**
[LIST=1]
[*]Download the .txt file
[*]Rename it to ".runScript.sh" and place it in your home folder (the fullstop at the start of the name will make it hidden so press Ctrl + H in nautilus to view hidden files)
[*]Right click on the task bar and select "Add to Panel"
[*]At the top of the window select "Custom Application Launcher"
[*]Set it up however you like but make sure the command is "/home/<username>/.runScript.sh" (replacing <username> with your username.
[*]Click OK and whenever you download a script you can just click on the launcher and it will walk you through running it.
[/LIST]

**Notes**
[list]
[*]If you would rather a menu item than a launcher then go to Applications > Accessories > Alacarte Menu Editor and set up a menu item in there.
[*]I didn't write a script for installing this as it would just need instructions on how to run that script but if somebody knows how to make a .deb file that can be installed that will copy it to the right place and set up a launcher (or a menu item) then please let me know.
[/list]

---

