---
title: "Why no one fix these problem?"
date: 2011-09-18
forum: General Help
---

### Post by mayagamer on 2011-09-18
I have tried Linux many many times since I first knew it like 10 years ago. And from the first time I tried it, my screen snows every time I boot it and shut it down. I have had more than 5 computers in the 10 years, and tried more than 10 different brand and different version of Linux
I don't know why no one fix this problem?
I am not a geek or programmer, I don't know how difficult it is. But if windows or macOS can do it, why can't linux?
Whoever want to try linux see this creepy screen will think linux must be a poor quality OS.

another problem is the black background and white text screen always appears in booting and shutting down stage. also poor quality feeling.

Do I need to post some screenshots&#65311;

---

### Post by ubudog on 2011-09-18
Um... can you get into your desktop and use Ubuntu?

What are your specs?

And yes, some screenshots would be nice.

---

### Post by Frogs Hair on 2011-09-18
I don't know what is meant "snows"  so , I  don't think have experienced this problem on any release I have used .

---

### Post by mayagamer on 2011-09-18
I can get in to desktop and use Ubuntu. It works well. The snowing screen flashes like only 3s. But still make me and every my friend feel it not stable. actually it is stable&#12290;
I will upload some screenshots later today. Because I just delete the Alpha version of fedora 16. I also tried Ubuntu 11.10 Beta recently . As it used to be in 10 years...

---

### Post by pharcycle on 2011-09-18
Why are you trying alpha and beta releases if you're having issues with stability? What graphics card are you using, have you disabled all the graphics gimmicks like bouncy windows, compiz fusion etc? there is even one that makes snow fall over your desktop

Post the system specs which it happens on
If you don't have a dedicated graphics card, i'd recommend trying one (unless of course it's a laptop) as you can get pretty good ones cheaply now- nvidia 7300 for about 20 bucks on eBay

If you don't file bug reports, how can anyone know there's a problem?

---

### Post by mayagamer on 2011-09-18
I just installed 11.04, guess what, it works great! the problem disappeared. Thank you!
But I didn't say it was unstable. It is stable, Truly. 

And there is another bug you guys can check it out by click this link
[http://wiki.oseems.com/operatingsystem/ubuntu/fix-no-sound-headphone-jack-dell-xps-studio-16](http://wiki.oseems.com/operatingsystem/ubuntu/fix-no-sound-headphone-jack-dell-xps-studio-16)

my laptop is dell xps studio. the problem is still since 10.04 although we can fix it as the link below, but it is not a good experience.
just hope it will be fixed in 11.10

---

### Post by WorMzy on 2011-09-18
I would still like to see a screenshot of this "snow". If it has affected you for 10 years over five different machines, and several different Linux distributions, I think it definitely needs to be brought to the attention of the powers that be. Unfortunately, without further information, it's difficult to say whether this is a *getty bug, or a kernel bug.

---

### Post by mayagamer on 2011-09-18
Ok, I'd like to show you. Which version or release do you prefer?the beta or alpha or a stable one? ubuntu or fedora?

---

### Post by WorMzy on 2011-09-18
One or two screenshots showing the problem would suffice. But if you could provide a list of as much of the hardware you've used on the affected machines that you can recall, and a list of affected distribution releases, that would be useful.

As it stands, all I know is that "a bug affects some hardware on some machines", and that's about as vague as it can get.

---

### Post by mayagamer on 2011-09-18
u r right.
I can only provide the one I am using. cos I forgot others.

Dell Studio XPS 1647
Intel i5-430M (2.26GHz, 3MB L2 Cache) Turbo Boost to 2.53 GHz, 15.6" HD Widescreen LED (1600 x 900), 4 GB DDR3 1066 MHz, 500 GB SATA 7200 RPM, 1 GB ATI Radeon HD 4670 Graphics, 8X DVD+/-RW, WiFi B/G/N, Integrated 1.3-megapixel webcam

and I find that 11.04 sometimes also have that problem when starting up.
check the attachment pic .
it just flash less than 1 second. I shot several times...

ok, it is not like snow....

---

### Post by pqwoerituytrueiwoq on 2011-09-18
is this a live cd/usb
if so try installing via the alternate cd and boot into recovery mode drop to console and install the video driver ```
apt-get install fglrx
```
swap [FONT=Courier New]fglrx[/FONT] for [FONT=Courier New]nvidia-current[/FONT] if you have a nvidia gpu

if you installed via live cd and you get that i would find it very odd that the live cd works and 1st time boot does not

---

### Post by mayagamer on 2011-09-18
This Ubuntu 11.04 is installed in my laptop, I installed it just now to show the problem. Not a live cd or usb. the gpu is 1 GB ATI Radeon HD 4670 Graphics

---

### Post by JD8182 on 2011-09-19
Your not alone


I have also had these exact same things happen when booting, restarting, powering off, etc.., I have just payed little to no attention to it because the stability is incredible. When shutting down or restarting, what happens is the TTY opens and displays the (system) programs shutting down one at a time as it goes down the list, before it actually reboots or shuts down. The "snow" as you referred to it as, I have no clue, but I have noticed this for almost all the Distro's that I have used also, except 11.04. But again I payed very little attention to it because the actual OS runs so well.

---

### Post by mayagamer on 2011-09-19
> **JD8182 said:**
> Your not alone


I have also had these exact same things happen when booting, restarting, powering off, etc.., I have just payed little to no attention to it because the stability is incredible. When shutting down or restarting, what happens is the TTY opens and displays the (system) programs shutting down one at a time as it goes down the list, before it actually reboots or shuts down. The "snow" as you referred to it as, I have no clue, but I have noticed this for almost all the Distro's that I have used also, except 11.04. But again I payed very little attention to it because the actual OS runs so well.

yea, I'm sure I am not alone;)
I find it almost all Distro and all my computers. Even 11.04, check the screenshot in my last replies.

 I can pay little attention to it, however the new users won't. they will feel it is kind of "cheap". Nowadays, every production is doing its best to show a perfect user experience. Like apple is the most successful one. when apple's market share was more or less the same situation as linux, what made it go further? And why ubuntu just stayed in the corner? I think the only reason is user experience. So I think Ubuntu could do more, could be even better.

as well as the ear phone problem I mentioned, the problem happened a long time. There were many users reported the bug, but it still.

---

### Post by mayagamer on 2011-09-19
and this happens on shutting down ubuntu 11.04
see, the dots in the center of the screen.

---

### Post by mayagamer on 2011-09-19
how can I check if someone else have reported the same problem?

---

### Post by Frogs Hair on 2011-09-19
Proprietary drivers can cause splash screen problems (none or text only) .  I use such a driver and this method has solved that problem .[http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/)

I have not had problems with the driver provided during Ubuntu installation , but I use 3D effects and Unity 3D , so I need the dirver .

---

### Post by 3rdalbum on 2011-09-19
A few versions ago, Canonical asked for people to report these cosmetic bugs to Launchpad, because it was concerned about the aesthetics of booting up and making sure everything looked nice.

Now I've got the feeling they don't really care at the moment and that a cosmetic bug during booting (such as the "snow" you've reported) would be marked as "wontfix".

---

### Post by WorMzy on 2011-09-19
I have a feeling that this is caused when radeonfb takes over during the boot process. There certainly seems to be a lot of discussion about it on mailing lists dating back to 2004. Unfortunately, I don't think there's much you can do about that.

---

### Post by gandaran on 2011-09-19
I had similar problems on an older PC, I used to fix them easily by changing grub resolution using startupmanager on ubuntu releases up to I think 10.04 and on newer ones just choosing 24 bits color instead of the default 8 bits would display correctly the splash screen.

---

### Post by mayagamer on 2011-09-19
Fine. Thank you guys!

---

### Post by Monsuco on 2011-09-19
I've seen it too. I use proprietary ATI drives. I guess it's just a quirk with the way ATI made their Linux drivers. It isn't pretty but it doesn't really hurt anything and only last for a little bit.

I'm not sure if the Ubuntu distro could even fix this sort of thing, it sounds kinda like it'd be something the driver manufacturer (ATI for example) would have to figure out but they probably won't bother.

---

