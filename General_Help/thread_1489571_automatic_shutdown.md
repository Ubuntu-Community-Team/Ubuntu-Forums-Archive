---
title: "automatic shutdown"
date: 2010-05-21
forum: General Help
---

### Post by nischalinn on 2010-05-21
Is there a way to have Linux Shut down after computer activity has stopped and not just with a timer. Lets say I'm trying to download something and I want it to turn off after it has finished with the down load.

---

### Post by rjcroy on 2010-05-21
From a terminal you could do
```
wget http://thesite.com/fileIwant.tar.gz && shutdown -P now 
```
The shutdown command may require that you execute it as root, in which case you could do the above from a root shell after "sudo -s"

---

### Post by Drenriza on 2010-05-21
```
wget http://thesite.com/fileIwant.tar.gz && shutdown -P now
```

As far as i can tell you download a widget, as a compressed tar file. And then you run a seprate shutdown command, telling it to shutdown and cut power NOW.

How does this close the system, when activity stops?

---

### Post by akakingess on 2010-05-21
Yes, I believe that the && in the script basically says wait until the first command is done  and then execute the next command.

---

### Post by Drenriza on 2010-05-21
the ```
&&
```

just means, if the first command succesfully execute then it will execute the next command in line.

---

### Post by rjcroy on 2010-05-22
```
wget http://thesite.com/fileIwant.tar.gz && shutdown -P now 
```
Yes, that's right. The line above calls two programs; wget, which is a command line program for downloading files from a network, and shutdown, which can be used to shutdown or reboot the computer.

---

### Post by nischalinn on 2010-05-22
Suppose I want to download a video from youtube and I want that after completion of download, my PC shuts down automatically.
How to do this?

---

### Post by dark-triad on 2010-05-22
Hmm... for youtube videos try the same sort of command but with youtube downloader instead of wget, i think that should would work

Code:
sudo apt-get install youtube-dl

Code:
youtube-dl [http://youtube.com/the-video-url](http://youtube.com/the-video-url) && shutdown -P now

example: 
youtube-dl [http://www.youtube.com/watch?v=h1fGJX_9a_M&feature=hp_SLN](http://www.youtube.com/watch?v=h1fGJX_9a_M&feature=hp_SLN) && shutdown -P now

See if that works, i havent tried it as i use a firefox plugin to download video not youtube-dl, but from a command line this should work i think and is the only way i know of, there may be a different way or the command may need a tweak by someone with a bit more knowledge, but give it a shot anyway

---

### Post by Drenriza on 2010-05-23
this is a bad example. What if you download something with a torrent program, and want to shutdown when download activity stops.

---

### Post by inameiname on 2010-05-23
Not sure if this what you would like, but it's just a gui shutdown way:

sudo apt-get install gshutdown

A delay works fine for me as I usually have some idea how long a download will take, so I just set it longer than I'm sure the download would take, and voila, good enough.

---

### Post by dark-triad on 2010-05-23
Yeah Drenriza is right, youtube-dl is a bad example and is limited for anything else apart from youtube, but its the only way i know of for Nischalinn's question about youtube videos.

Torrent wise you may want to take a look here [http://wiki.ubuntuforums.org/showthread.php?p=9103625]("http://wiki.ubuntuforums.org/showthread.php?p=9103625")

I think inameiname's right i think its easier to use a timer/delay shutdown as its universal.

Also i have a script that makes my torrent client (or whatever program/command you like) to automatically kick in when the screensaver activates, you may find it handy, u can then just leave your house with your computer running without worrying to turn your torrents on, your torrent client will fire up when your screensaver kicks in and your computer will suspend according to the idle time u specify in the power manager, give me a shout if you would like a copy and i'll post it

---

### Post by inameiname on 2010-05-23
Hmmm, your script, dark-triad, sounds pretty cool. I might be able to find a use for it as well. If you could post it on here I'm sure a few of us would love to see it.

---

### Post by dark-triad on 2010-05-23
For inameiname
Ok this goes a little bit off topic from the original question but here is the Screensaver script as requested by inameiname and a very basic how to:
This script runs in the background and watches for the screensaver to be activated and executes commands based upon the starting or ending of the screensaver. Depending on your needs and what you use it for you can add it to your startup applications or create a launcher and use it when you want too:

> #!/usr/bin/perl

#Executes commands based on the screensaver starting or ending

#Notes:
#boolean true = screensaver start
#boolean false = screensaver end

#Note an "&" may be needed after the commands 
#to put the program in the background and release the shell, 
#otherwise it may not work, eg: "transmission &"


my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='ActiveChanged'\"";
 
open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {

system("enter your command here");

} elsif (m/^\s+boolean false/) {

system("enter your command here");

}
}




Below is a way to use it with transmission, along with another script which is ran when the screensaver deactivates, it uses zenity to ask whether or not to close transmission when you return or deactivate the screensaver:


> #!/usr/bin/perl

#Screensaver-torrent

#Executes commands based on the screensaver starting or ending, in this case transmission

#Notes:
#boolean true = screensaver start
#boolean false = screensaver end

#The Zenity-Kill-Torrents script presents a yes/no box when the screensaver deactivates to choose whether or not to keep transmission running


my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='ActiveChanged'\"";
 
open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {

system("transmission &");

} elsif (m/^\s+boolean false/) {

system("/home/triad/myscripts/Zenity-Kill-Torrents");

}
}




Remember to change the file path to the zenity-kill-torrent script to suit your needs and if you want to add multiple commands then just stack them after one an other like:
> 
system("my command &");
system("my other command &");
system("my last command &");



The zenity-kill-torrent script is:


> 
#!/bin/bash

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




i also use it to turn my monitor off to save power instead of the screensaver and play a wav file to greet me when i return amongst numerous other things, and if it is left idle for a period of time then your computer will suspend or hibernate or whatever depending on your power manager settings (which may help nischalinn with his original post), im sure you will find something else fun to do with it than just activating torrents

Thats it
Have fun with it!

---

### Post by niziris on 2010-11-04
Ppl u should check Sentinella from Ubuntu software center...
  
Sentinella has options to shut down the system when network traffic  is lower then 10 kb/s for couple min, which mean that download is finished (probably)...

also can shut down the sistem when CPU load is lower than some values...and some other interesting staff...

---

### Post by inameiname on 2010-11-05
Thanks for the scripts, dark-triad. I must've completely forgotten about this thread, and my request. hehe. It's pretty cool.

---

