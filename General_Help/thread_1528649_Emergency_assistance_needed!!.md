---
title: "Emergency assistance needed!!"
date: 2010-07-11
forum: General Help
---

### Post by jackechanprime on 2010-07-11
My god i feel like an idiot.

I just (basically) completely uninstalled my OS by accident.

In synaptic package manager i selected to completely remove volume control (which had been going haywire for god knows what reason) with intent to immediately reinstall. i didn't put 2 and 2 together when it said it'd remove all related files including the kernal... hal... restricted drivers... >_< everything got uninstalled.

network manager crashed...

lord knows why, but i decided to try my luck with restarting (what was left) of the system...

now i'm looking at a boot screen of:

loading grub...

error 15: file not found.


;_; what do i do?

did i totally f*** myself over and have to just make a boot disc and reinstall the os? or can i just "put the pieces back together" as it were and reinstall with a 'sudo aptitude update' once i get network up again?

heeeeeeelp??

~Q

---

### Post by bodhi.zazen on 2010-07-11
Your data may be intact, but sounds as a reinstall is in your future.

You could try booting the live CD and mounting your ubuntu partition in a chroot, then install ubuntu-desktop. Assuming ubuntu s in /dev/sda1

```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt /bin/bash
apt-get install ubuntu-desktop
```

---

### Post by jackechanprime on 2010-07-11
I'll get a new live CD in the burner now. lord (and possibly a leprechaun) only knows where my original is....

thanks a ton.

~Q

edit: and yeah, everything should be in SDA1

---

### Post by jackechanprime on 2010-07-11
any way i can possibly bring up a rudimentary lan connection on my system and do an update while the cd is in the works?

somehow i doubt it.....

~Q

---

### Post by Agent24 on 2010-07-11
I think recovering your files and then reinstalling will be the best course of action.

Try repairing the OS and you could end up with all sorts of weird problems.

---

### Post by jackechanprime on 2010-07-11
uh... minor problem... i dont really have any external storage mediums available atm... just an ancient 512mb flash drive and a handful of cd's. Is there a way to reinstall without wiping all the files? not that there's anything excessivly important on the system (no gigs and gigs of pics and 'irreplaceable memories' and the usual) but my system has some wierd quarks to it *anyway*. (see the thread about my wireless problems from like 4 years ago.) i really dont want to go through getting basic hardware online again... :sad:

---

### Post by jackechanprime on 2010-07-11
by the way, this reminds me,

the fix that eventually wound up working and getting my oddball wi-fi card working comes undone every time i install a kernal update, so i've been installing all updates -except- the kernal as a rule for quite some time now. i did do a kernal update about a month ago (for the first time in a good year), but every time i do i have to deal with hooking up a LAN line and hunting down and completely re-creating the fix.

the error the same time is the same, i forget the exact text, but i think it was something like

error unknown symbol (#)

to fix it (the only way i know how) i have to purge the driver and reinstall it. is there a bug fix to stop this from happening for future reference?

~Q

---

### Post by HermanAB on 2010-07-11
Hmm, it is for these type of screw-ups that it is useful to always create a separate /home partition.  Then, when the inevitable happens and you need to re-install, you just do it without formatting /home and you are back up and running in about 30 minutes.

---

### Post by jackechanprime on 2010-07-11
new problem...

the computer wont read the live cd.

wtf. i've burnt about 6 cd's with various programs and multiple options over the past 3 1/2 or so hours, and the computer wont read any of them, as if the cd-drive weren't even there. did i scramble the things brains more thoroughly than i thought?

it tries to load grub, seems to do fine, then brings up:

error: 15

file not found.

every blasted time.

yes i've f-d around in the bios and changed boot sequence. no effect. i even physically removed the hard drive so the system would have no choice but to deal with the cd...

"no bootable device... yadda-yada"

so, either my cd drive is busted, my computer is totally baked (command line from boot prompt seems to be only avenue here), or i have no talent at burning cd's.

why do things always pan out this way for me =.=

~Q

---

### Post by WorMzy on 2010-07-11
Since the CD drive burnt the CDs, I expect it's fine. Try pressing various F# keys during POST to bring up a list of bootable devices (you may need to press Esc or Del instead of an F# key, it varies from motherboard to motherboard), and boot from the CD drive.

---

### Post by jackechanprime on 2010-07-12
sorry, wormzy, i was using another terminal to burn the cd's. multiple computer household, but the other wasn't technically mine to use. sorry i omitted that fact. the computer in question was completely incapable of so much as functioning as a calculator at the time, let alone burning a cd.

so anyway, issue is now resolved. once i got the live cd to finally detect via the code:

find (fd0,0)

entered in command line at the boot screen kernel selector prompt, which took me about 5 hours to figure out how to do... (why in lords name is there no 'list devices' command in that boot prompt?) i then followed .zazin's instructions above. Data recovery was immediately halted as the system could not resolve permissions, and apparently i didn't even have sufficient permissions to even read the majority of anything in the Sda1 directory, but it was all there. I was getting tired and cranky by this point, so i just installed ubuntu and wiped everything. no lost love, to be completely honest.

luckily for me, wireless now works out of the box, which certainly made my (by this point, dawning) day a little brighter...

=.= however...

the problem that got me into this mess in the first place still remains. my sound system is -still- on the fritz. Specifically, I cannot get it to run sound generated by a Java Runtime Environment applet run within firefox. This is overtly disruptive to my life and daily plans, to the point of generating full willingness to abandon ubuntu or even buy a new computer in order to get access a browser that will run the sound from this single darned java app.

If anyone knows a way to forcefeed my speakers a programs sound thread, i'd love to know.

currently, while running the app, volume control notes to me that

"no application is currently playing or recording audio"

excuse my minor angst for phrasing the question thus, but what's the simplest way to shove it's face into it?

please and thank you.
~Q

---

### Post by brandon dorney on 2010-07-12
if i where u i would reinstall because putting everything back together would be agravating

i would do what the other dude said is put in a live cd and boot up

then i would back up any data u hade on the filesystem on a flash drive that u wana keep


sorry if this didnt make sence i just got back from the dentist and im kinda loopy from the pain killerz LMAO

---

### Post by jackechanprime on 2010-07-12
to clarify:

reinstall complete after severe complications; all data lost. (dont care)
system running better than before now.

new problem:

java (and perhaps other) audio failures remain. (as clarified above)

need help with getting java to run audio, please.

thanks a ton all!! :)

~Q

---

