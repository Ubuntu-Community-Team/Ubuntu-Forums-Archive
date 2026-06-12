---
title: "First time Linux and *buntu  user. Need some help."
date: 2009-07-08
forum: General Help
---

### Post by iconz255 on 2009-07-08
hello all,just made the jump to installing Kubuntu after finally making my Sagem F@st 800 modem work thanks to this nice utility [_Ubudsl_]("http://www.ubudsl.com/en/start.php"). So i have some questions before finalising my setup and make Kubuntu my main desktop.


1) I am a longtime Windows user and i am used to my windows desktop and today changing to the KDE style desktop is daunting. What i am asking here is simply can i add icons directly on the desktop like windows and interact with them, that is rename etc without having to deal with the desktop panel/plasmoid?

Can the icons be treated like icons instead of everything having a panel open when i hover over it with my mouse? Something in the lines of KDE 3 or is it that the desktop concept has changed in KDE 4?

Also, can i resize all my icons to a certain size for the whole system. I would like to set all my icons to something like 16*16 so that i waste minimum space. I have attached my current windows desktop. i would like something similar in KDE. [i have masked all my personal files ;)]



2) Is there a tool that indicates me the software installed on the system in a list so that i can easily locate what i have instead of having to hunt them down in synaptic or kde add/remove software tool.



3)i have an Ati graphics card. the default kde settings works fine but i want to install the ati flgrx drivers so that i can use some 3d games in kubuntu. i have gone in system>drivers but there is no Ati proprietary drivers listed there. can someone indicate me where and how to get the proper ati flgrx drivers by add/remove or command line.

i rather not have to go download the drivers from Ati website and compile it because some users have reported mixed issues on the ubuntu forums and i do not want to mess up my display.


4) concerning swap space, i have read on forums that the recommended setup is actual RAM*2. I have 2 gb of RAM, so this would lead me to allocate 4 GB on my hard disk. i do not use hibernate mode or do anything very memory intensive like heavy image or video editing or use VMware etc. I would rather like to use 2GB as swap and put the saved 2GB to another use. Do you think that it is correct or should i allocate more to Swap space?


5)i plan to use ext4 for my /root partition and fat32 for my home parition when i finalise my setup. this is for just in case i still need windows XP so i can have access to my files. do you think that using fat32 for the home partition would decrease system performance.


Thanks everyone for their help.


Cheers

Iconz255

---

### Post by c0mput3r_n3rD on 2009-07-08
> **iconz255 said:**
> hello all,just made the jump to installing Kubuntu after finally making my Sagem F@st 800 modem work thanks to this nice utility [_Ubudsl_]("http://www.ubudsl.com/en/start.php"). So i have some questions before finalising my setup and make Kubuntu my main desktop.


1) I am a longtime Windows user and i am used to my windows desktop and today changing to the KDE style desktop is daunting. What i am asking here is simply can i add icons directly on the desktop like windows and interact with them, that is rename etc without having to deal with the desktop panel/plasmoid?

Can the icons be treated like icons instead of everything having a panel open when i hover over it with my mouse? Something in the lines of KDE 3 or is it that the desktop concept has changed in KDE 4?

Also, can i resize all my icons to a certain size for the whole system. I would like to set all my icons to something like 16*16 so that i waste minimum space. I have attached my current windows desktop. i would like something similar in KDE. [i have masked all my personal files ;)]



2) Is there a tool that indicates me the software installed on the system in a list so that i can easily locate what i have instead of having to hunt them down in synaptic or kde add/remove software tool.



3)i have an Ati graphics card. the default kde settings works fine but i want to install the ati flgrx drivers so that i can use some 3d games in kubuntu. i have gone in system>drivers but there is no Ati proprietary drivers listed there. can someone indicate me where and how to get the proper ati flgrx drivers by add/remove or command line.

i rather not have to go download the drivers from Ati website and compile it because some users have reported mixed issues on the ubuntu forums and i do not want to mess up my display.


4) concerning swap space, i have read on forums that the recommended setup is actual RAM*2. I have 2 gb of RAM, so this would lead me to allocate 4 GB on my hard disk. i do not use hibernate mode or do anything very memory intensive like heavy image or video editing or use VMware etc. I would rather like to use 2GB as swap and put the saved 2GB to another use. Do you think that it is correct or should i allocate more to Swap space?


5)i plan to use ext4 for my /root partition and fat32 for my home parition when i finalise my setup. this is for just in case i still need windows XP so i can have access to my files. do you think that using fat32 for the home partition would decrease system performance.


Thanks everyone for their help.


Cheers

Iconz255

1.) yes, and you do it same.

2.) YES! it's called add/remove applications in Applications -> add/remove applications, which is 100x betteer than in windows, you can actually clean install and uninstall all your applications from there.

3.)System->Administration->Hardware Drivers

4.)I think it's fine, I only have 1Gb of RAM and about 1 Gb of swap, and everything runs fine.

5.)I don't believe performance should decrease at all from having a fat32/fat16 filesystem, I'm using the same so that I can do the same :)

Basically, you can do everyting Ubuntu that you can in Windows, but better.  I guarantee it!!  Have fun, play around, and you can always ask questions.

---

### Post by iconz255 on 2009-07-09
First of all thank c0mput3r_n3rD for your reply.


5. I've tried it but it is not listed there. Ive tried to go looking in the repos but to no avail. Is there something that allows user to install the ati-flgrx drivers without having to download the drivers and compile it manually?


> **c0mput3r_n3rD said:**
> Basically, you can do everyting Ubuntu that you can in Windows, but better.  I guarantee it!!  Have fun, play around, and you can always ask questions.


Many thanks and you bet i'll be asking much more questions :).


Cheers
Iconz255

---

### Post by Cheesemill on 2009-07-09
Using a non ext2/3 partition for your home folder is very unwise (maybe not even possible).  Ubuntu expects files in your home folder to have certain permissions which cannot be given to them on a FAT/NTFS partition. You'll run into all sorts of problems attempting this.

---

### Post by iconz255 on 2009-07-10
> **Cheesemill said:**
> Using a non ext2/3 partition for your home folder is very unwise (maybe not even possible).  Ubuntu expects files in your home folder to have certain permissions which cannot be given to them on a FAT/NTFS partition. You'll run into all sorts of problems attempting this.


Thanks Cheesemil. Got the same answer in the Kubuntu forums. Guess i'll have to manage to try another way to share the same data between kubuntu and XP.


Thanks


Cheers

Iconz255

---

