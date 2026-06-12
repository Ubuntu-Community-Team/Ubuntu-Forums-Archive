---
title: "disable updates?"
date: 2006-04-24
forum: General Help
---

### Post by Angry penguin on 2006-04-24
I recently installed firefox 1.5 but I am still recieving updates for firefox 1.0.8.
I tried:
[HTML]sudo apt-get remove mozilla-firefox[/HTML]
and that didnt get rid of them.
I looked at trying to remove firefox using synaptic but it listed gnome, gnome-core and other critical portions of the OS, which i didn't wish to remove.

Is there a way to turn off updates for packages that I don't wish to update?

---

### Post by bswilson on 2006-04-24
I am experiencing the same issue.  However, I decided to test what'd happen if I went ahead and accepted the Fx 1.0x updates.  Guess what?  

Nothing happened.  I have an icon representing Fx 1.5.0.2, and it wasn't affected.  You might be able to get away with just accepting the updates.

Although I'm just learning about Synaptic and apt-get on Ubuntu, I *think* you'd have to disable an entire source of code to stop the Fx 1.0x udpates, and you probably don't want to do that.

---

### Post by Angry penguin on 2006-04-24
Well, I really don't want to take any chances with messing up my firefox install. I was kinda hoping there was an official fix or an option for this. If there isn't there should be, and I would hope that it will appear in Dapper.

---

### Post by bswilson on 2006-04-25
I'm right there with you!  I **hope** that the plan is not only to include Fx 1.5.x with Dapper, but that there's a way to CHOOSE which Firefox version you want to be installed, with a way to ignore all other (versions)...

---

### Post by Hairy_Palms on 2006-04-25
if u installed firefox with a .deb then it will automatically replace 1.08, if u installed with autoamtix or from mozilla then updateing the synaptic version wont affect 1.5 in the slightest.

---

### Post by Hoffmann on 2006-04-25
[QUOTE=Angry penguin]I recently installed firefox 1.5 but I am still recieving updates for firefox 1.0.8.
I tried:
[HTML]sudo apt-get remove mozilla-firefox[/HTML]
and that didnt get rid of them.
I looked at trying to remove firefox using synaptic but it listed gnome, gnome-core and other critical portions of the OS, which i didn't wish to remove.

Is there a way to turn off updates for packages that I don't wish to update?[/QUOTE]

I did the same bswilson did. I mean, I decided to accept updating to Firerox 1.0.8. NOTHING wrong happened at all.  My Firefox 1.5.0.2 was NOT affected. All is fine.

Hoffmann

---

### Post by Angry penguin on 2006-04-25
well I just accepted the updates, it didn't change me over to 1.0.8 but it changed my icon back to the original blue globe icon, not cool. I used the wiki to install 1.5, my suggestion to anyone in the future would be to copy the .mozilla folder in your home folder to the desktop before you do the update then copy it back after the update. I think that should retain all the original settings. PITA.

---

### Post by bluevoodoo1 on 2006-04-25
You can "lock" a package so you won't be prompted to update it. 
Search for firefox, highlight it, then go to Package and then Lock Version.

---

### Post by Hoffmann on 2006-04-25
[QUOTE=Angry penguin]well I just accepted the updates, it didn't change me over to 1.0.8 but it changed my icon back to the original blue globe icon, not cool. I used the wiki to install 1.5, my suggestion to anyone in the future would be to copy the .mozilla folder in your home folder to the desktop before you do the update then copy it back after the update. I think that should retain all the original settings. PITA.[/QUOTE]

In my case, I didn't get 'upset' with the original blue globe icon. The important is that we have the newest Firefox running.

---

