---
title: "HOWTO:  Install a firewall and have it run on startup"
date: 2006-02-14
forum: General Help
---

### Post by issueperson on 2006-02-14
Hey all,
I'm new to the Ubantu community and discovered on install that ubuntu does not have a built-in firewall.  Linux tends to be more secure than a windows box, but all it takes is one exploit to completely screw you up.  I highly recommend that one of your top priorities be to install a firewall and have it run at boot.

This will take you through the steps if you aren't too familiar with ubuntu/debian.

Open a terminal and paste this in the window:
---------------------------------------------
sudo apt-get install firestarter
---------------------------------------------
then follow the prompts to install it.

this will install the "firestarter" firewall.  the problem is, you have to have root privlages to run it, so if you don't want to get an error message every time you start your computer about how you don't have permission:

EDIT:[COLOR="Red"]
Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------[/COLOR]
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: /usr/sbin/firestarter
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.

The last step is to get firestarter to boot at startup.
Click on Applications > System > Preferences > Sessions
And click on the "Startup Programs" tab.  
Click "+ Add"
and paste 
--------------------------------------
sudo firestarter --start-hidden
--------------------------------------
into the command line.

next time you boot linux, your firewall should start too (it will appear as a play button icon on your toolbar).

if you want to go ahead and start it without rebooting, you can type in a terminal:
--------------------
sudo firestarter
--------------------
There is also a shortcut to Firestarter installed on the System Tools menu.
Hope that helps some of you.

issueperson

---

### Post by dcstar on 2006-02-14
[QUOTE=issueperson]Hey all,
I'm new to the Ubuntu community and discovered on install that ubuntu does not have a built-in firewall.  Linux tends to be more secure than a windows box, but all it takes is one exploit to completely screw you up.  I highly recommend that one of your top priorities be to install a firewall and have it run at boot.
......[/QUOTE]
The proper place for all of these detailed "HOWTO"s is the "Tips and Tricks" forum:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

This is supposed to be a general Gnome-based Breezy Ubuntu forum, and while information like this will be appreciated by quite a few people it may also be missed by the many who do not use Gnome and do not bother with this forum.

---

### Post by issueperson on 2006-02-14
sorry, i meant to post it in the other forum but i clicked on the wrong tab in my browser... oops.

---

### Post by Red Knuckles on 2006-02-14
[QUOTE=issueperson]Hey all,
I'm new to the Ubantu community and discovered on install that ubuntu does not have a built-in firewall.  Linux tends to be more secure than a windows box, but all it takes is one exploit to completely screw you up.  I highly recommend that one of your top priorities be to install a firewall and have it run at boot.

This will take you through the steps if you aren't too familiar with ubuntu/debian.

Open a terminal and paste this in the window:
---------------------------------------------
sudo apt-get install firestarter
---------------------------------------------
then follow the prompts to install it.

this will install the "firestarter" firewall.  the problem is, you have to have root privlages to run it, so if you don't want to get an error message every time you start your computer about how you don't have permission:

Open a terminal and type:
----------------------------------
sudo gedit /etc/sudoers
----------------------------------
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: /usr/sbin/firestarter
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.

The last step is to get firestarter to boot at startup.
Click on Applications > System > Preferences > Sessions
And click on the "Startup Programs" tab.  
Click "+ Add"
and paste
--------------------------------------
sudo firestarter --start-hidden
--------------------------------------
into the command line.

next time you boot linux, your firewall should start too (it will appear as a play button icon on your toolbar).

if you want to go ahead and start it without rebooting, you can type in a terminal:
--------------------
sudo firestarter
--------------------
There is also a shortcut to Firestarter installed on the System Tools menu.
Hope that helps some of you.

issueperson[/QUOTE]


This worked well for me EXCEPT that I need to open some ports for Azureus. When I click on >Firestarter>policy>Inbound Traffic Policy the 'Add' option remains grayed out hence nonfunctional. What am I doing wrong???:confused:

Duh, Red Knuckles you blithering idiot. Go to >Firestarter>policy>Inbound Traffic Policy and right click anywhere in the allow service area and add ports till your hands fall off!!!\\:D/

---

### Post by anil_robo on 2006-03-17
I followed the procedure precisely, but this method does not appear to be working on dapper! Any ideas? :confused:

(Ideally, there should be an option in firestarter preferences to run the program on startup).

---

### Post by encompass on 2006-03-21
Does Firestarter let me forward UDP ports?  I can't seem to let them in to my server.
<confused>

---

### Post by frodon on 2006-03-21
There's no interest to run the firestarter GUI even on startup, the firestarter GUI is usefull only to change the firewall rules, You don't need to have the GUI opened to have the firewall running since firestarter only write iptable rules which control the embedded firewall.
_Your firewall is always active on startup whatever you do (GUI opened or not)._

In addition, i personally think that's it's not a secure way to use the embedded firewall to make the firestarter GUI launchable by a simple user because if someone come in your computer he will be able to launch the GUI and therefore open the ports.

encompass, i don't know how firestarter generates iptable rules but iptable support any kind of forwarding.
See this link to learn more about iptables : [http://www.iptablesrocks.org/](http://www.iptablesrocks.org/)

---

### Post by entryname on 2006-04-08
Reference firewall always being on regardless of firestarter - this isn't entirely true.

There is a url, scan.sygate.com, that checks firewalls. It's there to be used by the sygate firewall, but never mind. If you tell it to do a stealth scan, by rights it should show all ports as blocked. It will if firestarter is running, but on startup without firestarter they are only closed and I gather this means they are vulnerable. 

Interestingly if you close firestarter, having had it open, the response is still blocked, which appears to show the system is still running firestarter's settings.

I'm interested in the idea of copying firestarter's settings and then maybe applying them directly via a script or some such, but simply starting ubuntu and hoping for the best does not fully effectively protect the system.

---

### Post by sissaq on 2006-04-09
Thanks to Issueperson - firewall up and running.

Question: Pathetic coincidence or reality?

username ALL= NOPASSWD: /usr/sbin/firestarter

Firestarter wouldn't autoload (username replaced with mine) till I removed the space after the word ALL=
Previous reboots did not start firestarter.  Since removing the space and rebooting it starts every time.
I have NO idea if that space made a difference - but now it's working.

---

### Post by nanotube on 2006-04-09
by the way, if you want a simple, robust, and functional firewall, without screwing around with firestarter, you can just make your own iptables script. 

see link in my sig, and go to the "firewall" section for a nice howto.

---

### Post by entryname on 2006-04-09
See also [URL="http://www.ubuntuforums.org/showpost.php?p=905740&postcount=5"]Having firestarter write your iptables
[/URL]

---

### Post by TheWizzard on 2008-02-24
> **issueperson said:**
> Hey all,
I'm new to the Ubantu community and discovered on install that ubuntu does not have a built-in firewall.  Linux tends to be more secure than a windows box, but all it takes is one exploit to completely screw you up.  I highly recommend that one of your top priorities be to install a firewall and have it run at boot.


by default there are no services listening. with this default configuration a firewall is not needed. 


> **issueperson said:**
> 
The last step is to get firestarter to boot at startup.
Click on Applications > System > Preferences > Sessions
And click on the "Startup Programs" tab.  
Click "+ Add"
and paste 
--------------------------------------
sudo firestarter --start-hidden
--------------------------------------
into the command line.


firestarter is NOT a firewall. firestarter is nothing but a gui to edit iptables, the ubuntu firewall. there is no need to have firestarter running. 


> **issueperson said:**
> 
this will install the "firestarter" firewall.  the problem is, you have to have root privlages to run it, so if you don't want to get an error message every time you start your computer about how you don't have permission:

EDIT:[COLOR="Red"]
Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------[/COLOR]
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: /usr/sbin/firestarter
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.


this is a serious security tread! 
@OP: please remove this "advice".

---

### Post by bred on 2008-02-26
so, do I have to do this "HOW TO" or not?

---

### Post by bred on 2008-02-26
well right now with issueperson's tips I can load my firestarter but the problem that it loads but I don't have it in the tray icon...have no ideea what to do?

---

### Post by bodhi.zazen on 2008-02-26
As has been pointed out by frodon and TheWizzard, this how to is, IMO, seriously flawed.

See here  : [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

And here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

While the OP means well, I am afraid this thread contains some bad advice and issueperson does not appear to be active on these forums.

On that ground am closing it now.

---

