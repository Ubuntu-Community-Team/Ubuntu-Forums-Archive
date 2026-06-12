---
title: "Anchor Free / Hotspot Shield go away!"
date: 2010-04-30
forum: General Help
---

### Post by jrmcc999 on 2010-04-30
I'm using Ubuntu 10.04 LTS - the Lucid Lynx.  Thanks to all for the excellent work.  It's great!  I'm a pretty experienced user, but I cannot figure out how to get rid of Anchor Free / Hotspot shield.  I'm using the Firefox version included (3.6.3 Canonical 1.0)  I'm forever getting the unwanted banner in my browser (graphic looks like a crescent).  Also, I'm often getting unwanted popups for Anchor Free when I clink on links.  It feels like AdWare, and I don't recall doing anything to install it.  I realize a VPN is a cool thing when you're using WiFi, but I don't need it in my home and don't want the free adware version.  Maybe this belongs in a Firefox forum, but how do I get rid of this stuff?  I cannot find it anywhere.  This Anchor Free plug-in situation doesn't happen with my Firefox on Windows.  Thanks for the help.

---

### Post by happyhamster on 2010-05-01
That looks like adware indeed. 

- First take a look in firefox's settings: Edit-->Preferences-->Privacy and untick "Accept third party cookies" 
- Take a look at Exceptions: get rid of all you don't trust or recognize.
- Choose "Show Cookies" and remove those you don't want (easiest is to get rid of all of them this time).
- Again, in the cookies section, regarding the "Keep until:" part: a safe option is "I close Firefox".

- Under the Private Data section: choose "Always clear my private data when I close Firefox", and then press Settings. At least make sure Cache and Cookies are ticked. Press "Clear Now" to clean the cache.
Note that I choose to disallow/block as much as possible myself (I also don't allow passwords to be remembered, etc), but that's just my personal choice. Just choose the privacy settings you're comfortable with.

- Anyway, next, take a look at which add-ons are installed: at the main menu bar, go to Tools-->Add-ons-->Extensions and Tools-->Add-ons-->Plugins. Disable/remove anything that clearly shouldn't be there.

- Finally, install adblock plus! Tools-->Add-ons-->Get Add-ons. Search for adblock plus. It's a very popular adblocker. After installing it you have to restart firefox and then choose a blocklist (I'm using Easylist Germany, because it's close to where I live :) ).
If, after installing adblock, the banner still shows, you can right-click that banner and add it to adblock's blocklist manually.

Good luck.

---

### Post by jrmcc999 on 2010-05-01
HappyHamster, thank you for the AdBlock Plus tip!   I should have been using this anyway.  However, I think I have found that a PROXY SERVER I was using was inserting this content!   It was not a Firefox add-in or plug-in.

Regards,

J

---

