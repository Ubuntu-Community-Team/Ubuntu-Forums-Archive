---
title: "Cannot delete planeshift because apparently it doesn't exist (but of course does)"
date: 2011-07-03
forum: General Help
---

### Post by zerobotman on 2011-07-03
So i tried to install planeshift in ubuntu without looking at the instructions and it is now both unusable cannot be deleted.  basically i've had a mental kernal panic being a linux nub and all and i think i made everything worse. Anyway so far as i can tell it's very messed up and here is what i did. Please help me delete this so i can install it right and not have 500 mb wasted.  

Step one: first installation. 

After torrenting the game from the web site i installed it with the following commands

> 
cd ~/Desktop
chmod +x PlaneShift-v0.5.7-x64.run
./PlaneShift-v0.5.7-x64.run
During the installer i found that the install location was not valid and so i chose the following directory which i created

> 
/home/steven/games/Planeshift
I then made the desktop icon functional with the following

> 
chmod +x PlaneShift.desktop
After the installer i clicked the game and it even updated. then it shut down and the desktop icon never worked again. the uninstaller however appeared to work fine so that's what i did

Step two: second install.

for this i did pretty much everything except i did it with the "sudo" prefix. the game however refused to load and i got this error when trying to launch it

> 
THERE WAS AN ERROR LAUNCHING THIS APPLICATION
Details: Failed to execute child process "/home/steven/games/Planeshift/PlaneShift/pslaunch" (Permission denied)
well... so i figured i needed to run it as root in terminal so i typed the following

> 
 cd ~/Desktop
./PlaneShift.desktop
 this is what i got for both the planeshift icon and uninstaller

> 
./PlaneShift.desktop: line 1: [Desktop: command not found
./PlaneShift.desktop: line 9: Application: command not found
./PlaneShift.desktop: line 9: Game: command not found
Step three: mindless command mashing that probably messed more things up

At this point i've gotten really upset. i start looking up commands. i started by doing what they tell me NOT to do in the ubuntu tutorials below and make my account root using the following commands (i didn't read the message below). thing is i couldn't get onto the desktop using "cd ~/Desktop" when i was root but i figured out i needed to do "cd /home/steven/Desktop" instead. here is what i typed 

> 
sudo -i -u <username>

and here's the tutorial i used
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

i then preceded to try to make the executable belong to nobody by doing this

> 
chmod 666 PlaneShift.desktop
which i did for the installer ty oo but to no avail. i really want to delete it so that i can reinstall it or at least be rid of it!

---

