---
title: "[HOW-TO]Chromium's &quot;Application Shortcuts&quot; functionality in Firefox WITHOUT Prism"
date: 2009-09-25
forum: General Help
---

### Post by chaanakya_chiraag on 2009-09-25
**NOTE: THIS MAY ONLY WORK PROPERLY ON UBUNTU.**  Please confirm if this does work in Kubuntu/Xubuntu and what the steps are for navigating Konqueror.  For now, I only have directions for Nautilus.


I don't know about you, but I really like the idea behind Chromium's "Create Application Shortcut".  Basically, what Chromium does when you create an "Application Shortcut" is it creates a desktop icon which opens a Chromium window **without toolbars, statusbars, and the like**.  The only problem is, I really love firefox and I wanted something similar.  After a bit of hunting around, I found Prism.  Here's the catch: it doesn't work! at least on my Jaunty install.  So I decided to figure out an alternate way.  After a bit of fiddling, I figured out a great way to duplicate Chromium's functionality.  Here are the steps:
1. Go to the terminal (Applications -> Accessories -> Terminal) and type the following (or copy and paste)
```
firefox -P
```Firefox should open with a window called "Profile Manager".  Click on "Create New Profile" and call it WebApps.  Click on "Finish" and click "Exit".

2. Download the script [here]("http://dl.getdropbox.com/u/1238977/appify.sh"), save it **to your home directory**, and make it executable (right-click on the file -> Properties -> Permissions -> check "Allow this file to run as a program").  Then, right-click on the Applications menu -> Edit Menu -> Accessories (in left-hand column) -> New Item -> fill in "Appify" for Name, /home/**username**/appify.sh for "Command", where **username** is your username, and click "OK".  To run the script, just click on the menu item or double click on the script and follow the prompts.  To run as a Terminal app, simply type in ```
appify install <URL> <Name>
``` or ```
appify uninstall <Name>
```3. [OPTIONAL] To apply a custom icon, follow the following steps (**Custom icons do not always work: I've had a few that just wouldn't show up**).  First, **create the application shortcut as above**.  Then, open a new Terminal window (Applications -> Accessories -> Terminal).  Then type in ```
cd ./.local/share/applications
```  Finally type ```
gedit **nameofwebsite**.desktop
``` where **nameofwebsite** is the name of the menu item you would like to change the icon of.  Add these two lines at the end to apply a custom icon:
```

Name[en_US]= **Name of website**
Icon[en_US]=**/path/to/local/icon**

```Getting the favicon for a website is really easy.  Just follow these steps.  First, browse to the web address.  Second, in Firefox, right-click and select "View Page Info" -> "Media" tab -> find the favicon in the list, select it, and click "Save As..."

4. DON'T CLICK ON THE SHORTCUT YET!!!  Download the file [here]("http://dl.getdropbox.com/u/1238977/iuxgcnco.WebApps.tar.gz"), untar it (right-click on it and click "Extract here"), and copy the **contents** of the extracted folder to the following location:
```
/home/**username**/.mozilla/firefox/[long string of characters].[name of profile]
```To get to this place graphically, start your File Browser.  For Nautilus, click on View -> Show Hidden Files and double-click on .mozilla.  Then click on firefox.  Finally, click on the folder that terminates with the name of the profile you created: for me, it would be [string of characters].WebApps.  Then copy the **contents** of the folder you extracted earlier into this folder.  If Nautilus asks you if it is okay to replace the files, click "Yes".  Now click on Applications -> Internet -> whatever the website name is and it should open up a Firefox window with no menubar, statusbar, bookmarks bar, or navigation bar! **Please note: you can only run one of these at a time.**  This means that if you open Facebook using the menu item, you cannot open Google using its menu item until you close the Facebook.  **This is due to limitations in Firefox, but I'm working on a fix for this.**
That's it!  Please feel free to reply with questions, comments, or concerns!
- Chiraag Nataraj

**Version 1.1 now uploaded!** - Fixed the no spaces issue in the menu item name. Please redownload the script.  
**Version 1.2 now uploaded!** - Now also can be used in the terminal.  Also added error checking.  Please redownload the script.
**Version 1.3 now uploaded!** - Now keeps a registry of the items "installed" in ~/.appify/list.  You can now also uninstall menu items created by the script!  Please redownload the script.
**Version 1.4 now uploaded!** - Fixed some bugs and removed the registry - now just checks .local/share/applications to see if it can uninstall.  Please redownload the script.

---

