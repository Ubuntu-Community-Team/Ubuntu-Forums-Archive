---
title: "Stupid 11.04 doesn't boot off cd"
date: 2011-05-06
forum: General Help
---

### Post by seseberg on 2011-05-06
I have a Toshiba Satellite A305D-S6848 that has 2 gigs of DDRAM2 and an AMD Turion 64 processor. I burned both 32 bit and 64 bit versions of the very latest Ubuntu 11.04 yesterday, and, the freaking thing won't even boot up off the cd. The reason why I'm not installing is because I don't have a hard drive and I usually just boot Ubuntu Live off a CD and suspend it when I'm away from the computer. All of my data is in an online Microsoft Cloud. (I don't have a Flash drive either, neither can I afford it, so leave me alone about that!) 

If I boot it up and let it do it's job as its supposed to, I get the small keyboard sign and the help sign of a stick figure next to it, and, if I let it be, that purple-ish screen dissapears and a small blinking white underline appears at the top left corner of the screen, as if Windows 95 or 98 would be booting up... however, it stays like that for hours and hours and there is no optical media activity of any kind...

If I hit random keys at the very first seconds of the purple-ish screen (that doesn't have the moving dots as if it were loading, they don't appear on both scenarios), then I get an old Ubuntu 7 like looking menu where I can select memtest, try without installing, install, language, blablabla... Memtest works fine, but, even from here if I select try without installing, I get the same freakin' white underline on the top left corner of my screen... 

Ubuntu 10.04 works perfect with both 32bit and 64 bit, so, there HAS to be something wrong with this newer version, I don't need a MemTest...

Does any of you have any suggestions, or, probably, nobody has ever come across this before. 

I so HATE it when Ubuntu releases CRAPPY newer versions... Ubuntu 10.04 was crappy as well at the begining when it had those stupid SATA controller bugs that would not allow people to even install the dang thing... 

Well, at least Mac OS X is commercial Linux which is why it's doing so well... Unix, Linux, kind of the same thing as the Latins and the Italic Peninsula... Get it? Latin-Italian?

---

### Post by GreatKeyHunter on 2011-05-06
Have you tried the same thing with 10.10 instead of 11.04?

---

### Post by Blasphemist on 2011-05-06
Which version of this unit do you have? ATI graphics or Intel? Post the whole model, example, PSAG0U-00U00K or PSAH0U-00Q009 or PSAG0U-02D00M. And which bios version do you have or have you updated the bios. I see a number of issues on the toshiba website that discuss the bios but it didn't look like an update is available for all versions.

---

### Post by metalf8801 on 2011-05-06
Sorry Blasphemist post basically the same thing while I was doing some googling trying to find some info. I will point out that the Laptop can't being using an Intel graphics card since the laptop has an AMD CPU.

---

### Post by Blasphemist on 2011-05-06
I did get confused and didn't read his post closely enough, good catch. The models I found didn't include one with the Turion so the best I could do until we hear back from OP is guess about the gpu. It does likely have ATI and plenty of memory for natty. I'm thinking it must be a driver issue having to do with running on the cd. It seems like I've seen something about that and will do some more looking.

---

### Post by Blasphemist on 2011-05-06
OP, please try this. Go into bios and see if there is an option for switchable graphics vs. discrete graphics. If so, choose discrete, save and exit bios, restart. This entry in launchpad seems to be people having the same issue and this seems to have been the solution. I don't think they had the same exact hardware as yours though as theirs was switching to intel graphics. That doesn't mean you aren't having much the same issue.

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/155512](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/155512)

---

### Post by seseberg on 2011-05-07
> **GreatKeyHunter said:**
> Have you tried the same thing with 10.10 instead of 11.04?

Sorry guys, I meant to say 10.10 instead of 10.04. I have the 64 bit version of 10.10 right here before me and it works perfectly. I actually never used 10.04, sorry about that confusion.

---

### Post by seseberg on 2011-05-07
Hey everyone, here's some more info about the whole thing.

AMD Turion TL-60 64 x2 Mobile Technology Processor @ 2.00 Ghz.

2048 MB of DDR2 

1.90 BIOS version, the very latest for this model off of support.toshiba.com 

I have absolutely 0 possibility of changing anything about the video memory of the thing, as far as I can remember it's an embedded ATI Radeon something that has it's own memory...

The exact model is this one: PASH0U-00Q009

Screw Natty.......

I got so annoyed at freakin' annoyed at the 10. version whatever it was that had the SATA stupid kernel bug I couldn't believe something fresh off the press didn't even freakin' start...

And now this................

I feel like I'm never going to use Ubuntu again...

I'll try out OpenSuse today actually...

(P.S. I LOVE Windows 7 64 bit, I have a license and DVD for it, I just don't have a HDD to run it from which is why I'm stuck with Linux Distros... I'll probably compile a PE Environment and run Win7 off of a CD and be done with all of this fiasco...
At least Windows boots and starts up...)

---

### Post by seseberg on 2011-05-07
Oh, BTW, the 2 Natty versions of 32 and 64 bit don't start on an IBM ThinkPad R50e either, which is confusing because this thing is such an old model... It does have 512 mb of whatever RAM technology it has, so it's not a RAM user, and it also has an Intel Pentium M 1.80 Ghz processor.

---

### Post by Blasphemist on 2011-05-07
I think there is a good chance that the pc could work if you'd try something but so be it. You have the exact minimum amount of video memory needed for natty. I can't see that you've tried anything in bios. If your IBM has a total of 512MB memory, you'll either want to add memory or use a distribution with little graphics requirements on that as well.

If you want to try other distributions, I recommend trying the least demanding for video requirements on both systems. Xubuntu would be worth a try.

---

### Post by seseberg on 2011-05-08
> **Blasphemist said:**
> I think there is a good chance that the pc could work if you'd try something but so be it. You have the exact minimum amount of video memory needed for natty. I can't see that you've tried anything in bios. If your IBM has a total of 512MB memory, you'll either want to add memory or use a distribution with little graphics requirements on that as well.

If you want to try other distributions, I recommend trying the least demanding for video requirements on both systems. Xubuntu would be worth a try.

What else is there for me to try? Why doesn't it work on my Toshiba???? That thing has way more than whatever Natty would need...

Stupid kernel! I bet I'll have to wait for freakin' 11.10 or 11.11 whatever it will be until this will be fixed, I HATE compiling my own OS with freakin' patches... 

Sheesh, at least Windows WORKED even though it always needed high maintenance which I obviously understood given the nature of being able to screw everything if the user doesn't know what they're doing. I'd rather have that over the second unbootable Ubuntu OS I've come by so far......

Snap

---

### Post by coldraven on 2011-05-08
I know you said don't bother but if I were you I would buy a 1GB SD card for £1 or a 2GB card for £2, that is really not expensive!
You can get a USB SD card adaptor for 99p if you don't have a card reader.
Then use the startup disk creator in 10.04 or 10.10 to make a bootable flash drive.
It will run faster, quieter and with no chance of scratching your CD and as a bonus you will have the option of saving any files that you download.
With a 1GB card you can have about 240Mb of spare space.

---

### Post by seseberg on 2011-05-08
> **coldraven said:**
> I know you said don't bother but if I were you I would buy a 1GB SD card for £1 or a 2GB card for £2, that is really not expensive!
You can get a USB SD card adaptor for 99p if you don't have a card reader.
Then use the startup disk creator in 10.04 or 10.10 to make a bootable flash drive.
It will run faster, quieter and with no chance of scratching your CD and as a bonus you will have the option of saving any files that you download.
With a 1GB card you can have about 240Mb of spare space.

This is not the point of this thread, as many ubuntu users try to divert it when they can't fix basic idiotic ubuntu issues like the freakin' OS booting up...

Please stick to the question and subject of this thread that is WHY stupid Natty doesn't boot up in either 32 and 64 bit versions on a perfectly good laptop.

I'm a volunteer for a charity organization in the UK and they take care of food/housing/utilities/internet for me and I don't even have a penny...

You might think that a pound or two is easy dough for anyone, but when you really don't have a pound or even 10 more pennies to buy something, then you really see and experience how tough life is.............

---

### Post by coldraven on 2011-05-09
Sorry to hear that you are skint :(
I did not have a problem with 11.04 64bit, my only guess is that either your CD has a defect or that you might need to clean the CD lens.
I had three brand new DVDs and only one would work.
I cleaned the lens and two would work.
I had to clean it again before all three would work.
I smoke and I think that the nicotine had made a film on what looked like a perfectly clean lens.
To clean it I used a cotton bud and some methylated spirit but a small wad of tissue and a bit of spit would do as well. Very gently stroke the lens, **do not put any pressure on it**. The lens is mounted on **very** soft springs and you do not want to make it go out of alignment.

You obviously have some talent at computers so I wish you well and hope that you make a living from your skills.
A friend of mine in London is always finding laptops in the re-cycling yard, maybe you could salvage a couple and sell them on with Linux running sweetly :)
Email me your address and I'll send you a USB stick. Good luck!

---

### Post by seseberg on 2011-05-11
> **coldraven said:**
> Sorry to hear that you are skint :(
I did not have a problem with 11.04 64bit, my only guess is that either your CD has a defect or that you might need to clean the CD lens.
I had three brand new DVDs and only one would work.
I cleaned the lens and two would work.
I had to clean it again before all three would work.
I smoke and I think that the nicotine had made a film on what looked like a perfectly clean lens.
To clean it I used a cotton bud and some methylated spirit but a small wad of tissue and a bit of spit would do as well. Very gently stroke the lens, **do not put any pressure on it**. The lens is mounted on **very** soft springs and you do not want to make it go out of alignment.

You obviously have some talent at computers so I wish you well and hope that you make a living from your skills.
A friend of mine in London is always finding laptops in the re-cycling yard, maybe you could salvage a couple and sell them on with Linux running sweetly :)
Email me your address and I'll send you a USB stick. Good luck!

Hi Coldraven!!! You are extremely generous, that's for sure!!!

In regards to cleaning the lens, I know that is not the problem with my laptop because other Linux distros boot up, and even Windows Preinstalled Environment boot up just fine, I've actually never had problems booting anything up from my laptop's optical drive, I'm writing to you from a Ubuntu 10.10 64 bit distro right now.

You might have read earlier on this thread that if I hit random keys right after BIOS post dissapears and the laptop keeps on booting, I get to the old Ubuntu OS Choice Menu where I can select my language and stuff like that, you know, the old school Ubuntu one. However, no matter what I choose from there (I am even able to run MemTest), this kernel of Linux just refuses to start and just sits there with a blinking Windows 98-like white underline.

Since I am able to boot some stuff off the CD like get to the menu and choose Memtest from there and run it just fine, it's clear that I am not having an issue with my optical drive lens, or an issue with the CD I am booting from. It was a brand new CD anyways.

The issue clearly lies with whatever kernel version 11.04 32/64 bit had when I downloaded both distros and burned them on a CD. 

Who knows, they might have updated them already, or a newer kernel might already be out, but God do I have compiling Ubuntu with patches just because of a stupid bug... What am I, an Operating System developer? I just want the thing to work since they're bragging so much about all of that open-mojo, but their freakin' OS doesn't even start... (same thing happened with 10.04 if I recall right, when the Kernel had a huge SATA issue...)

I thank you so much for the offer of sending me a USB stick, but I unfortunately discovered yesterday that I have a lump on my neck close to my right ear, and I will be going back to my country to have it checked out.

I live in Harpenden, so, I wasn't that far from London, but I'm really concerned about my lump...

Thanks man!!!

(P.S. I was so eager to try out the new Unity shell...)

---

### Post by coldraven on 2011-05-11
Strange, I installed 11.04 beta 1 and 11.04 final version without any problems on my Compaq [6715b laptop]("http://www.itreviews.co.uk/hardware/h1491.htm"). It must be a Toshiba thing :)
I hope that you enjoy your trip home and that your lump is of no concern. Over the years I've had a few bits chopped out of me but I'm still good to party :)
Bon voyage!

---

### Post by 3rdalbum on 2011-05-11
When you get to the old-style booting menu that you describe, have you tried using any of the special boot options? That menu tells you about some keys you can press to get special boot options, which might be enough for your computer.

I believe there's some for "acpi=off" and "noapic" and "nolapic"; if you turn those on, the CD might boot. Occasionally these sorts of things might be needed.

And before you say that "Windows always just works", I'll just remind you that Windows XP's installation CD will crash if you don't have any IDE devices.

---

### Post by Lars Noodén on 2011-05-11
> **GreatKeyHunter said:**
> Have you tried the same thing with 10.10 instead of 11.04?

When I had that same problem, I got the 10.10 alternate CD and then installed "Comandline" system, did an upgrade to natty and then added ubuntu-desktop.  It was a convoluted way to get the distro, but it was the only way that worked.  None of the natty CDs would boot.  The hardware is an older intel Mac Mini.

---

### Post by seseberg on 2011-05-12
@3rdalbum In regards to Windows XP, it depends what service pack you are talking about, I've never experienced that before and I'm an avid Windows user (when I have a HDD to install it on... I own multiple NT OS Licenses...)
The command line thingy won't help, because this is an AMD Motherboard kernel incompatibility that also happened to me with 10.04... No shell commands would help at all... It's not a Toshiba thing, it IS a Canonical thing because they're outrageous claims of "supporting all hardware" are false. If you just have a look on the Launchpad website, you'll see what I mean...

@Laars Nooden I would love to do that, but I do not have any storage at all except for an old LG Shine phone that has a 2 GB MicroSD card in it, but even though I've tried using the card as a startup disk, nothing would boot off of it because of the phone's driver... If I only had a MicroSD adapter for my card..... Snap...

You have to agree with me here guys, unfortunately a lot of times newer Ubuntu releases are characterised by immaturity...  I don't care about the freakin' Unity GUI as long as the OS doesn't boot up and support my AMD motherboard and our here friend's Mac..... 

I just hate all of this, I'm going for OpenSUSE and I'll never come back to Ubuntu again, it stinks anyways...

I just found out that Natty actually went for the Global Menu bar implementation which I CAN'T STAND!!!! It's is SOOOO unproductive on any screen bigger than 15 inches.... You loose A LOT of time dragging your mouse across the screen to the very top of the menu bar, not to mention the problems Unity is having with programs that have multiple windows.... 

I always hated this on a Mac, ALWAYS!!!!!!!! Now Ubuntu as well?????? Screw Unix man, screw Unix..... 

The other thing I hate about the Mac commercial Unix/Linux OS is that you can't move the freakin' app dock... Why, WHY??? For such a highly complicated and sophisticated OS, it should have been able to do this ages ago.....................

If I'm not wrong, even Windows 3.1 had this feature, and Windows 95.................................

You have to hand it over to Microsoft when it comes to GUI usability and productivity... Who wants to memorise kilo-metric commands???????? Where in the 21th century people, command lines are like the 60's..............

I wish I had a HDD and could use my Windows 7 Home Premium 64-bit OS... It was so, SOOO much better before my HDD crashed............ (got hit by someone's angry hand, I won't tell you who....OK, it was me, but it was my girlfriends' fault!!! I swear!!!)

---

### Post by seseberg on 2011-05-12
I actually found out my lump is a huge chicken pox red dot pack... great... I'm turning 21 and I have chicken pox... I wish I went to a pox party when I was 5....

---

### Post by dnguyen1963 on 2011-05-12
> **Blasphemist said:**
> I think there is a good chance that the pc could work if you'd try something but so be it. You have the exact minimum amount of video memory needed for natty. I can't see that you've tried anything in bios. If your IBM has a total of 512MB memory, you'll either want to add memory or use a distribution with little graphics requirements on that as well.

If you want to try other distributions, I recommend trying the least demanding for video requirements on both systems. Xubuntu would be worth a try.

He did say that his system has 2 GB of DRAM, which should be enough to run Natty.  I agree that Xubuntu should be looked at.  It has a lot less hardware requirements..

---

