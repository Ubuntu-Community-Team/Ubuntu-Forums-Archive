---
title: "New User, Strange Problem... Can you help?"
date: 2009-09-25
forum: General Help
---

### Post by Oaney on 2009-09-25
*please skip to the 3rd paragraph if you want to get straight to the problem. paragraph 1 and 2 are more history and basics*

This being my first ever post, let me start with a brief background. I started life using windows. I got a Mac laptop for college, used it for 3-4 years before there was a 'beer' accident, and it became unreliable (though still functional!!! HOORAH). Being a student and in desperate need of a reliable computer, I got a PC for only a few hundred dollars at BestBuy (running vista :-(... bleh). My friend wanted me to try Ubuntu, it being the most user friendly version of linux according to him. So I have some exposure to the Unix shell and OS, but dont call myself an expert... I am new to linux, but have been exposed to unix... Onto my problems.

I installed Ubuntu 9.04 recently without touching my vista installation. I needed a fall back in case I couldnt use linux very well, call me overly cautious, but I cant be caught without a system that is familiar whilst in the middle of classes. Ubuntu created a swap partition (of course), but there appears to be two windows partitions, and two Ubuntu partitions... Whatever, I used the first ubuntu in the selection list when I booted up. I immediately had problems with wireless internet, had to install ndisgtk, the ndisgtk common package, ndisk stuff, the wireless card drivers (which you cant get if you dont have internet, but i cant get internet without the drivers... FRUSTRATING). Alright so here we go with my problems right now.

Here is my problem. I somehow managed to break Ubuntu. I am using the Vista partition right now so forgive me if I mess up on the specifics. Firstly It appeared that I was still getting wireless, but pidgin would not load. Upon loading, It will open for half a second, then appear to minimize to the bar, but disappears completely (as verified by the system processes application). I also tried to type 'pidgin' into the terminal, and it did the same exact thing, open for half a second and minimize and close... with no real hints in the terminal text (i forget what it said). During that session I tried to load firefox and connect and It would appear to be loading and just stall. After leaving Ubuntu alone for 1-2 days and trying again, pidgin does the same thing, but I can access the internet and load google, yahoo, etc...

I read that deleting the purple folder would fix the exact issues i was having with pidgin... go to places>home(or user)... press CTRL+H to show hidden directories, find .purple and delete it, reload pidgin. So i tried that...

Now Pidgin will load and says I dont have any accounts stored, so I enter my AIM account information, and click OK or continue. Pidgin hangs, I close it after several minutes, reload it, it asks for account info again, like it never stored the original stuff. At least pidgin seems to be working slightly better... I load firefox to find another solution only to find that the back (and presumable forward button) are not working. I loaded firefox, got the ubuntu welcome page, typed in google.com, searched for 'ubuntu pidgin wont load' or something to that effect, found this forum, but could never use the back button. I reloaded firefox and found the same thing. I restarted into ubuntu and found the same thing.

My problems as of current are that Pidgin will not save my account information and will not connect to the aim server. Also Firefox accesses the internet just fine, and loads web pages, but will not allow the 'back' button. As I am only allowed to go forward through typing URLs and clicking links, I am never allowed to try the forward button, but i presume it is the same...

After one week of ubuntu it seems i have irreparably broken the OS, and need to do a fresh install to start back at square one. My question is this: can anyone help me fix the current install, or can you help me to completely remove the original ubuntu and install a fresh copy off of my (homemade) 9.04 boot CD?

I hope that by reading my entire post, though it may be lengthy, it will provide you with all the necessary information to help me out of this predicament... Dual boot partitions, etc

Thank you SO much for even taking the time to read this rather odd post!

---

### Post by MegaLoler on 2009-09-25
I don't know about pidgon, but have you tried control-[ in place of the back arrow?  If that works, and the forward arrow won't work then try control-] for forward.

---

### Post by Oaney on 2009-09-25
CTRL + [
and
CTRL + ]
Ill restart to Ubuntu and try that now, and post the results in an edit.

EDIT:
I just tried those two CTRL commands. I have also tried backspace, right click options, back button, history, everything, there seems to be no record of my internet webpage browsing history... By the way, I am accessing the internet right now through UBUNTU because I am posting this edit from the Ubuntu OS... Just no Pidgin, and no History of browsing...

This seems to have started after i went to Places > Home Folder... CTRL + H to show hidden... and delete .Purple as suggested by a google search... does .Purple have anything to do with it?

Another quick note... I have to enter the WEP passcode each time I restart to Ubuntu, so it wont recognise the internet passcode from history either... seems to be a problem in saving my settings?

---

