---
title: "Unable to Remove Broken TeamViewer Menu Link"
date: 2011-01-18
forum: General Help
---

### Post by Rybo85 on 2011-01-18
Ubuntu 10.04 32 bit

Background...

I was working with TeamViewer 5 just fine and then saw that TeamViewer 6 was available. I performed a complete removal of TeamViewer 5 via the Synaptic Package Manager and then did a clean install of TeamViewer 6 by executing the new deb file.

TeamViewer 6 was added to the Main Menu just fine, but after rebooting my laptop, the TeamViewer 6 Main Menu launcher was gone and a broken link was there in its place.

I have since followed the solution in the below thread to get a valid TeamViewer 6 launcher back in the Main Menu, but I cannot get rid of the broken link.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1665523](http://www.uluga.ubuntuforums.org/showthread.php?t=1665523)


In the System->Preferences->Main Menu window, the broken link is basically frozen. I can't hide it or delete it. Is there some file I'm just going to have to update to get rid of it?

In case it helps, I've attached a screen shot of the broken link.

---

### Post by kn0w-b1nary on 2011-01-18
u can try 2 remove it through:
1. (manual) in termianl: sudo natilus
goto /usr/share/applications/
and delete the broken file.

2. in terminal: sudo apt-get install bleachbit
then: sudo bleachbit

select "delete broken desktop files"

Hope this helps!

---

### Post by Rybo85 on 2011-01-19
Thanks for the response, but unfortunately neither did the trick.

I don't see any other TeamViewer item in /usr/share/applications/  and BleachBit wasn't able to get rid of it through deleting broken desktop files.

---

### Post by kn0w-b1nary on 2011-01-20
Have you tried using GNOME Menu Editor?

---

### Post by kn0w-b1nary on 2011-01-21
if u don't have it type in terminal:
sudo apt-get install alacarte

Good Luck!

---

