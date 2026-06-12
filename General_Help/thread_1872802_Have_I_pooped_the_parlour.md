---
title: "Have I pooped the parlour"
date: 2011-10-31
forum: General Help
---

### Post by bobski60 on 2011-10-31
Sorry if this is in the wrong thread.
I am living abroad in a country (Ukraine) that I do NOT speak the language...(and probably never will....COS its hard....yup its Russian)
Anyway anyway, I teach English to locals and fix all their computer needs (microsoft), the school down the road has heard and asked me to help them out with a seminar...thats no problem as I used to work in that environment when I was in England so I could do it anyway with my eyes closed....
Thats not the main problem though.....I have persuaded them to change to Ubuntu or Edbuntu (although apparently ubuntu is a bad word in Russian...so they say)
And well they have asked me to do the change over for them eeeeeeeeeeeeeeeeeeeeekkkkkkkkkk is all I am saying, I have only been on Ubuntu for about a month and the version has changed in the middle so am a bit behind.
is there anyway to set it up as DLoaded and then when its all correct and running change the whole system into Russian and keeping an English admin account.(so I can go into the system when needed. to do accounts and health and hygiene etc or do I stop holding my breath lol

be eassy with me am stillllllllllll a newbie with this ere Linux lol but love it

---

### Post by coffeecat on 2011-10-31
Don't take this the wrong way, but let me flag up some things for you to think about.

You are living and working in a country whose language you do not speak, you have one month's experience of Ubuntu and you have persuaded a school to change to Ubuntu/Edubuntu. Would this be one computer, a number of computers or a network? Would this be complementing or replacing their Windows system(s)?

Even if you found that all the hardware was 100% compatible with Ubuntu, and that you didn't have to go hunting around for drivers, there would be long-term support to consider. System updates sometimes go wrong - you need someone who can fix this. What happens when a new release of Ubuntu comes out? Do you upgrade or keep the current system(s) as they are? What happens if unexpected system errors occur - sometimes 6 months or a year down the line? Will you still be around? Is there anyone else with Ubuntu experience who can give long-term support? What about the network if there is one? What about future new hardware and configuring it to work with Ubuntu?

What about OS and software training? The interface is different from what they are used to - so is some of the software.

What age are the children in the school? Are they of an age where natural curiosity gives them the incentive (and skill) to try to hack into the system. Who does the mopping up? Will you be there?

Will you want to be there? :wink:

---

### Post by grahammechanical on 2011-10-31
Where to start? I have not tried this. So, it will be an experiment.

I know that you can set the language of Ubuntu or Edubuntu when you install. You can choose Russian or Ukrainian if your friends prefer. They may prefer Ukrainian. Do not think that they won't know the difference. Or that they will not care.

Once installed you can add other language support and install other language keyboard layouts which you can switch to. So, you could type in English even if the system language is Russian.

I think that it is possible to switch system languages after installation. I remember doing this with Russian a few years ago. I was trying to persuade a Russian friend to take up Ubuntu.

My advice is this:

1) Get hold of a computer that you can play with to demonstrate to your friends what is possible.

2) Study partitioning and dual booting.

3) Install Ubuntu - English for your own sanity. Then,

4) Install Ubuntu again but this time choose Russian or Ukrainian as the language. You dual boot. This is why I say study partitioning & dual booting.

5) Experiment. In Russian Ubuntu try to change the system language to English and back again. Try setting different language keyboard layouts.

6) Make a vocabulary of the Russian/Ukrainian equivalents of the English language menu and utility names. Make screenshots of English and Russian menus dialog boxes, etc. So, that if necessary you can make changes when in the non-English language system by using your cheat-sheet.

And remember, because you are not using this machine for actual work if you mess up the system you can just re-install.

Regards.

Oh, one more thing. Get in touch with a Ubuntu LOCO. I do not see one for the Ukraine. So, it have to one of the Russian ones.

[http://loco.ubuntu.com/]("http://loco.ubuntu.com/")

---

### Post by Paddy Landau on 2011-10-31
coffeecat is absolutely correct, and grahammechanical has some good ideas.

In addition, you need to check whether or not they have Windows-specific mission-critical programs that cannot be replaced with Linux programs. For example, if they depend on SAP or Microsoft Publisher, it's a bad idea to change.

To answer your question, though: Yes, it is possible.

[LIST=1]
[*]Set up Linux on one machine and make it right. Also:
[LIST]
[*]Ensure it is fully up-to-date.
[*]Use a separate partition for root (/) and /home.
[*]Set Update Manager to install updates automatically.
[*]Set the firewall to reject incoming requests unless it is from the LAN.
[/LIST]
 
[*]Create a DVD from it using something like [Remastersys]("http://www.geekconnection.org/remastersys/") (or, if the destination partitions are the same size as or larger than the source, [CloneZilla]("http://www.clonezilla.org/") -- but you'll need an external hard drive to store the data). (By the way, I said DVD, but a USB stick is even better as it is faster. Be sure to create a backup, though; you'd hate to lose your hard work.)
[*]When you install the Ubuntu on the new system, ensure it is connected to the Internet via Ethernet to allow it to download any new drivers.
[/LIST]

If the hardware they are using is old and slow, don't use Ubuntu but instead use [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"). Lubuntu is designed for old and slow hardware, and runs lightning-fast compared to Ubuntu.


[LIST]
[*]You will have to spend several intensive hours playing and experimenting with these tools in order to learn how to use them correctly.
[*]Schedule a full weekend to do the actual conversion, because it is inevitable that you will get unexpected problems.
[*]Preferably, do a single computer at a time, and leave it as a dual-boot so that Windows is available as a fall-back should things go horribly wrong. Check that you can sign into both Ubuntu and Windows as part of your testing.
[*]**Back up all data** on a machine before you start the conversion process. Even when you know what you are doing and despite the fact that these tools are well tried-and-proven, there is always a small risk of fatal failure. CloneZilla is an excellent tool for this.
[/LIST]

Before starting, you may want to register with [Canonical Support]("http://www.ubuntu.com/business/services/overview") (but it is expensive for a non-business) for a support contract.

---

### Post by bobski60 on 2011-11-01
Yup Coffeecup . I have thought of all those reasons for not....NOT doing it and leaving it upto someone else who may or mayNOT have a clue what he is doing, I have thought of what the local education office may have in respect of their mission...(its up to the school, with NO outside help from their bosses (on that point who is the BOSS ...only on pay matters do they care)
I am still on the fence on whether I should do it, but as some one said here its a big learning curve...
I have to go in this morning to sort out a USB prob on a russian system that is NOT seeing the usb port.....after having to do this over and over again I know exactly what it is as I have helped 20 or 30 ppls out and that is VIRUS malware and Trogens, their PC are full of them cos everything is pirate (even the shops sell PCs with dodgy or suspect OS....
I am still out for the count on this. BUT
grahammechanical thanks for the advise, I shall be doing that on my system its great fun to learn all these things and 4 x out 10 having to start again.
Thanks for the responses its great that you are all here....:)
Oh and I have persuaded the family to go Ubuntu, (I look after their machine anyway. they are all hard at it backing up their files (where they are going to find 4 or 5 GB backup I have NO idea as DVDs and flash cards are hard to come by on the money these ppls earn but as I said to them, thats their prob not mine if its not backed up IT will be deleted on the O/S.
You have to be firm or its narrrrrrr nearnarder (dont bother, forget it, dont even try)

---

### Post by bobski60 on 2011-11-01
Just got back from the school, My USB worked and what they did was format thier USBs not delete the files on their own Usb drives, so NO they have no idea, On the Ubuntu or Edbuntu instalation I have told them I would only install as a dual boot on the Library pc so the librarian can get used to the system (with my help) then when WE ALL are proficient at it then I would help them out as I am going to try to get sposorship for some newer pcs as they only have 3 in the school but NEED more.
Fingers crossed we can get them.
Every school is ion their own so even down to getting books its businesses that sponsor them.
Thanks again I shall be on here leaning and trying out. I am DL the Edbuntu to look around for my own sanity at the mo, and Dual boot on my system....learn learn learn :P

---

### Post by Paddy Landau on 2011-11-01
Listening to your story, noting that their software is pirated and that their computers may be old, you may be doing the right thing by putting on Ubuntu.

With Ubuntu, as long as they can get hardware, they will no longer be breaking the law by pirating software.

Remember that you have [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") as an alternative to Ubuntu should the hardware be old and slow.

Your idea to start with dual-boot with the librarian and get everyone au fait with Linux first is an excellent one. That way you will be able to troubleshoot teething problems.

Manage the people's expectations: tell them in advance that there *will* be teething problems, there *will* be lots to learn (but it will be fun), and that they *will* be able to ask you lots of questions before they can use it as easily as they use Windows.

And back up all their data before you start!

---

### Post by bobski60 on 2011-11-01
Thanks Paddy,
It is sad but true. I remember 2 yrs ago I went to the Big pc shop to buy this comp and they said that a CD was not available as all I needed to do was to go out and DL the OS off any web site.............I fumed and said I would go else where but their answer was darrrrh its the same everywhere.
needles to say I DID get the original CD before I left the shop. Only to find out that the son had lent it to the cousin who in tern lent it to a friend who in turn lent it to his brother.....Have no idea how many had the CD in the end, and all with my name..did I scream or what..........
So I took it off our system and now have brill-untu all legal like lol

---

