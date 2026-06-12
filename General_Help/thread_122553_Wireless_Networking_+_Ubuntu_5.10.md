---
title: "Wireless Networking + Ubuntu 5.10"
date: 2006-01-27
forum: General Help
---

### Post by hunter x az on 2006-01-27
Ok, new user here. I've had some success so far and I'll tell you where I'm getting stuck.

I have mounted my NTFS drive so I can download things in Windows then access them in Ubuntu, so I downloaded NDISWRAPPER but I'm having issues getting it installed / compiled.

Firstly, in the INSTALL it says this:

> You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Well, I type that, and I get "Directory Not Found" or some such result. I guess this is a major issue, but even if I press on and do the next step:

>   tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

I get "make not found" or something, make not a recognized program? I tried Makefile and make install and make uninstall and none worked. Any tips here? Am I missing a component? If so, how do I install it without INTERNET ACCESS?

My Wireless PCI Network card is a D-Link DWL-G510, if that helps. Thanks so much for any help.

---

### Post by byen on 2006-01-28
hey hunter...ndiswrapper comes with the UBUNTU Install cd (named ndiswrapper-utils). And as for compiling it to work with your wireless card...here is a [how-to]("http://www.ubuntuforums.org/showthread.php?t=25683") that might do the trick!!!.
Note: It is written for Hoary but works for Breezy too!
Hope that helps! Goodluck and Welcome to Ubuntu!

---

### Post by hunter x az on 2006-01-28
Cool, any idea on how to install ndiswrapper off of the CD, if I just pop it in will I be able to browse / search for it? I'll try that tutorial, I printed it out.

---

### Post by Crimguy on 2006-01-28
[QUOTE=hunter x az]Cool, any idea on how to install ndiswrapper off of the CD, if I just pop it in will I be able to browse / search for it? I'll try that tutorial, I printed it out.[/QUOTE]

Why dont you run Synaptic (on the Gnome menu)? Look for the package, right-click on it, select install, then apply. . .

---

### Post by hunter x az on 2006-01-28
Thanks!

---

### Post by byen on 2006-01-28
[QUOTE=hunter x az]Cool, any idea on how to install ndiswrapper off of the CD, if I just pop it in will I be able to browse / search for it? I'll try that tutorial, I printed it out.[/QUOTE]
Ok.. Im not sure if it comes default during install or not.. but this is how you can do to findout. 
go to > System>Administration>Synaptic Package Manager>Search>ndiswrapper-utils
If it is installed..go ahead and continue with the [how-to link ]("http://www.ubuntuforums.org/showthread.php?t=25683")that I have given you. If not.. With the Synaptic open, just insert the CD and do 
EDIT>Add CD Rom
now again do Search>ndiswrapper-utils (in the Synaptic package manager)
Right Click> Install.

Phew! thats a lot of typing... hope that helps man. Goodluck. Let us know if you need anymore info...

---

### Post by hunter x az on 2006-01-28
OK!

Major updates.

I am able to install ndiswrapper, install the drivers (I think) and I get to the Administration > Network part. When I do that It shows "Wireless Connection" as ath0 (not what was mentioned in the how-to, "wlan0", is this an issue?), and I bring up the properties to activate it, and I tick the checkbox to enable it, and I set it as the default gateway. Also, it can see the network SSID and a couple other networks around. I put in my WEP key in ASCII format (there is also a Hexidecimal or something format, but I used ASCII) and I clicked ok and closed all out. It took some time and a little bar saying "Activating Interface ath0" popped up for about 30 seconds, then it closed all out. The Wireless Connection now said "active" and the others (Ethernet, PPPOe?) were disabled / not configured. I figured everything was good to go, and I was happy!

BUT:

I opened up Firefox and it said could not find [www.google.com](www.google.com) :( So, I tried to type in [http://192.168.0.1/](http://192.168.0.1/) and it said the connection was refused.

Any ideas what's up? What should I do now? :(

I think I need to enter my WEP key in HEX format, in the how-to it says to PREFIX it with an s:

So would it be:

s:bbbbbaaaaa000009999

like that?

---

### Post by Titus A Duxass on 2006-01-28
Have editted your /etc/network/interfaces file?

If not go to the wiki and look at the guide HowToSetUpNdiswrapper, if you follow that you will up and running in no time.

---

### Post by alamba on 2006-01-28
Step 1: type "ifconfig ath0" do you have an IP now? 
Step 2: Can you ping your gateway?
Step 3: check /etc/resolv.conf are your DNS addresses in place?
Akshay

---

### Post by hunter x az on 2006-01-28
Got it!

All I had to do was ensure the drop down box for the WEP key was HEX and I entered my WEP key withOUT the S: prefix. Boom, works!

Thanks so much guys!

Anything else I should be doing to learn the OS now?

---

### Post by alamba on 2006-01-28
fantastic...good luck. 

Tip to learn the OS: start doing whatever comes to mind with it, u'll hit into trouble sooner or later and start learning!! Something I do for fun is read up the config files. Some popular ones I use are samba, postfix, ntop & nessus.

Akshay

---

### Post by byen on 2006-01-28
congrats man... glad to know it worked out! goodluck!
PS- About learning Linux... I think the best way is to learn as you go.... ;-)

---

### Post by Tichondrius on 2006-01-28
[QUOTE=hunter x az]OK!

Major updates.

I am able to install ndiswrapper, install the drivers (I think) and I get to the Administration > Network part. When I do that It shows "Wireless Connection" as ath0 (not what was mentioned in the how-to, "wlan0", is this an issue?), and I bring up the properties to activate it, and I tick the checkbox to enable it, and I set it as the default gateway. Also, it can see the network SSID and a couple other networks around. I put in my WEP key in ASCII format (there is also a Hexidecimal or something format, but I used ASCII) and I clicked ok and closed all out. It took some time and a little bar saying "Activating Interface ath0" popped up for about 30 seconds, then it closed all out. The Wireless Connection now said "active" and the others (Ethernet, PPPOe?) were disabled / not configured. I figured everything was good to go, and I was happy!

BUT:

I opened up Firefox and it said could not find [www.google.com](www.google.com) :( So, I tried to type in [http://192.168.0.1/](http://192.168.0.1/) and it said the connection was refused.

Any ideas what's up? What should I do now? :(

I think I need to enter my WEP key in HEX format, in the how-to it says to PREFIX it with an s:

So would it be:

s:bbbbbaaaaa000009999

like that?[/QUOTE]


You did almost everything correctly. The only thing you might have done wrong is enter the WEP key  - I don't think you need to enter "s" as prefix. Just type the key exactly as it appears in your router. Also make sure the channel is the same, the SSID is correct, and that they both have the same key type(64 or 128 bits), and same authentication mode (e.g. open  system or shared key).

To check that your connection was activated correctly, type "ifconfig" and check that there is a line showing an IP in the section for "ath0", for example: "inet addr:192.168.0.100".

Disregard what poster above said about efiting config files manually, you only need to use the networking adminstration menu like you did, and all the settings will be saved for you in the appropriate config files.

---

