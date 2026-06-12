---
title: "Remove gtk 3.0 and use gtk 2.24"
date: 2011-09-29
forum: General Help
---

### Post by nickos on 2011-09-29
Okay,so i am facing a big problem here.
I "accidentally" installed gtk 3.0 from synaptic on ubuntu 11.04,which,as far as i know,uses gtk 2.24
So now i have both gtk 3.0 and gtk 2.24.

by entering the command "dpkg -l | grep libgtk" here is what i get:


ii  libgtk-3-0                                            3.0.8-0ubuntu1                             The GTK+ graphical user interface library
ii  libgtk-3-bin                                          3.0.8-0ubuntu1                             The programs for the GTK+ graphical user interface library
ii  libgtk-3-common                                       3.0.8-0ubuntu1                             Common files for the GTK+ graphical user interface library
ii  libgtk-3-dev                                          3.0.8-0ubuntu1                             Development files for the GTK+ library
ii  libgtk-sharp-beans-cil                                2.14.1-1                                   Supplementary CLI bindings for GTK 2.14+
ii  libgtk-vnc-1.0-0                                      0.4.3-0ubuntu3                             A VNC viewer widget for GTK+ (runtime libraries)
ii  libgtk2-perl                                          2:1.223-1                                  Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2-ruby1.8                                       0.19.3-2ubuntu1                            GTK+ bindings for the Ruby language
ii  libgtk2.0-0                                           2.24.4-0ubuntu2                            The GTK+ graphical user interface library
ii  libgtk2.0-0-dbg                                       2.24.4-0ubuntu2                            The GTK+ libraries and debugging symbols
ii  libgtk2.0-bin                                         2.24.4-0ubuntu2                            The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                         2.12.10-1ubuntu1                           CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-cil-dev                                     2.12.10-1ubuntu1                           CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                                      2.24.4-0ubuntu2                            Common files for the GTK+ graphical user interface library
ii  libgtk2.0-dev                                         2.24.4-0ubuntu2                            Development files for the GTK+ library
ii  libgtk2.0-doc                                         2.24.4-0ubuntu2                            Documentation for the GTK+ graphical user interface library
ii  libgtkhtml-editor-common                              1:3.32.2-0ubuntu1                          HTML rendering/editing library - editor widget data
ii  libgtkhtml-editor0                                    1:3.32.2-0ubuntu1                          HTML rendering/editing library - editor widget
ii  libgtkhtml3.14-19                                     1:3.32.2-0ubuntu1                          HTML rendering/editing library - runtime files
ii  libgtkmm-2.4-1c2a                                     1:2.24.0-0ubuntu1                          C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview2.0-0                                 2.10.5-0ubuntu3                            shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-common                            2.10.5-0ubuntu3                            common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                                          2.0.16-1                                   a spell-checking addon for GTK's TextView widget


When i try to remove gtk 3.0,i get the message that it is beeing used and i cant remove it.What should i do?Is there any way to use gtk 2.24 instead of 3.0 or will i have to save my files and install ubuntu again? *arg*

---

### Post by dino99 on 2011-09-29
Removing GNOME3 and going back to stock 11.04

Following these steps will remove the GNOME3 PPA and revert your packages:

sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3

While downgrading, if aptitude gives the following output:

Leave the following dependencies unresolved:
     gnome-control-center-data recommends gnome-control-center (<< 2.91) [...]

Then type this when it asks you to enter yes/no: - gnome-control-center-data (Note the - in the beginning, its important). Then press enter, and then it shouldn't show any packages under Leave the following dependencies unresolved. Type y, and you should soon be downgraded normally to the Ubuntu 11.04 packages.

---

### Post by nickos on 2011-09-29
> **dino99 said:**
> Removing GNOME3 and going back to stock 11.04

Following these steps will remove the GNOME3 PPA and revert your packages:

sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3

While downgrading, if aptitude gives the following output:

Leave the following dependencies unresolved:
     gnome-control-center-data recommends gnome-control-center (<< 2.91) [...]

Then type this when it asks you to enter yes/no: - gnome-control-center-data (Note the - in the beginning, its important). Then press enter, and then it shouldn't show any packages under Leave the following dependencies unresolved. Type y, and you should soon be downgraded normally to the Ubuntu 11.04 packages.

while running the second command,i get this message:

Warning:  Could not find package list for PPA: gnome3-team gnome

---

### Post by nickos on 2011-09-29
okay, so i followed these:

sudo apt-get update sudo apt-get upgrade sudo apt-get install ubuntu-desktop

after restaring, using terminal i found out that i am now using gtk 2.24.
Still,i am not able to view GTK 2.24 content(like mnemonics and stuff)

should i take a back up and re install ?????????

---

