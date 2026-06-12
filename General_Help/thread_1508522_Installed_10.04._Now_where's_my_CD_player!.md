---
title: "Installed 10.04. Now where's my CD player!?"
date: 2010-06-13
forum: General Help
---

### Post by mar10d65 on 2010-06-13
I'm new to UBUNTU and Linux in general. I completely erased the version of Windows Vista that came with my Acer laptop and installed a fresh version 9.10 from a “The Best of LINUX” magazine. Then I upgraded to 10.04 from the update manager. Daring or stupid move (jury's still out) on my part not knowing if I was going to like the Linux world.
 

 With the exception of a few learning curves everything worked great. But then I noticed that I couldn't get any of my CDs to run after install. I checked some of the forums including this one and found that there seems to be a growing problem with UBUNTU 10.04 not recognizing or auto "mounting" CD players.  
 

 Is there a developing fix for this or am I simply too much of a Linux newbie to understand that all answers lie within the seemingly complicated command line lingo of the the “Terminal” world? Anybody got any ideas?

 
Please help convert a Microsoft Windows drone to this brave new world of Linux and Open Source.

_**References:**_
[http://newyork.ubuntuforums.org/showthread.php?p=7287286](http://newyork.ubuntuforums.org/showthread.php?p=7287286)
 [http://georgia.ubuntuforums.org/showthread.php?p=9037153](http://georgia.ubuntuforums.org/showthread.php?p=9037153)
[http://ubuntuforums.org/showthread.php?t=1456917&highlight=Auto+Mount+CD+Player](http://ubuntuforums.org/showthread.php?t=1456917&highlight=Auto+Mount+CD+Player)

---

### Post by germanix on 2010-06-13
You should have no problem playing CD`s, probably just need some codecs. The MPlayer that is already installed does a good job but the VLC player is better in my opinion. You can go to Synaptic Package Manager and install both the "Ubuntu Restricted Extras" which will give you the codecs and you can install the VLC player from there. It is however pretty simple and fast to install all that you need via the Terminal. Just open the Terminal and do the following.

Starting directions: All of the following are simple copy/paste commands. If a command is too long, wrapping to the next line in the terminal, don't worry about it. It'll be alright. Don't forget to copy every character that's needed per line since there can be no spelling errors. If prompted for a password, enter your Ubuntu user password. Don't forget to use your enter (return) key after each of the following pasted command (text) lines and if prompted to "OKAY" additional installations or space to be used up on your hard disk, respond with Y in the terminal (followed by enter).
Yes, all of the following must be copied and pasted as one line or command ...&#8232; 

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
Did you remember the enter key? Good, then let's continue with this line:&#8232;
 sudo apt-get --quiet update
Followed by this line here: (then enter key)&#8232;
 sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
And finally this important step (four more after this):&#8232;
 sudo apt-get --quiet update
Starting with the next line we'll be installing the actual playback codecs:&#8232;
 sudo apt-get install non-free-codecs
Let's not forget about DVD playback support:&#8232;
 sudo apt-get install libdvdcss2
Some needed Windows related codecs:&#8232;
 sudo apt-get install w32codecs
And finally, installation of codecs into the multimedia players:&#8232;
 sudo apt-get install vlc mplayer
There, that's it already! Make sure everything has completed and then type exit in order to close the terminal or console window. The multimedia players are located in your Sound & Video section, available by clicking on your Ubuntu start button.

---

### Post by Plumtreed on 2010-06-13
Easiest way to go is via Synaptic Package Manager

Search for and select Ubuntu-Restricted-Extras

Once downloaded you should be able to play CDs....you may have to reboot???

You don't have to go near a terminal untill you are ready.

You could also check on a OS called Mint, a fork of Ubuntu,  which has all these things included!

---

