---
title: "X hangs after ubuntu 9.04 startup screen + frozen keyboard"
date: 2009-10-14
forum: General Help
---

### Post by mr.ivan on 2009-10-14
Hello there... after I turned on my asus X51Lseries notebook with solo OS Ubuntu 9.04 /fully upgraded/ I only got black screen with forzen keyboard... completly frozen system...

first thing that crossed my mind was " turn it off and on again", but this does not work for me:)  same with booting from recovery console...

those basic check utilities in recovery console + memtest shown completely OK system...
so I went curious about the X server and this seems to be problem...
now i'm running ubuntu 9.04 liveCD on the same notebook, so I don't think, that problem is in hardware /also native installed 'buntu  was running without any problems for some 4 months, until today.../

so I would like to get any suggestions about what to check, maybe about posting some outputs for better understanding of my problem...  also maybe it could be in sommething i installed before, so i would also happily get any suggestions how to work it out with liveCD maybe... 

thank alot for any reliable suggestions...

---

### Post by Giblet5 on 2009-10-14
When the system hangs, can you flip to one of the text consoles?

(Ctrl-Alt-F1 - F6)

---

### Post by mr.ivan on 2009-10-14
no, keyboard acts as if it was not connected.. no screen, no keyboard, no mouse... this happens only during starting the Xserver... /everything works with recovery console window / or when I boot system to shell

---

### Post by Giblet5 on 2009-10-14
From recovery mode, have you tried running the xfix option?

---

### Post by mr.ivan on 2009-10-14
no, will try that ... thanks for suggestion...

---

### Post by mr.ivan on 2009-10-15
thanks for suggestion, but still not working...
 
-running xfix from recovery console menu does'n work... i'm getting same result every time i try it...  
-running xfix as root in recovery console prompt gives me an error message 
>xfix not found

after trying:
>dpkg-reconfigure xserver-xorg
error comes up saying that xserver is not installed...
then i started looking for sommething more with
>dkpg --info xserver
which came with the same result -- xserver not found
after few more attempts still the same error ... any dpkg search related to x resulted as  not found...
BUT when i simply try 
>startx /or any other cmd for running X/
X starts, but then screen blinks few times and i'm at the start again 
/now tell me someone... how could i run gnome2 for 4 months without xserver installed?/ something is wrong with my machine or me :), but i can't quite figure it out... any suggestions? maybe what logs should i search for?... or what else should i check?

thanks for advice...

---

### Post by mr.ivan on 2009-10-15
so i finally figured out how to get my keyboard to respont... 
after booting straight to ubuntu and getting black screen i sent system to sleep and than I woke it up again... after ctrl-alt-F1 i was able to enter tty1 and than looked for Xorg.0.log..

only error line i found was:

[COLOR=Red]EE libDRI version is 5.0.0 but version 5.4.x is needed[/COLOR]

i found related posts here on forum but none of them as solved or with any relevant advices /there were some, but not working for me/ 

any advices?

---

### Post by mr.ivan on 2009-10-15
heh finally sommething worked!

after searching throught forum i found this wiki entry:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

which gave me some answers on my problem...
solution seemed to be simple /as it always is/ :

>sudo apt-get remove --purge xorg-driver-fglrx

and this was it! after applying it from recovery concole my system started working again 
but I still am not quite sure what was going on... i took this step thinking either i save my system or totally screw it.. :) 

if anybody who reads this has any suggestions about what was going on, please respond here or via email. thanks

---

