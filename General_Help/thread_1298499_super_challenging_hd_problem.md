---
title: "super challenging hd problem"
date: 2009-10-22
forum: General Help
---

### Post by GnubbyaBush on 2009-10-22
Hi all, have i got a treat today, one the hardest computer problems i've run across. I have a hard drive that is taking literally forever to boot..i mean hours upon hours to boot.
 
heres the deal, every install disk whether it be xp, vista, or ubuntu can see the hard drive, as well as the BIOs. The hard drive can be partitioned, deleted, ect. The intial problem i ran into with it is that the vista install said a file was missing and to run chkdsk. So vista install fails, i say to myself lets try xp, xp installed just fine but when it came time to reboot..nothing but a black screen with a blinking prompt.
 
i used the repair option in both the vista and xp discs and booted up the cmd line. then i tried chkdsk /r. I don't remeber the exact errors but i do remeber they where both different. Vista chkdsk says the drive cannot be locked because it is write protected. If i type in C: just to access the drive neigther would let me do it...so chkdsk is a screwed option.
 
so my friend in my cobol class tells me to use ubuntu it may fix the problem..well it really didn't. sure the install goes fine but when it reboots..blinking prompt black screen. I went to class and worked all day i come back and viola ubuntu booted!!!
so at least i know the drive isn't really fried. but i shut it down and now i'm realizing it must have taken hours up hours to boot.
 
I've gotten a couple clues, for instance even when i went to install ubuntu it didn't boot the hd right away, instead it gave something like this 0x0 "something" 0x0 "somethin" 0x0 "something" 0x0 frozen (the something where differnt aspects i don't remember.) then after 5 mins the install started. 
 
also acronis says failed to get dma waiting for dma then eventually started.. I feel as if this drive is just supper slow. i think that maybe the drive has some stuff that for some reason isn't getting deleted when i'm killing the partition
 
so my question is basically can i boot into the ubuntu live cd and do something. I'm not an ubuntu noob persay but i don't know any of the HD tricks such as chkdsk or fixboot equivlents (and again these windows commands failed to work from the install cds) fixboot worked, but did not solve the problem. If anyone can please help me it would be super apreciated, this is seriously stumping me.
 
 
 
ok update emask 00x00x00  0x4 timeout, the says something like 0x6 frozen..mentions dma...just booted!! so now i'm open to any suggestions of what i can do from the actual ubuntu install..i'm not using the live disk now i'm using ubuntu off the drive

---

### Post by Johnny B on 2009-10-22
theres not much you could do with the live cd if its a hardware problem.
try a different hard drive, if the problem persists, its a motherboard problem.

---

### Post by GnubbyaBush on 2009-10-22
oh noooos don't tell me that..yea but i've been suspecting this i actually do have another HD in the case but not hooked up and when i do hook it up it is having the same issues, so i guess thats a sign. But then again i've been putting these 2 drives together for a while..like physically they where out of the case for a lil while and i thought maybe they both got srewed up the same way. I could try a third drive but that is in a server that i care alot about and would be pissed if it got screwed up...do you think that wiping the partition with several passes would do the trick? and if i take the mobo route would a hard boot (out of the case) fix the problem maybe..i've only done this in the past to fix mobo's stuck at the initial flash screen.
 
yea i neglected to mention the ram the m2ne mobo have worked great together in the past..i really think its the fact these two drives are ide b/c my sata drive boots just fine.

---

### Post by Bucky Ball on 2009-10-22
Sounds like you might have one dead hard drive. Definitely hardware issue. If the other drive is having similar problems you have a motherboard issue (as mentioned) or possibly ram. You could try changing the cable and see if that works in the first instance. If not, dig deeper.

---

### Post by GnubbyaBush on 2009-10-23
yea i'm havin to travel to hell and back on this one. i have another comp (the server) with ubuntu installed I plan on hooking up the drive to that now and do a badblocks on it..not to sure what its adress will be like /dev/sd?   i think sdc or something not to sure. Right now i just tried to boot cmd line and do a chkdsk c: /r and says cannot open volume for direct acess when i just type in c: it says system cannot find the drive specified, even thought it sees it during vista install. So now for the badblocks test. 
 
also i should mention when ubuntu finally boots the drive it gives a couple drdy errors which i know is bad. so we will see what the badblocks test has to say

---

### Post by GnubbyaBush on 2009-10-23
oh no!!! lol its the board ahh god painfull nearly brand new mn2e. IDE inputs on a board are only supposed to be missing 1 pin right? cause the ide on the problem board is missing 2. I guess the next question is, can i fix this at all? haha this really is a bad problem

---

