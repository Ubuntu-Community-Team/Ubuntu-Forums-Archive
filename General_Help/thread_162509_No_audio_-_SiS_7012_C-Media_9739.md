---
title: "No audio - SiS 7012 C-Media 9739"
date: 2006-04-19
forum: General Help
---

### Post by Pantera on 2006-04-19
Hello everybody,
i'm a real newbie with Linux OS, i've tried a few distributions and found Ubuntu/Kubuntu to be very user-friendly. I've installed it on a few PCs having no problem, until today.

I'm using an LCD-PC ECS Aio A950, the installation was simple as usual, but the soundcard it's not working.
I've tried to find a solution on the web, i'd read almost everything about sound issues, trying to fix it but with no success ](*,) 

> ubuntu@lcdpc:~$ lspci -v | grep -i audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)


the sound card is detected as SiS 7012 (the chipset is C-Media 9736), the mixer seems to be OK.

The only thing that sounds strange to me is that running alsamixer in console, there is *MASTER* cursor that can be only set on and off (at the moment in set ON anyway), while there is also a *MASTER MONO* cursor fully functional.

Any suggestion?

P.S.: please forgive me for my poor english, i hope i've been clear anyway. ;)

---

### Post by glimp on 2006-04-20
i was haunted with almost the same problem like yours, i am also using C-Media but 9880 , i got sound but only on the headphone not on my speakers, 

i browse the cmedia homepage for support and redirected me to alsa site, what i did is to install those alsa files via synaptic package, but still can't enable my speakers so i tried the alsamixergui and it was a success, just by opening the volume control via applications menu i was able to edit my preferrences and enable the six channel options now i have sound in my headphone and speakers and mic also

hope this can help you..

---

### Post by Pantera on 2006-04-21
Thanks for the hint, at C-Media site i've found a [specific driver]("http://www.cmedia.com/driverdownload/getdriver.php?os=Linux&prod=CMI9739&cat=Onboard+Audio&email=") for CMI 9739, but i'm unable to compile it (i receive lot of errors).
I thought that wasn't a problem, since the chipset was listed as supported by ALSA driver.

2 questions:
did you get the same MASTER and MASTER MONO cursor that i have, listed in alsamixer (as told in the previous post)?
how did you enabled the 6 speakers option? (i can't even see it listed... :-k  )

---

### Post by Pantera on 2006-04-21
***** UPGRADE *****

I've done a few test and looks like the problem is relate to the **[Xear Technology]("http://www.cmedia.com.tw/news/e-xear.htm")** supported by C-Media 9739 chipset.
I've realized it by reading the Readme.txt file of the linux driver got at the link posted before.

> [FONT="Courier New"]10.Support xear mode to swap front and surround speakers output.
   For PCCHIPS LCD PC, you should change the following codes in cmaudio.h:

        // For PCCHIPS LCD PC
        #define FORCE_LINEINASREAR_MODE 1
        #define FORCE_XEAR_MODE 1

        //#define FORCE_LINEINASREAR_MODE 0
        //#define FORCE_XEAR_MODE 0
[/FONT]

After to have read this, i've took a look at the windows drivers. There's a checkbox named "Enable Xear", if you uncheck it, you get no sound (even if the mixer continue working properly).

So that's it! :-D 

Now, the question is; is there any way of enabling Xear with Alsa drivers?
If not, how do i install the C-Media driver (i guess it's an OSS driver) i've found at the link in previous post? :confused:

---

