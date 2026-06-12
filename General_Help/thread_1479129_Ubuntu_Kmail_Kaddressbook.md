---
title: "Ubuntu Kmail Kaddressbook"
date: 2010-05-10
forum: General Help
---

### Post by RPGonzo on 2010-05-10
Sorry if this is posted I searched but found nothing for the past week including these forums.

KMail installed in Ubuntu Lucid along with KAddressbook, there is a known bug for the resource selection for KMail to be able to see the entries in the KAddressbook which has my imported contacts. 

Just a note, not using Evolution because it's very unstable with my two IMAP emails, tried it and was not happy with it, Thunderbird was worse which is weird because it works flawlessly in Windows, KMail has been working perfect ( to my liking anyways ) for the past week so now just putting some touches on it.

Problem being the menu the bug "workaround" points to is non-existent in Lucid, that or i can't find it.

[http://userbase.kde.org/KAddressBook#Enabling_Resources](http://userbase.kde.org/KAddressBook#Enabling_Resources)

My question is if there is a manual way to change the resource configuration? A package to install to enable me to browse to this resource configuration? Or am i not looking in the correct location for the configuration option?

Thanks for any input, it will probably be a basic/easy fix i just cant put my head around it right now for some reason.

---

### Post by ambler on 2010-06-09
I'm having the same problem.  I can't find anything obvious to modify in the resource files in .kde/share/config.
But a filter that checks the addressbook for the "from:" seems to work.

---

### Post by ecowan on 2010-09-13
Bump. Me too.

---

### Post by joaogpeixoto on 2011-04-01
I had the same issue and did the following:

1) Exit Kontact, kmail and kaddressbook
2) Export all kaddressbook contacts as a vcard (save as std.vcf in /home/.../.kde/share/apps/kabc)
3) Delete all other vcard files (*.vcf) in this folder
4) install akonadiconsole
5) open akonadiconsole, select the adressbook (named "resource", in my case) and press configure.
6) enter the addressbook location (in my case, it was empty)

Worked for me: Ubuntu Lucid, Kontact 4.4.8, Kmail 1.13.5, Kaddressbook 4.4.8, Akonadi Console 4.4.5.

Hope it works for you guys! :-)

---

