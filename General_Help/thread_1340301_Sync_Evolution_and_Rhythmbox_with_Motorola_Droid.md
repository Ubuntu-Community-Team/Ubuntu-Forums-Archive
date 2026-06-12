---
title: "Sync Evolution and Rhythmbox with Motorola Droid"
date: 2009-11-28
forum: General Help
---

### Post by gobbles414 on 2009-11-28
I'm running the i386 version of Ubuntu 9.10. Here are my questions...

I've searched these forums and Google, but cannot find a procedure that will allow me to sync contacts and calendars from Evolution to my Motorola Droid smartphone. My Droid is running the Linux-based Android 2.0 operating system. I'd prefer to avoid uploading to clouds such as Google or Ubuntu One as part of the syncing process, because a lot of my data contains confidential business information.

I also want to send music directly from Rhythmbox to my Droid. The plugins for MTP and iPod are both enabled in Rhythmbox, but my Droid doesn't appear in the Rhythmbox side pane. Most of my music is in FLAC format. I'd prefer to "transcode" my FLAC music to MP3 during the sync process because I could fit more songs on the Droid. But if necessary, I'd be willing to add FLAC support to the Droid instead of transcoding.

Although my Droid and my computer both have Bluetooth capabilities, syncing via USB would be fine (probably easier too). Thanks in advance for your ideas and help!

---

### Post by malkierie504 on 2009-11-28
i'm interested in the same things though i'm using a Sprint Htc Hero. If you find an answer could you post it to this thread and i'll do the same.

---

### Post by demosthenese on 2009-11-28
Not tried this myself, but if you can connect the Droid as a usb drive and then create a file in its root directory called ".is_audio_player" then rhythmbox should pick it up.

Info from here:

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/12011]("https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/12011")

---

### Post by gobbles414 on 2009-11-30
Your idea works perfectly demosthenese! Rhythmbox even automatically transcoded my FLAC files to MP3 on the first attempt! I did, however, decide to transcode to higher quality MP3s (the default is only 128 kbps). I went *Edit => Preferences => Music => Edit => CD Quality, MP3* and made the following changes...

Original: *audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! Id3v2mux*

Modified: *audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=256 ! id3v2mux*

Now that my music problem has been solved, **does anyone have any ideas on how I can get my Evolution data onto my Droid?** Thanks!

---

### Post by gobbles414 on 2009-12-03
bump

---

### Post by gobbles414 on 2009-12-11
I still need help syncing PIM data between Evolution and my Droid. Thanks!

---

### Post by vexation on 2009-12-16
As far as I can tell, Android picks up all of its contact information from cloud services (facebook, gmail, etc.) It doesn't store contacts locally on the phone itself in the first place, except as a cache of what it pulls from those cloud services. So there is probably no way to "sync" between only Evolution and the Droid.

---

### Post by fheinsen on 2009-12-18
Evolution on Ubuntu 9.10 syncs really well with google's PIM apps, which in turn sync perfectly with the Droid over the wireless network.  Here's what you need to do:

[LIST=1]
[*]In Evolution, click on Contacts, then File -> Save Address Book as VCard.  Then click on Calendars, right-click on your calendar, and click Save to Disk.
[*]Sign up for a new gmail account, and then import the address-book and calendar files you just created into google's calendar and contacts.
[*]Go back to Evolution, click on File -> New -> Address Book, choose "Google" as the type, and enter your credentials.  Then click File -> New -> Calendar, choose "Google" as the type, and enter your credentials.  You may want to set the google address book and calendar as your defaults.
[/LIST]
This will 'automagically' keep your calendar and contacts synchronized between Google, Evolution, and the Droid at all times without actually having to hook up the Droid to your PC.  We've been doing this for a little while with two Droids and have had no issues.

Hope this is helpful.

---

### Post by gobbles414 on 2009-12-20
Thank you vexation and fheinsen for your replies!

I must say that I am disappointed to learn that the Droid does not store PIM data on the device itself. Is there software in the Android Market or elsewhere that might add the ability to store PIM data on the Droid itself? I simply want to come home after work or recreation and sync my Droid with my Ubuntu computer (as I used to do with my Palm PDA). Storing contact and calendar information in a cloud such as Google's is not an option that I am willing to consider. Of course, security and privacy are significant concerns. Nevertheless, an even bigger worry is reliability -- see [http://en.wikipedia.org/wiki/Gmail#Outages](http://en.wikipedia.org/wiki/Gmail#Outages) and [http://en.wikipedia.org/wiki/Microsoft_data_loss_2009](http://en.wikipedia.org/wiki/Microsoft_data_loss_2009) for examples of why I am unwilling to trust a cloud.

My research indicates that I have three other possibilities:
[LIST=1][*]Find software in the Android Market... I have found some free programs that might be able import csv of vcf files exported from Evolution, but many of the reviews for the Droid-compatible calendar import programs I have found in the Market talk about frequent crashing and difficult import procedures. [*]Somehow fool Evolution into thinking my Droid is an iPod and then use Evolution's "Sync to iPod" option... I am unsure if this would be possible. Even if it is possible, it is unclear to me if PIM data originally entered on the Droid would successfully sync to Evolution. [*]Somehow use Exchange to communicate between Evolution and my Droid. This seems to me like the most promising option, but I do not know much about Exchange and would need lots of help to create/configure it.[/LIST]

I am currently using Documents to Go by DataViz to view/edit my PIM data on my Droid as doc and xls documents. To prevent duplicate PIM files, I am simply mounting my Droid in Ubuntu to view/edit my PIM data on my computer. Obviously, this is so inconvenient that almost anything would be an improvement (except cloud). **Any ideas?** Thanks again!

---

### Post by gobbles414 on 2009-12-27
It's been awhile since anyone has posted to this thread. Please help.

---

### Post by malfindin on 2010-01-02
I cannot understand your unwillingness to use cloud. I bought a brand new Droid, put in my Gmail user and password and that's all I've ever done.

Oh, I did add the file "is_music_player" to the root of my sdcard for sync with banshee.

It's seamless and not just easy to set up...it is essentially--no set up compared to any other mobile device I have every used.

I have all my contacts, email, calendar, music, etc...and in far less time than it has taken me to write this post.

Try it you'll like it.

---

### Post by kingttx on 2010-01-27
Android phones generally do not act the same way you are used to and are trying to force it to act. Instead of a veritable silo like a WinMo phone, it connects to your gmail account and syncs with it instead. Therefore, any contact you have in your gmail account is now on your phone. Paradigm shift, indeed. 

Once you wrap your mind around this fact, it's much easier to see how to share contacts between your computer and your Android phone. There was already some really good advice on how to do so. 

Enjoy!

---

### Post by Spr0k3t on 2010-02-01
I've started putting documentation together for the Verizon Droid.

[https://help.ubuntu.com/community/PortableDevices/VerizonDroid](https://help.ubuntu.com/community/PortableDevices/VerizonDroid)

I've taken information from the forums as well as documentation found on the G1.

Gobbles414: The best way to make sure you have a backup of your contacts and calendar information is to use the cloud sync and then set up evolution as suggested by fheinsen.  From there, you can backup the data any time you would like in Evolution.  In a situation with a loss of data, you can then reimport the vcard and ics files you've made backups of.  As for keeping critical data off of the cloud... can't help you with that.

---

### Post by gobbles414 on 2010-02-05
Thank you all for your replies. Also, many thanks to Spr0k3t for taking time to create a documentation page for the Droid.

Earlier in this forum, vexation said “...Android picks up all of its contact information from cloud services (facebook, gmail, etc.) It doesn't store contacts locally on the phone itself in the first place, except as a cache of what it pulls from those cloud services.” So, I can't even manually enter a phone number into the Contacts section of my Droid without that phone number going into Google's cloud?

Unfortunately, my clients' privacy concerns prevent me from storing any contact info in a cloud. Also, events such as the recent Sidekick cloud fiasco have proven to me that clouds are not a reliable means of storing PIM data. To be completely honest, I resent the attempts of some here to make me feel like an idiot for not loving clouds. Indeed, customers are even complaining in Motorola's forums about this issue (see [https://supportforums.motorola.com/thread/17291](https://supportforums.motorola.com/thread/17291) for more info).

Does Verizon Wireless sell any phones that don't require cloud but have a decent interface and amount of storage for music. If no, does the iPhone require the use of a cloud and can one easily sync PIM data between it and Evolution?

---

### Post by gobbles414 on 2010-02-09
After posting this issue on some other forums, it's become obvious to me that I'm not going to find an acceptable answer to my question. I have, however, decided to use the following workarounds:

CONTACTS
I uploaded some test contacts from Evolution to my Google account, synced them with my phone, turned off syncing, deleted the contacts from Evolution and Google, then activated "airplane mode" on my phone. The contacts were still on my phone, so I'm guessing that means those contacts are not being stored in the cloud. Not an ideal solution (especially when I need to add new contacts), but it's better than paying full price for a different Verizon phone...

CALENDAR
Since my contacts are apparently not being stored in the cloud, keeping my schedule in my Google Calendar is an acceptable risk. I simply won't use any last names or contact info when creating calendar entries. The most annoying part of the calendar will be remembering to uncheck the remember password option every time I use Evolution to manage my calendar.

Thanks again to all of you for your ideas!

---

### Post by merekat on 2010-05-03
Gobbles-

I empathize fully with your frustrations about the massive movement to sync with clouds, instead of being able to sync privately on our own machines. I have absolutely no interest in having my PIM data stored (ultimately) on someone else's server, and the privacy risks are totally unacceptable to me.

I am a long-time palm pda user, and it's frustrating to know that even the very simple but exceptionally functional palm sync process is also going to the way of clouds. My father and I have both been scratching our heads about what to do once we need to move on from our current palms.

I've been looking into the android platform to try to figure out what to do, and it's so bewildering to see there seems to be no momentum towards developing personal computer synchronization, even when developing software for syncing between a linux-based device and a linux computer could be relatively simple (it seems to me anyway, but I'm no programmer). If I had the skills, I'd do it in a second. I am also completely bewildered by the seeming huge numbers of people that are swayed by the idea that clouds are a paradigm that we should just swallow without consideration for the consequences; more simply, I can't understand for the life of me why folks like us who want to sync privately are in such the minority!!

I wish I could offer ideas or help; I'm as frustrated as you; all I can do is commiserate.

:confused:
Merekat

---

### Post by crazy_fox on 2010-05-12
gobbles414:

Android phones can store locally information and keep it that way. You can manually create a contact and tell it to store it on the phone. And turn of syncing.

I have an Android Hero, and although my contacts are possibly nothing too interesting and valuable to anyone else, the idea that everything has to go through google, is just scary. They know what we search, who do we speak to, what we say. Its not a matter of age, or trends. People are ignorant of those facts today. Most people as you so above have two huge priorities, 1) easy, 2) cheap. Beyond that security, privacy, redundancy, flexibility, follow very slowly. They dump their information on their clouds and beyond that, what happens behind the scenes, does not concern them.

Unfortunately beyond this rant, I have nothing else to contribute. I haven't found my self a solution, as synchronising the contacts to my linux machine has not been a show stopper for me. I am interested in a solution though.

---

### Post by seeyaduck on 2010-08-18
Create an empty file in your favorite text editor called " .is_audio_player" in the root of the droid. Which should be the first folder that pops up when you click on the device. When you save the file you won't see it in the windows manager. I was having the same problem with the Droid X. 

:lolflag:

---

### Post by ComputingFroggy on 2010-08-30
Here you may find some information to find a solution to your problem:
[http://syncevolution.org/](http://syncevolution.org/)

It uses SyncML and will need a local SyncML server (Funambol ?) as you don't want one on the cloud ... but that should work !
I am investigating this my self ... but I don't have much time for this right now.


Happy syncing,
L@u

---

### Post by Steelbak on 2010-09-26
This is the first thread I've found echoeing my feelings about simply synchronizing locally the PIM stuff. I bought a Droid just assuming it had to be there. I'm actually shocked no one is doing anything about this as it seems everyone would want this.

---

### Post by shane2peru on 2010-10-13
If someone finds a solution to this, I would be interested too, whether it is a Droid phone or another phone.  As much as I don't like to I'm going to have to stick to Palm phones from e-bay till I can find a better solution.  Blackberry has syncing options in the works, but I don't know if it is stable/working yet. 

Shane

---

### Post by oedsrm on 2010-10-21
Well... at least I don't feel so alone now.  I'm still plugging away on my Palm Centro (2.5 years old) holding out for something that will work with Linux (without the cloud).

This is my checklist:

[LIST]
[*]No cloud (info too sensitive)
[*]Linux email client & PIM
[*]Contacts, Calendar, memo phone sync
[*]Linux & Phone secure password manager
[*]Password phone sync
[/LIST]
I thought Android or WebOS might be candidates but I'm still waiting for reports of success.

---

### Post by ianni67 on 2010-11-06
At the time being, in my knowledge only two operating systems for pda's offer you such options for free and reliably: 
- nokia symbian (not Symbian^3, yet!) through syncevolution or opensync
- Micro$oft mobile (through synce and opensync)

I was told that iPhone can sync with syncevolution by means of an app which costs about 10$. But never tried it (I do not have an iPhone).

Note that symbian is available also on some Sony phones.

Also, as soon as MeeGo will be available on smartphones, it will be an option.

EDIT: I found out that there is a recent project which allows an android 2.0 or higher to sync with funambol (the mother project of syncevolution):
[https://android-client.forge.funambol.org/](https://android-client.forge.funambol.org/)

At the time being, I have no information about the compatibility of this client with syncevolution.

---

### Post by jaiotu on 2010-11-07
The harsh reality is that Android phones are going to be heavily tied to Google's cloud services... that's one of Android's selling points.

Because syncing with Google's cloud in trivial, that siphons off many developers who would otherwise be interested in developing software to sync Android with our desktop apps.

I've been on gmail since 2006... syncing with the cloud is not an issue for me. It's probably not an issue for a lot of developers either... and they aren't going to scratch an itch that they don't feel.

So... while Android is an "open" platform, the fact that it's "open" may actually be hampering it's ability to interoperate with Evolution. The PIM conduits for Palm and Blackberry probably wouldn't be where they are today if either of them had a "cloud" based solution for syncing that worked as well as Google's does.

No... I'm not knocking the folks who don't want to sync to the cloud. I fully understand the desire for privacy and control over your own data. I'm just expressing the reality that Google's Android may not be the best platform for someone who's shy of Google's other services.

---

### Post by gobbles414 on 2010-11-21
It's reassuring to learn that others are as skeptical as I am of syncing PIM data to clouds!

Has anyone successfully done a LOCAL sync of PIM data between their Android and syncevolution/funamobol? If yes, please post the necessary procedure to this thread.

---

### Post by yager01 on 2010-11-26
I realize that this answer is one year late, but it begs for an answer.

I have an HTC Evo 4G from Sprint and put it in airplane mode to test where the data is stored, cloud or local.  Short answers.
[LIST=1]
[*]Contacts are on your device and available.
[*]Gmail is not available
[*]Google Calendar appointments are available.
[*]Other email accounts are available but you get a warning when starting.
[*]text messages are available.
[*]If you use drop box, files are available if they were downloaded to the device.
[/LIST]

So other than Gmail, everything appears to be available locally when the phone has no network available to it.

---

### Post by gobbles414 on 2010-11-29
Hi yager01... Yes, as I documented in post #15 of this thread several months ago, contact/calendar data is stored locally on Android phones.

HOWEVER, it seems impossible to sync contact/calendar data from the phone to Evolution without first sending it to Google's cloud. One can then manually delete contact/calendar from the cloud, but that procedure is rather tedious (especially if one is dealing with multiple Google accounts)

Some on this thread have suggested that syncevolution/funamobol might allow one to bypass Google's cloud for syncing contact/calendar data, but nobody has yet posted procedures for installing and configuring either of those options. I investigated both options, but ran into confusing instructions, dead links, etc.

---

### Post by blacksmith1 on 2010-12-22
I see this is an old thread, but I only got my Moto droid a few days ago... I, too, don't like the google route. There IS a way to transfer from Evolution to the droid without google. I just did it.

In Evolution contacts, export your contacts as vCard.

Put the vcard file in the root dir of the SD card for the droid.

In 'contacts' on the droid, hit the menu button (not sure of the right name, but the one that takes you to settings, et al) and choose import.

There will be a selection to use 'phone' or Gmail. Choose 'phone'.

Select 'import from SD card'.

You have the option of one or all or many files. I chose one and it merged it into what I had entered into the phone manually up till then. I did do an 'export' of everything on the phone first and had a file I manually merged 'just in case', but didn't need it.

The fields came in reasonably well too. Some of my contact info has been imported-exported over 6 different pims starting with the old DOS Sidekick, so there are some oddities, but it seems to be pretty orderly in the phone now.

Hope that helps. Off to figure out Calendar now....

---

### Post by kevinlhamilton on 2010-12-31
I have used deja office - [http://www.dejaoffice.com/](http://www.dejaoffice.com/) to do exactly what you want to do, except under windows.  Dejaoffice will use usb to sycn all your calendar, contacts, and tasks with your android or iphone and keep your data off google's cloud.  

You download the dejaoffice app on both your phone and computer.

You need to use the deja office calendar on the phone.  If you use the native android calendar, it will sync up with the cloud.


Here is what I have not tried that you might want to give a shot.  If Wine will run the pc windows version of the deja office app on your version of ubuntu, you should be all set.



Hope this helps.

---

### Post by Templar21 on 2011-01-21
All,
I just got the Droid X, and I agree that using a cloud such as google's or ubuntu is risky for sensitive information. I was attracted to the droid because it was an open source device. There have been several good answers to the original question, however I think we have failed to answer this question in the true spirit of Luggers. 

1) The droid devices are designed to seemlessly use clouds, so why stop them?
2) Google/ubuntu clouds have security and stability problems, so why use them?
3) Evolution is awesome, so why not use it.
4) Personal/small business linux servers provide legendary security and stability, and are well documented.
5) A dedicated personal server setup to store contact, calender, and even a private email can be made from relatively cheap components and function superbly, securely, and be very stable. (You can always unplug them.)
6) Personal server access across the internet via static ip address or a service such as [www.no-ip.com](www.no-ip.com) is well documented.
7) Encryption is also well documented.
8) Linux knows no boundaries.

I propose we start development on a internet accessible, encrypted,
Linux based, preferably ubuntu, personal/small business(group) cloud.

T21

---

### Post by donhulio on 2011-03-01
I can strongly recommend Funambol - it is opensource and the service is free. You can use it to sync calendar, contacts and photos between your android phone and the web. This can also easily sync with evoloution in Ubuntu by installing sync - can be done using the software centre (has a blue logo with two circular arrows in).

---

### Post by philyook on 2011-06-09
Templar 21, there are many projects working on this.
One is [http://freedomboxfoundation.org/](http://freedomboxfoundation.org/)

---

### Post by philyook on 2011-06-09
From this link it seems that Funambol could sync locally between Evolution and your Android phone without going on the cloud:

[http://theregoesdave.com/2008/09/24/funambol-enables-contact-syncing-for-g1-and-android-phones/](http://theregoesdave.com/2008/09/24/funambol-enables-contact-syncing-for-g1-and-android-phones/)

---

### Post by kevinl on 2011-11-10
I've been watching this thread with some interest.

Firstly I agree entirely it is too dangerous to put the contents of your address-book into the cloud unencrypted.  If the vault in the cloud is broken into by professionals, they won't leave a trace of their visit but they will have all of your business contacts, passwords and bank details.  Using cloud based storage without heavy encryption is very, very foolish.

Next, the Android is a PC with a phone attached, almost as one would attach a modem.  Anything you can do with a PC, you can do with an Android if you've the time and expertise to write the necessary software modules to reach down into the Linux kernel.

Next, I agree totally with the suggestion that there should be a project to link Evolution on one's notebook and tablet to one's phone in a seamless yet secure fashion.  Indeed there is a lot of work that is needed to make Evolution everything it could be.  I like using Evolution but I find there are a lot of things in it that are quite limiting.  Like, for example, the way it mangles text with leading angle brackets if you do a cut and paste from text contained in a reply or forwarded email.  Wouldn't it be great if Evolution had a full text editor that rivalled LibreOffice Writer!  Wouldn't it be lovely to have Evolution help you create a Minute or formal letter, perfectly formatted according to company writing conventions, and let you send it such that, when it arrived, it presented itself perfectly to the reader?!  There is so much that could be done with this program to make it truly great for personal and for business use. I just wish I had the time and money to devote to this.

Lastly, (given, I've strayed a little from the subject!) as a suggestion, it may be possible to simulate a cloud environment by setting up an Oracle Virtual Box on your notebook, tablet or PC and running a Linux "Server" within it.  On that Server, run Apache WebServer and you would be able to browse to it from your "parent" environment, ie, the operating system in which you are running the Oracle Virtual Box and your Evolution.  You could then have your "Linux-Server" act as a private cloud and the exchange of everything between your evolution and your Android Phone would happen seamlessly.  The only negative of this is that every time you want to do this you have to start up the virtual machine.  We actually have this arrangement when writing database applications to synthesise a distant FirebirdSQL server.  

So this exercise may not be so much a matter of programming but the writing of instructions that are simple enough for every-day people to follow in order that they may set up such an environment under a Ubuntu distribution.  The challenge here will be to make it really, really simple.

Is anyone up for the challenge?

---

