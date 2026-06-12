---
title: "NTLDR missing"
date: 2011-08-11
forum: General Help
---

### Post by Killerbogan on 2011-08-11
hey guys it my first post so i just want to thank you for listening:popcorn:

ok the problem i have is this i have created a linux live usb or more accurately persistent usb i used LILI Usb creator my usb works fine on my netbook with no errors what so ever but when i take it to my desktop pc thats where the problems begin i am getting an error that says NTLDR is missing press ctrl+alt+delete to restart if i pull the usb out and reboot my windows vista runs fine but when i attempt to boot from my stick i get this error also to add to this problem i have had my desktop running on a live stick before with no errors i ran it like 2 days ago so i think it must have been a recent change in my computer or the stick but even when i created a new stick i still get the error i am using 11.04 natty 

thanks for your help :)

---

### Post by Bart92 on 2011-08-11
> **Killerbogan said:**
> hey guys it my first post so i just want to thank you for listening:popcorn:

ok the problem i have is this i have created a linux live usb or more accurately persistent usb i used LILI Usb creator my usb works fine on my netbook with no errors what so ever but when i take it to my desktop pc thats where the problems begin i am getting an error that says NTLDR is missing press ctrl+alt+delete to restart if i pull the usb out and reboot my windows vista runs fine but when i attempt to boot from my stick i get this error also to add to this problem i have had my desktop running on a live stick before with no errors i ran it like 2 days ago so i think it must have been a recent change in my computer or the stick but even when i created a new stick i still get the error i am using 11.04 natty 

thanks for your help :)

If you recently changed hardware, or a BIOS setting change, change it  back. 
This could be as simple as a usb stick or external hard drive being plugged in.
....
Try to create a Ubuntu live CD

---

### Post by westie457 on 2011-08-11
> **Killerbogan said:**
> hey guys it my first post so i just want to thank you for listening:popcorn:

ok the problem i have is this i have created a linux live usb or more accurately persistent usb i used LILI Usb creator my usb works fine on my netbook with no errors what so ever but when i take it to my desktop pc thats where the problems begin i am getting an error that says NTLDR is missing press ctrl+alt+delete to restart if i pull the usb out and reboot my windows vista runs fine but when i attempt to boot from my stick i get this error also to add to this problem i have had my desktop running on a live stick before with no errors i ran it like 2 days ago so i think it must have been a recent change in my computer or the stick but even when i created a new stick i still get the error i am using 11.04 natty 

thanks for your help :)

Hello and welcome to the Forums.

What version of Windows is on the netbook? Is it XP? 
NTLDR missing is a Windows error for XP if my memory is working. Vista might throw out the same error, cannot be sure though.

Do you have 11.04 working on the desktop pc? And is the problem only on the desktop pc? 

Now burn a LiveCD for use on the desktop pc. Boot into it remembering to set the bios to look for the cd drive first, and choose 'try' at the welcome window.
When the live desktop appears start Firefox and go to [here]("http://bootinfoscript.sourceforge.net/"). Download and usage instruction are here as are instructions on how to post the output.
Before you run the program plug the usb stick in. That is where the information we will be looking for is.

We might be able to repair the usb's mbr - I have never tried but hey a new challenge.

If we cannot fix this you can always use the Startup Disc Creator that is available on the LiveCD. So far that has always worked for me.

---

### Post by haqking on 2011-08-11
> **Killerbogan said:**
> hey guys it my first post so i just want to thank you for listening:popcorn:

ok the problem i have is this i have created a linux live usb or more accurately persistent usb i used LILI Usb creator my usb works fine on my netbook with no errors what so ever but when i take it to my desktop pc thats where the problems begin i am getting an error that says NTLDR is missing press ctrl+alt+delete to restart if i pull the usb out and reboot my windows vista runs fine but when i attempt to boot from my stick i get this error also to add to this problem i have had my desktop running on a live stick before with no errors i ran it like 2 days ago so i think it must have been a recent change in my computer or the stick but even when i created a new stick i still get the error i am using 11.04 natty 

thanks for your help :)

NTLDR means that the system is trying to boot windows but cant see the partition for the boot files.

This usually happens when partitions get messed up or boot devices, or the boot.ini gets changed somehow.

So when you try to boot to your Linux based USB you get the ntldr message ?

---

### Post by Killerbogan on 2011-08-12
> **Bart92 said:**
> If you recently changed hardware, or a BIOS setting change, change it  back. 
This could be as simple as a usb stick or external hard drive being plugged in.
....
Try to create a Ubuntu live CD

i have not changed any bios setting's i just press f12 and access the boot menu when i boot i boot from USB-HDD :confused:

> What version of Windows is on the netbook? Is it XP? 
The Netbook is running WIN 7 the problem is with the desktop it is running windows vista
> Do you have 11.04 working on the desktop pc? And is the problem only on the desktop pc? i have had 11.04 running on the desktop of of a diffrent usb and the one i am using at the moment that is failing with the ntdlr error msg and yes the problem is only with the desktop it is running on WIN vista perfectly :D
> Now burn a LiveCD for use on the desktop pc. Boot into it remembering to  set the bios to look for the cd drive first, and choose 'try' at the  welcome window.
When the live desktop appears start Firefox and go to [here]("http://bootinfoscript.sourceforge.net/"). Download and usage instruction are here as are instructions on how to post the output.
Before you run the program plug the usb stick in. That is where the information we will be looking for is.
I wish i could but my drive is broken :(
> So when you try to boot to your Linux based USB you get the ntldr message ?Yes my vista and 7 work perfect when im not trying to boot from USB the problem is i HATE windows :D
im thinking it may be the usb stick as i see this as the only vairable unless there has been someone fiddling with my system :(

---

