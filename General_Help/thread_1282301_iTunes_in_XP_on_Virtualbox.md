---
title: "iTunes in XP on Virtualbox"
date: 2009-10-04
forum: General Help
---

### Post by motorcity909 on 2009-10-04
Hi all, I've been happily using Ubuntu now for a couple of months but one programme I do miss is iTunes; not for playing music but for managing my iPod.  None of the Ubuntu equivalents does the job IMHO, while a couple of them screwed up my iPod.

Hence, I end up booting up my wife's XP laptop to use iTunes.

I've got a spare copy of XP and am thinking of installing Virtualbox and then installing XP.

Will I then be able to install iTunes and manage my iPod with it?  I've seen a few sites saying that USB devices don't work in Virtualbox.  

Will I be able to see my Music collection in my Ubuntu Home folder from within XP and iTunes, or would I temporarily have to copy new music into XP to add it to my iPod?

I know I've asked a bundle of questions there, I'll be very grateful for any help.

---

### Post by pilorama on 2009-10-04
Doesn't matter what kind of virtual machine you are using to run your XP as a guest OS.
I'm using vmware to run windows based software.
[[IMG]http://cash1000.org/images/th.png[/IMG]]("http://groups.adobe.com/people/838ec6d24c/profile")

---

### Post by motorcity909 on 2009-10-04
I've successfully installed Virtualbox and Windows XP onto my Ubutnu machine.  

However, I can't get a USB device to be recognised.  I've only tried a simple pen drive, not my iPod for now.

I've added myself to the vbox users groups but still no USB recognition.  I found that solution [here]("http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml").

On the plus side, XP can see and play my music collection, so if I can get this USB thing sorted there shouldn't be any problems in adding new music to iTunes and my iPod.

Thanks in advance for any further help.

---

### Post by motorcity909 on 2009-10-06
Job done!

Installed the other version of Virtualbox which has USB support.  Installed XP onto it.  Installed iTunes.  Plugged in iPod; told Ubuntu to ignore it, then mounted it in XP.  

iTunes started up, iPod appeared in it and have been able to copy music from my Samba-shared Ubuntu Music folder into iTunes and then onto my iPod.

Marvellous!

---

### Post by styven on 2009-10-06
> **motorcity909 said:**
> Job done!

Installed the other version of Virtualbox which has USB support.  Installed XP onto it.  Installed iTunes.  Plugged in iPod; told Ubuntu to ignore it, then mounted it in XP.  

iTunes started up, iPod appeared in it and have been able to copy music from my Samba-shared Ubuntu Music folder into iTunes and then onto my iPod.

Marvellous!

So, to get this clear, you can share music from your host samba share on ubuntu to your guest xp running in virtualbox?
Steve.

---

### Post by motorcity909 on 2009-10-07
Yep, the Samba share appears in XP's network places, just as it does on my wife's laptop or my son's netbook.  Screengrab attached.

I also came across some documentation on the [Virtualbox website]("http://www.virtualbox.org/manual/UserManual.html#sharedfolders") saying it's possible to share folders between host and guest *without* networking.

---

### Post by reader4 on 2009-10-21
I've been using this setup for a few years now with mostly success.  I keep my iTunes folder on the host, share the folder using VBox (no samba needed) and set that location in iTunes.  Occasionally I have run into problems syncing the iPod, which seems anecdotally more problematic when I include videos or the song format is not correct.  I haven't really taken the time to troubleshoot it.  Glad it's working for you!  iTunes does a much better job managing music for the iPod, IMO, especially for classical libraries.

---

### Post by motorcity909 on 2009-10-22
I do agree with you that iTunes is the best thing to manage an iPod.  I'd like nothing more than to use one of the Linux music players to manage it but Amarok, Rhythmbox and Banshee all screwed up my iPod in some way (deleting covers, id tags not appearing correctly).

It's a shame that Apple won't do a Linux version but there we are.  Running XP in Virtualbox for this one thing is an elegant solution; much easier and quicker than booting up our XP laptop.

---

### Post by styven on 2009-11-08
> **motorcity909 said:**
> Yep, the Samba share appears in XP's network places, just as it does on my wife's laptop or my son's netbook.  Screengrab attached.

I also came across some documentation on the [Virtualbox website]("http://www.virtualbox.org/manual/UserManual.html#sharedfolders") saying it's possible to share folders between host and guest *without* networking.

Thanks for your reply, I have indeed got that set up now. However I have an issue in that Itunes won't update with newly added songs saying I don't have access permission to the shared folder from my ubuntu host. I have tried to apply the relevant permissions to the files in the music folder.

As it stands I have to manually adjust the permissions of the new tracks individually and then add them individually in Itunes.

Using the Virtualbox shared folder option works and I have for the time being pointed Itunes to that, but still Itunes will not update it's library, even though the permissions issue has gone.

Any thoughts............

Steve.

---

### Post by motorcity909 on 2009-11-08
Unfortunately, I don't have iTunes set to automatically add new albums/songs or to then sync with my iPod.  I manually add new albums to my iTunes library.

Can you access the Ubuntu Music folder okay in Windows Explorer Network Places?  And play tracks therein?

---

### Post by jimmy the saint on 2009-11-08
This thread is why I use a Sanza Fuze instead of an ipod.  That and it cost me 40 bucks, has microSD support, great for recording lectures, is drag and drop, and doesn't require Windows or Apple.

---

### Post by motorcity909 on 2009-11-09
So there we go Styven.  The solution isn't to try and figure out how to solve the problem but to simply dump our iPods and buy something else instead. ;)

---

### Post by styven on 2010-01-31
> **motorcity909 said:**
> So there we go Styven.  The solution isn't to try and figure out how to solve the problem but to simply dump our iPods and buy something else instead. ;)

I absolutely agree, I have a 4gb Sanza Clip, it's brilliant cost me £35. But sadly peer pressure is very strong and my kids want ipods and they will want iphones, in the same way that they to use MSN Messenger not Skype to do webcam and "Daddy why can't we have MS Office".

I have some very strong views on the sheep mentality of consumers and product lock in, I can't expect my kids to have to explain to there friends why the don't have Ipods and everyone else does, it crap and bothers me a lot.

It not made any easier when some parents of one of my daughters friends recently upgraded there iphones and gave the old ones to there kids, there only 13!!

---

### Post by styven on 2010-01-31
> **motorcity909 said:**
> Unfortunately, I don't have iTunes set to automatically add new albums/songs or to then sync with my iPod.  I manually add new albums to my iTunes library.

Can you access the Ubuntu Music folder okay in Windows Explorer Network Places?  And play tracks therein?

I pretty much have this set up as well, however i am trying to set it up for my daughter to make it as painless as possible. Sadly Itunes does not scan and and add automatically new files in the music folder you point it to (unless you buy your tunes through itunes, then it does) nor does it have a button to click to do so.

---

### Post by banerjeerupak on 2010-03-24
I would like to install vbox and then xp followed by itunes. It was mentioned previously that i should install the vbox with usb support. However vbox site shows it to be closed source. How can i get hold of that?

---

### Post by motorcity909 on 2010-03-24
Download the Personal Use and Evaluation License version here -

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

It's closed-source but still free.

Cheers
Dave

---

### Post by kickwin on 2011-03-27
Where do you have all your songs? My Virtualbox is very small (only 4GB) and I cant simply move all my songs to Guest. Having the songs in a shared folder takes forever to load library when ITunes start. Do I have any other option?

---

### Post by rgb1701 on 2011-03-27
> **styven said:**
> I absolutely agree, I have a 4gb Sanza Clip, it's brilliant cost me £35. But sadly peer pressure is very strong and my kids want ipods and they will want iphones, in the same way that they to use MSN Messenger not Skype to do webcam and "Daddy why can't we have MS Office".

I have some very strong views on the sheep mentality of consumers and product lock in, I can't expect my kids to have to explain to there friends why the don't have Ipods and everyone else does, it crap and bothers me a lot.

It not made any easier when some parents of one of my daughters friends recently upgraded there iphones and gave the old ones to there kids, there only 13!!

+1

I just bought the Sansa Clip+, and have been using the Fuze for about two years now.

These Sansa players are the FOSS of the MP3 player world.

They support open standards, drag and drop file management, and support Rockbox, the open source firmware (the OS for the MP3 player) replacement, easy to install-

[http://www.rockbox.org/download/](http://www.rockbox.org/download/)

[http://build.rockbox.org/](http://build.rockbox.org/)

The Sansa will dual boot Rockbox and the original firmware/OS on the Fuze and I assume the Clip+, as I only put it on my Fuze.

I have strong negative feelings about parents who just get their kids/wife whatever "everyone else" has and fall for peer pressure- just bad parenting and bad life lessons for the kids.

Teaching independence and critical thinking (buying on technical and feature merit) is more important to them in the long run than just following pop culture, fads, and succumbing to marketing peer pressure, letting the advertising brain washing "win" :(

And to a casual passerby, the Fuze looks like an iPod anyways with its real mechanical scroll wheel :D

[http://www.overstock.com/Electronics/SanDisk-Sansa-Fuze-4GB-Multimedia-MP3-Player-Refurbished/4136459/product.html](http://www.overstock.com/Electronics/SanDisk-Sansa-Fuze-4GB-Multimedia-MP3-Player-Refurbished/4136459/product.html)

But seriously, I believe the Sansa's to be technically and mechanically superior to iPods.

---

### Post by motorcity909 on 2011-03-29
> Where do you have all your songs? My Virtualbox is very small (only 4GB)  and I cant simply move all my songs to Guest. Having the songs in a  shared folder takes forever to load library when ITunes start. Do I have  any other option?     All of my songs sit in the Ubuntu Music folder which is shared and accessible in Vbox XP.  

I add songs to iTunes only to add them to my iPod.  Once they're on it, I remove them from iTunes.  After all, I don't use iTunes as a media player for my entire library - I do that within Ubuntu.

Talking of which, I use Guayadeque as my music player and as of version 0.2.9 it comes with iPod support so I am happily adding songs to my iPod without Virtualbox, Windows XP or iTunes.

The Guayadeque in the Ubuntu software centre is an older version so if you want to give this a try you'll have to get it from their website - [http://guayadeque.org](http://guayadeque.org)

> I just bought the Sansa Clip+A whole 4gb?  I don't have an iPod because I'm a sheep or trying to be a dedicated follower of fashion but because I want loads of space = 80gb Classic.

:guitar:

As for the rest of that post, not sure this is the place for a treatise on parenting.......

---

### Post by kickwin on 2011-03-29
> **motorcity909 said:**
> 

The Guayadeque in the Ubuntu software centre is an older version so if you want to give this a try you'll have to get it from their website - [http://guayadeque.org](http://guayadeque.org)


Which IPod do you use? I have a 5th Gen Nano and it doesn't work with Rhythmbox and Banshee.

---

### Post by linuxuser12345 on 2011-03-29
Have any of your heard of Wine? Wine is a program for Linux, etc. that *lets* your run Microsoft Windows programs without actually *owning* Microsoft Windows.
Wine runs iTunes just fine.
Check it out in the Ubuntu Software Center or [www.winehq.org](www.winehq.org)

---

### Post by motorcity909 on 2011-03-30
> Have any of your heard of Wine?Yep tried Wine but could barely get iTunes to install never mind run or see my iPod.  Hence I've been using Virtualbox but now don't even need that with Guayadeque.

> Which IPod do you use?It's a 6th Gen 80gb Classic.

I could never get it to work with Rhythmbox or Banshee.  One wouldn't even see my iPod while the other wiped all my album covers off!  That's how I ended up using iTunes on XP under Virtualbox.

---

