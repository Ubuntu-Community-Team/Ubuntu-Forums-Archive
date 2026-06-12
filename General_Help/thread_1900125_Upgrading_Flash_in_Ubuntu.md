---
title: "Upgrading Flash in Ubuntu?"
date: 2011-12-25
forum: General Help
---

### Post by Franknj229 on 2011-12-25
Can someone please help me install the latest version of Adobe Flash? I really have trouble with Linux because I'm not a programmer and nothing is intuitive. I need a very specific walkthrough.
 
I click on the link for the Flash player and it brings me to a screen with "Select version to download". My choices are .tar.gz for other Linux OR .rpm for other Linux.
 
Regardless of which one I choose, I then click "download" and I get a pop-up box that says "open with" and my only choice is Archive Manager.
 
I assume those first two steps are pretty basic. It's what to do AFTER the download is complete that has me completely baffled. I need step by step instructions on what to do with the 20 or so folders and files that pop up when the download is complete. I guess I have to extract something to somewhere or type seemingly random letters and symbols in the terminal. Can anyone help me out with this?
 
Thank you!
 
Frank

---

### Post by saneearth on 2011-12-25
The most recent version of flash is available from the Synaptic package manager or I assume the software center. I just checked and version 11 is available and should suit your needs. I prefer the Synaptic Package manager to download things. It is no longer installed by default, but you can get it from the Software Center or by opening a console and typing "sudo apt-get install synaptic". Then just do a search for "Flash" and you will find it listed. Right click and select for install along with anything else you might want to install then go to the top bar and select apply. It will ask for your admin password when you open Synaptic initially. Hope this helps. I would always try and see if available packages are listed before going for "outside"packages.

---

### Post by Dennis N on 2011-12-25
The flashplugin-installer package will give you the latest version from the repository through the update-manager. Just wait for the update-manager to offer the update. It is not always immediate after the release of a new version by Adobe.

---

### Post by Franknj229 on 2011-12-26
Everything in the Software center that has anything to do with Flash is already installed.  I apparently don't have the most recent version though, because I can't view certain games or watch certain videos posted on Facebook or other sites.  It tells me I need the latest version of Flash and provides a link to download it.  Please re-read my original post.  That is what happens when I attempt to download it.  What do I do at each point I mentioned?
 
Thank you for any help you can provide.
 
-Frank

---

### Post by wildmanne39 on 2011-12-26
Hi, open firefox click on tools, addons, type flashaid into the search field, install it and follow the directions it will need to run a small script.
Thanks

---

### Post by jmadero on 2011-12-26
Yes use flashaid, it is NOT true that synaptic has the newest version, it rarely does and you can even install the beta version from flashaid which has always proven to be really good for me. I haven't used flash from synaptic since flashaid came out quite awhile back

---

### Post by QIII on 2011-12-26
Flash-Aid, by the way, was developed by an Ubuntu Forums poster who goes by the handle lovinglinux.

He develops Firefox add-ons.  You can trust it as safe.

Find out more here:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Franknj229 on 2011-12-27
Thank you all.  That was very easy, and it said the installation was successful.  Unfortunately, I'm still getting the following message:  "Adobe Flash Player Version 10.1.82.76 or greater is required...."
 
Refer back to original post.
 
Any thoughts?
 
-Frank

---

### Post by Derek Karpinski on 2011-12-27
Which version of Ubuntu are you running? When you ran 'flash-aid', did you pick the beta version of flash?
 
In the firefox address bar type:
 
```
about:plugins
```
 
And tell us what version of flash it says is running there.

---

### Post by wildmanne39 on 2011-12-27
Hi, if you have noscript installed you need to allow java on that page.
Thanks

---

### Post by Franknj229 on 2011-12-27
> **Derek Karpinski said:**
> Which version of Ubuntu are you running? When you ran 'flash-aid', did you pick the beta version of flash?
 
In the firefox address bar type:
 
```
about:plugins
```
 
And tell us what version of flash it says is running there.
 
THANK YOU!!!  No, I didn't install the beta version originally.  I just did and it finally works.  Thank you all for your advice.
 
-Frank

---

### Post by Derek Karpinski on 2011-12-27
Great! :D
 
Please mark the thread as solved using 'Thread Tools' above the first post in the thread.

---

