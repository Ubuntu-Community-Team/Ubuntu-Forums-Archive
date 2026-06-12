---
title: "Installing Ubuntu"
date: 2006-04-19
forum: General Help
---

### Post by aftershock on 2006-04-19
Hey, It is not letting me install it.  I'd imagine I would need a boot disk.  I downloaded one fromt a post and the computer said "non system boot disk please replace and strike any key when ready"  Any advice?
-I appreciate your posts, Aftershock

---

### Post by gpeck157 on 2006-04-19
[QUOTE=aftershock]Hey, It is not letting me install it.  I'd imagine I would need a boot disk.  I downloaded one fromt a post and the computer said "non system boot disk please replace and strike any key when ready"  Any advice?
-I appreciate your posts, Aftershock[/QUOTE]

I would download it directly from Ubuntu, then burn it with Nero or other ISO burning software to make certain the disk is bootable. Also, make sure your CD/DVD Rom drive is set as your first boot device. It could just be a bad disk too. Good luck...

Glen

---

### Post by aftershock on 2006-04-19
Hey,
I tried that I have the first boot at CD-ROM but it won't boot from the CD-ROM.  I am not sure what the problem is.  It won't detect any of my hardware either.  I have a completely blank HDD that I am installing it on.. Here's screenshots of the BIOS settings if this helps with an answer ([www.geocities.com/aftershock_024/bios](www.geocities.com/aftershock_024/bios)).
-Thanks!
Aftershock

---

### Post by Ptero-4 on 2006-04-20
Hi. aftershock, I just saw your BIOS screenshots and wonder: Doesn't need your HD and CD drives to be listed among the four "IDE" entries (second screenshot)? I ask b/c they say "none" and IIRC they should list (at least the primary and secondary masters) the names of your HD and CD drives.

---

### Post by gpeck157 on 2006-04-20
[QUOTE=aftershock]Hey,
I tried that I have the first boot at CD-ROM but it won't boot from the CD-ROM.  I am not sure what the problem is.  It won't detect any of my hardware either.  I have a completely blank HDD that I am installing it on.. Here's screenshots of the BIOS settings if this helps with an answer ([www.geocities.com/aftershock_024/bios](www.geocities.com/aftershock_024/bios)).
-Thanks!
Aftershock[/QUOTE]

Hey Back,

Ptero-4 is correct. You should be able to see your drives in the BIOS, otherwise nothing will install.

G

---

### Post by aftershock on 2006-04-20
Hey,
First of all I'd like to comment all of you on all the posts.  I am in a lot of forums, and NEVER got help this fast.  Second, That's what I was wondering also.  I tried to get them listed there and I couldn't.  Any advice?
-Thanks!

---

### Post by gpeck157 on 2006-04-20
[QUOTE=aftershock]Hey,
First of all I'd like to comment all of you on all the posts.  I am in a lot of forums, and NEVER got help this fast.  Second, That's what I was wondering also.  I tried to get them listed there and I couldn't.  Any advice?
-Thanks![/QUOTE]

Just make sure your cables are connected properly to the drives, and that the connectors are seated properly on the motherboard. Also make sure your harddrive is set as "master" and put them both on different channels. (Not required but easier on powerup.) After everything is hooked up, power it up. The drives should be recognized by the bios. If this does not work, I would start looking at the hardware and make sure each item is working as it should. 

Glen

---

### Post by Twisted1616 on 2006-04-21
I'm just a noob here but I've had the problem of BIOS not detecting my HDDs or CD/DVD drive...  what you should do is check that S-ATA is set as primary but also select enable both (S-ATA and P-ATA) in the BIOS. It should be under IDE connections that is under Chipset features... or something like that (or so it is in my BIOS).
Know it's not a very precise help but it's bin a while since I was in the BIOS.. although you aughta be able to find it and figure it out... I did. :)
I will reboot though and check it out better now and post a more descent answer if this aint enough for you.

Ok. here's the better version:  go to BIOS and do the following:
1) find "Integratd Peripherals" and enter that...
2) there select "On-Chip IDE configuration"..
2.a) there select in "ATA configurations"  S-ATA only..
2.b) and select in "P-ATA keep enabled"  yes..
2.c) and select in "P-ATA channel selection"  both..
2.d) finally select in "S-ATA ports definition"  p0-1st./P1-2nd.
3) Save and exit BIOS
4) Automatic reboot (happens automatically :D  dont do anything here)
Done

oh, but I ought to mention that this is done with referance to my own BIOS and yours might be different... although it shouldn't be a lot different and the main part of this should apply anyway. :)

---

### Post by aftershock on 2006-04-21
Hey, Thanks for all the help.  I finally got it workin.  Don't ask how, haha all I did was just change how stuff was plugged in, reformat the HDD, and then it finally worked.  I'm not exactually sure what I all did but it works now.  In fact I am writing this on my new ubuntu system right now.  Thanks again for the help!!
-Aftershock

---

### Post by gpeck157 on 2006-04-21
[QUOTE=aftershock]Hey, Thanks for all the help.  I finally got it workin.  Don't ask how, haha all I did was just change how stuff was plugged in, reformat the HDD, and then it finally worked.  I'm not exactually sure what I all did but it works now.  In fact I am writing this on my new ubuntu system right now.  Thanks again for the help!!
-Aftershock[/QUOTE]

Congrats! Enjoy...

Glen

---

