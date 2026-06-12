---
title: "ubuntu help for data recovery"
date: 2010-05-02
forum: General Help
---

### Post by JaxDeVo on 2010-05-02
Hello, looking for assistance. I am new to ubuntu, I  have some instructions to boot to ubuntu because my iomgega storcenter NAS failed and I need to recover some data. It was configured in a mirror set and the instructions allow to boot to ubuntu, but I don't want to make the wrong move and lose my data. Here is roughly the steps I found in a post on Iomega's site. Iomega does not support thier hardware beyond basics and told me I had to send off to a data recovery company! Here is what the .....
 
The post starts here.
 
...  [SIZE=2]6.10 Ubuntu instructions didnt work out for me but the currently latest version 9.10 did. 

I did NOT need a thumbdrive nor did I have to install Ubuntu to my desktop. I was able to get matters done running FROM THE CD. 

I bought TWO sata data cables of 18 inches because the ones in my desktop PC were too short to reach outside of the box. 

Inside my desktop pc, while POWER IS OFF ON YOUR DESKTOP, I disconnected one DVD drive and one harddrive from their SATA cables - _**both **_the POWER and the data connectors. you MUST leave at least one DVD or CD drive connected either by PATA or SATA otherwise you will not be able to boot from the Disc. (I suppose tthats where a thumbdrive IS needed) . One harddrive needs to be left connect (I think) do that temporary changes can occur. I COULD be wrong about that as I am very much a unix newbie. 

The two sata drives INSIDE your stor ix2 will need power and data _**from **_the PC, hence the need to free up power and sata connections inside your PC and hence the possible need to buy longer data cables. 

I left my ixor's drives inside the box, just removing the sata data and power connectors completely to clear room for the cables coming from my desktop pc. again with power off, I connected each stor ix2 drive to my desktops sata data and power cables. 

I powered up the desktop - booting from the ubuntu 9.10 CD 

When I got to the graphical interface, I opened up a terminal window. 

[/SIZE]**NOW HERE IS WHERE YOUR EXPERIENCE MAY VARY. **

[SIZE=2]as I stated I am a newbie in the world of linux. however I have decades of experience troubleshooting software so what I can do is INVESTIGATE and LOOK UP instructions and solutions. **That **is THE skill you will need, second only to the ability to follow instructions. 

per instructions from another thread referred to ealier in this topic, I started with the command [/SIZE]**sudo su**[SIZE=2] 
That command tells linux that you want to run in supervisor/admin mode - aka super user mode. Then I typed [/SIZE]**fdisk -l**[SIZE=2] 
this tells me every PHYSICAL drive ubuntu sees and each LOGICAL drive (aka partition) that the physicals have. Now this isnt REALLY a necessary step; however if the next commandline instruction fails then the fdisk info will help you figure out if the computer/ubuntu even see the two stor drives at all. 

The command that saved my world was this [/SIZE]**mdadm --assemble --scan**[SIZE=2] 

I found a few threads here and via google about this utility called mdadm. The dozens and dozens of combinations you can make with the options is mind bending. I have a degree in computer science and I needed three diffferent sessions before I understood the gist of whats what. LUCKILY for me all I needed was one combination --assemble and --scan and mdadm worked like magic in seconds. 

OK, now for your windows people/ linux newbies, when something in linux works what happens is NOTHING. if you correctly enter in a command and its options, and its successful, 90 percent of the time NOTHING HAPPENS but the command prompt comes back. very very non windows. then again, it works and works quickly, which is also anti-windows;-) 

Now I was not done, but I did jump over a major hurdle which was to get the two drives connected and back together as a RAID pair. 

the following is non windows users friendly. such people will need to GOOGLE what or HOW to do what I am saying next. (which by the way was exactly what I was doing between today and the date of my previous posting aboive) 

I made a directory called bob - [/SIZE]**mkdir /mnt/bob**[SIZE=2] 

then I mounted bob onto the new raid that was created. 
[/SIZE]**mount -t auto /dev/md0 /mnt/bob**[SIZE=2] 

in linux, instead of dir to list files use this command as its more complete [/SIZE]**ls -a**[SIZE=2] 

I did this and bob showed me several folders/directories. Problem is, I didnt recognize a single name. Not one of these was anything I remember using as my file or share names. And thats because I would not see anything I recognized until I find the folder called shares 

So what I needed to find - and was there (!) - was the folder called [/SIZE]_**Samba**_[SIZE=2] 

I cd to that directory and then I did a listing ( thats the ls -a) and there it was the folder called _**shares**_ 

change to that directory and now a listing will show you all the shares you created (or were defaulted to you). and now - this is where having a USB drive would be handy. because you want to copy your data over to the target drive that. Of course you can make use of space on a connected harddrive in your desktop - but that will take some more learning by you to make this space accessible to your windows OS when you reboot without the ubuntu disk. So the usb drive is the easier way. 

The command you want to use for copy is called cp 
there are a zillion options the big one you need to remember is -R so that the copy traverses down all the subfolders. 

I ran cp with the source as /bob/Samba/shares/harry/ and I used -R so everything from the harry share when to the thumb drive. 

Of course with several shares I had to make a seperate directory on the thumbdrive and then run the cp command TO each folder FROM each share. 

This is not enough detail for a windows only person. I understand that. its not meant to be. I am not going to tutor a child how to perform brain surgery. its not likely to end well. if command prompt isnt something you get or if you dont know a folder and a directory are the same thing, you should not be playing around the insides of your NAS RAID drives. 

OK I am done typing........Remember its[/SIZE]** mdadm --assemble --scan **[SIZE=2]and you are on your way to recovery;-)![/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Sadly this guy was isn't likely to help me, so I thought I would try here! If you are ubuntu savy and don't mind helping out, I would greatly appreciate it. I am windows and hardware savy, can follow instructions very well so I think we can get it done rather quickly once I have the confidence and support to try it. Thanks!:) [/SIZE]

---

### Post by koanhead on 2010-05-02
Quoting big chunks of other peoples' posts isn't a great idea, as it can be hard to tell what parts are you and what parts are the other person. It's better to link to the other post to which you want to refer, while concentrating on making your question as clear as possible.
It sounds like you want to take the RAID(1?) mirror out of your NAS device and mount it in your computer in order to slurp the data off it. Please correct me if I'm wrong.
In order to do this, the advice presented in the post will likely work. Some caveats:
1) You need enough connections for all the drives in the array, plus at least one drive to which to write your recovered data (of course). They don't all have to be the same, but obviously things will go more quickly if it's all SATA.
2) mdadm is not installed to Ubuntu by default unless your initial install is to a RAID-equipped machine. You can install it using Synaptic.

I will subscribe this thread and try to help you as best I can.

---

