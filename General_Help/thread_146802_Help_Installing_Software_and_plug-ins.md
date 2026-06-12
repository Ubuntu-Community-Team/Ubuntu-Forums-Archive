---
title: "Help: Installing Software and plug-ins"
date: 2006-03-19
forum: General Help
---

### Post by benblur4 on 2006-03-19
I am a noob and I can't figure out how to install software or plug-ins.
I had windows 2000 and I downloaded firefox for it,  I had some cool plug-ins on there and then I tried a live CD of several linux os's and I was sold.  I mainly liked the free software deal.  I have formated my hard drive and installed Ubuntu (they shipped me some free cds) and I love it but I can't get any of the free software installed.
I am specificaly trying to install "stumble upon-2.4"
Thanks for Your Help!

P.S.  I realy no almost nothing about Ubuntu so please be specific on any instructions.  Thanks again.

---

### Post by IYY on 2006-03-19
The easiest way to install software on Ubuntu is using apt. This can be done graphically, or using the command line. The graphical way is easier for beginners:

Go to **System > Administration > Synaptic Package Manager**. 
Enable extra repositories (only need to do this once): **Settings > Repositories**. Click on "Breezy Badger" (Binary), click on edit, and to the "sections" textbox, add **universe** and **multiverse**, so that it looks like **main restricted universe multiverse**.

Search for the package you want (stumble upon, in your case), double click on it, and then click Apply.

If you were to do the same through the terminal, you'd need to run

**sudo apt-get install mozilla-stumbleupon** after adding universe and multiverse to the file /etc/apt/sources.list.

---

### Post by psychicdragon on 2006-03-19
Firefox extensions can be installed exactly the same way as on Windows. Specifically, go to the [mozilla update webpage]("https://addons.mozilla.org/extensions/?application={ec8030f7-c20a-464f-9b0e-13a3a9e97384}") and search for the extension you're looking for. The stumbleupon extension is [here]("https://addons.mozilla.org/extensions/moreinfo.php?id=138&application=firefox").

To install software in Ubuntu, you can use the "Add Applications" option in your Applications menu, or for more software you can use System > Administration > Synaptic Package Manager.

---

### Post by tuxcantfly on 2006-03-19
Click system - administration - synaptic package manager

enter your password in the dialog that shows up

click reload to update software list

find something you want to install, double click, press appy, wait while it downloads and installs, and you're ready to go

---

### Post by dpaint4 on 2006-03-19
No no no. Psychicdragon has the right idea. He's talking about Firefox extensions, not software for his OS. He can do it through the extensions manager in Firefox itself. It's under the menu Tools, in your Firefox browser. Just do it like you did in Windows.

---

