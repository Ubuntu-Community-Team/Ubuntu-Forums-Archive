---
title: "Downgrading Firefox to 3.5 from 3.6 in Ubuntu 10.04"
date: 2011-11-28
forum: General Help
---

### Post by h0w13r on 2011-11-28
Hey everyone!

I have been having some trouble downgrading Firefox from 3.6.x to version 3.5.0 in Ubuntu 10.04 LTS. I have a plugin that is not compatible with 3.6.x and would like to downgrade. 

I have tried uninstalling 3.6.x and then installing the program from Synaptic. When I open Firefox after this, it is still version 3.6.x even after rebooting. After searching around on Google I am unable to find a download for 3.5 since it is a fairly old version.

If anyone could help it would be greatly appreciated!!!

Thanks!

---

### Post by searchfgold6789 on 2011-11-28
What is the plugin? The case might be that it is compatible with 8.0, the latest version of firefox, but not ancient versions such as 3.5. If this plugin is really necessary, I can tell you how to add the appropriate Ubuntu repository to your sources.list file. Post back and let us know.
 - search

---

### Post by h0w13r on 2011-11-28
> **searchfgold6789 said:**
> What is the plugin? The case might be that it is compatible with 8.0, the latest version of firefox, but not ancient versions such as 3.5. If this plugin is really necessary, I can tell you how to add the appropriate Ubuntu repository to your sources.list file. Post back and let us know.
 - search

It's Firesheep. After some further reading, I guess it is compatible with 3.6 but when I try to install the add-on it says it is not compatible with my version 3.6.24. I'm doing a presentation on wireless security and would like to show this to the class. :popcorn:

---

### Post by Dangertux on 2011-11-29
> **h0w13r said:**
> It's Firesheep. After some further reading, I guess it is compatible with 3.6 but when I try to install the add-on it says it is not compatible with my version 3.6.24. I'm doing a presentation on wireless security and would like to show this to the class. :popcorn:

If you're doing a presentation on wireless security talk about wireless security.

Firesheep and other methods of session riding are more in line with intrinsic security flaws in certain protocols. For instance, blasting login credentials plain text over HTTP is stupid. If it were done on a broadcast network  (hub), wireless, or switched network with mitm conditions the implications would be the same.

If I were your instructor and you made this presentation in my class I would probably fail you on the spot. 

That being said if you want to do a 1337 demo that's actually related, use aircrack to demonstrate the ineffectiveness of WEP versus WPA. Demonstrate with kismet, or airodump that there is no such thing as a hidden SSID and whitelisting MAC addresses is pointless.

My 2 cents.

P.S : I'm not flaming you or trying to put you down -- however I think if you're trying to do an actual presentation on a topic in a classroom environment you should actually use the presentation to demonstrate that you learned what you're talking about, your initial post indicates you did not. Hence why I would fail you.

---

### Post by h0w13r on 2011-11-29
> **Dangertux said:**
> If you're doing a presentation on wireless security talk about wireless security.

Firesheep and other methods of session riding are more in line with intrinsic security flaws in certain protocols. For instance, blasting login credentials plain text over HTTP is stupid. If it were done on a broadcast network  (hub), wireless, or switched network with mitm conditions the implications would be the same.

If I were your instructor and you made this presentation in my class I would probably fail you on the spot. 

That being said if you want to do a 1337 demo that's actually related, use aircrack to demonstrate the ineffectiveness of WEP versus WPA. Demonstrate with kismet, or airodump that there is no such thing as a hidden SSID and whitelisting MAC addresses is pointless.

My 2 cents.

P.S : I'm not flaming you or trying to put you down -- however I think if you're trying to do an actual presentation on a topic in a classroom environment you should actually use the presentation to demonstrate that you learned what you're talking about, your initial post indicates you did not. Hence why I would fail you.

I should probably add that I'm also doing exactly what you just suggested. The presentation is focused on threats that people should be aware of while using/owning a wireless network. I have that all set up already using my ALFA AWUS036H wireless adapter. I just thought it would be cool to spend a minute or so demonstrating Firesheep. :)

That being said, in order to get Firesheep working I need to either downgrade to Firefox 3.6.12 or upgrade to Firefox 5 (I recently found a Firesheep compilation that works with Firefox 5). However, I cannot figure out how to downgrade successfully. I also cannot figure out how to install Firefox 5 from the firefox-5.0.tar.bz2 that I downloaded. I extracted the files but there is no make file or installation instructions. 

If anyone can throw me some pointers that would be great. :)

---

### Post by vasa1 on 2011-11-29
> **h0w13r said:**
> .... I also cannot figure out how to install Firefox 5 from the firefox-5.0.tar.bz2 that I downloaded. ...

From where? I can't understand why you want to stick with old versions or downgrade. As a security-conscious person, that is a bit contradictory!

Clicking on this link -http://www.mozilla.org/products/download.html?product=firefox-8.0.1&os=linux&lang=en-US-
 will get you a tar than you can move to, and uncompress in, a **new** folder **in your home folder**. I'd suggest not trying to put it in **/opt**.

There's no need to look for makefile or any such high falutin stuff. Just find the subfolder called "firefox" and click on the file called simply "firefox". There'll also be firefox.bin but I've never clicked on it.

Before that, **with Firefox not running**, you should find the profile folder of your existing old Firefox and rename it by appending "old" to it.

Then uncompress the tar you downloaded. It will create a new profile folder within the folder you have downloaded (or moved) the tar to.

If you don't like it, simply delete the new folder containing all the new stuff. Rename your old profile to what it was and you'll be back to square one!


**Incidentally, I couldn't find Firesheep! Maybe it's been pulled??** I think it was quite controversial.

---

