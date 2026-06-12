---
title: "Help please!"
date: 2010-07-29
forum: General Help
---

### Post by Rhye on 2010-07-29
OMG im sick of this ive been unable to use my computer for almost 3 days and I need it for work.

I installed linux to my xp computer.

I have one hard drive that is 500gb

its partioned to:
440gb {XP} + 60gb {Ubuntu}

Grub will not boot to xp it only boots into linux. i mostly use xp. and even if i wanted to change to ubuntu i only have 60gb of space to do so >.<

and a further notice... i dont want to change to JUST linux.

CAN SOMEONE PLEASE HELP!?

---

### Post by Rhye on 2010-07-29
AND ALSO

someone told me to get into gparted and unmount the xp drive and check it... i did so and got errors, the errors are attached here.

AND NOW i cant mount my xp drive anymore or see my files >.<

---

### Post by Rhye on 2010-07-29
is there ANY WAY i can just remove GRUB and LINUX from my computer and try a fresh install!! please!

---

### Post by Rhye on 2010-07-29
OMG honestly no one is helping me >.< i want to be rid of linux. someone help me do this.

---

### Post by nothingspecial on 2010-07-29
Calm down

Stick your windows disk in and it will wipe ubuntu and grub for you.

---

### Post by Rhye on 2010-07-29
My pc will not boot from cd. There is my main problem. I need another way around this :/

---

### Post by nothingspecial on 2010-07-29
Like I said, calm down.

You have ubuntu. Use it for now. It is a fully functioning opperating system.

Tomorrow, or later in the week, get an external disk drive and solve your problems.

You are not going to get much help on a linux forum with what you have posted so far.

---

### Post by Rhye on 2010-07-29
Sorry guys... I do love linux it is a very wellmade OS and I think it is even better then xp but as a first time experience you can imagine I'm freaking out a bit :P

I will continue to put this on my pc until it works but I need support to fix my problem

I still don't no how to fix it :/

---

### Post by kerry_s on 2010-07-29
go to accessories-> terminal
type-> sudo update-grub
reboot

---

### Post by jsyl on 2010-07-29
If what kerry_s doesn't help you, download Super Grub Disk and burn it to a CD. 
[http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)

---

### Post by jsyl on 2010-07-29
I just read that your PC can't boot from CD, so forget what I just said

---

### Post by Rhye on 2010-07-29
I have been told to do what kerry said in other threads and it didn't work...

And now because of other advice my xp drive is unmounted and I won't be able to get into it now even if grub was fixed... I need to fix the partition (somehow?) And then grub

Sometimes it boots from cd.... I might dl the grub disk but how big is the iso

---

### Post by kerry_s on 2010-07-29
> **Rhye said:**
> I have been told to do what kerry said in other threads and it didn't work...

And now because of other advice my xp drive is unmounted and I won't be able to get into it now even if grub was fixed... I need to fix the partition (somehow?) And then grub

Sometimes it boots from cd.... I might dl the grub disk but how big is the iso

lets get a picture. 
go to system-> disk utility
click on your drive & press print to take a screen shot.

once we see what you got will go from there.

---

### Post by lukster91 on 2010-07-29
Some side advice. You may not be able to boot from CD, but if you can make a LIVE USB stick drive. Using UnetBootin (if you have another windows computer), or Ubuntu's Start up disk creator. Put another version of Ubuntu on it and use that (in LiveCD mode), you may be able to see the windows drive to back up any files you need? It might mount it, or give you the ability too.

Shot in the dark, I've had a fairly similar problem before and it worked for me.

---

### Post by Rhye on 2010-07-29
I'm currently at school and I live in australia so I will be back with a picture that u request at about 9pm GMT+10

Please reply around then (if its not too late in your time zone of course)

And thanks kerry for your help I can see your trying :D

---

### Post by kerry_s on 2010-07-29
> **Rhye said:**
> I'm currently at school and I live in australia so I will be back with a picture that u request at about 9pm GMT+10

Please reply around then (if its not too late in your time zone of course)

And thanks kerry for your help I can see your trying :D

i'll subscribe to the thread, if anything happens it will e-mail me & i should respond pretty fast. ;)

---

### Post by Rhye on 2010-07-29
Thankyou!! :d will be on later

---

### Post by vandorjw on 2010-07-29
If you don't have a CD or DVD drive..how did you install Linux?
Did you use Wubi? Also, you keep saying "Linux". What distro did you put on?
Knowing how it got there might help fixing it/taking it off.

Ubuntu, Arch, Debian?
Arch still uses the older version of grub...to keep it simple to understand.

Either way, I am sure we'll come up with a solution.

[SIZE="4"]If you don't care for trying to mount your windows XP partition, skip this...[/SIZE]

To try and force XP to mount...you can do this. (I'll assume you run Ubuntu.)

Open up a shell ....Either by clicking Applications ---> Accessories --> Terminal. 
<<OR>> 
Press ctrl + Alt + F2  simultaneously and log in

then type this
**sudo mkdir /media/windowsXP** 
   <enter>
   <type your password>

**sudo blkid** 
   <enter>
   *this with give you bunch of informations.*
   *You will need the UUID from the windows XP partition*

**sudo mount -t ntfs-3g -U** <insert UUID here> **/media/windowsXP -o force** <enter>

now hopefully the folder /media/windowsXP should contain your windows files.

(I assumed your windows XP was formated to ntfs)

**Note, if you pressed ALT + CRT + F2...ALT_+ CTRL + F7 will bring you back :)

OR Do what he said :) 
\|/
||
||
V

---

### Post by kerry_s on 2010-07-29
actually, it's a lot easier. there's gui tools for that & it's already installed.

---

### Post by Rhye on 2010-07-30
my drive

---

### Post by Rhye on 2010-07-30
and no i cant mount my drive through there... since the guy told me to unmount it those errors came up and now i cant remount it... and i can no longer see my xp files -_-

---

### Post by kerry_s on 2010-07-30
yeah, your partition is corrupted. not even sure if thats savable.

the best you can do is google for some ntfs tool to try & get your data, then format & reinstall.

---

### Post by Rhye on 2010-07-30
I can't lose my files on my xp drive... is there any way to keep my files??

---

### Post by kerry_s on 2010-07-30
> **Rhye said:**
> I can't lose my files on my xp drive... is there any way to keep my files??

i'm googling now, be patient.

---

### Post by Rhye on 2010-07-30
okay.

i googled ntfs tools and all the listings are the same program and it doesnt work :/ my disk wont show up in the recovery

---

### Post by kerry_s on 2010-07-30
i'm thinking you can try "testdisk", but its cli, so not really friendly.

you can install testdisk with synaptic. then in the terminal run "testdisk"

give this a read: [http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by Quackers on 2010-07-30
Can I ask why you can't boot from cd? Do you have a backup partition? Do you have a boot cd?

---

### Post by Rhye on 2010-07-30
IDK why it doesnt. no and no

and im messing around with the testdisk program now lol

---

### Post by kerry_s on 2010-07-30
> **Rhye said:**
> IDK why it doesnt. no and no

and im messing around with the testdisk program now lol

i wish you luck, remember to run that "sudo update-grub" after you finished testdisk before you reboot, so if it got fixed windows can be added back to the menu.

---

### Post by Quackers on 2010-07-30
Have you been into the bios and set first boot device to cd drive?

---

### Post by kerry_s on 2010-07-30
> **Quackers said:**
> Have you been into the bios and set first boot device to cd drive?

it don't matter right now. the priority is to recover the bad partition and data. the booting can be tackled later if a reinstall is necessary.

Rhye, i'm hitting the sack, it's 330 am here, i'll catch you later.

---

### Post by Rhye on 2010-07-30
yes :) i do no how to set up boot from cd haha it just doesnt work for some reason :/

thankyou! i didnt really understand that guide so i have no idea what im doing im just pressing random things lol :/

---

### Post by Quackers on 2010-07-30
You miss my point. If you can boot from cd you can download a boot cd with recovery environment, then maybe repair the installation with diskpart and fixboot

---

### Post by lukster91 on 2010-07-30
Do you have a Windows XP recovery tool?

For example, the ability to recover it or reset it to factory default settings. The Acer Aspire One with Linpus Linux Lite has a recovery disk incase of problems, I was wondering if XP has something similar.

---

### Post by kerry_s on 2010-07-30
> **Rhye said:**
> yes :) i do no how to set up boot from cd haha it just doesnt work for some reason :/

thankyou! i didnt really understand that guide so i have no idea what im doing im just pressing random things lol :/

i've never used that testdisk before, so i can't really talk you through it.

does it look like it's doing anything?
i think you might have to run it as root "sudo testdisk".

---

### Post by Rhye on 2010-07-30
Okay guys testdisk has now fully put my pc out of operations... -_-

It now doesn't even go to grub it just sits there and says something about bad partition

I put in my xp disk and it worked now for some reason but it goies to boot from it and also says bad partition. So I can now boot from disks but I have my drives unmounted and a lot of mbr and boot problems.

Is there a disk I can download and burn on my mums laptop that can mount my drives and just do an overall huge repair on my system? Thanks

---

### Post by kerry_s on 2010-07-30
> **Rhye said:**
> Okay guys testdisk has now fully put my pc out of operations... -_-

It now doesn't even go to grub it just sits there and says something about bad partition

I put in my xp disk and it worked now for some reason but it goies to boot from it and also says bad partition. So I can now boot from disks but I have my drives unmounted and a lot of mbr and boot problems.

Is there a disk I can download and burn on my mums laptop that can mount my drives and just do an overall huge repair on my system? Thanks

i don't think so, it sounds like it's to badly corrupted to be saved. best to format the whole thing & reinstall. sorry for the loss. :(

---

### Post by Rhye on 2010-07-30
How do I format a drive if I can't access my computer?

And laptops don't usually have exrra hd cables...

-_- I really needed all my stuff

---

### Post by kerry_s on 2010-07-30
> **Rhye said:**
> How do I format a drive if I can't access my computer?

And laptops don't usually have exrra hd cables...

-_- I really needed all my stuff

just put the installer disk in & boot from it.

---

### Post by theozzlives on 2010-07-30
Boot off the XP CD and choose recovery console, then run chkdsk /r. If that runs good, run fdisk /mbr, then fixboot. Exit to reboot.

---

### Post by Rhye on 2010-07-30
Up above what I said was... It now will try to boot from cd.

But it still doesn't boot from cd

It says

Boot from CD/DVD:
Booting from cd...
Bad partition...

And it just doesn't do anything else :(

---

### Post by theozzlives on 2010-07-30
Try to boot from an Ubuntu Live CD, and let me know soon.

---

### Post by kerry_s on 2010-07-30
> **theozzlives said:**
> Try to boot from an Ubuntu Live CD, and let me know soon.

if that don't work try to create a usb installer, see #2
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

---

### Post by Rhye on 2010-07-30
I've almost gone over my monthly download limit and I don't have enough left to spare 700 mb I need something to boot from for a lot less /: unless if I get linux will it fix my whole computer ?? 

I will stay with linux IF. Like I mean ONLY linux if I can web design/ graphics and if I can run a thing called

RSbot

I really need to run rsbot

---

### Post by theozzlives on 2010-07-30
We're at the point to where I want you to try to save your data and start over. Restoring your data after all the dust clears.

---

### Post by mr clark25 on 2010-07-30
what happened to the disk that you used to install ubuntu on your laptop the first time?

---

### Post by Rhye on 2010-07-30
So I will be able to keep my data? And xp files??

How do I do this :p I'm a noob I need lots of explanations haha

---

### Post by theozzlives on 2010-07-30
> **Rhye said:**
> So I will be able to keep my data? And xp files??

How do I do this :p I'm a noob I need lots of explanations haha

You need to boot with the Live CD to see if we can, but that's the plan.

---

### Post by Rhye on 2010-07-30
Its actually not a laptop its a pc I just installed notebook to test it out for my netbook I'm getting in a few days...

I don't have a disk I used a program called LinuxONUSB and the .iso file

My .iso is on my xp partition so there's no way I can get it /:

---

### Post by Rhye on 2010-07-30
I can't take any chances with my downloads /: I need to no if this will happen

Will it restore my xp files? If not

Will it atleast just mount my drive and format it ?

---

### Post by theozzlives on 2010-07-30
Well now we know some important info you with-held. Can you boot USB and get to a desktop? I'm running to 7-11 but will be back in a sec.

---

### Post by Rhye on 2010-07-30
I really honestly don't know what I can do now... Before my computer screwed up I had booted into puppy linux from usb but I don't no know.

And booting from usb most likely won't fiz the problem because in linux before we couldn't fiz my problem..

---

### Post by theozzlives on 2010-07-30
If you don't think we can help, why ask? A lot of us are professionals that do this just because we like to help. If you don't take our advise, we can't help.

---

### Post by theozzlives on 2010-07-30
You need to get into a live envionment to try to access your XP partition so you can save your files to USB, Ext HD, CD, DVD.

---

### Post by Rhye on 2010-07-30
Sorry 

So what are your suggestions? 

What will the live ubuntu CD be able to do?

---

### Post by theozzlives on 2010-07-30
> **Rhye said:**
> Sorry 

So what are your suggestions? 

What will the live ubuntu CD be able to do?

look at post #54

---

### Post by theozzlives on 2010-07-30
You need to boot CD/USB and choose "try" Ubuntu. Then when you get to the Desktop, I'll walk you through the rest.

---

### Post by Rhye on 2010-07-30
My parents have a ext hd and I can most likely get my hands on their laptop to download ubuntu and burn to cd

---

### Post by Rhye on 2010-07-30
Okay well I need to redownload ubuntu...

Do you think DamnSmallLinux would work for this? Because I'm trying to not use downloads

---

### Post by theozzlives on 2010-07-30
> **Rhye said:**
> My parents have a ext hd and I can most likely get my hands on their laptop to download ubuntu and burn to cd

Then do it. I'm going to bed soon so please be speedy.

---

### Post by Rhye on 2010-07-30
Okay I'll go download now... 

Hey just write down instructions dude so u can go sleep now haha I don't wanna keep u up my dl speeds arnt too fast

---

### Post by theozzlives on 2010-07-30
You got Yahoo?

---

### Post by Rhye on 2010-07-30
Sorry I only have hotmail, msn and gmail

Do you need any?

---

### Post by Rhye on 2010-07-31
i got onto the desktop.... but now your asleep :P

hmm i have no idea what to do :/

---

### Post by theozzlives on 2010-07-31
1. Go to Places and look for your Windows partition and click on it.
2. If Nautilus opens and displays your files, copy them to the external HD.
3. After you're sure you have all your stuff (ie: Documents, Pictures, etc), NUKE the drive with gparted.
4. Re-install Windows from your installation CD (save room for Ubuntu if you so choose).

---

### Post by kerry_s on 2010-07-31
> **theozzlives said:**
> 1. Go to Places and look for your Windows partition and click on it.
2. If Nautilus opens and displays your files, copy them to the external HD.
3. After you're sure you have all your stuff (ie: Documents, Pictures, etc), NUKE the drive with gparted.
4. Re-install Windows from your installation CD (save room for Ubuntu if you so choose).

1. the partition is corrupted, so won't mount. see pic in post #20

---

### Post by theozzlives on 2010-07-31
> **kerry_s said:**
> 1. the partition is corrupted, so won't mount. see pic in post #20

Says the disk is healthy.

---

### Post by kerry_s on 2010-07-31
> **theozzlives said:**
> Says the disk is healthy.

it says unknown partition, meaning "unreadable", it knows it's ntfs, but the file structure is screwed. you need to recover the structure before the data can be accessed.

---

### Post by theozzlives on 2010-08-01
> **kerry_s said:**
> it says unknown partition, meaning "unreadable", it knows it's ntfs, but the file structure is screwed. you need to recover the structure before the data can be accessed.

Oh I can't read that small print, old man here. Norton Disk Doctor or Boot the CD and go into recovery mode and run chkdsk /r.

---

