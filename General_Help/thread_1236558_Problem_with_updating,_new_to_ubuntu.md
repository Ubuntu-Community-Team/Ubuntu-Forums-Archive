---
title: "Problem with updating, new to ubuntu"
date: 2009-08-10
forum: General Help
---

### Post by Neliel on 2009-08-10
This is the error message I get when trying to update my list.
I am using the x64 version of ubuntu jaunty. I used a guide to setting up my ubuntu and 
I had to update this list, but now when i try to update i get this error message.
Im new to ubuntu and if anyone could help that would be great

GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEGPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 66D5C734F6EFB904GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CBGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768DFailed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404 Not Found [IP: 212.72.53.130 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by realzippy on 2009-08-10
You have the sources,but not the keys:

NO_PUBKEY 58403026387EE263GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available

For this example to get the key,open terminal and type:

**sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -**

then:
**sudo apt-get update**

---

### Post by P4man on 2009-08-10
or you can just go ahead and install without verification :)

---

### Post by Neliel on 2009-08-10
Why does ubuntu need keys anyway?
How would I edit the sources also?

---

### Post by snowpine on 2009-08-10
> **Neliel said:**
> Why does ubuntu need keys anyway?
How would I edit the sources also?

Hi Neliel, you're having this problem because you've added about a dozen software "repositories" to your sources list. This software is not tested or trusted by your Ubuntu system, so you need to provide a "key" to verify each source.

Is there any particular reason you need all these extra sources, instead of using the version of each application that's part of the tested, stable Ubuntu repository? For a beginner, I would definitely recommend sticking with the main repository, unless you have a very specific need for a newer version of one or two particular applications.

ps You would edit the sources the same way you added all of them in the first place... they are not part of the standard Ubuntu install. You can do it either through the Synaptic Package Manager, System->Software Sources, or in the terminal with 'gksu gedit /etc/apt/sources.list'. Whatever method you used in the first place is probably the least confusing...

---

### Post by Neliel on 2009-08-10
No, there really is no reason as to why I have so many. It was part of a guide to setting up ubuntu. But now I would like to try to remove them and go back to the old list but I dont know how and need help with it.

---

### Post by P4man on 2009-08-10
keys are used to verify downloaded packages. That way you can be sure they haven't been tampered with, as the packages are all signed by whowever runs the repository. It makes it impossible for a hacker to tamper with the files on the server and make everyone download some hacked version of whatever app. If you're only downloading from sources like canonical, then the risk you take by downloading without signatures, isn't all that big.

As for how to change sources? System > administration > software sources.

Or if you prefer editing text files: 

gksudo gedit /etc/apt/sources.list

---

### Post by snowpine on 2009-08-10
I would recommend System->Administration->Software Sources. Click on the Third Party tab and uncheck the ones you don't need. (They'll still be there, so if you decide you need them later, you can re-check them.)

Guides to setting up Ubuntu are all well and good, but it's also good to make sure 1) You trust the person writing it; 2) It's for the same version of Ubuntu you have; 3) You understand the purpose of each step (and agree it's something you want to do to your system).

---

### Post by Neliel on 2009-08-10
Alright thanks for the help. I understand it now. Thats probably the only thing I don't like about ubuntu. The fact that you have to do so much to install or uninstall somethings. But thats usually only for things that were designed on windows

---

### Post by snowpine on 2009-08-10
Applications->Add/Remove... it's really really easy. Every application on that list is tested and trusted to work well with your version of Ubuntu. There is an application to replace just about anything you can do in Windows (Gimp instead of Photoshop for example).

---

### Post by Neliel on 2009-08-10
Yeah I have actually used both and I like gimp better. seems easier to me. And Virtualbox helps when testing OS cds, Gresistor helps for my trade, never could memorize the color code :/. And the tons of games :D that are also free

---

### Post by agas on 2009-08-12
I get this massage went reload the Synaptic package manager:

[COLOR="Sienna"][SIZE="4"][HTML]"W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release:The following signatures couldn't be verified because the public key is not available:NO_PUBLIC KEY 7889D725DA6DEEAA"[/HTML]
[/SIZE][/COLOR]
Please tell me what to do..Thank's.

---

