---
title: "Avant Windows Navigator AWN loading problem - solved"
date: 2012-08-22
forum: General Help
---

### Post by Trent T on 2012-08-22
Getting Avant Windows Manager (AWN) to work in Ubuntu 11.10

After upgrading to Ubuntu 11.10, I was able to install AWN, but unable to activate it.
The Cairo Dock Manager works well, but I missed the fortunes available thru the 'Animal Farm' docklet-- Here's how I got AWN to work again.


**1) Start AWN from CLI – Using the command avant-windows-manager, I got the error message;**
[B]
Unable to locate theme engine in module_path: "pixmap"[/B]

This error was fixed by installing the pixbuf-based theme for GTK+ 2.x from the Ubuntu apps directory.  I was unable to find it directly in the software center, but if you highlight your ubuntu version on the left side of their webpage and click the button marked 'available on the Software Centre', the Software Center opens, and eventually displays the file for download.

[https://apps.ubuntu.com/cat/applications/oneiric/gtk2-engines-pixbuf/](https://apps.ubuntu.com/cat/applications/oneiric/gtk2-engines-pixbuf/)

**2) Next error - Unable to retrieve panels config value: Key file does not have group 'panels'**

Searching this one out led eventually to a solution from Michal Hruby (mhr3) at the Avant Window Navigator bug list, Question #101984. 

[https://answers.launchpad.net/awn/+question/101984](https://answers.launchpad.net/awn/+question/101984)

Michal says, 

“There are two ways to fix this:
a) Quit Awn, navigate to ~/.config/desktop-agnostic/ and delete all files inside.
b) Install libdesktop-agnostic-cfg-gconf and remove libdesktop-agnostic-cfg-keyfile.”

The desktop-agnostic subdirectory holds settings for AWN.  After deleting these files, 
I went back to CLI and installed and removed the requested files;

[B]sudo apt-get install libdesktop-agnostic-cfg-gconf

sudo apt-get remove libdesktop-agnostic-cfg-keyfile[/B]

Running avant-window-navigator command from CLI gave a long list of errors, but the AWN Docklet appeared at the bottom of my screen.  AWN lives!

I went to AWN preferences, check the box to start AWN automatically on boot.  Other features did not work—yet.
[B]
3) Restart to resolve remaining errors[/B]

After restarting, I was able to add AWN applets – Most importantly, Animal Farm, and my Fortunes.

I am posting here so that I'll have a clue how to fix AWN the next time I upgrade.  Thanks to Michal Hruby for his essential information!

Please post corrections to errors I may have made, or suggestions to make an AWN installation more trouble-free):P

---

