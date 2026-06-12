---
title: "Saving or copying files to USB memory stick corrupts them"
date: 2010-04-21
forum: General Help
---

### Post by TomD22 on 2010-04-21
I've just bought a USB memory stick. 

When I save files on it from Ubuntu, or copy files onto it, they get sporadically corrupted. Jpeg images get peppered with artefacts or sometimes can't be opened at all; .doc or .odt files the character encoding gets messed up and the text can't be read, etc. Oddly, PDF documents are not affected.

I've tested this with large numbers of files, individually and in batches.

Conversely, the drive works perfectly from a Windows machine. No files get corrupted, and they can be opened fine from both Windows and Ubuntu.

This behaviour occurred with the drive formatted however it came by default from the shop. I also tried to format it in Ubuntu, but it gave me an error and failed. So I formatted it in Windows, with FAT32, which worked fine, so that's how the drive is set up at present.

Does anyone have any idea what is going on?

Many thanks for any suggestions... :)

---

### Post by The Real Dave on 2010-04-21
Are you unmounting the drive before you pull it out? :) Right click, click unmount in regular Gnome, may be different in UNR :)

---

### Post by TomD22 on 2010-04-21
Yep, I am. And the corruption is visible immediately after copying, even without removing and re-inserting the drive.

Another detail I forgot to add: sometimes when I copy folders with files or other folders in them, the progress dialogues show their contents being copied but the folders show up as empty on the drive afterwards...

---

### Post by quadproc on 2010-04-21
> **TomD22 said:**
> 
When I save files on it from Ubuntu, or copy files onto it, they get sporadically corrupted. Jpeg images get peppered with artefacts or sometimes can't be opened at all; .doc or .odt files the character encoding gets messed up and the text can't be read, etc. Oddly, PDF documents are not affected.
...
Conversely, the drive works perfectly from a Windows machine. No files get corrupted, and they can be opened fine from both Windows and Ubuntu.

Are you doing the tests on two different computers?  If so, there may be a hardware issue between the memory stick and the Ubuntu computer.

A different brand or size of the memory stick might work OK.  I would suggest borrowing a different kind of memory and seeing if they work; then you could buy that type.

One other thought: you could use gparted to clean out and reformat the memory stick.  That *might* eradicate the problem.

Good luck!

quadproc

---

### Post by TomD22 on 2010-04-21
Thanks for the ideas.

Yes, I'm doing the windows testing on a separate computer. 

The only other memory stick I have access to I have tested, and it works fine with this Ubuntu machine.

I already tried to use gparted on mine. Trying to partition or format the memory stick using gparted just generates an error message saying it can't be completed because of an I/O error.

I'm a bit constrained by situation resources (I'm posting this from rural Kenya) so unfortunately just buying a different memory stick isn't an option. I'm really hoping I can get this one to work...

---

### Post by quadproc on 2010-04-21
> **TomD22 said:**
> Thanks for the ideas.
...
I'm a bit constrained by situation resources (I'm posting this from rural Kenya) so unfortunately just buying a different memory stick isn't an option. I'm really hoping I can get this one to work...
Ah, I understand.

Here are a few other thoughts.

You might be experiencing a problem with digital signal timing or levels.  In most cases, semiconductor devices work better when they are cold (but not wet!) so you might try putting the USB memory in the refrigerator for a while, then quickly trying it in the machine.  If this succeeds then you will know that some characteristic of the memory is marginal.

If you have access to some inert liquid refrigerant such as one of the Freons then you could induce cooling that way.

The power supply voltage in the unhappy hardware might be off.  If you have access to a voltmeter then you could try measuring the voltages on the mother board; please be careful - a lot of damage can happen if your probe slips and connects two points!  The nominal USB supply voltage is 5.0 volts and it should be very close to that.

Some USB ports are remote from the mother board and are connected by means of a cable.  This connection degrades the signal somewhat.  Using a USB connector that is on the mother board might gain a little margin.

If the failing system/memory is using overclocking then try setting the clock rates to normal.

Some BIOSes allow the user to enable or disable the USB 2.0 speed.  You could try disabling this.  Of course, that may make things so slow that it isn't worth using.

Good luck!

quadproc

---

### Post by TomD22 on 2010-04-22
Thanks again. I'm using a netbook though (hence the netbook-remix version of ubuntu specified) so getting at the motherboard is not an option. Besides which I have no voltmeter. Or fridge to try cooling the mem stick. And this netbook (Acer Aspire One)'s BIOS is astonishingly simple (honestly, the *only* three options the user can edit are system time, security password, and boot device order) so I can't check let along change the USB settings, unfortunately.

As I say, I'm in a rural bit of Kenya - so what I have here in sum total to work with is one Ubuntu netbook, one windows laptop, and two memory sticks. Not ideal for troubleshooting I know!

---

### Post by aseemrane on 2010-05-31
I am facing exact same problem. I am using Kubuntu 10.04 though. Rest all details mentioned by TomD22 apply to me as well. I am absolutely clueless :(

---

