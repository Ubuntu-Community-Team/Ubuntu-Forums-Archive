---
title: "How to Sync Nokia E51?"
date: 2009-11-23
forum: General Help
---

### Post by viktorzk on 2009-11-23
Hello,

I need a way to sync a Nokia E51 with Evolution.

-It should sync contacts, calendar, and preferably notes.
-It should be quick, i.e. not involve manual exporting of CSV files, etc.
-It should sync both ways.
-It should work [almost] every time, not once every 15 attempts.
-It should not involve internet access from the phone, as I have neither Wi-Fi nor GPRS.

-I don't mind changing the PIM or running some KDE applications or even switching to KDE.
-I have a USB cable compatible with the phone.

I am aware that being free, Linux does not have to be capable of doing these things. But I am considering switching from Windows, and not being able to sync my phone will be decisive.

After following this: [http://forums.overclockers.com.au/showthread.php?t=657196](http://forums.overclockers.com.au/showthread.php?t=657196)
I managed to sync the calendar (with bugs and creating many duplicates) over bluetooth. The contacts didn't work. Since then I have been unable to connect over bluetooth.

I am aware of the existence of many other how-to's on similar topics. I have tried following many of them without success. I am intentionally not listing most of what I have tried, as I am a Linux newbie, so I might have done something the wrong way.

I am running 64bit Ubuntu 9.10 (Karmic), kernel 2.6.31-14-generic, GNOME 2.28.1. The laptop is HP nw8440.

Thank you in advance!
Viktor

---

### Post by suyog on 2009-11-24
Many people have been able to sync with phones with few issues.

check following links

[http://ubuntuforums.org/showthread.p...a+Sync&page=17](http://ubuntuforums.org/showthread.p...a+Sync&page=17)

Can you tell me at what point you are getting error? I will be glad to help you out.

---

### Post by forest555 on 2009-11-24
Use jaunty. It does not work in Karmic anymore.

---

### Post by viktorzk on 2009-11-24
Thank you for the replies!

suyog, I can't open the link.

forest555, it does work with Jaunty. The only bug I found is that after a connection error (for example if I try to sync while the phone is off) multisync reloads all entries from both devices, then asks for each contact which version to keep, and creates duplicate calendar  entries on the phone only.

---

### Post by suyog on 2009-11-24
Link is 
[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)

I guess you should report issues/bugs in launchpad also contact opensync team

---

### Post by suyog on 2009-11-24
I didnt face any issue with syncing contacts, calendar and todos.

I am having latest updated Karmic with proposed updates and I am using it over Bluetooth.

---

### Post by leoh on 2010-02-17
I am looking for exactly the same thing the original poster is looking for.
However, I read a few guides and they didn't work for me. Some packages don't even exist in Synaptic.
I think the how-tos may be outdated - most are from 2007 or even older.
Can someone point me to an updated how-to to make my phone work?
I am using Ubuntu 9.10 and Nokia E51. As the original poster, I am looking to sync with any app (Thunderbird, Evolution or any other).

Thanks!

---

### Post by Bharath on 2010-02-18
After breaking my head for close to 5 years trying all kinds of tools, I found one easy way to "Transfer Contacts" from Evolution to Nokia E71. You can't call it a Sync... but you can easily transfer Evo Contacts. This should work on all S60 phones....

In Evo -> Save Address Book as vCard.

Go To Gmail-> Contacts-> Import -> import the *.vcf file you have saved.

On your mobile-> follow instructions given here to set up Google Sync -> 

[http://www.google.com/support/mobile/bin/answer.py?answer=98230&topic=15015](http://www.google.com/support/mobile/bin/answer.py?answer=98230&topic=15015)

Syn from your mobile to your Gmail Account.

Note: Keep your Evo Contacts up-to-date and do not enter (or change) any new contacts in your phone. Note down new contacts and update them in Evo.
And when you want to re-transfer updated contacts, delete contacts on your phone and gmail and follow the above process.

.... What a relief... now the search still continues for a perfect Sync.

Bharath

---

### Post by leoh on 2010-02-18
Thanks... however I am looking for something more... automatic.
I am looking something like Ovi Suite or PC Suite, that syncs between the phone and the PC.
What can I do?

---

### Post by leoh on 2010-02-21
Anybody?
I tried the tutorials posted here, but the repositories, versions and/or instructions are no longer valid with Ubuntu 9.10.
Can anybody provide me with an up-to-date tutorial or instructions?

---

### Post by suyog on 2010-03-06
can you check this? look for last post
[http://ubuntuforums.org/showthread.php?t=260676&page=32](http://ubuntuforums.org/showthread.php?t=260676&page=32)

---

### Post by suyog on 2010-03-06
check this
[http://ubuntuforums.org/showthread.php?t=260676&page=32](http://ubuntuforums.org/showthread.php?t=260676&page=32)

---

### Post by engellion on 2010-03-24
Hi. I came up against the same problem trying to sync my **Nokia E71** with Evolution via Bluetooth on Ubuntu 9.10. I have finally got it to work. Once you set it up, it is pretty straight forward. I've been successful using the OpenSync and Multisync tools + Multsyc0.90 gui.  Syncs are bothways.

Here is a [**Step-by-Step**]("http://ubuntuforums.org/showthread.php?t=1437399") Guide to how I got it going on my E71. Not sure if anything is different for the E51, but if the E51 uses SyncML then it should be the same setup process.

[http://ubuntuforums.org/showthread.php?t=1437399](http://ubuntuforums.org/showthread.php?t=1437399)

Cheers.

---

### Post by leoh on 2010-03-31
I used this tutorial and it worked with my E51! Thanks!

---

