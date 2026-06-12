---
title: "Program that changes wallpapers every x seconds like Windows 7"
date: 2009-10-03
forum: General Help
---

### Post by riahc3 on 2009-10-03
Hey

Im looking for a program that changes wallpapers that are in a folder everything x seconds like the feature in Windows 7.

Also when I unplug the power cord from my laptop, it should stop changing backgrounds as it uses battery life. When I plug it back in, it should resume changing backgrounds.

---

### Post by dcstar on 2009-10-03
> **riahc3 said:**
> Hey

Im looking for a program that changes wallpapers that are in a folder everything x seconds like the feature in Windows 7.

Also when I unplug the power cord from my laptop, it should stop changing backgrounds as it uses battery life. When I plug it back in, it should resume changing backgrounds.

This script updates my background (using the xplanet image), you can use the relevant section for any sort of background file:

```
#!/bin/bash
#xplanet-gnome.sh shell script v0.3
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
# Change these to match your screen settings and your particular location
# One day someone might want to replace these with commands to automatically
# get them from your generic Linux system (but not today...)
#
GEOMETRY=1680x1050
LONGITUDE=144.833328
LATITUDE=37.666668
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

if [ ! -e $lockfile ]; then
   # Delete lockfile if program receives command to end:
   trap "rm -f $lockfile; exit" INT TERM EXIT
   # and let's make one now....
   touch $lockfile
else
   # Lockfile exists for this user profile, get me outa here!
   exit
fi

if [ -z $PROJECTION ]; then 
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE
else
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE -projection $PROJECTION
fi

#update Gnome backgound - this works in Ubuntu 9.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0
```

---

### Post by MaxIBoy on 2009-10-03
EDIT: Just reread your post. The part about stopping the script when you unplug is misinformed-- it would be like turning down the volume on the radio in a Humvee to improve the gas mileage, it's not enough improvement for you to even notice. Unless you have huge desktop backgrounds-- but a typical laptop-screen sized picture is less than 5 MB for a PNG, less than 800 KB for a JPEG, not enough to make a difference.




You can write a simple script to do this. The complete script is at the bottom of the post but I would encourage you to read my whole post, that way you learn something about scripting! Scripting is a great tool for automating your system and doing simple tasks. I've got all kinds of scripts on my system doing all kinds of cool custom things!

Here I am assuming you use Ubuntu with GNOME (i.e. not Kubuntu or Xubuntu, the script would be different for those.)

GNOME (the software which provides the look-and-feel of the standard Ubuntu version) uses a program called [Gconf]("http://polishlinux.org/gnome/gconf-gnome-under-the-hood/") to change its settings. When you change its settings graphically, the graphical program is really just translating your actions into Gconf commands and running them. You can create Gconf commands yourself and run them. In this case we can write a simple computer program to generate Gconf commands which will set the desktop background. The program will be a script, which is the same as if you were typing commands into a terminal, but in this case its a list of commands in a file.

First, we create a folder where we store all the desktops. For this example I'll make it Pictures/desktops, but you could really make it anything you want. Go to your pictures folder and make a folder called "desktops," add whatever pictures you want to it.

Now, we can start writing our script! Create a file called random_desktop.sh and add the following line to the beginning:
```
#! /bin/bash
```In UNIX-land, "#!" means "open me with." So when you run random_desktop.sh as a program, it will open the file with /bin/bash, which is the program that can understand and run our script.

Since the pictures we're working with are in Pictures/desktops, the next line of the script should tell the script that we are working in that directory. The "cd" command stands for "change directory." It's like clicking on a folder in the filebrowser, it lets you move around the filesystem. We call it as "cd /place/you/want/to/go", in this case "cd ~/Pictures/desktops". The tilde "~" character is automatically substituted for the name of your home folder.
```
cd ~/Pictures/desktops
```Now, we need the code to pick the random file. I borrowed this code from [here]("http://ubuntuforums.org/archive/index.php/t-501904.html") a while back and it's come in very handy since then: 
```
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
```Next, we run the gconf command to change the desktop background.
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME 
```One last thing, we want the script to repeat itself after a certain amount of time. Suppose we want it to be 240 seconds (4 minutes) we would do this:
```
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.
```The final script looks like this:
```
#! /bin/bash
cd ~/pics/desktops
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0 &disown    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.

```Not including comments this is only 9 short lines of code! 

Final step: right-click on the script you just wrote. Go to "properties." In the window which pops up, go to "permissions" and check the tickbox labeled "Allow executing this file as a program." Now you can double-click on the script whenever you like to activate your desktop switcher! If you want it to start up automatically whenever you boot, go to system>preferences>startup applications, click "add," type "desktop switcher" for the name and drag-and-drop the icon for the script into the "command" field. Click "add" again and you should be good.


And yes, there's probably some program somewhere you can install instead of writing your own, but where's the fun in that?!

---

### Post by riahc3 on 2009-10-03
> **dcstar said:**
> This script updates my background (using the xplanet image), you can use the relevant section for any sort of background file:

```
#!/bin/bash
#xplanet-gnome.sh shell script v0.3
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
# Change these to match your screen settings and your particular location
# One day someone might want to replace these with commands to automatically
# get them from your generic Linux system (but not today...)
#
GEOMETRY=1680x1050
LONGITUDE=144.833328
LATITUDE=37.666668
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

if [ ! -e $lockfile ]; then
   # Delete lockfile if program receives command to end:
   trap "rm -f $lockfile; exit" INT TERM EXIT
   # and let's make one now....
   touch $lockfile
else
   # Lockfile exists for this user profile, get me outa here!
   exit
fi

if [ -z $PROJECTION ]; then 
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE
else
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE -projection $PROJECTION
fi

#update Gnome backgound - this works in Ubuntu 9.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0
```

This really isnt what I am looking for.

---

### Post by MaxIBoy on 2009-10-03
What about mine, did that help?

---

### Post by misfitpierce on 2009-10-03
[quote="random_person"]There is a really nice app available in the repos, called **wallpaper-tray**.

It stays on the system tray, and looks for images in any directory of your choice, and then changes them at certain user-specified intervals (the minimum interval being 1 minute).

There is another one, called gbackground, which does the same, but can be set to change the background image at a faster rate (any given number of seconds --even 1 second). It is also available in the repositories.

A, perhaps, "geekier" approach, would be to write an xml file to set the background and then change it after some time, with --even-- a nice fade in/out transition. Then you could just go to **system > preferences > appearance > background > add > all files**, and select your xml script.

It would look something like this:

 	Code:
 	<background>
	<static>
		<duration>1.0</duration>
		<file>/background/image/one</file>
	</static>	
	<transition>
		<duration>2.0</duration>
		<from>/background/image/one</from>
		<to>/background/image/two</to>
	</transition>
	<static>
		<duration>2.0</duration>
		<file>/background/image/two</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/background/image/two</from>
		<to>/background/image/one</to>
	</transition>
	<static>
		<duration>1.0</duration>
		<file>/background/image/one</file>
	</static>
</background> 
where **duration** is measured in seconds.

But then, if you ask me, I'd say wallpaper-tray. :smile:
It's a lot easier.[/quote]

Got that from a diff thread on these boards... Maybe work?

---

### Post by akakingess on 2009-10-03
If it's any consolation MaxIBoy, I have bookmarked this page to read your post more thoroughly (I am currently reading books on shell/bash scripting, python, PHP, among others), so I appreciate the detail you went into!!!

---

### Post by themusicalduck on 2009-10-03
I have no idea how well this works, but I heard of this software somewhere before:

[http://drapes.mindtouchsoftware.com/](http://drapes.mindtouchsoftware.com/)

---

### Post by HomoGleek on 2009-10-03
> **MaxIBoy said:**
> EDIT: Just reread your post. The part about stopping the script when you unplug is misinformed-- it would be like turning down the volume on the radio in a Humvee to improve the gas mileage, it's not enough improvement for you to even notice. Unless you have huge desktop backgrounds-- but a typical laptop-screen sized picture is less than 5 MB for a PNG, less than 800 KB for a JPEG, not enough to make a difference.




You can write a simple script to do this. The complete script is at the bottom of the post but I would encourage you to read my whole post, that way you learn something about scripting! Scripting is a great tool for automating your system and doing simple tasks. I've got all kinds of scripts on my system doing all kinds of cool custom things!

Here I am assuming you use Ubuntu with GNOME (i.e. not Kubuntu or Xubuntu, the script would be different for those.)

GNOME (the software which provides the look-and-feel of the standard Ubuntu version) uses a program called [Gconf](http://polishlinux.org/gnome/gconf-gnome-under-the-hood/) to change its settings. When you change its settings graphically, the graphical program is really just translating your actions into Gconf commands and running them. You can create Gconf commands yourself and run them. In this case we can write a simple computer program to generate Gconf commands which will set the desktop background. The program will be a script, which is the same as if you were typing commands into a terminal, but in this case its a list of commands in a file.

First, we create a folder where we store all the desktops. For this example I'll make it Pictures/desktops, but you could really make it anything you want. Go to your pictures folder and make a folder called "desktops," add whatever pictures you want to it.

Now, we can start writing our script! Create a file called random_desktop.sh and add the following line to the beginning:
```
#! /bin/bash
```In UNIX-land, "#!" means "open me with." So when you run random_desktop.sh as a program, it will open the file with /bin/bash, which is the program that can understand and run our script.

Since the pictures we're working with are in Pictures/desktops, the next line of the script should tell the script that we are working in that directory. The "cd" command stands for "change directory." It's like clicking on a folder in the filebrowser, it lets you move around the filesystem. We call it as "cd /place/you/want/to/go", in this case "cd ~/Pictures/desktops". The tilde "~" character is automatically substituted for the name of your home folder.
```
cd ~/Pictures/desktops
```Now, we need the code to pick the random file. I borrowed this code from [here]("http://ubuntuforums.org/archive/index.php/t-501904.html") a while back and it's come in very handy since then: 
```
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
```Next, we run the gconf command to change the desktop background.
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME 
```One last thing, we want the script to repeat itself after a certain amount of time. Suppose we want it to be 240 seconds (4 minutes) we would do this:
```
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.
```The final script looks like this:
```
#! /bin/bash
cd ~/pics/desktops
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.

```Not including comments this is only 9 short lines of code! 

Final step: right-click on the script you just wrote. Go to "properties." In the window which pops up, go to "permissions" and check the tickbox labeled "Allow executing this file as a program." Now you can double-click on the script whenever you like to activate your desktop switcher! If you want it to start up automatically whenever you boot, go to system>preferences>startup applications, click "add," type "desktop switcher" for the name and drag-and-drop the icon for the script into the "command" field. Click "add" again and you should be good.


And yes, there's probably some program somewhere you can install instead of writing your own, but where's the fun in that?!
Thanks, this works great :) 
And also thanks for the notes in the code.

---

### Post by riahc3 on 2009-10-03
> **MaxIBoy said:**
> EDIT: Just reread your post. The part about stopping the script when you unplug is misinformed-- it would be like turning down the volume on the radio in a Humvee to improve the gas mileage, it's not enough improvement for you to even notice. Unless you have huge desktop backgrounds-- but a typical laptop-screen sized picture is less than 5 MB for a PNG, less than 800 KB for a JPEG, not enough to make a difference.




You can write a simple script to do this. The complete script is at the bottom of the post but I would encourage you to read my whole post, that way you learn something about scripting! Scripting is a great tool for automating your system and doing simple tasks. I've got all kinds of scripts on my system doing all kinds of cool custom things!

Here I am assuming you use Ubuntu with GNOME (i.e. not Kubuntu or Xubuntu, the script would be different for those.)

GNOME (the software which provides the look-and-feel of the standard Ubuntu version) uses a program called [Gconf](http://polishlinux.org/gnome/gconf-gnome-under-the-hood/) to change its settings. When you change its settings graphically, the graphical program is really just translating your actions into Gconf commands and running them. You can create Gconf commands yourself and run them. In this case we can write a simple computer program to generate Gconf commands which will set the desktop background. The program will be a script, which is the same as if you were typing commands into a terminal, but in this case its a list of commands in a file.

First, we create a folder where we store all the desktops. For this example I'll make it Pictures/desktops, but you could really make it anything you want. Go to your pictures folder and make a folder called "desktops," add whatever pictures you want to it.

Now, we can start writing our script! Create a file called random_desktop.sh and add the following line to the beginning:
```
#! /bin/bash
```In UNIX-land, "#!" means "open me with." So when you run random_desktop.sh as a program, it will open the file with /bin/bash, which is the program that can understand and run our script.

Since the pictures we're working with are in Pictures/desktops, the next line of the script should tell the script that we are working in that directory. The "cd" command stands for "change directory." It's like clicking on a folder in the filebrowser, it lets you move around the filesystem. We call it as "cd /place/you/want/to/go", in this case "cd ~/Pictures/desktops". The tilde "~" character is automatically substituted for the name of your home folder.
```
cd ~/Pictures/desktops
```Now, we need the code to pick the random file. I borrowed this code from [here]("http://ubuntuforums.org/archive/index.php/t-501904.html") a while back and it's come in very handy since then: 
```
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
```Next, we run the gconf command to change the desktop background.
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME 
```One last thing, we want the script to repeat itself after a certain amount of time. Suppose we want it to be 240 seconds (4 minutes) we would do this:
```
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.
```The final script looks like this:
```
#! /bin/bash
cd ~/pics/desktops
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME
sleep 240 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.

```Not including comments this is only 9 short lines of code! 

Final step: right-click on the script you just wrote. Go to "properties." In the window which pops up, go to "permissions" and check the tickbox labeled "Allow executing this file as a program." Now you can double-click on the script whenever you like to activate your desktop switcher! If you want it to start up automatically whenever you boot, go to system>preferences>startup applications, click "add," type "desktop switcher" for the name and drag-and-drop the icon for the script into the "command" field. Click "add" again and you should be good.


And yes, there's probably some program somewhere you can install instead of writing your own, but where's the fun in that?!

Amazing post. Too bad there is no thanks button.

I perfer a GUI application but Ill try to write this script. I know about scripting but the post was just amazing :)


BTW Drapes only allows me a 1 minute; Im looking for something to do this in seconds.

MaxIboy, you have to take in account that each time it selects a picture it has to read from a HDD, so every 5 seconds it would read the HDD and take a picture. That drains battery life; Thats why this option is in Windows 7. How, in that script, would I detect power state and disable it if the laptop is unplugged.

---

### Post by MaxIBoy on 2009-10-03
Wait a sec, you want every **5** seconds? I personally think that would be needlessly distracting, but there *is* a solution. 

Which is: use tmpfs. It's like creating a mini-partition in RAM. You can set up a script which, each time the computer boots, will copy over your desktops into a, say, 30 MB tmpfs ramdisk. Point the desktop changer toward this ramdisk, and now all your pictures are in RAM, and the HDD no longer needs to spin up. And honestly, 30 MB isn't that much RAM these days. 



If you want to detect the current battery state, you can add this to your script: 
```
POWER_STATE=$( acpi | grep Discharging )
if [ "x$POWER_STATE" = "x" ]; then
#put everything in here
fi
```However, as far as I know the "hooks" for ACPI events are depriciated and don't do anything anymore, so you can't have the script be "interrupted" whenever you unplug. You just have to "poll" the battery within your script ("Are  you unplugged yet? [5 seconds later] How bout now? [5 seconds later] How bout now?" and so on.)

---

### Post by riahc3 on 2009-10-04
> **MaxIBoy said:**
>  How bout now? [5 seconds later] How bout now?" and so on.)
There isnt a problem with that.

If the laptop is plugged in, it should do the script and change. If it isnt, it should just leave the current wallpaper that the script has selected.

How can I do that?
(I dont like the RAMdisk solution too much...)

---

### Post by bluelamp999 on 2009-10-05
> **MaxIBoy said:**
> And yes, there's probably some program somewhere you can install instead of writing your own, but where's the fun in that?!

@MaxiBoy - absolute peach of a post...

Thanks!

---

### Post by brianbanksia on 2010-03-21
Excellent thanks

---

### Post by shvahabi on 2011-03-19
You can edit the XML file placed in a folder under desired name within /usr/share/backgrounds. There is an example in the folder named cosmos. Also you can give crebs a try. It is a software distributed under GPL and facilitates editing the XML file for such slide show!
Have fun!

---

### Post by sieve on 2011-05-05
Ah.  Will try that.

---

### Post by tsger on 2011-06-01
+1 for crebs (Create Background Slideshow).  Details here: 

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)

```
sudo add-apt-repository ppa:crebs/ppa
sudo apt-get update
sudo apt-get install crebs
```

---

