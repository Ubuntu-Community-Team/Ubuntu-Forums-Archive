---
title: "Visual Effects automatically resets."
date: 2010-03-09
forum: General Help
---

### Post by binoysankar on 2010-03-09
Hello guys i am new to ubuntu/Linux... i have one query.

I have downloaded Nvidia hardware driver which is recomended and when i enable **Visual Effects>Extra** it works fine. but when i restarts the PC the extra effect have changed to the **None** option. why is it so?
 i have already given the read-write permissions and all other permissions to root... but it seems to be reset after restarting...

Waiting for the experts solutions.

Thanks in advance...:KS

---

### Post by sikander3786 on 2010-03-09
There is already a thread on this topic.

[http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2](http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2)

Check it out and get back here if problem persists.

Regards.

Sikander.

---

### Post by shockandawe on 2010-03-09
I had the same problem. Had tried every workaround on the net, with no success.

However,

I uninstalled EVERYTHING compiz related from Synaptic Package Manager.

I also removed Cairo-dock.


Then I re-installed compiz by: 

searching for compiz in Synaptic, then I installed the option named 'compiz'. That installed everything, including extras.


After that I added it to my start up programs, by:

System -> Preferences -> Startup Applications

click on Add, and added the command: 

compiz --replace

click Save

------

Now it starts compiz every time after boot/login (you can see the screen flicker for a sec, this means it worked)

------

Extra: I installed 'Docky 2.1' instead of Cairo-dock. It is MUCH better. Smoother, and cleaner.



Hope this works for ya. It was driving me nuts for a while.

---

### Post by binoysankar on 2010-03-09
> **sikander3786 said:**
> There is already a thread on this topic.

[http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2](http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2)

Check it out and get back here if problem persists.

Regards.

Sikander.

Thanks for the help buddy...:p

> **shockandawe said:**
> I had the same problem. Had tried every workaround on the net, with no success.

However,

I uninstalled EVERYTHING compiz related from Synaptic Package Manager.

I also removed Cairo-dock.


Then I re-installed compiz by: 

searching for compiz in Synaptic, then I installed the option named 'compiz'. That installed everything, including extras.


After that I added it to my start up programs, by:

System -> Preferences -> Startup Applications

click on Add, and added the command: 

compiz --replace

click Save

------

Now it starts compiz every time after boot/login (you can see the screen flicker for a sec, this means it worked)

------

Extra: I installed 'Docky 2.1' instead of Cairo-dock. It is MUCH better. Smoother, and cleaner.



Hope this works for ya. It was driving me nuts for a while.

You saved my day...;) i was pissed off by this problem... now its really working fine... but i didn't find the Docky 2.1 anywhere...
thanks for the step by step procedure for helping a newbie...:D

Liking...UBUNTU very much:P

---

### Post by shockandawe on 2010-03-09
Glad it worked for ya. I know how annoying that was.

Here's how to add docky 2.1:

type these comands in a terminal:

sudo add-apt-repository ppa:docky-core/ppa
sudo apt-get update
sudo apt-get install docky

Here's the link where I got that info from:

[http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/](http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/)

-----

To start docky (after you have installed it) go to:

Applications -> Accessories -> Docky

-----

Enjoy!

---

### Post by binoysankar on 2010-03-09
> **shockandawe said:**
> Glad it worked for ya. I know how annoying that was.

Here's how to add docky 2.1:

type these comands in a terminal:

sudo add-apt-repository ppa:docky-core/ppa
sudo apt-get update
sudo apt-get install docky

Here's the link where I got that info from:

[http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/](http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/)

-----

To start docky (after you have installed it) go to:

Applications -> Accessories -> Docky

-----

Enjoy!

Thanks man... when i tried to install Docky using terminal the following error occured...

root@Kran:~# sudo add-apt-repository ppa:docky-core/ppa
sudo: unable to resolve host Kran
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault
root@Kran:~# 

what's the problem... even this problem occured when i tried to change the root password using the terminal... using the command sudo passwd root...


One more problem occured... after the successfull reinstallation of compiz, whenever i restarts the PC, web browser(firefox) automatically starts... i checked the Startup Applications but can't find it.... also help me in this too...:)

---

### Post by shockandawe on 2010-03-09
I'm not sure about the errors you are getting. 

Try typing in terminal:

sudo bash

it will ask you for your password, then you will be root.

If that works, type those commands again, but without the sudo at the start, like:

add-apt-repository ppa:docky-core/ppa
apt-get update
apt-get install docky

when you're done, type exit in the ternimal to exit root.

-----

About the firefox:

try going into:

System -> Preferences -> Startup Applications

then click on 'Options' tab

untick 'Automatically remember running applications when logging out'

or

Close all programs (including firefox) and click the 'Remember Currently Running Applications' button.


Thats about all I got hehe. I'm pretty new to this too, putting in plenty of hours of research.


------

Or if all else fails, use Google Chrome. I prefer it to firefox due to the fonts and its quickness. But it doesnt have as many options as firefox....something to think about.


Good luck!

---

### Post by binoysankar on 2010-03-09
> **shockandawe said:**
> I'm not sure about the errors you are getting. 

Try typing in terminal:

sudo bash

it will ask you for your password, then you will be root.

If that works, type those commands again, but without the sudo at the start, like:

add-apt-repository ppa:docky-core/ppa
apt-get update
apt-get install docky

when you're done, type exit in the ternimal to exit root.

-----

About the firefox:

try going into:

System -> Preferences -> Startup Applications

then click on 'Options' tab

untick 'Automatically remember running applications when logging out'

or

Close all programs (including firefox) and click the 'Remember Currently Running Applications' button.


Thats about all I got hehe. I'm pretty new to this too, putting in plenty of hours of research.


------

Or if all else fails, use Google Chrome. I prefer it to firefox due to the fonts and its quickness. But it doesnt have as many options as firefox....something to think about.


Good luck!

sudo bash also don't works showing the same error... but in the case of firefox it works fine... anyways thanks for all my clarifications...

OT: bye the way where you from? am from India... nice to meet you here...:D

---

### Post by shockandawe on 2010-03-09
No probs man. Im from Australia, nice to meet you too. Newbies have to help eachother out hehe :P

As for your sudo problem, I think that's a little too technical for me. I think it happened when you tried to change the root password -- apparently it is not recommended to change root password in Ubuntu (I could be mistaken, but I'm sure I read that somewhere)

------

Extra: If your 'maximize window' or 'show desktop' is slow, with delay/lag , you should see this thread:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8938814#post8938814](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8938814#post8938814)

My post is at the bottom. I just applied the fix and my Ubuntu effects run like a dream!

------

Cheers


edit: Actually, you should try fix your sudo/root before trying any fixes, incase something goes wrong.

---

### Post by rudihawk on 2010-04-18
> **shockandawe said:**
> I had the same problem. Had tried every workaround on the net, with no success.

However,

I uninstalled EVERYTHING compiz related from Synaptic Package Manager.

I also removed Cairo-dock.


Then I re-installed compiz by: 

searching for compiz in Synaptic, then I installed the option named 'compiz'. That installed everything, including extras.


After that I added it to my start up programs, by:

System -> Preferences -> Startup Applications

click on Add, and added the command: 

compiz --replace

click Save

------

Now it starts compiz every time after boot/login (you can see the screen flicker for a sec, this means it worked)

------

Extra: I installed 'Docky 2.1' instead of Cairo-dock. It is MUCH better. Smoother, and cleaner.



Hope this works for ya. It was driving me nuts for a while.

Thanks man, that helped me fix my problem I hope :D

---

