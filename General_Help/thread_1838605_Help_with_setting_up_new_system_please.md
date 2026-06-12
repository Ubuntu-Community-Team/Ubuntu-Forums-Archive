---
title: "Help with setting up new system please"
date: 2011-09-04
forum: General Help
---

### Post by KaIIen on 2011-09-04
My new laptop (and my old one) are running 11.04. I have had some trouble getting everything set up on the new system. I tried this first:

[[COLOR="Blue"]_Moving you Ubuntu system in 3 easy steps_[/COLOR]]("http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/")

This resulted with nothing but trouble. I copied files without being root (gksu nautilus) and Ubuntu wouldn't boot. So I wiped it and reinstalled fresh and tried as root. It sort of worked that time, but still had severe issues. Firefox refused to open, etc. So I reinstalled fresh again, and as root have just copied my files into my new home. I am thinking my issues are because this is the first fresh install for me since either 9.10 or 10.04. I have does the live upgrade since.

A few questions here, thanks for any assistance!

1. What do i need to move to new system to have all my saved login and password info for both Firefox and Chrome?

2. Am i able to copy setup info for Evolution? It was a pain to set up before and would like to simply move it somehow.

3. ALL the files I have copied to the new system have a little padlock on the icon. I assume it's because these files were created on my old system with a "different" owner. I Googled to no end and found nothing about that little padlock on the icons...

4. On sire such as this, when using Chrome, there is no word wrap at the end of a line instead of the whole word moving to the next line. It posts ok, but I find this disconcerting to see as I type... 

5. I can not get the cap lock to come on at boot. I have it set to "Numlock on at boot" in the bios but Ubuntu chooses to ignore that. 

Anything else you guys think would be worth my while to migrate?

THANK you!

---

### Post by josephmills on 2011-09-04
> **KaIIen said:**
> My new laptop (and my old one) are running 11.04. I have had some trouble getting everything set up on the new system. I tried this first:

[[COLOR=Blue]_Moving you Ubuntu system in 3 easy steps_[/COLOR]]("http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/")

This resulted with nothing but trouble. I copied files without being root (gksu nautilus) and Ubuntu wouldn't boot. So I wiped it and reinstalled fresh and tried as root. It sort of worked that time, but still had severe issues. Firefox refused to open, etc. So I reinstalled fresh again, and as root have just copied my files into my new home. I am thinking my issues are because this is the first fresh install for me since either 9.10 or 10.04. I have does the live upgrade since.

A few questions here, thanks for any assistance!

1. What do i need to move to new system to have all my saved login and password info for both Firefox and Chrome?

2. Am i able to copy setup info for Evolution? It was a pain to set up before and would like to simply move it somehow.

3. ALL the files I have copied to the new system have a little padlock on the icon. I assume it's because these files were created on my old system with a "different" owner. I Googled to no end and found nothing about that little padlock on the icons...

4. On sire such as this, when using Chrome, there is no word wrap at the end of a line instead of the whole word moving to the next line. It posts ok, but I find this disconcerting to see as I type... 

5. I can not get the cap lock to come on at boot. I have it set to "Numlock on at boot" in the bios but Ubuntu chooses to ignore that. 

Anything else you guys think would be worth my while to migrate?

THANK you!



How big is your system? There is a tool called remastersys 
remastersys has a couple of options one of them is to back up your hole entire system. 

what this does is copys your whole entire home dir and all of its settings then makes a squafs file and also a casper 

what does that mean 
welll 
a live dvd or your system that you can take anywhere with you and also install on any computer with all of your data all ready on there 

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by KaIIen on 2011-09-04
> **josephmills said:**
> How big is your system? There is a tool called remastersys 
remastersys has a couple of options one of them is to back up your hole entire system. 

what this does is copys your whole entire home dir and all of its settings then makes a squafs file and also a casper 

what does that mean 
welll 
a live dvd or your system that you can take anywhere with you and also install on any computer with all of your data all ready on there 

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

I think my old system would be way too big to make it into a livecd. And I have to say the new install is a little peppy compared to the previous. 


Aside from that, what the easiest way to get my bookmarks and saved login info brought over for Chrome and Firefox?

---

### Post by Quarkrad on 2011-09-04
I have done this many times with new installs (copy the setup of my old firefox environment, bookmarks, passwords, etc) from old to new PC.  I don't use Chrome but the logic may well be the same. On the new system in the Home folder there is a hidden folder called .Mozilla - rename this folder .oldMozilla  Open the .Mozilla folder and delete all the contents so you land up with an empty folder.  Go to you old system (backup) and copy the contents of /Home/.Mozilla to .Mozilla in your new system.  Restart firefox and your new firefox setup will look/be the same as your old system.  If it all works OK delete the .oldMozilla folder on your new system.  When I have done this (many times) I do not bother with the re-naming I just delete and copy/paste from old to new.  I do all this as normal user - not root.

---

### Post by KaIIen on 2011-09-04
> **Quarkrad said:**
> I have done this many times with new installs (copy the setup of my old firefox environment, bookmarks, passwords, etc) from old to new PC.  I don't use Chrome but the logic may well be the same. On the new system in the Home folder there is a hidden folder called .Mozilla - rename this folder .oldMozilla  Open the .Mozilla folder and delete all the contents so you land up with an empty folder.  Go to you old system (backup) and copy the contents of /Home/.Mozilla to .Mozilla in your new system.  Restart firefox and your new firefox setup will look/be the same as your old system.  If it all works OK delete the .oldMozilla folder on your new system.  When I have done this (many times) I do not bother with the re-naming I just delete and copy/paste from old to new.  I do all this as normal user - not root.

Thanks! 
As for Chrome, I dunno where it's info is saved. There doesn't appear to be a hidden folder for it.

---

### Post by Quarkrad on 2011-09-04
OK - I've just installed Chrome.  It looks like the files you need to transfer are again in a hidden folder in your **home** folder.  Have a look at .config/chromium - it looks like all you need is there.  Set up some bookmarks and experiment - looks like this may do the same job as .mozilla

---

### Post by KaIIen on 2011-09-04
> **Quarkrad said:**
> OK - I've just installed Chrome.  It looks like the files you need to transfer are again in a hidden folder in your **home** folder.  Have a look at .config/chromium - it looks like all you need is there.  Set up some bookmarks and experiment - looks like this may do the same job as .mozilla

Man you're awesome, thank you! I didn;t think to look inside .config!Thanks!

---

