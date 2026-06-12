---
title: "fonts gone funny"
date: 2009-09-09
forum: General Help
---

### Post by paxmark1 on 2009-09-09
My fonts went a little funny in Opera awhile ago (weeks ago).  They did not scale well when zooming, got funny.  And it just seemed to increase.  This only happens on some web sites.  

I went to Firefox, too lazy to figure out how to keep my Opera bookmarks; aptitude purge Opera and then reinstall.  Would be easy enough to do, but Firefox was working better with Distributed_Proofreaders site also.

Today, my font have gone crazy in Firefox, on several websites, they only look good on certain magnificications.  So one set of fonts will look good on a page, but smaller fonts on the same page are near gibberish.  And then CTL + or CTL - will get that font correct, but other size font will then go gibberish.

And, to be beyond bizarre, the cards in the old program of spider (linux spider solitaire) suddenly  are blurred on the right hand side of the page.  When the blurred cards are moved to the left, they remain blurred.  When cards on the left side are moved to the right, they do not degrade.

Moi, not a super nerd but I started with Corel Linux in 99.  
Ubunty 9.04, pretty standard and up to date with aptitude safe-upgrade.  

2.4 ghz Dual Intel on a Asus pkkpl-vm board with 4 gb of ram.  Onboard intel gm3100 for video.

Just updated VirtualBox.  Had windows7 going in background when this happened in Firefox.  My board does not support the correct bindings (or the bios doesn't) for virtualbox to run 64 bit guests, I am pretty much ready to aptitude purge Virtualbox.  

Any help would be deeply appreciated

---

### Post by paxmark1 on 2009-09-10
screen shot

after sudo aptitude purge virtualbox-3.0
      sudo aptitude purge opera
      sudo dpkg -i opera10...  64.deb
note.  sudo aptitude purge opera does not destroy old old bookmarks.  

maybe you have to wipe -qrc * ~/.opera/*  to do that

---

### Post by philak on 2010-05-17
I'm struggling with this issue also. Chromium,FF & Seamonkey fonts and display degrade with certain websites open. Z.filter.com seems to be the common denominator. All is fine until I go to that site. Font degradation will spread system wide including gnome menus. ATI Radeon x200G

---

