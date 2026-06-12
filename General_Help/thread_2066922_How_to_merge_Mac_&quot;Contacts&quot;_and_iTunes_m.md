---
title: "How to merge Mac &quot;Contacts&quot; and iTunes music on iPhone 5 (iOS 6)"
date: 2012-10-05
forum: General Help
---

### Post by Fidelio1st on 2012-10-05
So I kind of have a mess here and any help in solving my issues would be much appreciated.  I just got an iPhone 5, and I'm trying to be able to do a couple things with my home computer running Ubuntu 8.04 with Windows Vista running in Virtualbox:

1) Take my 1500 work contacts from an iMac OSX 10.8.1 in the new "Contacts" program (formerly Address Book on older Macs) and put them on my iPhone, and possibly my home computer as well, however not really necessary.  

2) I want to keep my personal 500 contacts on my iPhone - the 1500 can be merged on the iPhone, that's fine.  But I can't plug in the iPhone to the iMac because then it will merge my personal 500 contacts on the iMac, and I can't do that because other iPhones are accessing these contacts on the iMac, and I don't want the 500 personal contacts on the other phones.

The 500 personal contacts I will be updating periodically on my phone.  The 1500 work contacts I will be updating periodically on the iMAC, therefore, say once a month, I will need to reupload the 1500 contacts to my iPhone so it is up-to-date.

So is there a way I can do this on Ubuntu or through Windows Vista in virtualbox?


3) I want to be able to take my iTunes music (some of it not from iTunes, for instance, much of it I turned from personal CD's into music files) and put it on my iPhone.  I believe I can just use the iTunes program in Windows Vista on Virtualbox for this, correct?  And will iTunes allow me to change .m4a files into a playable file in iTunes?


I'm basically trying to figure out if keeping the iPhone 5 is worth it, or if I should trade it in for something else.  My whole reason for getting it was for contacts and music.  I thought I had it figured out because I have an old Mac computer at home, but it has a PC Power Processor which won't upgrade to Leopard OS, therefore it won't read my new iPhone 5.

If anyone has suggestions for a better phone that would accomplish what I need and run off Ubuntu or Windows Vista system, I'd appreciate that as well.

---

### Post by jingaling on 2012-10-05
First of all, shame on you for buying an iPhone - Android all the way - I'm joking of course.

So if I understand you correctly you effectively have 2 address books, 1 personal, one work and you want them to update independently. Is that correct?

If that's the case then the best thing I advice is can offer is not to use an iPhone. Syncing though iTunes is a kind of all or nothing deal which makes it very difficult to pick and chose what you want to to sync.

However, if you want to keep the iPhone then I would suggest you sync you personal address book completely separately from iTunes. To do this I would suggest you do this over the air (OTA) via a gmail account. Here is a link to a guide on how to accomplish this on an iOS device:

[http://support.google.com/mail/bin/answer.py?hl=en&answer=2753077&topic=21369&ctx=topic](http://support.google.com/mail/bin/answer.py?hl=en&answer=2753077&topic=21369&ctx=topic)

This will mean that you personal address book is synced OTA and kept completely seperate from iTunes, thus allowing you to sync your seconds address book through iTunes to both of your phones.

I'm not an iTunes/iOS user so I'm not 100% how well this would work but it's gotta be worth a try.

With regards to your music, you could use iTunes through your Vista VM or you could use something like Floola or Rhythmbox to sync your iPhone with your music library natively in Ubuntu. However, doing this means you won't be able to sync it with iTunes. This is because of the close nature of Apple devices unfortunately.

If you want my advice, I'd say switch to an Android device. They're much easier to use and you will be able to easily accomplish your goals with the use of completely separate address books tied to separate accounts on the device. Your music can be transferred either by drag and drop onto the device vis mass storage or by pretty much any music manager like Rhythmbox, Banshee etc.

Finally, why are you using 8.04? Dude you should really upgrade :)

Hope this all helps. Let us know how you get on.

Jing

---

### Post by Fidelio1st on 2012-10-06
Thank you - this advice is very helpful.

Basically I received an Apple GC, so that's why I got an iPhone.  Any suggestions on a good Android phone?  Trying to work here on a budget, and a free iPhone fits well in that budget.  And I do love the camera on the iPhone 5, takes great pics.

I'm gonna try the stuff you suggest. In regards to the old version of ubuntu, I have certain software that works fine now, and I'm afraid if I upgrade, it will either stop working or it will be a real pain to get it working again.  It's kind of like if it ain't broke, don't fix it thing.
A couple programs I'm worried about not working or that I will have to spend a lot of time trying to find a more recent copy then figure how to install are virtualbox and k9copy (which I believe requires a bunch of other programs to work properly).  Do you know if these will work fine if I upgrade to the most recent Ubuntu?

---

### Post by jingaling on 2012-10-06
Hey,

There are so many Android devices out there different people have different preferences. Personally I like the Nexus and Galaxy devices (Google's own and Samsung respectively) they are great devices. The Nexus devices do tend to be cheaper as well. Although they're not as cheap as 'free'. :)

Really you found the camera to be good? I've heard a lot of stories about the purple flares being visible on pictures taken with the iPhone 5. Anyway, I digress...

I don't use K9Copy but according to [Launchpad]("https://launchpad.net/ubuntu/precise/amd64/k9copy") there are 12.04 binaries so it should work. I'm not sure if it's available in USC though as I'm on a Windows machine at the moment. With regards to Virtualbox, it's faultless in 12.04. I use it all the time.

As you probably know though, the best way to test compatibility is to burn a live CD and take it for a spin. You could also use [Clonezilla]("http://clonezilla.org/") to backup your machine before upgrading so you can revert back if you need to.

---

### Post by Fidelio1st on 2012-10-06
jingaling, thank you so so much.  Due to your help, I got my contacts onto my iPhone and believe I figured out the synching.  

One last question: my groups I set up in "Contacts" on the iMac for the work contacts transferred to my Gmail account (when I imported the vCard file from Contacts to Gmail), however, the groups did not move over to my iPhone.

Do you know if there is a way to make the groups go from gmail to iPhone?


Once this is answered I will post a reply some instructions I wrote up to help others that may want to do this....

---

### Post by jingaling on 2012-10-06
No problem at all. Happy to help. :)

Unfortunately I don't know of a way to sync Gmail groups to your iPhone. As I said, I'm not an iPhone user but I do know Google pretty well so I made some assumptions. Happy you figured it out though.

I've had a look online and can't find any details on how to sync groups either. Apparently there is an app call "Soocial" (that's not a typo, it has two O's) and that can sync Gmail contact also, again not groups though. This may be an easier way to do it. But like I said, I'm not an iPhone user so I can't really say.

---

### Post by Fidelio1st on 2012-10-10
So it looks like Windows Vista running in virtualbox through Ubuntu 8.04 sees my iPhone - it shows it under the USB devices icon on the bottom.  But I need internet connection for iTunes Store or for iTunes to see my iPhone.

So how can I connect to the internet through Windows Vista running in Virtualbox (in Ubuntu)?  I can't seem to figure it out - I've tried right clicking on the internet icon, and then "connect to a network", but then it says "Windows cannot find any networks".  

I'm trying to connect through the same wifi I am connected to in Ubuntu.

---

### Post by jingaling on 2012-10-10
You need to make sure that the VM has a network adapter and it is enabled. Go into the VM settings and select network from the left hand pane.

When the network settings are displayed make sure adapter 1 is enabled and the "attached to" drop down is set to "NAT". That should get your VM online.

Although this is the default config on VM's anyway so I would imagine this is already configured. If it is it may be because you're running an old version of Virtualbox.

---

### Post by Fidelio1st on 2012-10-14
One again, you've been a big help and I'm almost there with iTunes.  My Nat was off, so once I turned that on, I had internet connection in Vista and iTunes.


What I'm trying to do is get my entire music library (backed up onto a harddrive) onto my iphone.  I was able to transfer a test folder over into iTunes and it's now in my music library.  However, when I play the music through Vista iTunes, it doesn't play well, almost like it's skipping or slowed down a bit (in the end this doesn't matter because I won't be playing music from my computer, but just not sure if there is a problem with the files or not, they are .m4a files).

I have iTunes 10.7.0.21, most up to date version. In Virtualbox, when I go to devices/USB devices, it shows my iPhone 5.  However, iTunes is not showing my iPhone on the left bar and I can't figure out how to access the iPhone through iTunes in Vitualbox/Vista.  I've shut down and restarted iTunes several times, and then I shut down and restarted Vista, but still the same.

I ran a device connectivity test through iTunes and everything checks out under ports, except "no iPod, iPhone, or iPad found".  Below is the entire diagnostic (I replaced some #'s with [NA] as I wasn't sure if I should post on a public form).

If I must, I'll update Ubuntu to 12 and Virtualbox to the most recent, it's just I'm afraid I'll have problems getting certain programs to work (or just that I'll have to refigure them out) and since most my stuff works now except for this, still trying to make this work.  So please let me know if you have any suggestions for getting it to read my iPhone, thanks.


_DIAGNOSTIC_


Microsoft Windows Vista Home Premium Edition (Build 6000)
innotek GmbH VirtualBox
iTunes 10.7.0.21
QuickTime not available
FairPlay 2.2.19
Apple Application Support 2.2.2
iPod Updater Library 10.0d2
CD Driver 2.2.3.0
CD Driver DLL 2.1.3.1
Apple Mobile Device 6.0.0.59
Apple Mobile Device Driver 1.62.0.0
Bonjour 3.0.0.10 (333.10)
Gracenote SDK 1.9.6.502
Gracenote MusicID 1.9.6.115
Gracenote Submit 1.9.6.143
Gracenote DSP 1.9.6.45

iTunes Serial Number [NA]

Current user is not an administrator.
The current local date and time is 2012-10-14 15:40:15.
iTunes is not running in safe mode.
WebKit accelerated compositing is disabled.
HDCP is not supported.
Core Media is not supported. (16002)

Video Display Information

Oracle Corporation, VirtualBox Graphics Adapter


**** External Plug-ins Information ****

No external plug-ins installed.

**** Network Connectivity Tests ****

Network Adapter Information

Adapter Name:    { [NA]}
Description:    Intel(R) PRO/1000 MT Desktop Adapter
IP Address:    [NA]
Subnet Mask:    [NA]
Default Gateway:    [NA]
DHCP Enabled:    Yes
DHCP Server:    [NA]
Lease Obtained:    Sun Oct 14 15:02:01 2012

Lease Expires:    Mon Oct 15 15:02:01 2012

DNS Servers:     [NA]
         [NA]

Active Connection:    LAN Connection
Connected:    Yes
Online:        Yes
Using Modem:    No
Using LAN:    Yes
Using Proxy:    No

Firewall Information

Windows Firewall is on.
iTunes is NOT enabled in Windows Firewall.

Connection attempt to Apple web site was successful.
Connection attempt to browsing iTunes Store was successful.
Connection attempt to purchasing from iTunes Store was successful.
Connection attempt to iPhone activation server was successful.
Connection attempt to firmware update server was successful.
Connection attempt to Gracenote server was successful.
Last successful iTunes Store access was 2012-10-14 15:32:21.


**** Device Connectivity Tests ****

iPodService 10.7.0.21 is currently running.
iTunesHelper 10.7.0.21 is currently running.
Apple Mobile Device service 3.3.0.0 is currently running.

Universal Serial Bus Controllers:

Standard OpenHCD USB Host Controller.  Device is working properly.

No FireWire (IEEE 1394) Host Controller found.

**** Device Sync Tests ****

No iPod, iPhone, or iPad found.

---

