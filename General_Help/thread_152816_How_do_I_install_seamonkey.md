---
title: "How do I install seamonkey"
date: 2006-03-30
forum: General Help
---

### Post by kevin tough on 2006-03-30
I've tried this many times. I had seamonkey installed once with an icon on my taskbar but never been able to do it again. I've got a SeaMonkey readme from mozilla but some things don't check out.

I believe I installed to /home/kevin/programs  and was able to create the icon or short cut.  The KDE Panel doesn't have  Add to Panel|Launcher that the install directions talk about. 

They also say you should right-click the icon for Seamonkey.  If I had the icon on the panel I would be finished.

Is there a repository that has seamonkey on it?

In the shell how does a person remove a directory and all files and directories under it?

Kubuntu beginner,

Kevin Tough

---

### Post by towsonu2003 on 2006-03-30
check out [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
installing seamonkey is almost the same as firefox (untar, change permissions, run). Checking out the last section (dirty quick install or something) will *also* give you some insight on how to install seamonkey (again, untar-change permissions-run). 

I'm not familiar with creating "launchers" in kde. try right clicking on your desktop and choosing something that looks like "create launcher/shortcut/??". If you can find it, it will be asking you for a command. it will be /full/path/to/seamonkey/seamonkey --in that when you cd to /full/path/to/seamonkey using the *terminal* and do ./seamonkey, the browser will be launched.

---

### Post by kevin tough on 2006-03-31
Here it is for you other beginners from A to Z

Download from mozilla.org/projects/seamonkey/releases/
the file under the heading Linux (x86) called "tar,gz format"

For simplicity just save the file to your home directory. In my case that is "/home/kevin/. You can remove it or archive it later if you wish.

I hope you are familiar with the package manager adept and are able to find the following packages. libgtk 1.2, libgtk 1.2-common, libglib 1.2, and libstdc ++.so.5   These packages or equivalent packages are mentioned as necessary in one or another install documents I found.

Open a console and move to the directory where you saved the download.  Now enter this command without the quotes (please check your download file name, it might change from my example);

"sudo tar xfvz seamonkey-1.0.en-US.linux-i686.tar.gz -C /opt/"

This will unzip the download to your /opt/ directory. Now use the following command to create a link to what I guess is a special linux directory (/usr/local/bin/), here is the command

"sudo ln -s /opt/seamonkey/seamonkey /usr/local/bin/seamonkey"

Alright we're in action, just to put an icon on your panel(taskbar). Right click on a empty place on your panel. Select - Add to Panel | Select - Special Button | Select - Non-KDE Application

Now we should have a new window opened called "Non-KDE Application Configuration - KDE Panel".  Click on the browse icon at the end of the Executable Textbox and navigate to usr/local/bin/seamonkey and select (that's the link we made).

Now do a double click on the Icon in the top left corner of this new window.  Kde will now open its available icon list. Select one of these icons or like I did, chose the radio button "Other Icons". Click on the browse icon and navigate to /opt/seamonkey/chrome/icons/default/default.xpm and select it.  Now close this Application Configuration - KDE Panel window and your icon should show on the taskbar.

Happy monkeying around,

Kevin Tough

---

