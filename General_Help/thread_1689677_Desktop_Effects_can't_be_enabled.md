---
title: "Desktop Effects can't be enabled"
date: 2011-02-17
forum: General Help
---

### Post by itsamecameron on 2011-02-17
Ok guys here is the deal. Ive had this issue myself and have found that some of the fixes out there work, and well some of them dont.

 First id like to start with the scenario that ive found many users are having, that way you will know if this is what you are looking for or not.   The situation will usually start when an application informs us that it needs compositing enabled to run. So we enable it in metacity or do a google search to figure out "how to enable compositing" we run the command in the terminal and hey its enabled and the application stops complaining and really doesnt run any different than it ever did before. Thats all fine and dandy until you realize that your compiz desktop effects are no longer running. 
So you go  to SYSTEM>Preferences>Appearance and move on over to the Visual effects tab and click whatever one you want. Then the computer hangs for a second or two and a nice box pops up and tells you that desktop effects cant be enabled/started. WHAT!? It worked ten mins ago! 

So we do another google search and find that we have to run some commands to replace metacity with compiz. So we copy and paste the command into the terminal and run it. Doesnt work and well now you have either no window manager running so you have no minimize maximize close ect... or compiz fails to start and metacity is still running.

More searching and no help............til now anyhow

 This issue is because compiz and metacity are confused and are fighting over who is suppost to be running, and metacity is winning and so compiz wont start at all.  

This is the best and well only fix that ive found to actually work short of reinstalling the os, we will be doing this in the terminal and its best to do it in the ROOT TERMINAL.

 First go to the applications menu and move on down to system tools, and click on Root Terminal. At this point you will be asked for your password, so put it in. 

Now that we have the terminal up and running you will need to enter this command  "sudo apt-get remove compiz"  and press enter, follow the process and enter Y and enter where applicable  Now compiz is removed from your system.  

After that you will need to remove metacity so type in  "sudo apt-get remove metacity" press enter and follow the same procedure that we used when removing compiz. 

After this we will need to restart Great so now we have no window/compositing managers installed.   After you log in the GUI will look weird and so will the mouse cursor. Thats normal remember we have no window managers installed. The cursor will still let you click on things even though its an X... and the only way to close windows is using file quit or the appropriate keyboard shortcut 

Now lets get compiz back.  Open up the Root Terminal like before and input your password.  Now type "sudo apt-get install compiz" and press enter.

 Follow the installation and type Y and enter when applicable. After the installation is complete restart your system. 

Now you can go back to the appearance menu and enable desktop effects. BOOM now they are back on but please do note if you had any compiz extras installed you will need to reinstall them. These include compiz config and any add on packs. You will also need to reconfigure compiz to run as you had it set up before.   Total PITA to do I know, but it works and all of the other fixes ive that I found on the forums didnt....

---

### Post by piquat on 2011-02-17
Only question I'd have is, why do this in the root terminal if you're using sudo anyway?  Wouldn't you do this either in a root term or, probably safest, just use a normal terminal and use sudo?

---

