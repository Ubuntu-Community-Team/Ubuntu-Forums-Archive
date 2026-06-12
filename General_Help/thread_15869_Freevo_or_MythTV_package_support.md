---
title: "Freevo or MythTV package support?"
date: 2005-02-17
forum: General Help
---

### Post by Fozzy on 2005-02-17
First, let me congratulate all involved for an elegant and very impressive distro.  Very, very nice work!  :-) 

Now to the question... Does anyone here have any experience in setting up a PVR package like Freevo or MythTV on Ubuntu?  I've added APT sources according to the recommendations respective to each package (treating Ubuntu as Debian, of course), and have found myself mired in unresolved dependencies when attempting to install either one.  Being something of an amateur in Linux, I'm a bit stumped here  ](*,) , and would be grateful for a nudge in the right direction.

Even better... perhaps someone can come up with a customized DEB package to make either or both of these install properly???   \\:D/   I would if I knew how...

TIA

---

### Post by rwillmer on 2005-02-18
I'm currently getting mythtv set up, and it seems to be close to working (a few minor probs to fix)

My setup is this: hoary, running on a EPIA-M 800 MHz, with a Hauppauge PVR-350, running PAL.

So far, I've installed the current version of the ivtv device driver for the PVR-350 card from source.

Then I grabbed mythtv from multiverse repository, which seemed to install OK.

Spent some time setting up X to display on the TV, which is where I'm at now.

So it *should* be just a question of getting MythTV configured to use the right inputs/outputs now.

We'll see.

Rachel

---

### Post by rwillmer on 2005-02-18
Just to confirm, for at least one happy Hoary user, MythTV works just fine with Ubuntu...

(and with a PVR-350 card, you don't even need a fast machine, this is running on an old 800 MHz mini-itx box and seems to be just fine...)

Will write up HOWTO doc once I've finished sorting out the Infra-Red bits.

And I'd even attempt a ubuntu package for the ivtv driver if I find time...

:-)

---

### Post by Fozzy on 2005-02-18
Very cool, Rachel... thanks for the feedback!  I've got a PVR-250, which I believe is based on the same decoder.  So, what works for you should probably work for me as well.  Looking forward to your hw-to!  :grin:

---

### Post by schaez on 2005-02-18
I would check out this Debian how-to for help with lirc and ivtv setup:

[http://www.wilson-stowe.com/mythtv/installguide](http://www.wilson-stowe.com/mythtv/installguide)

It helped me with my PVR-250 setup and MythTV.

---

### Post by Fozzy on 2005-02-23
Thanks for the tip!  I'll definitely look into the how-to...  :smile:

---

### Post by bpilgrim1979 on 2005-03-09
Hi, I am going to wipe a PC and try to setup an Ubuntu MythTV box.  Do I need to add any special modules during Debian installation to support a PVR-250?

---

### Post by rwillmer on 2005-03-10
You'll need the ivtv driver to support the PVR 250 card, which doesn't come as a Debian package. You can get it from <http://ivtv.no-ip.info> - try the 0.2 version if you want stable, 0.3 if you want bleeding edge.

---

### Post by Civil on 2005-08-12
Hi,

I am working on installing MythTV on my Ubuntu box.  I had it all setup and working with my PVR-350, except it was not using the video out of the PVR-350.  So, I knew the quality of the output was not as good as it could be - plus I spent extra to get the MPEG decoder and want to use it.

Well, after some hunting and tweaking, I am now using the PVR-350 as my output card and I have plugged in the SVIDEO output from the card to my TV.

The box boots up automatically into MythTV and I can see the frontend perfectly - nice vivid color.  I go to view a recording, and I can see the sample window play the video clip.  But, when I hit "enter" to actaully watch it, all I see is a purple and green mess of about 12 horizontal streeks.  And they are not even moving - just frozen there.  I hit escape and I am back to the frontend and it all looks good.  The same thing happens when I go to "Watch TV".

I would really appreciate any ideas on how to fix this.

Thanks,
Rich

---

### Post by Civil on 2005-08-12
OK.  You can ignore my last post.  I did some more digging and found out what I was doing wrong.

WOW - what a difference.  After seeing the difference between CPU decoding and built-in decoding on the PVR-350, I wouldn't have it any other way.

Now, I am trying to get the closed captions to work.  On LiveTV and recording, the CC is really hard to follow.  I'll get one good line, then a bunch of gibberish.  And, if I advance the recording, then the CC turns off.

Has anyone been able to get CCs working?  I am using ivtv-0.3.0.

Thanks,
Rich

---

### Post by rwillmer on 2005-08-13
Sorry, I can't help with the closed caption question, its not something I use. But your post reminded me that I'd said I'd write a Howto.

Here it is...

[MythTV on Ubuntu with a Hauppauge PVR-350]("http://www.willmer.com/kb/mythtv/")

Hope that helps someone :)

Rachel

---

### Post by mtron on 2005-08-13
Sorry for the off-topic question. 

A frind of mine gave me his old DVB card. It's a Hauppauge WINTV Nova SE ( SAA7146 PCI bridge), without a MPEG2 decoder chip. I read that these Second Edition is still problematic. but the [LinuxTV wiki](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV_NOVA-s_PCI  ) lists it as fully supported. 

Does sb. have this card succesfully working under ubuntu, and which software should i use?

Cheers mtron

---

