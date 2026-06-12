---
title: "Kaddressbook Akonadi-server-No resource agents found"
date: 2010-05-11
forum: General Help
---

### Post by Foggy on 2010-05-11
I use KAddressBook to store membership details of a club up till now this applicationn has worked well but having fresh installed 10.04 on the 1st May, kaddressbook will not function due to error; Akonadi is not working as "No resource agents found"
Unless I can be directed to an other similar book I am very much in need of assistance.
Is a fresh install of 10.04 a good idea..?? I have purged Akonadi-Server and re-installed, no change.
I have the Akonadi test report if needed.
My thanks in advance.
bj

---

### Post by Maximus_ARNP on 2010-05-19
I used the instruction from the following link. It solved my problems:

[http://userbase.kde.org/Akonadi_and_AddressBook#Examining_your_Resources](http://userbase.kde.org/Akonadi_and_AddressBook#Examining_your_Resources)

> 
 Examining your Resources

KRunner offers you Akonadi Resource Configuration, or you can access this through the Akonadi tray icon > Configure. You may find several resources set up. You may find one labelled

Address Book - No KDE address book plugin configured yet.

That's the old compatibility bridge (possibly created by the migrator tool). You should remove this one!

std.vcf - Ready

This is the 'VCard File Resource' which points to $HOME/.kde/share/apps/kabc/std.vcf per default. It is not recommended that you use that one, as it doesn't share the benefit of Akonadi.

Personal Contacts - Offline

That's the preferred resource for your local contacts which points to

 $HOME/.local/share/contacts

Note that this may say 'Offline' when in fact you are using it. This is a display bug, and can safely be ignored.



---

### Post by paydaydaddy on 2010-05-20
I had the same problem and was able to fix it by using the info from the test report and applying the fixes on this page:

[http://userbase.kde.org/Akonadi_4.4/Troubleshooting](http://userbase.kde.org/Akonadi_4.4/Troubleshooting)

It took some time and careful reading, but I was able to work through it. Pay particular attention to the section on Kubuntu 10.04.

---

### Post by Foggy on 2010-05-20
Maximus_ARNP and paydaydaddy, many thanks for your advice, after some fiddling I installed 'virtuoso server' and 'virtuoso soprano plugin' (a small window popped up telling me that they needed to be installed), I still get the transparent window confirming that it is not connected to resource but it clears after second or so and I am up and running. However I will now take your advice and perfect the instillation. I am greatfull for your replies,Thank you. 
bj

---

