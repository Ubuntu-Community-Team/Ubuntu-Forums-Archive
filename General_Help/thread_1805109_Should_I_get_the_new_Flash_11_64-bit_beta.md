---
title: "Should I get the new Flash 11 64-bit beta?"
date: 2011-07-15
forum: General Help
---

### Post by jcd29 on 2011-07-15
I'm about to install Ubuntu 11.04 64-bit, and I'm wondering if I should install that Flash 11 64 bit beta? If so, a couple of questions:

- Should it perform better than the 32-bit version?

- If I install the 32-bit or an older version before, can I overwrite with the new one or is a full clean install preferred?

- How do I install it once I download it from here? [http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html) Is it really as simple as replacing the *.so file?

- Does Chromium/Chrome need this too or just Firefox?

---

### Post by Frogs Hair on 2011-07-15
If you are happy with the current performance of flash player there is no reason to change . It is a beta , so it may or may not work better . If you have Flash Aid installed in Firefox you can install a beta flash release using the Quick Mode and It will remove the old version for you . Unlike Windows I don't need to install flash player for each browser , but I am a Opera / Firefox user and don't know about Chome/Chromium .

---

### Post by ratcheer on 2011-07-15
It is working great for me in Natty. I need to go install it in Oneiric.

Yes, it really is as simple as replacing the .so file.

Tim

---

### Post by szal on 2011-07-15
It’s even simpler with the Sevenmachines PPA: [COLOR=Blue]sudo apt-get install flashplugin64-installer[COLOR=Black] :)[/COLOR][/COLOR]

---

### Post by lovinglinux on 2011-07-15
> **Frogs Hair said:**
> If you are happy with the current performance of flash player there is no reason to change . It is a beta , so it may or may not work better . If you have Flash Aid installed in Firefox you can install a beta flash release using the Quick Mode and It will remove the old version for you . Unlike Windows I don't need to install flash player for each browser , but I am a Opera / Firefox user and don't know about Chome/Chromium .

Also, if you use Flash-Aid you can easily switch between the stable and the beta version with two clicks. Just select "Quick Mode >> Install stable flash" or "Quick Mode >> Install beta flash". I won't hurt to try and Flash-Aid removes any left overs from other flash versions. The Wizard and the Advanced Modes offer more options, like removing tweaks and installing other versions of Flash.

Chromium/Chrome 64bit will detect the plugin installed by Flash-Aid as well.

I have released a new version (2.2.0) of Flash-Aid today, that uses SSL encryption for getting the plugin urls and also checks for file hash before installing. You can get this version from [my site]("http://www.webgapps.org/add-ons/flash-aid/download-firefox") or from the [review queue at Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/").

BTW, the beta version is working great for me on 32bit. I tested the 64bit on a VM and is working fine as well.

---

