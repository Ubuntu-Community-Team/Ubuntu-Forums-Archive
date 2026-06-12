---
title: "help me get back to windows again"
date: 2006-04-19
forum: General Help
---

### Post by Vlatko on 2006-04-19
hello!

i have one sata drive that is the master and has xp on it. one ide drive set as slave and has all my music/movies/stuff on it. i pluged in a 3rd ide drive, set as slave, and installed ubuntu on it.

the thing is i wanted to give linux a shot. i did and i'm afraid it was not for me. so i unplugged the newd drive and hoped everything would be as before. but no. grub started as well only this time he gave some "error 17" and i couldn't boot anything. unless i replug my new drive and boot from there. linux isn't for me so i want to get back to my xp and system before.

someone on the ubuntu forums said grub has taken over my "mbr" and that i need to fix it in order for windows to boot properly. so i did as i was said and put my xp cd in, booted from it, went to repair windows, entered the told command "fixmbr". 

all it did was is not starting the grub anymore, but right after the first screem i get a few lines of some windows errors. windows has detected some hardware issues, something was not connected properly...and i don't know what else.

any ideas?

help me!!  ](*,)

---

### Post by Ulokye on 2006-04-19
Linux is for everyone ;) 

Naa maybe not okey this is what you do (if I recall correctly I have not used XP in 2 years mind you)

1. pop a boot cd in your drive to get the dos promt.
2. type "fdisk /mbr"
3. run the windows xp cd and choose repair system.
4. I don't recall the command look for fix "boot order" or fix master boot record.
5. reboot and enter windows. 

Oh, and switching to linux is not done in a blink of an eye it takes time and some work to learn the new commands, the comunity is allways open to help, thought you should know if you wish to try it again sometime :) 

Give the GPF my best:twisted: .

-Ulokye

---

### Post by Vlatko on 2006-04-19
[QUOTE=Ulokye]Linux is for everyone ;) 

Naa maybe not okey this is what you do (if I recall correctly I have not used XP in 2 years mind you)

1. pop a boot cd in your drive to get the dos promt.
2. type "fdisk /mbr"
3. run the windows xp cd and choose repair system.
4. I don't recall the command look for fix "boot order" or fix master boot record.
5. reboot and enter windows. 

Oh, and switching to linux is not done in a blink of an eye it takes time and some work to learn the new commands, the comunity is allways open to help, thought you should know if you wish to try it again sometime :) 

Give the GPF my best:twisted: .

-Ulokye[/QUOTE]
erm..i only have the original xp cd. how do i get to the ms dos prompt with it?

yeah i believe you. this is the 2nd time i tried. it's just so damn hard. :D all these things are confusing me, so many problems. but i won't give up so fast. a little more blue screens of death, ctd's and i'll be back here trying in no time. :D

---

### Post by Vlatko on 2006-04-19
please people i'm gonna get murdered soon if i don't resolve this. :D

---

### Post by dmizer on 2006-04-19
you have to make sure you boot to the windows xp cd.  then choose the "repair" option.

something like this i believe:
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by Ulokye on 2006-04-19
[www.bootdisk.com](www.bootdisk.com) should solve your problem with not having a bood cd

If I recall corectly FIXMBR needs to have a clean MBR to write to (but that might just have been me remembering things that just isn't right, getting old maybe?) anyhow if it doesn't work to do what Dmizer said, do the fdisk /mbr part and redo what Dmizer said.

---

### Post by dg_w on 2006-04-19
Ok

Make sure the correct hard drives are in the PC as they were (before you tried Linux)

Boot the pc from the Original Windows XP CD
At the point where you have 2 or 3 options (to install etc) select the option to enter the recovery console ( I think its R )
This will drop you into a command line enviroment.
You need to choose the Windows partition (normaly press 1)
Give the administrator password for windows
type fixmbr
answer yes to confirm
reboot

You should now be back into windows :)

---

### Post by Vlatko on 2006-04-19
thanks for the help guys. BUT..that's exactly what i did. unpluged the linux drive, started the recovery console, entered fixmbr, confirmed yes, wrote exit and the pc restarted.

i thought that was it but no... after the screen where it lists all drive and stuff, and just after the boot from cd option passes, cause there is no cd in it, i get a error. windows won't boot, hardware not connected properly...5,6 lines, can't remember them all and i'm at work now so can't check.

is there anything else i can try? apart from the fixmbr option? perhaps the fix boot option? what does it do? i wanted to try it as well but it asked me are you sure you want to write boot sector to c: drive or something like that. i would have said yes but the c drive is the one where i keep ALL my important stuff, d: drive is the windows one, so i didn't want to mess with it. is there a risk of loosing data with these fixmbr, fixboot options?

---

### Post by dmizer on 2006-04-19
[QUOTE=Vlatko]perhaps the fix boot option? what does it do? i wanted to try it as well but it asked me are you sure you want to write boot sector to c: drive or something like that. i would have said yes but the c drive is the one where i keep ALL my important stuff, d: drive is the windows one, so i didn't want to mess with it. is there a risk of loosing data with these fixmbr, fixboot options?[/QUOTE]
do you know which disk windows booted from before?  if you do not have windows installed to the c: drive, you have performed a non standard install, and you may be out of luck.

if there are no system related files on the c: drive, then remove it as well.  if your important data is there, just remove it to protect it.  then try fixboot or fixmbr again ... at least that way you have all your important data safe.

if you have any system data (ie ... installed programs) on the c: drive, then you are probably out of luck.

---

### Post by dg_w on 2006-04-19
Just a guess

But it sounds like you ide drives are not in order ?
Ie the master, slave setups.
The pc is trying to boot from a non system partition ?
Plug in the linux drive back in and try the fixmbr again ?
Check in the BIOS the boot options ?
Is the IDE master the windows drive, and booting first ?

If all else fails:
Un plug ALL but the drive with Windows on it
Make sure that drive is IDE 1 Master
CD rom id IDE 1 Slave
Boot from cdrom and try the fix mbr 

That should get you into windows, then power down and add the D drive as IDE 2 Master 

:) 

Let me know how u get on

---

### Post by Vlatko on 2006-04-19
[QUOTE=dmizer]do you know which disk windows booted from before?  if you do not have windows installed to the c: drive, you have performed a non standard install, and you may be out of luck.

if there are no system related files on the c: drive, then remove it as well.  if your important data is there, just remove it to protect it.  then try fixboot or fixmbr again ... at least that way you have all your important data safe.

if you have any system data (ie ... installed programs) on the c: drive, then you are probably out of luck.[/QUOTE]
windows booted from a sata disk, D: drive. i also have a slave ide drive, C: drive, which has all my data on it. no programmes whatsoever.

i will try and unplug it as well. then see what is done. 

but what do you mean non-standard install? last 2 years this hard disk(c: ) was the one with all my stuff and (d: ) was where the windows was installed. don't see how can that be a problem.

if i format the d: drive with windows and create a fresh install will the problem be fixed? i mean the boot sector or whatever?

---

### Post by Vlatko on 2006-04-19
[QUOTE=dg_w]Just a guess

But it sounds like you ide drives are not in order ?
Ie the master, slave setups.
The pc is trying to boot from a non system partition ?
Plug in the linux drive back in and try the fixmbr again ?
Check in the BIOS the boot options ?
Is the IDE master the windows drive, and booting first ?

If all else fails:
Un plug ALL but the drive with Windows on it
Make sure that drive is IDE 1 Master
CD rom id IDE 1 Slave
Boot from cdrom and try the fix mbr 

That should get you into windows, then power down and add the D drive as IDE 2 Master 

:) 

Let me know how u get on[/QUOTE]
i think that is a good guess. :D as you probably noticed by now, i'm not too into this hardware stuff. i never really got the hang of those slave/master things and those jumpers on hard disks.

before the linux disk it was like this i think:
channel 2: sata drive, windows drive, set as master
channel 1: dvd/rw, set as master
channel 3: ide drive, with stuff on it, set as slave

hard disk boot priority was set as follows:
1. the ide drive without windows
2. sata drive with windows

i guess that looks wrong but that worked. if i changed the order and put the windows drive on top and the drive with stuff second it would not boot. i would get a error "NTLDR is missing". but when i changed the order it could boot properly.


something tells me i'm screwed... ](*,)

---

### Post by dg_w on 2006-04-19
I think what were getting at:
"Normal" C drive (MASTER) holds the operating system and boot record
Slave "D" drive would have the Data ..
Though with sata and IDE it kinda throws that up in the air , Sata 1 and 2  and IDE master and slave.

With windows installed on SATA. (and the error you are getting) I think you will find that windows is installed on sata though the boot record is being read from the IDE drive... ?

---

### Post by Vlatko on 2006-04-19
[QUOTE=dg_w]With windows installed on SATA. (and the error you are getting) I think you will find that windows is installed on sata though the boot record is being read from the IDE drive... ?[/QUOTE]
that could be the case. if so, can i somehow remove the boot record from the ide drive with the stuff on, without formatting it of course, and put the boot record on the sata with windows installed?

---

### Post by dg_w on 2006-04-19
Umm I dont think so ..

Running fixmbr on the IDE drive will "I THINK" setup that drive to be the
booted drive (so your sata does not boot)

You have probably tried it, but running fixmbr on the SATA ? (other drives unplugged) Though I doubt this would work as the windows installation is expecting IDE1 ...
Umm,,
Run on all !  lol  
Seriously I would have to look into it ...  But I can see the problem you are having and why its not working ..

IDE 1 master /  Sata sata1 /  cdrom IDE I slave
Does r console find the partition ok ?
Fix MBR on IDE ..
Boot from IDE

What version of XP are you running ..  You may well be able to re-install over the top (so not loosing DATA) but it has been so long sinceI tried it I can not rember.

Keep the ide data disk unplugged till you are done .....
Re-install Ubunto and login to windows using grub :)

---

### Post by salman16 on 2006-04-19
i have the same problem with him i just instail ubuntu yesterday and in boot screen its shows 

ubuntu,
ubuntu update,
i cant remember the other 1

and its didint show the windows anyone knows why?:( 

Thanks....

---

### Post by Vlatko on 2006-04-19
just got back home. i plugged the third drive, the one that had linux on it, and windows booted immediatelly. when i unplug it i can't boot to anything anymore.. i'm really stumped at this....

---

### Post by dmizer on 2006-04-19
your problem is very similar to one i had a while back.

1 - windows expects to boot from the master disk.
2 - windows expects the master disk to be drive c:

standard install means that you installed windows to drive c: and drive c: is the master drive.  if you have reconnected the drive with ubuntu on it, and now windows boots, you definately have some very strange hardware configuration that will prove to be difficult to reconfigure and correct.

in some configurations, it is not possible to boot from a hardware device that is not master.  your boot record may have been on the c:, it may have been on the d: drive, but there's really no way to tell for sure without risking your data.

my suggestion is this.  reinstall windows on the sata drive (without the ubuntu drive or your critical data drive connected), then reconnect your ide drive (with all your critical data) and you should be able to view it again.

as a side (but important) note ... most windows programs' install wizards are setup to install on the c: drive.  so unless you manually changed the install location for your programs, they have likely installed themselves onto your drive with all your critical information.

sorry to say, but your problem is very complex, and it will take time to completely resolve.

---

