---
title: "i cannot upgrade from ubuntu 8.04"
date: 2011-08-07
forum: General Help
---

### Post by dan0804smith on 2011-08-07
when ever i go to the update manager and click update nothing comes up.  my gui doesnt match the ones on the tutorials online.  the laptop i got directly from dell and it came with 8.04 on it. i dont know if that maeks a difference.  is there a place where i can download the the UPDATE file and upgrade it manually useing the command prompt?  if this is possible then what command would i use?  is there an easier way to do this?  should i back up mu files?

---

### Post by dan0804smith on 2011-08-07
whenever i check for updates it says:W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE

---

### Post by Nithogger on 2011-08-07
I had the same problem and I simply Reinstalled ubuntu, but that means losing lots of personal themes and settings which you obviously don't want to. There is a way of dealing with this manual. My brother once did it with a computer of mine. I don't know exactly what it is. I will ask him later and post what to do here. 
For now I can only tell you what will happen. It's quite simple:  You open a specific folder (don't know which one) and rename all the 'Hardy Heron's to Natty Narwhal (Ubuntu version 11.04). so you are basicly telling your ubuntu version that you have a different version installed and thus will update manager look for updates that are for the 11.04 version. It takes a long time to update all your programmes but it is faster then reinstalling ubuntu :P Make sure you have a good movie to watch while ubuntu is updating. hehe

So, it can be done and I will post it here how to do it manual.
[SIZE=1]*[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][I]*[/COLOR][/FONT][/COLOR][/I][/SIZE]

---

### Post by goldshirt9 on 2011-08-07
save all of the items you wish to keep and then do a fresh install
from 8.04 to 11.04 is a big upgrade and is asking for things to go wrong :(

i went from 10.04 to 11.04 and it went wrong so dont take the chance.

---

### Post by isee on 2011-08-07
I have a fresh install of 10.04, and am not planning anything until the next LTS version.

Save everything and do a fresh install, thats what I would do

---

### Post by Matt__ on 2011-08-07
two things...what dell is it?
and is this what youve tried so far?
```

[SIZE=2]**Network Upgrade for Ubuntu Desktops (Recommended) **[/SIZE]You can easily upgrade over the network with the following procedure. 

[LIST=1]
[*]Start System/Administration/Software Sources
[*]On the **Updates** tab, set **Show new distribution releases:** to **Long term support releases only**, then press **Close**.
[*]Press Alt-F2 and type update-manager
[*]Click the **Check** button to check for new updates.
[*]If there are any updates to install, use the **Install Updates** button to install them, and press **Check** again after that is complete.
[*]A message will appear informing you of the availability of the new release.
[*]Click **Upgrade**.
[*]Follow the on-screen instructions.
[/LIST]

```you could also try this in the terminal
```
sudo apt-get dist-upgrade
```but to be honest you would be better off saving all your data and doing a fresh install via live cd or usb.
 


//edit: a fresh install will not include the dell proprietary restore partition (not that you need it really)

---

### Post by Nithogger on 2011-08-08
alright. 
What you also can do is this: start up terminal. type in ```
sudo gedit /etc/apt/sources.list
```
you enter your password, wait a little bit, and you see a document appearing with some text in it. search for the name of your ubuntu version (ctrl + h to replace, option can also be found in the 'search' tab) . which is hardy (not the heron part) and change it to natty (this is ubuntu 11.04). Aftrer you're done with the replacing, save it and you might want to restart your computer to be super safe. Start update manager and update the whole thing. There you. It worked for me, without the loss of data. But! Make a back up to be even more super safe.. :)
Hope this'll help

---

### Post by mue.de on 2011-09-14
I had a long hard road from Hardy Heron direct to Lucid Lynx, did it wrong: you should take the steps between the versions first
 
If your familiar with german, look at that: [http://wiki.ubuntuusers.de/Upgrade_Hardy_auf_Lucid](http://wiki.ubuntuusers.de/Upgrade_Hardy_auf_Lucid)

---

