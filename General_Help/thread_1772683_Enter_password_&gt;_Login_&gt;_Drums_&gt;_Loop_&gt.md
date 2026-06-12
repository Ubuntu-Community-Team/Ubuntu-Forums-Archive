---
title: "Enter password &gt; Login &gt; Drums &gt; Loop &gt;  Enter password &gt; Login &gt; Drums &gt; Loop....."
date: 2011-05-31
forum: General Help
---

### Post by darren123web on 2011-05-31
[http://ubuntuforums.org/showthread.php?t=1278395&page=3](http://ubuntuforums.org/showthread.php?t=1278395&page=3)

Hi guys -

I'm running 10.04 LTS,

I was originally searching for info re my networking problems below ->>>>

Unfortunately one of the suggestions (uninstall and reinstall nautilus) seems to have left me in an endless Loop trying to login.
Enter password > Login > Drums > Loop back to login screen > Enter password > Login > Drums....rinse & repeat

->>>>>(original issue)
My Windows 7 PC can see the home folder on 10.04 Ubuntu no probs.

I can see in Nautilus my WORKGROUP, and Windows 7 machine, but was getting 'Nautilus cannot handle "network" locations' type error, now I get ''Failed to mount Windows share'' when I try to navigate there from within Nautilus.

Have tried

sudo apt-get install samba
sudo apt-get install gvfs-backends

in both cases both are the latest versions already....

I've only been tinkering with Ubuntu for a very short time, so I'm a little hesitant to start uninstalling stuff I'm not sure about - but is the best way forward to remove samba and gvfs through Synaptic?


UPDATE - 

Oh dear.

I also tried something noted in this thread.....

[http://ubuntuforums.org/showthread.php?t=1444433](http://ubuntuforums.org/showthread.php?t=1444433)

which suggested uninstalling and reinstalling nautilus might do the trick.

Now when I try to login, I just go round in circles - enter password and Enter, get a little drum, then it comes back to login screen, enter password and enter, just repeating like so....

Any ideas anyone? I'm fried.....

Any pointers at all, would be great!

Thanks.
Darren

---

### Post by darren123web on 2011-05-31
Okay, so thanks to this thread - [http://ubuntuforums.org/showthread.php?t=1603117&highlight=login+loop&page=3](http://ubuntuforums.org/showthread.php?t=1603117&highlight=login+loop&page=3)

I tried a few things, but basically I got to the login screen, hit Ctrl + Alt + F1.

Entered login details.

Then I tried a few commands as suggested in the thread above - 


[LIST]
[*]sudo dpkg-reconfigure gdm
[*]sudo apt-get --purge --reinstall install gdm gnome-session
[/LIST]
The didn't work for the guy on that thread - but they did work for me.

I'm now logged in.  (Have tested shut down & power up - that seems fine.)

Back to trying to figure out why I can't see my Windows machine over the network.....;-)

Hope that helps someone else at some point....
D

---

