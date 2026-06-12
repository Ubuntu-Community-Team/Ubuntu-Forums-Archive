---
title: "My Fate in your hands ..."
date: 2011-11-09
forum: General Help
---

### Post by Atlus on 2011-11-09
Hi all,

I hope someone can help me... im running out of time and here is what happened, enjoy:

So, I work remotely for a company connecting through VPN and using Citrix on a Laptop with pre-installed Windows 7.  It worked fine up until around 2 days ago, when I wanted to start as usual my Laptop and Windows 7 barely manages to load up. It bringt me to the login screen, which already takes way more time than usual but its takes ages to eventually beeing logged in - hours actually - the harddisc seems to have problems, not making the usual sounds, just little noises, like it would be loading, stopping, loading ... impossible to work in any way.. cant even load up any applications. So lucky me, i was off yesterday and still am today and have to work tomorrow, in about 18 hours... 

What did I do so far? First I downloaded Ubuntu , made an USB Stick with it, loaded it up, perfect... i might be not the worst newbie in Computers (used Mandrake like ages ago) so I managed to get VPN running and got the Citrix ICA thing... managed to log in through the Stick .. amazing to me, so far so good.

Next thing I did, I downloaded the Ultimate Boot Disc and made a CD, started it and used HDAT2 to test my harddisc (RAM is definatly fine, I checked before), here I dont fully understand everything but it tells me about MBR Errors... so from what I understand the MBR Errors are some starting partition thing... how to fix that, I have no clue and basically I dont think I will manage in time. 

So, I downloaded the latest Ubuntu Version, made a CD and tried to install BUT ... I want to keep my Windows 7, I still need the files and will get them at some point, I can access all of them through Ubuntu anyway at the moment... I tried following the manual - how to - thing .. BUT I dont have any option to do "install ubuntu alongside windows 7" ... i can chose between erasing all windows 7 or other .. and the other, it lists me:

/dev/sda
/dev/sda1 14221 MB
/dev/sda2 104 MB
/dev/sda3 485779 MB


But, manually doing this, I dont feel confident knowing what im doing ... I thought there is an option, like years ago in Mandrake where I just say how much space I want to give to Linux and thats it... I dont want to erase anything by mistake... please, someone tell me, how do I install it alongside windows, but in a way that someone drinking rum and has to work soon would understand... I mean, the manual is talking about an option like I imagine, but I dont find it...

Please Obi-Wan-Kenobi ... youre my only hope... I need to install that thing today, get everything running and be ready for tomorrow and still have Windows 7 installed... else, I guess, I will have some long vacation soon.

Thank you,
Alejandro

---

### Post by Dangertux on 2011-11-09
> **Atlus said:**
> Hi all,

I hope someone can help me... im running out of time and here is what happened, enjoy:

So, I work remotely for a company connecting through VPN and using Citrix on a Laptop with pre-installed Windows 7.  It worked fine up until around 2 days ago, when I wanted to start as usual my Laptop and Windows 7 barely manages to load up. It bringt me to the login screen, which already takes way more time than usual but its takes ages to eventually beeing logged in - hours actually - the harddisc seems to have problems, not making the usual sounds, just little noises, like it would be loading, stopping, loading ... impossible to work in any way.. cant even load up any applications. So lucky me, i was off yesterday and still am today and have to work tomorrow, in about 18 hours... 

What did I do so far? First I downloaded Ubuntu , made an USB Stick with it, loaded it up, perfect... i might be not the worst newbie in Computers (used Mandrake like ages ago) so I managed to get VPN running and got the Citrix ICA thing... managed to log in through the Stick .. amazing to me, so far so good.

Next thing I did, I downloaded the Ultimate Boot Disc and made a CD, started it and used HDAT2 to test my harddisc (RAM is definatly fine, I checked before), here I dont fully understand everything but it tells me about MBR Errors... so from what I understand the MBR Errors are some starting partition thing... how to fix that, I have no clue and basically I dont think I will manage in time. 

So, I downloaded the latest Ubuntu Version, made a CD and tried to install BUT ... I want to keep my Windows 7, I still need the files and will get them at some point, I can access all of them through Ubuntu anyway at the moment... I tried following the manual - how to - thing .. BUT I dont have any option to do "install ubuntu alongside windows 7" ... i can chose between erasing all windows 7 or other .. and the other, it lists me:

/dev/sda
/dev/sda1 14221 MB
/dev/sda2 104 MB
/dev/sda3 485779 MB


But, manually doing this, I dont feel confident knowing what im doing ... I thought there is an option, like years ago in Mandrake where I just say how much space I want to give to Linux and thats it... I dont want to erase anything by mistake... please, someone tell me, how do I install it alongside windows, but in a way that someone drinking rum and has to work soon would understand... I mean, the manual is talking about an option like I imagine, but I dont find it...

Please Obi-Wan-Kenobi ... youre my only hope... I need to install that thing today, get everything running and be ready for tomorrow and still have Windows 7 installed... else, I guess, I will have some long vacation soon.

Thank you,
Alejandro

It is strange that is not giving you the option to install along side.

Consult this documentation it is fairly well written and a simple guide for using Gparted for shrinking an NTFS partition.

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

A note : You will want to shrink /dev/sda3

Hope this is helpful.

---

### Post by Atlus on 2011-11-09
> **Dangertux said:**
> It is strange that is not giving you the option to install along side.

Consult this documentation it is fairly well written and a simple guide for using Gparted for shrinking an NTFS partition.

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

A note : You will want to shrink /dev/sda3

Hope this is helpful.


Hi,

Thanks alot for your reply.

Just a question, I have Ubuntu 10.0 (I think) on a USB Stick and the latest one now on CD. Both, when I click on Install, dont give me the option to install it alongside Windows but to shrink manually a harddisc. Im using a Sony Vaio VPCEA3S1E (one of the worst laptops I ever bought IMO). Is there any trick to get that option? Is Ubuntu made in a way not to offer this option for some reasons when used on certain hardware?

Im just really scared to do this manually, I looked into your link but, Im not really confident knowing what Im doing..I dont have anything to store my files in at the moment and I really dont want to risk of losing anything.. is there perhaps any distribution of Linux which the same features that would allow me to have an option for an automatic install alongside Windows?

Thanks alot,
Alejandro

---

### Post by Claus7 on 2011-11-09
Hello,

> **Atlus said:**
> Hi,

...

Im just really scared to do this manually, I looked into your link but, Im not really confident knowing what Im doing..I dont have anything to store my files in at the moment and I really dont want to risk of losing anything.. is there perhaps any distribution of Linux which the same features that would allow me to have an option for an automatic install alongside Windows?


Take a backup first! I have not read your initial post, yet don't play or tamper with partitions. Or else one mistake might cause you a lot of trouble. Take a backup first and then do whatever you like.

Regards!

---

### Post by Atlus on 2011-11-09
> **Claus7 said:**
> Hello,



Take a backup first! I have not read your initial post, yet don't play or tamper with partitions. Or else one mistake might cause you a lot of trouble. Take a backup first and then do whatever you like.

Regards!


Hi,

Thanks for your time,

I have the problem with the backup cause Im running out of time and I dont have around 200gb to save anywhere.. just big files... I mean, I trust Ubuntu/Linux anyway, I know it, I just need an option how that thing will do everything for me.. to install it alongside Windows, I cant use Windows at the moment anyway, I just want to leave it untouched and use Ubuntu for the time beeing (which is amazing btw.... I havent looked into Linux for years and im amazed from what I see, compared to Mandrake 10.0 ages ago)

Thanks,
Alejandro

---

### Post by sammiev on 2011-11-09
Use [Clonezilla]("http://clonezilla.org/clonezilla-live.php") to backup your HD and you can return your HD to that state at any which given time in 30 min or less. :)

---

### Post by Atlus on 2011-11-09
> **sammiev said:**
> Use [Clonezilla]("http://clonezilla.org/clonezilla-live.php") to backup your HD and you can return your HD to that state at any which given time in 30 min or less. :)

Hi, 

Thanks to you as well taking time for this,

Hmmm.. Clonezilla, thing is, its around midnight here, I had 2 blanks which I used for Ultimate Boot Disc and one for Ubuntu... and I got one stick left on which is Ubuntu 10.00 now... perhaps if there is no option to install this thing alongside Windows... could someone tell me what to do with the /dev/sda3 .. its 485gb, and I think around 200GB is occupied by Windows... how do I tell that thing to use like 100GB for Ubuntu and install it?

Thanks,
Alejandro

---

### Post by Illux on 2011-11-09
Hey, 

I had basicly the same problem, sadly I couldnt figure out how to fix it so I took a backup, earased the entire HDD, installed Ubuntu First, than Windows, Bootmanager blablabla. But this will get you nowhere, so lets try to figure things out. Any chance to connect the HDD to another laptop, terminal pc, external harddrive?! whatsoever n take a backup there? In that case we could go through the steps I took. If u need help to connect the device to whatsoever I ll assist you.

In case a) brilliant

case b) ****.

Case b). Try to log into windows, if possible, use the ootb partitionmanager, clear some space, try to install Ubuntu using the free space.

Case a) almost brilliant

case b) ****

Again, case b) Any chance to get a 4GB + USB Stick? We could install Ubuntu right on the stick so u ll just hv to work one day using a stick - sould work. Even alongside Windows. 

I ll try to finger out more ideas, keep us in the loop.

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> Hey, 

I had basicly the same problem, sadly I couldnt figure out how to fix it so I took a backup, earased the entire HDD, installed Ubuntu First, than Windows, Bootmanager blablabla. But this will get you nowhere, so lets try to figure things out. Any chance to connect the HDD to another laptop, terminal pc, external harddrive?! whatsoever n take a backup there? In that case we could go through the steps I took. If u need help to connect the device to whatsoever I ll assist you.

In case a) brilliant

case b) ****.

Case b). Try to log into windows, if possible, use the ootb partitionmanager, clear some space, try to install Ubuntu using the free space.

Case a) almost brilliant

case b) ****

Again, case b) Any chance to get a 4GB + USB Stick? We could install Ubuntu right on the stick so u ll just hv to work one day using a stick - sould work. Even alongside Windows. 

I ll try to finger out more ideas, keep us in the loop.

Hello,

Thanks alot for your help,

So, things are like this:

I have only one stick, on which I have Ubuntu 10.0 still, and 2 Blanks which I used for Ultimate Boot CD and for the latest Ubuntu Version (currently running from CD). I have this weird Sony Vaio, and, im not scared of opening up PCs and all that (did alot), but this Vaio is build in a way that I think I have to do McGyver-style to get through to the harddisc...so I was thinking, how can I safely just leave the Windows stuff on the harddisc and just giving Ubuntu the space it needs, lets say 100Gb, lets say 80... even less, whatever makes it run, from there I would be able to install the rest myself. Ubuntu itself is not giving me the option to install it alongside windows, so it has to be done manually somehow.. and this partition thing.

When I click on "Install Ubuntu  11.10" it tells me:

This computer has currently Windows 7. What would u like to do:

Replace Windows 7 with Ubuntu

Something else

So I click on something else...

then I get to the dev/sda thing .. .from here, its too complicated for me... how do i give Ubuntu what it needs without harming the windows part?

Thanks alot
Alejandro

---

### Post by Dangertux on 2011-11-09
> **Atlus said:**
> Hi,

Thanks alot for your reply.

Just a question, I have Ubuntu 10.0 (I think) on a USB Stick and the latest one now on CD. Both, when I click on Install, dont give me the option to install it alongside Windows but to shrink manually a harddisc. Im using a Sony Vaio VPCEA3S1E (one of the worst laptops I ever bought IMO). Is there any trick to get that option? Is Ubuntu made in a way not to offer this option for some reasons when used on certain hardware?

Im just really scared to do this manually, I looked into your link but, Im not really confident knowing what Im doing..I dont have anything to store my files in at the moment and I really dont want to risk of losing anything.. is there perhaps any distribution of Linux which the same features that would allow me to have an option for an automatic install alongside Windows?

Thanks alot,
Alejandro

For the "install side by side" option to be available you must have free space which can be partitioned, you acheive the free space by shrinking your windows parition. Once it is shrunken it should give you the option to install side by side.

hope this helps.

---

### Post by Atlus on 2011-11-09
> **Dangertux said:**
> For the "install side by side" option to be available you must have free space which can be partitioned, you acheive the free space by shrinking your windows parition. Once it is shrunken it should give you the option to install side by side.

hope this helps.

Hi,

Thanks for joing this,

Thats the thing, there is still enough space left.. this dev/sda3 is 485gb in total and around 250 or so are used by windows, I just dont understand how to shrink it... how to make it for ubuntu.. there is no option that ubuntu will tell me "look u got this amount, how much of that u want to use?" ... it was like this in mandrake many years ago... the idea of "shrinking" manually for me could end up in a total mess... i just want to install ubuntu alongside it... is there any installer file or something that would do it for me?

Thanks,
Alejandro

---

### Post by Illux on 2011-11-09
> **Atlus said:**
> Hi,

Thanks for joing this,

Thats the thing, there is still enough space left.. this dev/sda3 is 485gb in total and around 250 or so are used by windows, I just dont understand how to shrink it... how to make it for ubuntu.. there is no option that ubuntu will tell me "look u got this amount, how much of that u want to use?" ... it was like this in mandrake many years ago... the idea of "shrinking" manually for me could end up in a total mess... i just want to install ubuntu alongside it... is there any installer file or something that would do it for me?

Thanks,
Alejandro

You hv a Vario? Oh damn, things just changed from sh.it to holy crap...I know why I m a fan of IBM / Lenovo ever since I can remember...one screw to change the HDD, 3 to change the processor - and still waterproof...technic you love....anyway, we gotta sort ur crap out.

R u using Gnome or KDE? Whatsoever, log out n login using KDE. Then click on partition manager n shrink down your partition - if there is NO WAY to do it using windows. I know...strange Idea....but do u hv a Mac OS CD close at hand? Cuz the ootb partitionmanager Mac OS is using ( n which u can use the moment u placed in the CD) is pretty sweet.... And is there def NO WAY to do the partition thingy using winDOOHs?

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> You hv a Vario? Oh damn, things just changed from sh.it to holy crap...I know why I m a fan of IBM / Lenovo ever since I can remember...one screw to change the HDD, 3 to change the processor - and still waterproof...technic you love....anyway, we gotta sort ur crap out.

R u using Gnome or KDE? Whatsoever, log out n login using KDE. Then click on partition manager n shrink down your partition - if there is NO WAY to do it using windows. I know...strange Idea....but do u hv a Mac OS CD close at hand? Cuz the ootb partitionmanager Mac OS is using ( n which u can use the moment u placed in the CD) is pretty sweet.... And is there def NO WAY to do the partition thingy using winDOOHs?


Hi there,

Thanks for your help,

I will definatly never ever buy a Vaio in my life again, not because windows is not working at the moment, but the whole thing is just not worth the money. My former HP Elitebook made a more solid impression.

Anyway,

Im using currently the Ubuntu LIVE CD, the latest one, im connected with it. I dont think its KDE running, i actually am not sure cause I know KDE from many years ago. Also Ubuntu is having this partition thing, but im just scared that I do something wrong. 

I do not own a mac or have a mac CD and windows is really unsuable, its something with the MBR, according to HDAT2 on Ultimate Boot Disc, but I can access all files fine through Ubuntu.

So for me the problem is, how do I tell Ubuntu, on dev/sda3, to take like only 80gb for it and leave Windows as it is.

Thanks alot,
Alejandro

---

### Post by Illux on 2011-11-09
> **Atlus said:**
> Hi there,


I do not own a mac or have a mac CD and windows is really unsuable, its something with the MBR, according to HDAT2 on Ultimate Boot Disc, but I can access all files fine through Ubuntu.


Ok ...having said that, we can try some mcgyver stuff. do u hv a win cd? no matter what windows actually...we can try to fix the mbr. or can u access the windows repair console? Start the pc, hit f8f8f8f8f8f8f8f8f8. Start recovery n once u get the prompt, type "fix mbr" and "fix boot".

In case u r still after option b) (the-everything-sucks-option) do u hv at least a CD so I can send u an ISO to burn a Win Recovery tool?

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> Ok ...having said that, we can try some mcgyver stuff. do u hv a win cd? no matter what windows actually...we can try to fix the mbr. or can u access the windows repair console? Start the pc, hit f8f8f8f8f8f8f8f8f8. Start recovery n once u get the prompt, type "fix mbr" and "fix boot".

In case u r still after option b) (the-everything-sucks-option) do u hv at least a CD so I can send u an ISO to burn a Win Recovery tool?


So, I dont have a Win CD cause these Vaios dont come with one. But its a full valid registered Windows 7 Version, the Vaio is VPCEA3S1E and the registration number and all is on the package and beneath the laptop.

I tried the F8 thing, which I didnt see before, I only knew F2 for the Bios. So I get into this menu, its all spanish (im not spanish, I just happen to live here and I speak so so but not technical terms) and it gives me apart from the options Secure Mode, Secure Mode with Network etc. some others which I dont understand, but I tried 3 and all of them still have the start up screen of windows, which turns again into a slowmotion boot-up sequence so I canceled it. Do you know how its called in english, what I have to select to get to the prompt? Perhaps the MBR thing can really fix it all.

Unfortunately I dont have any blanks left, I had 2 and one I used for Ultimate Boot CD and the other for the latest Ubuntu Version.

Thanks alot for your help

---

### Post by Illux on 2011-11-09
> **Atlus said:**
> So, I dont have a Win CD cause these Vaios dont come with one. But its a full valid registered Windows 7 Version, the Vaio is VPCEA3S1E and the registration number and all is on the package and beneath the laptop.

I tried the F8 thing, which I didnt see before, I only knew F2 for the Bios. So I get into this menu, its all spanish (im not spanish, I just happen to live here and I speak so so but not technical terms) and it gives me apart from the options Secure Mode, Secure Mode with Network etc. some others which I dont understand, but I tried 3 and all of them still have the start up screen of windows, which turns again into a slowmotion boot-up sequence so I canceled it. Do you know how its called in english, what I have to select to get to the prompt? Perhaps the MBR thing can really fix it all.

Unfortunately I dont have any blanks left, I had 2 and one I used for Ultimate Boot CD and the other for the latest Ubuntu Version.

Thanks alot for your help

Spanish? This crap aint gettin any better dude.... alright its called Recovery or Repair Console, Repair your computer ( Reparos los computos...lol...) ...something like that...I ll try to find out what it means in actual spanish...brb

---

### Post by Illux on 2011-11-09
Just found something...dunno if that works...never gave it a try...so...


[LIST=1]
[*] 								
[LIST]
[*] 															1 														 																Insert the Ultimate Boot CD into your computer.

 							
[*] 															2 														 																Restart the machine and press any key as the PC is loading to boot from CD.

 							
[*] 															3 														 																Highlight the "Filesystem Tools" option and press "Enter."

 							
[*] 															4 														 																Highlight the "MBRTool" option and press "Enter."

 							
[*] 															5 														 																Select the "Restore" option and press "Enter" to repair your Master Boot Record.

 							
[*] 															6 														 																Reboot your computer.


[/LIST]
[/LIST]
I d give it a shot...sounds fairly easy...

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> Just found something...dunno if that works...never gave it a try...so...


[LIST=1]
[*]
[LIST]
[*]                                                             1                                                                                                                          Insert the Ultimate Boot CD into your computer.
[*]                                                             2                                                                                                                          Restart the machine and press any key as the PC is loading to boot from CD.
[*]                                                             3                                                                                                                          Highlight the "Filesystem Tools" option and press "Enter."
[*]                                                             4                                                                                                                          Highlight the "MBRTool" option and press "Enter."
[*]                                                             5                                                                                                                          Select the "Restore" option and press "Enter" to repair your Master Boot Record.
[*]                                                             6                                                                                                                          Reboot your computer.
[/LIST]
 
[/LIST]
I d give it a shot...sounds fairly easy...

Man, thanks alot, I will try this right away.

In the meanwhile I was rebooting and writing down the options, so here they are (after pressing F8)

Mode Seguro
Mode Seguro con funciones de red
Mode Seguro con simbolo del sistema

Habilitar el registro de arrangue
Habilitar video de baja resolucion (640 x 480)
La ultima configuracion valida conocida (avanzada)
Mode de restauracion de servicios de directorio
Mode de depuracion
Deshabilitar el reinicio automatico en casa de error del sistema
Deshabilitar el uso obligatorio
Deshabiliar de controladares firmados


I will try now the ultimate boot cd thing, thanks alot, brb

---

### Post by dFlyer on 2011-11-09
Just my 2 cents. Backup windows or fix the mbr if that's what is causing your problems before you mess with the partitions. If I remember correctly, I haven't used windows in 10 - 15 years, but you will need to defrag your windows partition before you make any modifications to it.

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> Just found something...dunno if that works...never gave it a try...so...


[LIST=1]
[*]
[LIST]
[*]                                                             1                                                                                                                          Insert the Ultimate Boot CD into your computer.
[*]                                                             2                                                                                                                          Restart the machine and press any key as the PC is loading to boot from CD.
[*]                                                             3                                                                                                                          Highlight the "Filesystem Tools" option and press "Enter."
[*]                                                             4                                                                                                                          Highlight the "MBRTool" option and press "Enter."
[*]                                                             5                                                                                                                          Select the "Restore" option and press "Enter" to repair your Master Boot Record.
[*]                                                             6                                                                                                                          Reboot your computer.
[/LIST]
 
[/LIST]
I d give it a shot...sounds fairly easy...

I just tried it, but, the problem is, the CD loads up straight to the MENU, it doesnt matter whether I press anything. So there, there is no Filesystem Tools, but I found something like MBRTool, but there is no restore options. Perhaps this is based on an older Ultimate Boot CD? But I think we are getting closer and closer... 

Just one question, out of curiousity, cause I dont fully understand MBR. Could a MBR error cause a problem like I described? Meaning, it goes to the Windows Bootup sequence, its gets to the login screen (after like 5minutes) from there on it takes literallly hours to load up... Im just asking cause I remember, many years ago, the MBR would perhaps not allow to boot at all?

Can I do something wrong when I just try around with the MBR tool?

---

### Post by Atlus on 2011-11-09
> **dFlyer said:**
> Just my 2 cents. Backup windows or fix the mbr if that's what is causing your problems before you mess with the partitions. If I remember correctly, I haven't used windows in 10 - 15 years, but you will need to defrag your windows partition before you make any modifications to it.

Hi there,

Thanks for joining this,

Im trying to fix the MBR somehow now, Im just not that fluent in computers to manage all with an understanding of what I do actually. Im having the latest Ultimate Boot CD and there is an MBRTool on it, im just not sure what to select (there is no restore option) in order not to mess up things.

---

### Post by Illux on 2011-11-09
Win 7 is using NTFS, no need for defrag if u asked me. FAT n FAT 32 Days are long gone mate ;)

Alright, heres your spanish

Safe mode

      "              with networking
      "              with command prompt
Enable boot logging
Enable low resolution
Last known good configuration
Directoy service restore mode
Debugging mode
Disable automatic restart on system failure
Disable driver signature enforcement

I d go for the Directory service restore mode n try the McGyver tricks there...

That CD thing is not working like the guy suggested whos entry I was just posting?

---

### Post by MDguy on 2011-11-09
You may be able to fix the MBR using Ubuntu.
Boot into an Ubuntu desktop using your USB stick, and then open a terminal using ctrl+alt+t.

then type
```
sudo apt-get install lilo
```and enter your password and hit enter.
followed by:
```
sudo lilo -M /dev/sda mbr
```and hit enter again.
See post #6 in [this thread]("http://ubuntuforums.org/showthread.php?t=1541022").

---

### Post by Atlus on 2011-11-09
> **Illux said:**
> Win 7 is using NTFS, no need for defrag if u asked me. FAT n FAT 32 Days are long gone mate ;)

Alright, heres your spanish

Safe mode

      "              with networking
      "              with command prompt
Enable boot logging
Enable low resolution
Last known good configuration
Directoy service restore mode
Debugging mode
Disable automatic restart on system failure
Disable driver signature enforcement

I d go for the Directory service restore mode n try the McGyver tricks there...

That CD thing is not working like the guy suggested whos entry I was just posting?

Hey,

OK, first this,

I tried all this, when i go into Directory Service Restore it still goes to the boot screen of windows.. then goes into some "secure mode" , i end up on the desktop but it takes ages to get there.. i aborted after 15min or so ... so there is no prompt to enter things ...

The CD , its not working when i press "any key" .. there is a menu, and i found something like MBRTools but there is no Restore option, I downloaded the latest version today.

---

### Post by Atlus on 2011-11-09
> **MDguy said:**
> You may be able to fix the MBR using Ubuntu.
Boot into an Ubuntu desktop using your USB stick, and then open a terminal using ctrl+alt+t.

then type
```
sudo apt-get install lilo
```and enter your password and hit enter.
followed by:
```
sudo lilo -M /dev/sda mbr
```and hit enter again.
See post #6 in [this thread]("http://ubuntuforums.org/showthread.php?t=1541022").

Hi, 

thanks for the tip,

I just did it and restarted, but it seems its loading up faster to the login screen but still when it comes loading the Desktop its in slowmotion and this time I didnt even get the Icons... im really thinking my harddisc is all done, but again I can access all the files fine through ubuntu... 

One question, could someone please please please just tell me, HOW to install the ubuntu alongside windows... please.. I cant run it on the stick or cd alone for work.. or, ok, if it doesnt work like that, I know its an ubuntu forum, but please, if you know any distribution that will do automatically, like asking me how much space to use etc.. please tell me... I dont know what else to do .. i think i will smash this laptop against the wall ... I just dont understand what is wrong.. and how to see what is wrong.. i mean, again, i dont understand MBR.. what does MBR do? is it like i described? can mbr do this? .. is it my harddisc? i tested it with HDAT2 tool on ultimate boot cd .. it says errors with mbr but rest fine.. but why it loads in slowmotion?... the thing is, is all fine with the stick .. i just want the same as the stick on my pc so i can use the space and install stuff... i remember mandrake 10.0 or so .. it had this option, would leave windows alone, install itself and then i have a boot menu... can i have the same with some distribution?

please please please

---

### Post by Atlus on 2011-11-09
Guys, cause I dont see any other option than somehow to install ubuntu... can someone please tell me, how this works:

**Automatic partition resizing (recommended)**

 
[LIST]
[*]Choose the first option, which should say "Install them side by side, choosing between them each startup". 
[*]Specify the size of the new partition by dragging the slider at the bottom of the window. 
[*]Click on "Forward".
[/LIST]

I went to the "install ubuntu" link , windowsdualboot, but why I dont have the "Automatic partition resizing" , which is recommended and which I would love to have... if i understood right before, I need to have already space for Ubuntu, ok, but this is the official guide to install windowsdualboot, here it is:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

so, when I follow the steps, I dont have that option, there is no "automatic resizing" .. i have the latest version 11.10 ... 

it says chose one of the 2 following options, manual and automatic... is there no automatic anymore in 11.10? Please someone

---

### Post by Stupid_newbie on 2011-11-09
> **Atlus said:**
> Hi, 

thanks for the tip,

I just did it and restarted, but it seems its loading up faster to the login screen but still when it comes loading the Desktop its in slowmotion and this time I didnt even get the Icons... im really thinking my harddisc is all done, but again I can access all the files fine through ubuntu... 


You Think you can access all files in ubuntu, but, in fact, you cannot. Ubuntu is not dependent on the hard drive to work as Windows 7 is. Ubuntu is actually depending on the USB and RAM to operate. Ubuntu can see a majority of your data and is working as best as it can with your current hard drive. I will tell you this, from my experience: You are extremely close to losing all your data and will need a data recovery program to get your stuff back!!! 

> **Atlus said:**
> 

One question, could someone please please please just tell me, HOW to install the ubuntu alongside windows... please.. I cant run it on the stick or cd alone for work.. or, ok, if it doesnt work like that, I know its an ubuntu forum, but please, if you know any distribution that will do automatically, like asking me how much space to use etc.."


you will need a software package similar to partition magic. i know the unix version is called GNU parted  or GParted and you can install it in your "live usb" version of Ubuntu. it is very simple to use and may help.. leave yourself about 10gb for file system and 3gb for SWAP area and your off to the races....BACK UP IMPORTANT STUFF. IE My documents (/users/-yourname- documents.)
after you re size your partition and go to install ubuntu. now that you have free space in the partitions it will ask you "would you like to run ubuntu along windows" 


> **Atlus said:**
> 
 please tell me... I dont know what else to do .. i think i will smash this laptop against the wall ... I just dont understand what is wrong.. and how to see what is wrong.. i mean, again, i dont understand MBR.. what does MBR do? is it like i described? can mbr do this? .. is it my harddisc? i tested it with HDAT2 tool on ultimate boot cd .. it says errors with mbr but rest fine.. but why it loads in slowmotion?... the thing is, is all fine with the stick .. i just want the same as the stick on my pc so i can use the space and install stuff... i remember mandrake 10.0 or so .. it had this option, would leave windows alone, install itself and then i have a boot menu... can i have the same with some distribution?

please please please
MBR - Master boot record is basically like the INDEX in a book. The MBR tells the computer where every file is located on your hard drive. IE - you are looking for a file called "my documents" the MBR tells your computer "MY documents is located in sector 202230230-2030302030" and your hard drive will search sectors 202230230 for those files" if your MBR is corrupted, it may affect your computers ability to read the partition data or the way the system boots up. There are several ways to FIX an MBR, but, its ALWAYS recommended to BACK UP what you CAN/NEED (NEED not WANT) before playing with your MBR

May the FORCE be with you young JEDI

For your sake, I suggest this. Spend the $30 (or whatever it costs) for an external 200gb hard drive, use your UBUNTU live usb thing and back your data up. once its backed up, FORMAT, CHKDSK, FORMAT, FDISK, CHDSK and if everything passes RE INSTALL windows 7. if your tests fail on the hard drive, DONT CHEAP OUT...BUY A NEW HARD DRIVE

---

### Post by Atlus on 2011-11-09
> **Stupid_newbie said:**
> You Think you can access all files in ubuntu, but, in fact, you cannot. Ubuntu is not dependent on the hard drive to work as Windows 7 is. Ubuntu is actually depending on the USB and RAM to operate. Ubuntu can see a majority of your data and is working as best as it can with your current hard drive. I will tell you this, from my experience: You are extremely close to losing all your data and will need a data recovery program to get your stuff back!!! 


you will need a software package similar to partition magic. i know the unix version is called GNU parted  or GParted and you can install it in your "live usb" version of Ubuntu. it is very simple to use and may help.. leave yourself about 10gb for file system and 3gb for SWAP area and your off to the races....BACK UP IMPORTANT STUFF. IE My documents (/users/-yourname- documents.)
after you re size your partition and go to install ubuntu. now that you have free space in the partitions it will ask you "would you like to run ubuntu along windows" 



MBR - Master boot record is basically like the INDEX in a book. The MBR tells the computer where every file is located on your hard drive. IE - you are looking for a file called "my documents" the MBR tells your computer "MY documents is located in sector 202230230-2030302030" and your hard drive will search sectors 202230230 for those files" if your MBR is corrupted, it may affect your computers ability to read the partition data or the way the system boots up. There are several ways to FIX an MBR, but, its ALWAYS recommended to BACK UP what you CAN/NEED (NEED not WANT) before playing with your MBR

May the FORCE be with you young JEDI

For your sake, I suggest this. Spend the $30 (or whatever it costs) for an external 200gb hard drive, use your UBUNTU live usb thing and back your data up. once its backed up, FORMAT, CHKDSK, FORMAT, FDISK, CHDSK and if everything passes RE INSTALL windows 7. if your tests fail on the hard drive, DONT CHEAP OUT...BUY A NEW HARD DRIVE


Hey there,

Thanks alot for the answer,

Ok, i understand, nothing I can do right now and honeslty I was never a fan of windows and just for work 6 years ago i switched back to it. Since i found out i can use vpn and citrix through linux, its all fine for me, company cant tell the difference anyway, but for me its like, I have to work again in about 11 hours from now.. perhaps it will be fate, i hated working for them anyway, so perhaps good time to quit... but just one question, i tested it so far with a 8GB stick, do you think I can run:

VPN (alot applications)
CItrix ICA
Firefox with like 10-15 tabs
Flash Video same time
Open Office
Skype
aMSN

All at the same time with the stick without any problems for like 10/12 hours, without problems?

The only thing that bothers me... i dont understand the steps, why they say there is an automatic way to install ubuntu when you have windows already? Where can I get this?

Thanks again,
Alejandro

---

### Post by Stupid_newbie on 2011-11-09
> **Atlus said:**
> Hey 
The only thing that bothers me... i dont understand the steps, why they say there is an automatic way to install ubuntu when you have windows already? Where can I get this?

Thanks again,
Alejandro

you CAN install ubuntu along side windows...BUT... you need to free up some space on your HARD drive by Resizing the existing NTFS partition. using "gparted" will help you do this. 

boot into your USB stick ubuntu
open a terminal
run this command

```

sudo apt-get install gparted

```

it will prompt you "do you want to install this software y or n"
type "y' and press enter

once its installed type 
```

sudo gparted

```
,
Once this is loaded, you should now see a graphical image of your hard drive

shrink your windows 7 partitition to so that you have 25GB FREE. leave this 25 gb as "unpartitioned space"

apply changes and commence finger crossing

once this process is complete, re boot laptop and attempt to install ubuntu.... the install should see this "unpartitoned space" and will say "do you want ubuntu to run along side windows?" or something like that
 god willing, ubuntu will then install the dual partiton automatically and you can backup tomorrow or something.

once again
Live long and prosper

im off to bed :) i wish you luck

---

### Post by Atlus on 2011-11-09
> **Stupid_newbie said:**
> you CAN install ubuntu along side windows...BUT... you need to free up some space on your HARD drive by Resizing the existing NTFS partition. using "gparted" will help you do this. 

boot into your USB stick ubuntu
open a terminal
run this command

```

sudo apt-get install gparted

```it will prompt you "do you want to install this software y or n"
type "y' and press enter

once its installed type 
```

sudo gparted

```,
Once this is loaded, you should now see a graphical image of your hard drive

shrink your windows 7 partitition to so that you have 25GB FREE. leave this 25 gb as "unpartitioned space"

apply changes and commence finger crossing

once this process is complete, re boot laptop and attempt to install ubuntu.... the install should see this "unpartitoned space" and will say "do you want ubuntu to run along side windows?" or something like that
 god willing, ubuntu will then install the dual partiton automatically and you can backup tomorrow or something.

once again
Live long and prosper

im off to bed :) i wish you luck

Hey,

Thanks alot for that,

I did it and im in the graphical interface, only it tells me with a red symbol that something is wrong with the disc. when i click on properties it says:

ntfsresize v2.0.0 (libntfs 10:0:0)
Device name: /dev/sda3
NTFS volume version 3.1
Cluster size: 4096 bytes
Current volume size: 485779067392 (485780 MB)
Current device size: 485779067392 (485780 MB)
Checking filesystem consistency:
Cluster 81176 is referenced multiple times!

the same goes on until

Cluster 81185

Error: Filesystem check failed!
Error: 16 Clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!


I cant get into Windows doing the chkdsk... can someone please advise what is wrong here? Is the disk all done? is it easy to repair? Please

---

### Post by Stupid_newbie on 2011-11-10
you need to create a windows boot disk and run a dos prompt.

[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc]("http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc")

this will allow you to run chdisk and help you fix your mbr

do  google search on "how to repair windows 7 mbr" and im sure you can get all the info to get yo up and running again

---

### Post by Atlus on 2011-11-10
> **Stupid_newbie said:**
> you need to create a windows boot disk and run a dos prompt.

[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)

this will allow you to run chdisk and help you fix your mbr

do  google search on "how to repair windows 7 mbr" and im sure you can get all the info to get yo up and running again


Im getting crazy with this thing ... now I cant do anything but try to run it from the stick today and now when i try to install vpn it tells me "I need super user priviledges" ... but, why suddenly? what kind of password i have to enter? im running it from a stick .. I didnt need to do that yesterday... what password is set on the ubuntu usb stick?

---

### Post by nothingspecial on 2011-11-10
Did you free up the space?

---

### Post by Atlus on 2011-11-10
> **nothingspecial said:**
> Did you free up the space?

No, I dont have any time to do anything .. I need to work in around 45min .. what i dont understand is, why suddenly I need to enter some super user password? im running everything from a stick like yesterday.. what is the super user password on a stick? i mean, i just put it in and run it.. please someone, i need to do this 

sh ./vpnsetup.sh ... and it asks me for super user priviledges..

---

### Post by nothingspecial on 2011-11-10
Type sudo before the command.

```
sudo ./vpnsetup.sh
```

---

### Post by Atlus on 2011-11-10
> **nothingspecial said:**
> Type sudo before the command.

```
sudo ./vpnsetup.sh
```


Ohhh it worked.. thanks alot, thank you very much ... I hope I survive the day somehow and then I will try the chkdsk thing mentioned before... thanks again everybody

---

### Post by Atlus on 2011-11-13
> **Atlus said:**
> Ohhh it worked.. thanks alot, thank you very much ... I hope I survive the day somehow and then I will try the chkdsk thing mentioned before... thanks again everybody

Hi all,

So a few days passed and Ive been using the Ubuntu USB Stick every day so far, works great. 

Windows-wise, I did the chkdsk /f and it did find some errors, and managed to fix them (automatically) but the problems remain the same. Its impossible to boot up Windows, takes hours basically. The harddisc seems to load little by little, very slow, then suddenly for 2-3 seconds faster again and back to slow. 

Im not sure what else to do with the windows-problem but at least I can access most files I need. So I think I will try around for 1-2 days and if nothing works, I will try to back up all and just format the whole disc.

Thanks alot to everyone helping me with this.

Just one question,

I really like the Ubuntu Im using from the USB Stick, and I think I will install Ubuntu on the machine after formatting the disc. I was just wondering whether its very complicated to modify the Ubuntu USB stick in a way that it would load up already with everything I would need instead of getting it. Is there a huge performance difference between the LIVE Version and when e.g. installing the full version on a USB stick and using it?

---

### Post by bapoumba on 2011-11-13
You may have mentioned this already, how old is the computer ? Maybe the drive is dying..

Get a few CDs and save anything you can using ubuntu from the usb stick, or the other way around.

---

### Post by Atlus on 2011-11-13
> **bapoumba said:**
> You may have mentioned this already, how old is the computer ? Maybe the drive is dying..

Get a few CDs and save anything you can using ubuntu from the usb stick, or the other way around.

The laptop is fairly new, I got in May/June this year, but it fell down once but was always working fine (sony vaio vpcea3s1e). The strange thing is that chkdsk corrected found errors, but still didnt change anything to the problem. I dont understand how to fix the MBR error that HDAT2 Tool is showing me, is there a similar command-run program like chkdsk for this?

I will back up everything soon, and then format all.

Thanks

---

### Post by bapoumba on 2011-11-13
> **Atlus said:**
> The laptop is fairly new, I got in May/June this year, but it fell down once but was always working fine (sony vaio vpcea3s1e). The strange thing is that chkdsk corrected found errors, but still didnt change anything to the problem. I dont understand how to fix the MBR error that HDAT2 Tool is showing me, is there a similar command-run program like chkdsk for this?

I will back up everything soon, and then format all.

Thanks

[http://ubuntuforums.org/showpost.php?p=11226369&postcount=5](http://ubuntuforums.org/showpost.php?p=11226369&postcount=5)
Helped me decide this hard drive was dead..

---

