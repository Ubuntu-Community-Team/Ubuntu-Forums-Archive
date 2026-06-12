---
title: "Broken USB 1.1"
date: 2010-01-26
forum: General Help
---

### Post by warfacegod on 2010-01-26
I need to fix my USB ports. 6 months ago they worked. Come home from work wife says they don't. I suspect she tried to suspend and that's what did it. With a fresh install, I have the same issue. When I plug in a flash drive or my keyboard the lights go on but I get nothing else. Thanks.

---

### Post by audiomick on 2010-01-26
when something is plugged in, does it turn up with
```
lsusb
```

---

### Post by warfacegod on 2010-01-26
No. I just get the root hubs.

---

### Post by 73ckn797 on 2010-01-27
If you apply a little pressure, up or down and hold it there, on the USB connector, does anything happen? I am just wondering whether the port could have a loose contact internally at the board or in the port itself.

---

### Post by warfacegod on 2010-01-27
Pressure doesn't work. Besides, it's unlikely that the two USB's in front and the two in back would become loose at the same time. The front one connects via wore and the back is hard wired onto the motherboard.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Pressure doesn't work. Besides, it's unlikely that the two USB's in front and the two in back would become loose at the same time. The front one connects via wore and the back is hard wired onto the motherboard.
you could try to find a cheap pci usb card... should be too expensive ;)

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> you could try to find a cheap pci usb card... should be too expensive ;)

That's not a bad idea. Let me shoo the moths out of my wallet and I'll go to Bestbuy.

---

### Post by 73ckn797 on 2010-01-27
> **warfacegod said:**
> That's not a bad idea. Let me shoo the moths out of my wallet and I'll go to Bestbuy.

Best Buy never has what I am looking for, especially at a low price.

Check this out:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=723748&Sku=M501-1002](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=723748&Sku=M501-1002)

There are other brands and different prices. Just want to help.

---

### Post by warfacegod on 2010-01-27
Thanks for the link. I need one for my wife's desktop or fix the one's she'd got so I can use her computer to make an install USB so I can fix my laptop.

---

### Post by 73ckn797 on 2010-01-27
> **warfacegod said:**
> Thanks for the link. I need one for my wife's desktop or fix the one's she'd got so I can use her computer to make an install USB so I can fix my laptop.


Here is another link. They have 2 stores near me but not in Conn. (where your info states you are).

[http://www.microcenter.com/index.html](http://www.microcenter.com/index.html)

---

### Post by Leppie on 2010-01-27
amazon has 1 for under $10 (2ports)... another one at under $20 (5ports): [http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Dmi&field-keywords=usb+pci&x=0&y=0](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Dmi&field-keywords=usb+pci&x=0&y=0)

---

### Post by warfacegod on 2010-01-27
Thanks guys. I'm gong to see if I can get a USB to Firewire adapter from Radioshack. I've got a Firewire card and I suspect an adapter would be cheaper. If not, then cheap USB card, here I come.

---

### Post by Leppie on 2010-01-27
not sure how it is where you are, but here adapters are extremely expensive (for instance, regular price for sata > usb is like €40+)...

---

### Post by warfacegod on 2010-01-27
You know...my head is about to explode off of my neck like a Saturn V rocket from the sheer lunacy that I am having to go through to fix one blasted laptop.


...And I didn't even *do* anything to it!

---

### Post by warfacegod on 2010-01-27
3..2..1..KaBBOOOMMM!!!!

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> 3..2..1..kabbooommm!!!!

> bestrafe mich 
            bestrafe mich 
            stroh wird gold 
            und gold wird stein 
            deine größe macht mich klein 
            du darfst mein bestrafer sein 
          der herrgott nimmt 
            der herrgott gibt


:p

---

### Post by egalvan on 2010-01-27
Before you spend the precious shekels...

have you checked the BIOS?

have you tried anotehr LiveCD such as Puppy or TinyCore or TinyMe?


I always have the latest Puppy, TinyCore, TinyMe and PartedMagic LiveCDs to do hardware checks.

---

### Post by 73ckn797 on 2010-01-27
> **warfacegod said:**
> 3..2..1..KaBBOOOMMM!!!!

I heard that all the way down here! No, wait. I think it was from the rock quarry nearby.

---

### Post by warfacegod on 2010-01-27
> **egalvan said:**
> Before you spend the precious shekels...

have you checked the BIOS?

have you tried anotehr LiveCD such as Puppy or TinyCore or TinyMe?


I always have the latest Puppy, TinyCore, TinyMe and PartedMagic LiveCDs to do hardware checks.

I checked the BIOS twice yesterday, to make sure. It's not just my jump drive but my key board, external HDD, external DVD drive, printer, camera, and scanner. The computer sends power to them but nothing gets mounted or put to use. So I can't even get to the point of using the USB Startup Disc Creator.

Although, you just gave me an idea. I'm going to try the USB's from a Live CD.

---

### Post by warfacegod on 2010-01-27
> **73ckn797 said:**
> I heard that all the way down here! No, wait. I think it was from the rock quarry nearby.

Full of Rednecks?

---

### Post by 73ckn797 on 2010-01-27
> **warfacegod said:**
> Full of Rednecks?
Probably. They are widening 30 miles of I-85 down here and there are a lot of dump trucks around.

Have you disassembled the computer to check for any loose connections? If all of those things have quit, that would be my first thing to check.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> I checked the BIOS twice yesterday, to make sure. It's not just my jump drive but my key board, external HDD, external DVD drive, printer, camera, and scanner. The computer sends power to them but nothing gets mounted or put to use.
so maybe it's something in the os, not hw?

---

### Post by warfacegod on 2010-01-27
I took the cover off this morning. Everything seems fine.

Can't be OS (I don't think) this happened in 8.10 and I'm on a fresh (sort of) install of 9.10

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> I'm on a fresh (sort of) install of 9.10
"sort of" fresh install???
is that like the mythbuntu into the unr install? :P

---

### Post by no2498 on 2010-01-27
dont jump the gun
look at all the bugs for usb's
my webcam just took a dump its down to .7 fps
only thing plugged  in
804 hardy

---

### Post by Leppie on 2010-01-27
is the cdrom working on the desktop (sorry, don't remember...)?
if so, just download another distro's livecd (like knoppix).

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> "sort of" fresh install???
is that like the mythbuntu into the unr install? :P

Fresh as in leaving an unopened jug of milk on the table for a week. I installed it last month. My wife and stepson gave themselves Administrator accounts when I left it on in my user account. That kind of fresh.

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> is the cdrom working on the desktop (sorry, don't remember...)?

Yes.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Fresh as in leaving an unopened jug of milk on the table for a week. I installed it last month. My wife and stepson gave themselves Administrator accounts when I left it on in my user account. That kind of fresh.
hmm... would they not require your pw first?

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Yes.
then try knoppix or some other livecd?
and see if usb works ;)

---

### Post by warfacegod on 2010-01-27
> **no2498 said:**
> dont jump the gun
look at all the bugs for usb's
my webcam just took a dump its down to .7 fps
only thing plugged  in
804 hardy

Look on the bright side. At least it still works.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Look on the bright side. At least it still works.
lol...

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> hmm... would they not require your pw first?

Not when it was a temporary p.w. that I left taped to the wall like a dolt.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Not when it was a temporary p.w. that I left taped to the wall like a dolt.
handy... for them... :P

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> handy... for them... :P

Yeah, but I didn't really care because they can't mess up my account and I only use it for emergencies. Just like now!

---

### Post by audiomick on 2010-01-27
Did you also have a good look at the plug in side of the connector? It sounds like maybe only one pin is not making contact. Maybe there's a bent one.

@ Leppie
where did you find the poem?
```
bestrafe mich
bestrafe mich ...
```

---

### Post by Leppie on 2010-01-27
> **audiomick said:**
> @ Leppie
where did you find the poem?
```
bestrafe mich
bestrafe mich ...
```
Rammstein...

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Yeah, but I didn't really care because they can't mess up my account and I only use it for emergencies. Just like now!
maybe not your account, but the system around it?

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> maybe not your account, but the system around it?

I am discovering this as we speak. I rebooted the desktop after LiveCD and it went berserk. Ubuntu refused to boot, recovery mode had a red maintance shell warning staggered all over the screen, then went entirely red with words randomly scattered all over the screen, hitting enter brought more words until it showed the recovery menu with the CLI super imposed over the middle of the screen, and reboot from there kicked me into the root account desktop where I am now. HUH!?

---

### Post by audiomick on 2010-01-27
> **Leppie said:**
> Rammstein...

Oh, that explains it then. Want me to translate?;)

---

### Post by Leppie on 2010-01-27
> **audiomick said:**
> Oh, that explains it then. Want me to translate?;)
thanks for the offer, but i speak a bit of german ;)

---

### Post by warfacegod on 2010-01-27
> **audiomick said:**
> Oh, that explains it then. Want me to translate?;)

Du...Du Hast...Du Hast Mechagodzilla!

---

### Post by audiomick on 2010-01-27
> **Leppie said:**
> thanks for the offer, but i speak a bit of german ;)

The man is full of surprises...

---

### Post by Leppie on 2010-01-27
well, i'm magical... :P

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> well, i'm magical... :P

Leperchaun thing again? The Irish still want your pot?

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Leperchaun thing again? The Irish still want your pot?
i wish it were only the irish... ;)

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> i wish it were only the irish... ;)

Hey, don't look at me. Now, I'm too busy trying to fix my wife's computer before she gets back.

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Hey, don't look at me. Now, I'm too busy trying to fix my wife's computer before she gets back.
yeah, but earlier i saw you lurking for my gold... :P

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> yeah, but earlier i saw you lurking for my gold... :P

'Twern't me, Doppleganger. <<See! I know German too!

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> 'Twern't me, Doppleganger. <<See! I know German too!
that's what they all say... :P
aren't gods free of human language bounderies?

---

### Post by audiomick on 2010-01-27
> **warfacegod said:**
> 'Twern't me, Doppleganger. <<See! I know German too!

3 languages then: English, German and Redneck ?

---

### Post by warfacegod on 2010-01-27
> **audiomick said:**
> 3 languages then: English, German and Redneck ?

Actually, I'm most fluent in Gibberish.

---

### Post by Leppie on 2010-01-28
> **warfacegod said:**
> Actually, I'm most fluent in Gibberish.
that's my favorite ;)

---

