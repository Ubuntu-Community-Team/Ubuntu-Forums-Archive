---
title: "i cant found the Both panels"
date: 2010-04-21
forum: General Help
---

### Post by X-Cursed-Devil on 2010-04-21
[LEFT]Hi all , i am total new in linux
i am running ubuntu 9.4 
yesterday i was trying to remove evolution mail and it's okay it's done removed 
after restart - i cant found the Both panels 
i found a way to restore them on this [site]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html") but the way is by using terminal 
and . i cant open the terminal - cuz i cant found the panels 
even alt+f2 - do nothing 
i found a download link for gnome-terminal-2.30.0 packege , But i don't know how to install it 
i downloaded it form [here]("http://caesar.acc.umu.se/pub/GNOME/sources/gnome-terminal/2.30/gnome-terminal-2.30.0.tar.gz")

i want to get the panels back :(

plz any one can help me :confused: or give me a tip 

sorry for my bad english :(
 [/LEFT]

---

### Post by jaco223 on 2010-04-21
What happens when you press "alt+f2"?
Does it bring up a window that say Run Application? 
Let me know then i can further try to help.


Jaco

---

### Post by X-Cursed-Devil on 2010-04-21
nothing happen - just nothing 

thanks for you attention

---

### Post by 2hot6ft2 on 2010-04-21
Have you tried rebooting and going into Recovery mode then once all the text goes by and you have choices choose Shell Prompt.
It will show up at the bottom of the screen then you can run the commands from there.
```
sudo gconftool --recursive-unset  /apps/panel
```
```
sudo rm -rf ~/.gconf/apps/panel
```
then ```
sudo reboot
```
and boot like normal.
No need to run
```
pkill gnome-panel
```
Because gdm hasn't started yet when you ran the other 2 commands and you're rebooting.

P.S. Welcome to the forum

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> 
i found a download link for gnome-terminal-2.30.0 packege , But i don't know how to install it 
i downloaded it form [here]("http://caesar.acc.umu.se/pub/GNOME/sources/gnome-terminal/2.30/gnome-terminal-2.30.0.tar.gz")

That may break your system. That is NOT how we do things in ubuntu. We use apt-get, Synaptic Package Manager, software center and stuff.
The terminal should be in
Applications > Accessories > Terminal

Although I must say that is an unusual source you have there ...lol
Academic Computer Club Umeå University

---

### Post by akakingess on 2010-04-21
As last I had heard, Evolution was a part of the Gnome desktop, so that you couldn't uninstall it without doing the same with the whole GDM. Someone please correct me if that has changed, but he would have to load into the recovery/shell prompt mode and then reinstall the Gnome Desktop Manager. Again, I may have missed something amongst the updates, but that is what I thought was the case?

---

### Post by 2hot6ft2 on 2010-04-21
> **akakingess said:**
> As last I had heard, Evolution was a part of the Gnome desktop, so that you couldn't uninstall it without doing the same with the whole GDM. Someone please correct me if that has changed, but he would have to load into the recovery/shell prompt mode and then reinstall the Gnome Desktop Manager. Again, I may have missed something amongst the updates, but that is what I thought was the case?
If I go to Synaptic and mark Evolution for complete removal it only marks 4 other packages each starting with evolution
Screenshot attached

---

### Post by akakingess on 2010-04-21
Dang, wish I would have known that sooner, because I know for a fact that in some previous versions you couldn't uninstall Evolution without doing the GDM, which is the only reason that it's still on my system (Thunderbird user, myself). Thanks for the info. Sorry if I got y'all barking up the wrong tree ;)

---

### Post by X-Cursed-Devil on 2010-04-21
> **2hot6ft2 said:**
> Have you tried rebooting and going into Recovery mode then once all the text goes by and you have choices choose Shell Prompt.
It will show up at the bottom of the screen then you can run the commands from there.
```
sudo gconftool --recursive-unset  /apps/panel
``````
sudo rm -rf ~/.gconf/apps/panel
```then ```
sudo reboot
```and boot like normal.
No need to run
```
pkill gnome-panel
```Because gdm hasn't started yet when you ran the other 2 commands and you're rebooting.

P.S. Welcome to the forum

okay i just did what you said and it restore every thing like if i just install new ubuntu ( the themes the options the desk top ) 
but i still have my programs and still have my add-ons 
and the panels didn't back :(

---

### Post by X-Cursed-Devil on 2010-04-21
> **2hot6ft2 said:**
> If I go to Synaptic and mark Evolution for complete removal it only marks 4 other packages each starting with evolution
Screenshot attached

yes i did that , but i marked tow more packages witch was having Evolution word in the description 
i don't remember the tow packages names

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> okay i just did what you said and it restore every thing like if i just install new ubuntu ( the themes the options the desk top ) 
but i still have my programs and still have my add-ons 
and the panels didn't back :(
Can you open a terminal now by going with Alt+F2
and run the commands
```
sudo gconftool --recursive-unset  /apps/panel
```
```
sudo rm -rf ~/.gconf/apps/panel
```
then
```
pkill gnome-panel
```
And why would you not have your programs?
What else have you done?

---

### Post by X-Cursed-Devil on 2010-04-21
but why the terminal not opining  with alt+f2 ?
i sill can't found the panels or open the terminal 
one more thing i also removed many things not just evolution 
i also removed Bluetooth and office stuff 
i hope this will help you finding the problem :(

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> yes i did that , but i marked tow more packages witch was having Evolution word in the description 
i don't remember the tow packages names
Let me guess, you removed
evolution-data-server-common
Yes, that would mess things up (see screenshot)
Now you'll have to reboot into recovery mode and select Shell prompt with networking and re-install it.
gnome-panel was part of it.

You might just be better off re-installing ubuntu and not removing things you don't know about yet. At least until you learn about it some.

---

### Post by akakingess on 2010-04-21
I guess maybe that's what I was thinking of, was the gnome-panel, not the whole desktop, but at least I was kind of headed in that direction? ;)

---

### Post by X-Cursed-Devil on 2010-04-21
> **2hot6ft2 said:**
> Let me guess, you removed
evolution-data-server-common
Yes, that would mess things up (see screenshot)
Now you'll have to reboot into recovery mode and select Shell prompt with networking and re-install it.
gnome-panel was part of it.

yes you are right i removed evolution-data-server-common 
okay i will try this now - i hope i works 
but what is the code ?

---

### Post by X-Cursed-Devil on 2010-04-21
is it sudo apt-get install evolution-data-server-common
i hope i am right :)

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> is it sudo apt-get install evolution-data-server-common
i hope i am right :)
Yes, that's it. Maybe you wont need to do them each one at a time.

---

### Post by 2hot6ft2 on 2010-04-21
> **akakingess said:**
> I guess maybe that's what I was thinking of, was the gnome-panel, not the whole desktop, but at least I was kind of headed in that direction? ;)
Just selecting "Evolution" will only take 4 more with it but yeah the rest is pretty integrated into the system. I almost went that way a few years ago when I used Thunderbird too.

---

### Post by X-Cursed-Devil on 2010-04-21
okay i got to the shell and installed the evolution-data-server-common package
but unfortunately i sill can't found the panels or open the terminal :(
maybe some thing more need to be installed

---

### Post by X-Cursed-Devil on 2010-04-21
maybe i removed the terminal .what if i did 
how to re-install it

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> okay i got to the shell and installed the evolution-data-server-common package
but unfortunately i sill can't found the panels or open the terminal :(
maybe some thing more need to be installed
Each one of the items you removed until you get them back.
Seriously I would just re-install the whole system it would be faster and then it would work right. Be careful when removing things and look at what else they affect before doing it.
When in doubt as to whether or not it's safe to remove something ask. Many things are interdependent. They rely on each other to work.

If you want a minimal install use the server edition and build it up from there to what you want.
The terminal is
```
sudo apt-get install gnome-terminal
```
At least

---

### Post by X-Cursed-Devil on 2010-04-21
> **2hot6ft2 said:**
> Each one of the items you removed until you get them back.
Seriously I would just re-install the whole system it would be faster and then it would work right. Be careful when removing things and look at what else they affect before doing it.
When in doubt as to whether or not it's safe to remove something ask. Many things are interdependent. They rely on each other to work.

If you want a minimal install use the server edition and build it up from there to what you want.

i know that i make i mistake but i hope if i can fix it :(
plz try one more time 
what items that the panels depend on 
and i will install it all

---

### Post by X-Cursed-Devil on 2010-04-21
> **2hot6ft2 said:**
> Each one of the items you removed until you get them back.
Seriously I would just re-install the whole system it would be faster and then it would work right. Be careful when removing things and look at what else they affect before doing it.
When in doubt as to whether or not it's safe to remove something ask. Many things are interdependent. They rely on each other to work.

If you want a minimal install use the server edition and build it up from there to what you want.
The terminal is
```
sudo apt-get install gnome-terminal
```At least

it said that the terminal is already installed :confused: then why it wont open by alt+f2

---

### Post by 2hot6ft2 on 2010-04-21
Because it depends on something else you removed.
> **X-Cursed-Devil said:**
> i know that i make i mistake but i hope if i can fix it :(
plz try one more time 
what items that the panels depend on 
and i will install it all
See the list in the picture I attached to [post #13 here]("http://ubuntuforums.org/showpost.php?p=9156284&postcount=13")
The last one in the list you probably didn't have in the first place but I have it.

---

### Post by X-Cursed-Devil on 2010-04-21
okay that's did it 
the system be come lite bit slow but it's good 
thanks really thank you for helping me
last thing pls - how can i open the ubuntu studio ??

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> okay that's did it 
the system be come lite bit slow but it's good 
thanks really thank you for helping me
last thing pls - how can i open the ubuntu studio ??
Like I said you probably didn't have that in the first place.
It's not a single app. I'm not even sure what all it has since I run Ubuntu Ultimate Edition so my stuff isn't the same a regular Ubuntu.

I have a lot more stuff which you would be going nuts trying to uninstall.

Just remove ubuntu-studio

And you're welcome.

---

### Post by X-Cursed-Devil on 2010-04-21
i want to remove the print packages what items should i remove ??

---

### Post by X-Cursed-Devil on 2010-04-21
also how to remove ubuntu studio ??

---

### Post by 2hot6ft2 on 2010-04-21
> **X-Cursed-Devil said:**
> i want to remove the print packages what items should i remove ??
What print packages?
cups is what I think you mean and I wouldn't recommend removing it.

> **X-Cursed-Devil said:**
> also how to remove ubuntu studio ??
To remove it use
```
sudo apt-get remove ubuntustudio-desktop
```
Or search for it in synaptic
System > Administration > Synaptic Package Manager
then right click and select remove package
Then on Apply

---

### Post by X-Cursed-Devil on 2010-04-22
System > Administration > Synaptic Package Manager
that is where i found it 
okay man - really thanks i makes you busy 
thank you :)

---

### Post by 2hot6ft2 on 2010-04-22
Welcome
Have fun, and you may just want to start with a minimal install next time and only add what you want.
And on that note I'm calling it a night.

---

