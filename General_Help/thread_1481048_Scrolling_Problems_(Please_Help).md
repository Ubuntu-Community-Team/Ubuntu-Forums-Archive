---
title: "Scrolling Problems (Please Help)"
date: 2010-05-12
forum: General Help
---

### Post by MusicalAlchemy on 2010-05-12
I recently installed the newest version of Ubuntu (64 bit) switching from windows vista.  Everything works great and is much faster than Vista except for scrolling (especially in Mozilla Firefox).  It works fine for a while and then at random times it will start getting glitchy and the top third of the page in the browser will scroll down, the middle third will stop moving, and the bottom third will scroll up.  Or everything on the page just sort of mushes together when you scroll.  When I minimize it and re-enlarge it, the page looks normal again until I scroll and it repeats itself.  I have tried Linux Mint, PCLinuxOS, and ELIVE ZEITGEIST version, and they all do the same thing in both the 32 bit versions and the 64 bit versions.  I've searched and searched online and have found nothing that is relevant to this.  Do I need to install something?  I've seen Ubuntu on a quite old computer working fine, and while mine isn't the top of the line, it's ten times better than that old computer.  It has an AMD Anthalon 64 3300+ 2.41Ghz processor, 1 GB of ram (that somehow fluctuates between 1 GB and 800 and something MB), and an SIS Mirage Graphics card? (I think).  Somebody, please help me with this problem so I can enjoy Ubuntu.

Thanks

---

### Post by warfacegod on 2010-05-12
Disable "Smooth Scrolling" in Firefox. Edit> Preferences> Advanced> General tab.

---

### Post by MusicalAlchemy on 2010-05-12
Alright, I shall try that and hopefully no problem arises.  What is the cause of it? This problem also happens when I view .pdf files.  Any advice on that?

---

### Post by warfacegod on 2010-05-12
Allot of the scrolling gets put into your Video cards RAM. If your card sucks or the driver for the card sucks then you'll probably always have this issue with a pdf.

Open a Terminal and type:

```
sudo lshw
```

Then scroll to where it says "display" and highlight that section. You can copy it (in Terminal) by hitting Shift+Ctrl+C.

Now paste it into a Reply by clicking the # icon and Ctrl+V inside the two code brackets.

Here's what mine looks like:

```
      *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200 64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:c1000000-c1ffffff memory:e0000000-e7fff
```

---

### Post by MusicalAlchemy on 2010-05-13
The smooth scrolling didn't effect anything, it still glitches.  So it's probably the video card.  I went to the terminal and typed it in as you said, and this is all I got,

anubis@Treedar:~$ sudo lshw
SCSI  

I found nowhere to scroll to as you stated.  What am I doing wrong?  Also, my electricity was out since shortly after my last post is why it took me so long to get back on here.

---

### Post by warfacegod on 2010-05-13
Assuming you did the code correctly, as in lower case L not upper I or a 1 then SCSI should display for a bit and then show you lots of hardware info. If it didn't do this after, say 30 seconds, then you may have a more serious problem than I can help you with.

---

### Post by MusicalAlchemy on 2010-05-13
I let it sit for an hour and nothing appeared.  What type of problem would you suspect I have?  Where can I go to get help for this particular problem?  Could it be my video card just sucks that bad?  I wasn't able to use the Aero features in Vista.

---

### Post by warfacegod on 2010-05-13
I'm not sure what your issues could be at this point. That code should absolutely always work. lshw is short for "list hardware", it should give you some info on every piece of hardware in your computer and yet it behaves as though you have no computer at all. I'll see if I can find you some help because I'm baffled.

---

### Post by MusicalAlchemy on 2010-05-14
I thank you for your efforts.  I shall await to see if you find anything.

---

### Post by warfacegod on 2010-05-14
Try:

```
lspci
```

If it works, your video card will be under "VGA Compatible..."

---

### Post by nothingspecial on 2010-05-14
Also type and post back the output of 

```
cat /var/log/Xorg.0.log | grep \(EE\)
```

```
cat /var/log/Xorg.0.log | grep PCI
```

---

### Post by MusicalAlchemy on 2010-05-14
It worked.  Here's what it says:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by MusicalAlchemy on 2010-05-14
For the 
cat /var/log/Xorg.0.log | grep \(EE\)

  
anubis@Treedar:~$ cat /var/log/Xorg.0.log | grep \(EE\)
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

For the 
cat /var/log/Xorg.0.log | grep PCI
anubis@Treedar:~$ cat /var/log/Xorg.0.log | grep PCI
(--) PCI:*(0:1:0:0) 1039:6330:103c:2a06 Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xe0000000/134217728, 0xed000000/131072, I/O @ 0x00009000/128
(II) Primary Device is: PCI 01@00:00:0

---

### Post by nothingspecial on 2010-05-14
It doesn`t seem that your card is well supported in linux. 

I`ll have a good look though.

---

### Post by nothingspecial on 2010-05-14
Hopefully this link will help.

[http://www.winischhofer.eu/linuxsispart2.shtml](http://www.winischhofer.eu/linuxsispart2.shtml)

---

### Post by tom.swartz07 on 2010-05-14
Ive been creeping on this for a little while, and Im trying to think of what is causing this problem.


Does this problem only occur in Firefox?

Do you have any visual effects enabled, even low settings?

Ive been having troubles recently with Compiz locking up and lagging out many of my windows. It usually happens when Im in Google Chrome and the page has a large amount of text and graphics. The scrolling tears (looking like this, kindof: [http://blog.screenaid.com/wp-content/uploads/2009/09/Screen-Tearing-001.jpg](http://blog.screenaid.com/wp-content/uploads/2009/09/Screen-Tearing-001.jpg)) and many of the programs output dont update right away.

---

### Post by warfacegod on 2010-05-14
I've been doing some reading on the SIS cards. It doesn't look to good.

This is from apparently the only guy (that I could find) that has done anything serious with SIS drivers:

> SiS is unfortunately one of those companies that do not support Linux or X.org/XFree86. They don't (and will not) release any documentation on their products (with a few exceptions) and write drivers only for Microsoft's DOS-extensions (called "Windows" by many people; and yes, "Windows" is a trademark). Although they have released XFree86 drivers previously and have released a (binary) driver for the SiS650 in the past, these are and were heavily buggy and not developed any further from a certain point. In other words: Their XFree86 drivers are useless. If you have a notebook, you don't even need to consider trying them.

He evidently hasn't been doing much with the drivers for like six years.

Here's the site if you care to look: [http://www.winischhofer.eu/linuxsispart1.shtml]("http://www.winischhofer.eu/linuxsispart1.shtml")

If you download his driver and it doesn't work out, assuming you are running a desktop as opposed to a laptop, I would get a midgrade nVidia card. Check newegg.com

---

### Post by tom.swartz07 on 2010-05-14
are we sure its a hardware problem? i.e.- is it his video card, or is there something messed with his settings?

---

### Post by warfacegod on 2010-05-14
> **tom.swartz07 said:**
> are we sure its a hardware problem? i.e.- is it his video card, or is there something messed with his settings?

I agree that there are other issues. The video card and/or driver being what it is doesn't (or at least shouldn't) explain 

```
sudo lshw
```

not doing anything.

---

### Post by MusicalAlchemy on 2010-05-14
For tom.swartz07, everything has the scrolling problems and when I move windows, they glitch as well I have recently found out.

Okay, I went to the site, read everything, and downloaded the correct file.  I am just having problems getting it saved in the correct spot.  He says I must stop X.org before completing, and that I need to be in root to install the file.  How do I do this?  I know sudo lets you do things with root privileges or something like that.  Of course, I simply tried to just copy and paste in where it needs to go, but my permission, it says is denied.

---

### Post by warfacegod on 2010-05-14
If copying the file to a specific place is what you need to do (mind you, I haven't read most of the site) then hit Alt+F2> type gksudo nautilus

This will open a root browser. Be certain you don't delete or move something accidentally, being root can be potentially extremely dangerous to your system.

---

### Post by MusicalAlchemy on 2010-05-15
So far it's been working quite well.  I greatly thank all of you for your help.  I will try it out for a while and post back if any more of the problems should arise  or if it continues work correctly.

---

### Post by MusicalAlchemy on 2010-05-22
It has continued to work great with no problems what-so-ever, well, besides that it still shows nothing after sudo lshw.  Once again, thank ye all for your help.  It nice to see that there are still people willing to help others with no gain for themselves.

---

### Post by tom.swartz07 on 2010-05-23
> **MusicalAlchemy said:**
> It has continued to work great with no problems what-so-ever, well, besides that it still shows nothing after sudo lshw.  Once again, thank ye all for your help.  It nice to see that there are still people willing to help others with no gain for themselves.

Sure thing buddy! I know I didnt help too too much with this, but I would just like to point out that the desire to help and do without personal gain is exactly why Ubuntu exists!

Open source and freedom of information :D

---

### Post by warfacegod on 2010-05-23
> **MusicalAlchemy said:**
> It has continued to work great with no problems what-so-ever, well, besides that it still shows nothing after sudo lshw.  Once again, thank ye all for your help.  It nice to see that there are still people willing to help others with no gain for themselves.

nothingspecial should get the credit for this one although I'm willing to ride coattails. I did, after all, go get help and I found the same site nothingspecial did (40 minutes later but still). Actually, I've decided *I* should get all the credit. No, no, a standing ovation is not necessary but it is welcome. Let's see... I'd like to thank my agent and my co-stars... Wait! Sorry, wrong speech.

Seriously. I get plenty out of helping people. I would still know virtually nothing about using my own set up, if I hadn't decided to start wandering the forums rendering assistance. Which I hadn't considered until just now. Great! You completely ruined my altruistic image of myself.:biggrin:

---

### Post by MusicalAlchemy on 2010-05-23
Indeed, Ubuntu and all it stands for, well Linux in general(for the most part), are very honorable and things such as that will help advance the human race.  Helping the whole of humanity, not striving for personal gain while the rest of the world is left behind in the dust to rot. On that topic, you should check out The Zeitgeist Movement.  That would be a great speech for the right occasion warfacegod. Ha.  The trees will give you a standing ovation.  If you accomplish something just go in the woods and or forest and most will give you a standing ovation.  The ones that don't, BURN THEM!!!  Also, while in the woods, avoid the Knights who say Neigh.  Well even if it does give you a gain, it helps the others as well, and if you do it for the sake of helping them but receive benefits from that, I would still consider you altruistic.  By the way, if any of you have the time, would you kindly go give my band a listen?  [www.myspace.com/mailordermiracle](www.myspace.com/mailordermiracle)

---

### Post by warfacegod on 2010-05-25
I just remembered, I get ***_beanses_*** for helping people!

---

