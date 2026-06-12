---
title: "Ubuntu Firefox vs. Mozilla Firefox"
date: 2006-04-29
forum: General Help
---

### Post by Hoffmann on 2006-04-29
I am just curious: 

What is the difference between Ubuntu Firefox and Mozilla Firefox? The same about Ubuntu Thunderbird and Mozilla Thunderbird. Which of those programs should be used, preferable?

Hoffmann

---

### Post by Resurrection on 2006-04-29
Well, AFAIK, nothing is different between the two, except that the Firefox within Ubuntu isn't the latest version.  Same with Thunderbird.  And I don't think you can uninstall the old Firefox, you have to do a separate install of the newest version.

I recommend using the newest version as it has all the latest security fixes, and I suggest using Automatix to install it if you are new to Linux.  Just search for Firefox on here, and you'll find there is a complicated way to install, and an easy way, using Automatix.  

Post back if you need more help.

---

### Post by Hoffmann on 2006-04-29
[QUOTE=Resurrection]Well, AFAIK, nothing is different between the two, except that the Firefox within Ubuntu isn't the latest version.  Same with Thunderbird.  And I don't think you can uninstall the old Firefox, you have to do a separate install of the newest version.

I recommend using the newest version as it has all the latest security fixes, and I suggest using Automatix to install it if you are new to Linux.  Just search for Firefox on here, and you'll find there is a complicated way to install, and an easy way, using Automatix.  

Post back if you need more help.[/QUOTE]

Resurrection,

I have installed the newest Firefox by using the 'complicated' approach. And it is working with no problem. 
What about Automatix you mentioned? What is that, and how does it work?

Thanks!
Hoffmann

---

### Post by astoltz on 2006-04-30
The firefox in breezy DOES get security updates.  It does not get feature updates - 'till the Dapper release.

---

### Post by John64 on 2006-04-30
well i personally hate using the Ubuntu compiled package.  I dont know why, but thats me.  If you have a problem,  please be sure to redirect it to /dev/null.

Anywho.  If you want the official Firefox, from the people who make it (Mozilla) all you need to do is download the file from [www.getfirefox.com](www.getfirefox.com).  Then in a gnome-terminal type

sudo nautilus

then open your freshly downloaded Firefox fileset with file-roller, then extract to /usr/lib/firefox replacing things if nescesary (sp?)

Also if you are insane about having mozilla everything,  copy the new /usr/lib/firefox/icons to /usr/share/firefox/icons and /usr/share/pixmaps

Hope you like it, i do!

---

### Post by aysiu on 2006-04-30
[QUOTE=John64]
Anywho.  If you want the official Firefox, from the people who make it (Mozilla) all you need to do is download the file from [www.getfirefox.com](www.getfirefox.com).  Then in a gnome-terminal type

sudo nautilus

then open your freshly downloaded Firefox fileset with file-roller, then extract to /usr/lib/firefox replacing things if nescesary (sp?)[/QUOTE] Or you could use [this script](http://www.psychocats.net/ubuntu/firefox) to have the Mozilla Firefox downloaded and installed for you. It's basically just an automation of these [Wiki instructions](https://wiki.ubuntu.com/FirefoxNewVersion).

---

### Post by Resurrection on 2006-04-30
Info about Automatix:

[http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix]("http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix")

You'll find that it can be very helpful for installing a wide variety of other things as well, like Flash, other plugins, some codecs, etc.  Alot of stuff that you might want or need, and it can do it in one shot, instead of having to figure it all out.

---

### Post by Hoffmann on 2006-05-03
Is Ubuntu Firefox as secure as Mozilla Firefox?
Which one is more safe?

---

### Post by aysiu on 2006-05-03
[QUOTE=Hoffmann]Is Ubuntu Firefox as secure as Mozilla Firefox?
Which one is more safe?[/QUOTE] As long as they're both version 1.5.0.3, they're both equally safe/dangerous.

---

### Post by Hoffmann on 2006-05-03
[QUOTE=aysiu]As long as they're both version 1.5.0.3, they're both equally safe/dangerous.[/QUOTE]


aysiu:

But, Ubuntu Firefox is 1.0.8 , and Mozilla Firefox is 1.5.0.3....

Well, the reason for posting my previous question is that it seems like there exist some problems in the last Mozilla Firefox (the 1.5.0.3). I noticed that some times it is necessary to double click on its icon in order to make it lounch. I am not having the same type of crash another person have mentioned, but the 'double' click is 'stupid'. Have you got the same problem?

Hoffmann

---

### Post by _linux_ on 2006-05-03
They're basically the same thing. It's just that the Ubuntu one is older (1.0.?) and has a different icon. But you can still upgrade to the new one (wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by aysiu on 2006-05-03
[QUOTE=Hoffmann]Have you got the same problem?[/QUOTE] No, and I am using the Mozilla (not the Ubuntu) Firefox 1.5.0.3.

---

### Post by sinkxdie on 2006-05-03
Mabey it's just me, but I use epihany. I dont like using 150mb of my memory when I'm browsing the web. I'd rather only use 120mb. :D

---

### Post by Hoffmann on 2006-05-03
[QUOTE=sinkxdie]Mabey it's just me, but I use epihany. I dont like using 150mb of my memory when I'm browsing the web. I'd rather only use 120mb. :D[/QUOTE]

Please, telll us about your experience with epihany. What about its security and performance?

---

### Post by sinkxdie on 2006-05-05
For security, it's linux. I don't really care about security that much exept one Avast scan once in a while. And preformance, it's a little faster then firefox, and still has tabbed browsing and pretty good pop-up blocking.

---

### Post by Hoffmann on 2006-05-05
[QUOTE=sinkxdie]For security, it's linux. I don't really care about security that much exept one Avast scan once in a while. And preformance, it's a little faster then firefox, and still has tabbed browsing and pretty good pop-up blocking.[/QUOTE]

I tried Epiphany this week. Well, in my opinion, it is as fast as Firefox, and it's really cool. I thing I didn't like on Epiphany is that you have just two options: either you permit cooks or not. I see no way to have a list of safe places (for allowing cooks and pop up), or an option to delete cooks when closing the browser. Since I am serious about security (even in linux), I will continue with Firefox.

---

### Post by reinouts on 2006-05-05
[QUOTE=Hoffmann]I thing I didn't like on Epiphany is that you have just two options: either you permit cooks or not. I see no way to have a list of safe places (for allowing cooks and pop up), or an option to delete cooks when closing the browser. Since I am serious about security (even in linux), I will continue with Firefox.[/QUOTE]

Hi,

Epiphany developers take security as seriously as you do. First, the View > Popup windows menu item will remember its setting for each site you visit. There is nothing more you have to do about that then just select that menu item. For cookies, you are correct that there is not a very fine-grained cookie management in Epiphany, but then again, they are not a security problem in and of themselves. You can find (and delete) the currently stored cookies from the View > Personal Info window.

Good luck!

---

### Post by Hoffmann on 2006-05-05
[QUOTE=reinouts]Hi,

Epiphany developers take security as seriously as you do. First, the View > Popup windows menu item will remember its setting for each site you visit. There is nothing more you have to do about that then just select that menu item. For cookies, you are correct that there is not a very fine-grained cookie management in Epiphany, but then again, they are not a security problem in and of themselves. You can find (and delete) the currently stored cookies from the View > Personal Info window.

Good luck![/QUOTE]

Definitely, I do agree that Epiphany is a nice browser for linux. I have more experience with Firefox and, probably, I need to try Epiphany with more attention. One of the best things in the linux world is the large number of alternatives we have. Don't you think?;)

---

