---
title: "Activate command/program when screensaver activates"
date: 2010-05-23
forum: General Help
---

### Post by dark-triad on 2010-05-23
Ok wasnt sure which forum to post this, i originally posted this in another thread for inameiname and to try and help nischalinn with his post here [http://ubuntuforums.org/showthread.php?t=1489571]("http://ubuntuforums.org/showthread.php?t=1489571") 

But thought i'd also post it here as others may benefit from it too, or further improve it, so here is the Screensaver script as requested by inameiname and a very basic how to:
This script runs in the background and watches for the screensaver to be activated and executes commands based upon the starting or ending of the screensaver. Depending on your needs and what you use it for you can add it to your startup applications or create a launcher and use it when you want too:


> #!/usr/bin/perl

#Executes commands based on the screensaver starting or ending

#Notes:
#boolean true = screensaver start
#boolean false = screensaver end

#Note an "&" may be needed after the commands 
#to put the program in the background and release the shell, 
#otherwise it may not work, eg: "transmission &"


my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSave r', member='ActiveChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {

system("enter your command here");

} elsif (m/^\s+boolean false/) {

system("enter your command here");

}
}


Below is a way to use it with transmission, so that your torrents start when the screensaver starts, along with another script which is ran when the screensaver stops, it uses zenity to ask whether or not to close transmission when you return or deactivate the screensaver:



> #!/usr/bin/perl

#Screensaver-torrent

#Executes commands based on the screensaver starting or ending, in this case transmission

#Notes:
#boolean true = screensaver start
#boolean false = screensaver end

#The Zenity-Kill-Torrents script presents a yes/no box when the screensaver deactivates to choose whether or not to keep transmission running


my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSave r', member='ActiveChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {

system("transmission &");

} elsif (m/^\s+boolean false/) {

system("/home/triad/myscripts/Zenity-Kill-Torrents");

}
}



Remember to change the file path to the zenity-kill-torrent script to suit your needs and if you want to add multiple commands then just stack them after one another like:


> system("my command &");
system("my other command &");
system("my last command &");

The zenity-kill-torrent script is:


> #!/bin/bash

#Called through screensaver script, asks whether or not to kill torrent client (transmission)
#This does not close transmission gracefully or softly, it kills transmission, transmission 
#will not update or send your tacker info before it shutsdown but will update them when 
#transmission is restarted next time

zenity --question --text="Do you want to close your torrents?" --title="DOWNLOADS"
if [[ $? == 0 ]] ; then
kill -9 "$(pgrep -f transmission)"

echo "Torrents are now closed"

else

echo "Torrents are staying active"

fi

i also use it to turn my monitor off to save power instead of the screensaver or blank screen and play a wav file to greet me when i return amongst numerous other things, and if it is left idle for a period of time then your computer will suspend or hibernate or whatever depending on your power manager settings (which may help nischalinn with his original post), im sure you will modify it to find something else fun to do with it than just activating torrents

Thats it
Have fun with it!

---

