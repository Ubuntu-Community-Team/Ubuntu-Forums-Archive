---
title: "Bios Problems after updating bios"
date: 2009-12-15
forum: General Help
---

### Post by gawadelnil2002 on 2009-12-15
I have asrock N73v-s ,its good motherboard works good with linux but i wanted to flash my bios
I had dos bootable cd that can run on boot and i used it to flash my bios
after flashing my bios using AFUDOS ,I restarted my system but it was :( and still damned
my bios update failed
It was making alot of beebs then it stopped beebs and it was dark all on screen my monitor even didnt start , no Asrock splash as i used to see nothing except darkness
and then without seeing any line on screen my gdm appears and ubuntu opens
I thought my system all gone but I'm happy now that at least I can access forums here

I googled alot how to repair bios and fix mixed up bios updates
i saw alot of ways butnothing willwork cause I can't boot anything else excpet the hard disk i cant log into the bios itself cause I dont see anything when it opens even dos I cant see it
i cleared cmos by jumper way and by removing battery it didn't change anything

 the only solution for me is to put my bios in another motherboard looks like mine have windows installed on it

My friend use the same version of my motherboard and I'm going to do that but I don't how

  I don't where is my bios in this picture and how to replaces it
usually when i look at boards i can recognize the bioses but in this I dont know how
and I have some thoughts but I want to  ask first I don't want to damage anything else
[IMG]http://www.asrock.com/mb/photo/N73V-S%28Enlarge%29.jpg[/IMG]
i think its the one in middle of the board but I'm not sure and if im right how to take bios chip from it
thank you for listening





Update: I see that I can install open bios or any free bios on my motherboard and i see it will be better for linux But i dont how is the instructions too to install openbioses on my motherboard

Update: Or can I update bios using native linux software instead of AFUDOs that work in dos or in windows ????

---

### Post by Carborundum on 2009-12-15
AFAIK BIOS are not usually removable. The thing in the middle of your motherboard is the chipset. Your BIOS are not broken though, as you would not be able to boot at all if they were. My first guess would be that the new version has some kind of quick-boot feature that skips the BIOS splash screen, but the beeping does seem suspicious. Google "troubleshooting  + your motherboard model", as the beeps almost certainly mean something. You should be able to figure out what's wrong by listening to them.

---

### Post by gawadelnil2002 on 2009-12-15
> **Carborundum said:**
> AFAIK BIOS are not usually removable. The thing in the middle of your motherboard is the chipset. Your BIOS are not broken though, as you would not be able to boot at all if they were. My first guess would be that the new version has some kind of quick-boot feature that skips the BIOS splash screen, but the beeping does seem suspicious. Google "troubleshooting  + your motherboard model", as the beeps almost certainly mean something. You should be able to figure out what's wrong by listening to them.
So my bios cannot be taken outside the board and be reprogrammed as u tell me now 
and i saw now what I used to update bios wasnt new version it was old version and I did mistake with updating bios with it , and it is not only my bios setup that i cant see anything excpet the gdm i cant see ubuntu splash i cant see when i press del to go to bios setup i cant see the bios setup ,bios splash i cant see anything  i cant see i thank god that it opens gdm after this long black screen
I don't know what to do now?

---

### Post by eriktheblu on 2009-12-15
If you physically disconnect your HDD, can you then boot from CD-ROM?

---

### Post by gawadelnil2002 on 2009-12-15
> **eriktheblu said:**
> If you physically disconnect your HDD, can you then boot from CD-ROM?

I did that and I saw my CD-Rom flashing and heared the cd rotating inside as it boot from it but the dos page is not appearing on the screen I know it booting and it is On dos now but i cant see anything and when i connect the hard disk it boots to gdm after 5 minutes of black screen without any writing on monitor even ubuntu splash i dont see it , the monitor opens up on gdm directly :(, god i shouldn't do that

---

### Post by jocko on 2009-12-15
Sounds like the graphics card is not properly initialized by the bios?
Do you use the onboard graphics card? In that case test with a pci-e card. If you already use an pci-e card, try the onboard graphics...

---

### Post by gawadelnil2002 on 2009-12-15
> **jocko said:**
> Sounds like the graphics card is not properly initialized by the bios?
Do you use the onboard graphics card? In that case test with a pci-e card. If you already use an pci-e card, try the onboard graphics...
I think that too but i dont have spare pci-e card my card is built in nvidia 7050 geforce integrated
There is away to flash bios im sure but i dont know how ?????
for linux i googled i didnt find any thread to flash bios inside dos 
but i think if they cant flash bios inside linux because AFUDOS is not working in linux they might can flash bios with free bioses like openbios or any other kind of free bios
i readed about openbioses on internet and how much it is good?

---

### Post by jocko on 2009-12-15
I don't think you can flash your bios from within linux. Either try to borrow a pci-e card and hope that it works well enough for you to flash your bios from dos, or if your friend that has an identical motherboard have windows installed you *may* be able to boot to windows from his hard drive and use asrock's windows tool for flashing the bios.
Otherwise you probably need to get professional help...

Edit: There is a program called [flashrom]("http://www.flashrom.org/Flashrom") (sudo apt-get install flashrom) that *may* work (or may make things much, much worse).
Your motherboard is not listed as supported, but that probably just means no-one has tested it... And I don't recommend testing it...

---

### Post by gawadelnil2002 on 2009-12-16
> **jocko said:**
> I don't think you can flash your bios from within linux. Either try to borrow a pci-e card and hope that it works well enough for you to flash your bios from dos, or if your friend that has an identical motherboard have windows installed you *may* be able to boot to windows from his hard drive and use asrock's windows tool for flashing the bios.
Otherwise you probably need to get professional help...

Edit: There is a program called [flashrom]("http://www.flashrom.org/Flashrom") (sudo apt-get install flashrom) that *may* work (or may make things much, much worse).
Your motherboard is not listed as supported, but that probably just means no-one has tested it... And I don't recommend testing it...
I will borrow hard disk in the next few hours and try it, it may open windows :) or it may not :( , I'll see what my luck will put me through
Flashrom didn't recognize my bios so it is not helpful

---

### Post by gawadelnil2002 on 2009-12-16
I tried pci viga card and that didnt help
i dont know what i have to do now for real i dont know anything i dont have idea excpet one idea ( can i install free bios version) like openbios or coreboot or anyother open free bios using linux
 
Edit : I Discovered when I was reading That is kind of bioses is not real bioses can be installed on Machine instead of asrcok bios So My problem was solved by buying  a new mother board and the old mother board is in the company under repairing :)
and For anybody was seeing me an idiot just forgive a beginner

---

