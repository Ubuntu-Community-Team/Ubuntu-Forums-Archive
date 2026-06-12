---
title: "Can't run Ubuntu from the CD"
date: 2011-07-20
forum: General Help
---

### Post by Acoustics4me on 2011-07-20
Hey there. This is my first time using Ubuntu. I've always used generic windows OSs. Also, I am not open source literate, so please go easy on me...lol.

Yesterday, I downloaded the Ubuntu.iso file (v11.04) and then burned it to a CD. Today, I attempted to boot Ubuntu from the CD with no joy. I booted on my other PC (a Compaq Presario). 

This was what happened. First, I made sure that my BIOS was set to boot from my DVD drive first. Then I inserted the CD and restarted my pc. I saw the MS screen that is the first screen I get when booting up in Vista, and then there was a blank screen - just black. I waited for a while as I thought perhaps it needed some time, but nothing happened. So, I removed the disc and the system booted up to Vista. 

As I said, it worked fine on my other pc. The pc that it didn't work on is an NEC Powermate V6250, which uses an Intel chip and has a GeForce 8500GT card installed. I really would love to try this new OS, so if there's anything you can do to help me get it going, then awesome!

Thanks,

Michaela

---

### Post by Niocora on 2011-07-20
On the BIOS load there should be an entry like: Press FSomething to enter boot menu. Press the key and boot from the Optical drive, just to make sure it is trying to boot from that and not the HDD. If it still doesn't work, try re-burning the disc. If that still doesn't work, well... I don't know.

---

### Post by coffeecat on 2011-07-20
Hi, and welcome to the forum.

First a couple of questions.

> **Acoustics4me said:**
> Today, I attempted to boot Ubuntu from the CD with no joy. I booted on my other PC (a Compaq Presario). 

Just to be clear, do you mean that it booted OK on the Compaq? Were you able to boot up to the live Ubuntu desktop?

> **Acoustics4me said:**
> I saw the MS screen that is the first screen I get when booting up in Vista, and then there was a blank screen - just black.

Are you sure what you refer to as the "MS screen" isn't the BIOS splash? If you get the first part of the Vista boot sequence, then the BIOS has bypassed the CD, and you need to check your BIOS settings again. If it is booting from the CD but failing and leaving you with a blank screen, then it sounds as though you will need to try some boot options to work around some possible incompatibility in your computer's ACPI.

Try this:

Start booting from the CD and when you see the two small icons of a stick figure and keyboard at the bottom of the screen tap the spacebar. Select your language and then when you see the text menu, press F6 to add boot options. Try "acpi=off", "noapic" or "nomodeset" either singly or in combination. You can select them by highlighting your choice and pressing the spacebar - you'll see a cross marked by your choice. Press Esc to close the F6 menu and the try booting up from the first choice in the main menu.

---

### Post by Acoustics4me on 2011-07-20
Hi CoffeeCat. Yes, that was supposed to read "It booted on my other PC" (the Compaq). So I know the burn is good.

No, it's not the BIOS screen. The MS screen that I'm talking about has the word Microsoft, and below it is what looks like a progress bar with the green progress squares in it. So you're saying I shouldn't see any of the MS screens, right? I was actually wondering at the time whether I shouldn't be seeing that.

So, your recommendation is easy to reverse if it doesn't work? I'll just read up about that a little before I try it, just to understand what it is I'm doing. No offense. I just like to do things without being blind. I'll let you know how it goes after I try it. It's my night over here in NZ so probably won't try it until tomorrow.

Thanks, CoffeeCat.

---

### Post by fahadintern on 2011-07-20
Hey there All.
 This is my first time using Ubuntu. 
 Dears , 
me want to  get a translator for translation of urdu language to englsih & Engliah ti urdu ,
How can i get these software or Translator from net ?
Plz tell me thanks.

---

### Post by Acoustics4me on 2011-07-20
> **fahadintern said:**
> Hey there All.
 This is my first time using Ubuntu. 
 Dears , 
me want to  get a translator for translation of urdu language to englsih & Engliah ti urdu ,
How can i get these software or Translator from net ?
Plz tell me thanks.

Hey'a. You need to start your own thread for that, and not use mine. Good luck.

---

### Post by mastablasta on 2011-07-20
> **Acoustics4me said:**
> So, your recommendation is easy to reverse if it doesn't work? I'll just read up about that a little before I try it, just to understand what it is I'm doing. No offense. I just like to do things without being blind. .
 
 
that's the correct approach!!!
 
Otherwise these are just boot settings parameters on how system loads. but sure read about it and learn. it's a good way to familiarize with the system:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
 
 
yes there shouldn't be any MS screen. if it is, then CD got bypassed. What you could do is try to boot from USB key (use some simple programme like uNetbootin or this one: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)). my computer also ignores boot on USB key but works on CD (so it's the other way arround as in your case). 
 
another option is that bootCD has some small error on it. it could be unnafected on another computer as it maybe doesn't call for that particular parameter that is damaged on the CD.
 
you could also give 10.04.2 a try. it's a bit older version (from last year) but possibly a bit more polished by now.

---

### Post by coffeecat on 2011-07-20
> **Acoustics4me said:**
> No, it's not the BIOS screen. The MS screen that I'm talking about has the word Microsoft, and below it is what looks like a progress bar with the green progress squares in it. So you're saying I shouldn't see any of the MS screens, right? I was actually wondering at the time whether I shouldn't be seeing that.

That's interesting. If it's not the BIOS screen and you get a screen with the word Microsoft on it then that must mean the CD isn't booting on that machine. If the CD boots OK, you see your BIOS/POST screen first, then the CD's purple screen with the two little icons at the bottom. If you tap any key at that point, you get the text menu as I described before. If you don't tap any key, you get the word ubuntu with the pulsing dots against a purple background as it boots up.

> **Acoustics4me said:**
> So, your recommendation is easy to reverse if it doesn't work? I'll just read up about that a little before I try it, just to understand what it is I'm doing. No offense. I just like to do things without being blind. I'll let you know how it goes after I try it. It's my night over here in NZ so probably won't try it until tomorrow.


My suggestion to add the boot options is only valid if the CD was actually booting and then hanging on a black screen, but this sounds as though this is not what is happening. But yes, adding the options is easy to reverse because you are doing this in a live session and the changes are held in volatile RAM and are lost as soon as you power down.

And no offense taken. :) It's good to hear from someone who questions things rather than following advice blindly.

---

### Post by grubbymitts on 2011-07-20
Here's a stab in the dark - maybe your DVD drive is broke and not reading CDs?  I had this problem once.  Read DVDs fine, but wouldn't look at CDs at all.
 
Open up the PC, unplug the Hard Drive so that the only thing bootable is your DVD drive and then try again.  If Ubuntu boots up from the DVD drive, you know it's a BIOS thing.  If it doesn't boot up then it's a DVD drive thing.

---

### Post by Acoustics4me on 2011-07-20
> **mastablasta said:**
> What you could do is try to boot from USB key (use some simple programme like uNetbootin or this one: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)). my computer also ignores boot on USB key but works on CD (so it's the other way arround as in your case). 
 
you could also give 10.04.2 a try. it's a bit older version (from last year) but possibly a bit more polished by now.

Hey'a Mastablasta. Thanks for those tips. I like the above two becaues they are the easiest...lol, and they are what I understand. If I wanted to boot Ubuntu from a USB key, I'm thinking I'll need a different file type than iso. Could you possibly point me to the appropriate form of the Ubuntu files for putting on the USB?

CoffeeCat, thanks for the clarification. Yes, I do see the BIOS screen first, as always. It is after that that (yes, a double 'that'...lol, looks awkward..lol) I see the microsoft bit, and then nothing - just black. No sign of Ubuntu booting up at all. What I saw on my other pc (which my daughter uses for home schooling, which is why I'd like it on the pc I use) looked very nice! I really want to get this working. Only thing is that, although I'm happy to try the simple stuff, I'm not as pc savvy as you guys and probably won't understand anything too difficult. But I'll try...lol.

GrubbyMitts, hmmmm, did you put your grubby mitts on those CDs? Maybe that's your problem...lol. Just kidding. I don't think that will my problem as my hard drive has always been able to play, rip and read CDs. But it is fussy as to what media I use (I always use Verbatim as I read good things on that, and my machine likes it). However, if nothing else works, I can always give that a try.

Cheers
Me

---

### Post by Acoustics4me on 2011-07-20
Duh! Never mind, thanks Mastablasta. It's the same page, but I just choose the usb option for downloading. Sorry. Blonde moment...lol.

---

### Post by nothingspecial on 2011-07-20
Same iso

Just download unetbootin from here

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

run it, tell it where your usb stick is, tell it where the iso is.

Make a cup of tea.

Come back, reboot, chose boot from usb, hello ubuntu \\:D/

---

### Post by Acoustics4me on 2011-07-20
> **nothingspecial said:**
> Same iso

Just download unetbootin from here

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

run it, tell it where your usb stick is, tell it where the iso is.

Make a cup of tea.

Come back, reboot, chose boot from usb, hello ubuntu \\:D/

Ahh, got it. Thanks. Umm, your signature makes me a little nervous about trying Linux!...lol.  Of to download unetbootin.

Me

---

### Post by nothingspecial on 2011-07-20
> **Acoustics4me said:**
> Ahh, got it. Thanks. Umm, your signature makes me a little nervous about trying Linux!...lol.  Of to download unetbootin.

Me


Ubuntu on the other hand, assumes you don't ;)

When you get the hang of it, it's possible you may want to try some stuff out. You search google and some idiot has put something on a web page

```
for f in $(blah -t -y); do more --gobbldy-gook "${f##blah/nonsense}"; done
```

And you have no idea what it means, but you copy and paste it into your computer......

.....and your computer blows up :shock:

because linux assumed you knew exactly what you were doing.

That's what it was refering to, don't worry :P

---

### Post by Acoustics4me on 2011-07-20
> **nothingspecial said:**
> Ubuntu on the other hand, assumes you don't ;)

  :P

Ahhh, thank you!

Ok, downloaded and installed UNetbootin. It successfully located the iso file and did its thing with my usb drive (which is FAT32, by the way), and rebooted when it had finished. I went into the BIOS and made sure 'Removable Devices' was listed first in boot order, followed by CD-DVD Drive, and then HDD. No joy, I'm afraid. PC booted, showing BIOS screen first, then came a black screen with a flashing white cursor. At least this time it didn't show anything from the MS system, but still no success with booting Ubuntu. Perhaps I will try that previous version that MastaBlasta suggested. Or maybe the whole problem lies with my pc not being able to successfully boot from anything other than the HDD? What do you guys think?

---

### Post by nothingspecial on 2011-07-20
Do you know how much ram the pc has?

---

### Post by Acoustics4me on 2011-07-20
> **nothingspecial said:**
> Do you know how much ram the pc has?

4 gigs.

---

### Post by Acoustics4me on 2011-07-20
NothingSpecial, gotta get myself to bed now. It's half past midnight here, but I will pop on here tomorrow and check the posts. Also, will try an earlier version of Ubuntu, tomorrow.

Thanks for your help so far, everyone. See you tomorrow.

Cheers,

Michaela

---

### Post by mastablasta on 2011-07-20
> **Acoustics4me said:**
> Ahhh, thank you!
 
Ok, downloaded and installed UNetbootin. It successfully located the iso file and did its thing with my usb drive (which is FAT32, by the way), and rebooted when it had finished. I went into the BIOS and made sure 'Removable Devices' was listed first in boot order, followed by CD-DVD Drive, and then HDD. No joy, I'm afraid. PC booted, showing BIOS screen first, then came a black screen with a flashing white cursor. At least this time it didn't show anything from the MS system, but still no success with booting Ubuntu. Perhaps I will try that previous version that MastaBlasta suggested. Or maybe the whole problem lies with my pc not being able to successfully boot from anything other than the HDD? What do you guys think?
 
no, using linuxliveUSB does the same as unetbootin. just the interface is maybe more user friendly. both programmes are good.
 
it would be good to do a md5 checksum especially if you didn't downoad via torrent:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
blinking cursor is unnusual. it could mean various things. but usually this comes up later as an issue.
 
also with 4 Gb ram and (and i suspect it is) 64 bit processor you could use 64 bit version. thoguh 32 bit should work as well (at least live to test it out). only 32bit linux can only address up to 3GB ram unless if you use PAE kernel (which is usually loaded on install).

---

### Post by alphaamanitin on 2011-07-20
I would suggest you manually select what drive to boot from.  Also, do as mastablasta says and check the .isos with a md5 hash.  Maybe you just have corrupted isos.  I would try using the 10.04 LTS version in 32bit architecture.  I would try both USB and CD versions and always manually select what drive to boot from.  

AlphaA

---

### Post by Acoustics4me on 2011-07-20
> **mastablasta said:**
> it would be good to do a md5 checksum especially if you didn't downoad via torrent:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
blinking cursor is unnusual. it could mean various things. but usually this comes up later as an issue.
 
also with 4 Gb ram and (and i suspect it is) 64 bit processor you could use 64 bit version. thoguh 32 bit should work as well (at least live to test it out). only 32bit linux can only address up to 3GB ram unless if you use PAE kernel (which is usually loaded on install).

Hey'a, MastaBlasta. I'll do that Checksum. The blinking cursor is familiar to me, actually. Normally I see that if I have left an SD card plugged in, or a usb drive plugged in and it stops the pc from completing a bootup. In that circumstance, I simply remove the offending object, press ctrl + alt + delete and the pc restarts and boots up normally.

My system is 32 bit, actually, as is my other Compaq machine.

---

### Post by nothingspecial on 2011-07-20
Good morning :P

(late at night here)



Can you select what to boot from at boot (if you see what I mean). Rather than changing boot order, bring up a boot menu.

---

### Post by Acoustics4me on 2011-07-20
> **nothingspecial said:**
> Good morning :P

(late at night here)



Can you select what to boot from at boot (if you see what I mean). Rather than changing boot order, bring up a boot menu.

Ooh, yes, I think I saw an option like that when I was altering the boot order. Ok, so I'll take a look at that. I was going to do a checksum, but i have no idea what a 'terminal' is, and it all looks a bit technical! Be back soon. Don't go to sleep yet!...lol.

---

### Post by nothingspecial on 2011-07-20
> **Acoustics4me said:**
> Ooh, yes, I think I saw an option like that when I was altering the boot order. Ok, so I'll take a look at that. I was going to do a checksum, but i have no idea what a 'terminal' is, and it all looks a bit technical! Be back soon. Don't go to sleep yet!...lol.

Who mentioned a terminal? Or have you been googling? 

I really have to go to bed in a minute. If all else fails, try downloading the iso again. But there's plenty of help. This forum is 24 hours.

---

### Post by Acoustics4me on 2011-07-20
Ok, so what I discovered in the boot order was very interesting. It didn't even list my usb drives as an option to boot from, but it did list my memory card drives, as below:

1st      [USB: Generic - Compaq]
2nd     [USB: Generic - SM/xD]
3rd     [USB: Generic - SD/MM]
4th     [USB: Generic - MS/MS]

So, I made the SD/MM option the first device to boot from as I have my camera's SD card for that slot. I am currently using UNetbootin to create a live bootable disc of Ubuntu 11.04 on my SD card, so I'm excited to see what happens on next reboot. Will get back to you.

Me

---

### Post by Acoustics4me on 2011-07-20
> **nothingspecial said:**
> Who mentioned a terminal? Or have you been googling? 


One of the posts mentioned doing a checksum and gave me a link to an Ubuntu 'how to' page for that. Then, as I was reading it, the instructions mentioned that I had to use the terminal. At that point, my eyes glazed over a little. For me, it'll be one of those possible options if nothing else works.

---

### Post by Acoustics4me on 2011-07-20
SUCCESS!!  Ok, NothingSpecial, you can sleep easy....lol. I am typing this post from within the Ubuntu environment. Yipee! I used my SD card, as I mentioned in my previous post, and created a bootable Ubuntu on there using UNetbootin. I'm so glad. 

Thank you to everyone for your helpful suggestions. I guess the whole problem lay with my machine not being able to boot from different locations, apparently!

Just a thought, because vista isn't running, my anti-virus won't be running. Do I have to worry about that when I'm working from the Ubuntu disc? Thanks.

Michaela

---

### Post by nothingspecial on 2011-07-20
You can't open a terminal if you can't boot ubuntu.

A terminal is one of those things that makes linux seem difficult. The whole point of ubuntu is that you should never have to open one.

But you can if you like :)

Don't worry about terminals for now (or ever if you don't want).

---

### Post by nothingspecial on 2011-07-20
> **Acoustics4me said:**
> SUCCESS!!  Ok, NothingSpecial, you can sleep easy....lol. I am typing this post from within the Ubuntu environment. Yipee! I used my SD card, as I mentioned in my previous post, and created a bootable Ubuntu on there using UNetbootin. I'm so glad. 

Thank you to everyone for your helpful suggestions. I guess the whole problem lay with my machine not being able to boot from different locations, apparently!

Just a thought, because vista isn't running, my anti-virus won't be running. Do I have to worry about that when I'm working from the Ubuntu disc? Thanks.

Michaela


:guitar::guitar::guitar:

Great news Michaela!!

You do not have to worry about viruses, with Ubuntu.

Ok, I'm off to bed.

Leave this thread. It's solved. You can mark it solved using the thread tools button.

Any other questions. Make a new thread.

Enjoy it.

Night.

---

### Post by westie457 on 2011-07-20
> Just a thought, because vista isn't running, my anti-virus won't be running. Do I have to worry about that when I'm working from the Ubuntu disc? Thanks.

Hi there is no need to worry about virii? or other malware with a 'nix os.
This is because of the built in security that requires your password everytime you want to install anything or change system settings. No password nothing happens.

To explain in more detail with some general assumptions - hopefully easy to understand. Compared to Windows which is a closed-source operating system and has a limited number of eyes looking at it and Ubuntu or any other open-source operating system which has many more eyes looking.

Any virus is os/kernel specific and relies on the fact that the main kernel does not change very often. Examples are obviously Windows, kernel updates happen 2 or 3 times a year and are not completely rewritten until a completely new release EG XP to Vista to 7. With Linux/Ubuntu/Unix the kernels are renewed on average about every six weeks. This is too quick for a virus to spread itself around and it is halted.

In the last 10 years there has been around 30 viruses and none of them are active. Windows on the other hand has 100's maybe 1000's everyday. Take a look [here]("https://help.ubuntu.com/community/Linuxvirus").

Catching something nasty is possible but unlikely. Just be careful what you click on. If you are not sure then just cancel the install.

---

### Post by Acoustics4me on 2011-07-20
> **westie457 said:**
> Hi there is no need to worry about virii? or other malware with a 'nix os.
This is because of the built in security that requires your password everytime you want to install anything or change system settings. No password nothing happens.

To explain in more detail with some general assumptions - hopefully easy to understand. Compared to Windows which is a closed-source operating system and has a limited number of eyes looking at it and Ubuntu or any other open-source operating system which has many more eyes looking.

Any virus is os/kernel specific and relies on the fact that the main kernel does not change very often. Examples are obviously Windows, kernel updates happen 2 or 3 times a year and are not completely rewritten until a completely new release EG XP to Vista to 7. With Linux/Ubuntu/Unix the kernels are renewed on average about every six weeks. This is too quick for a virus to spread itself around and it is halted.

In the last 10 years there has been around 30 viruses and none of them are active. Windows on the other hand has 100's maybe 1000's everyday. Take a look [here]("https://help.ubuntu.com/community/Linuxvirus").

Catching something nasty is possible but unlikely. Just be careful what you click on. If you are not sure then just cancel the install.

Thanks for that, Westie.

Thanks, NS. I will close this thread as 'solved' now. Cheers. Sleep well.

---

