---
title: "Grub rescue??"
date: 2011-10-12
forum: General Help
---

### Post by Skyline911 on 2011-10-12
Good evening. My son is away at university with his Toshiba Laptop running Windows Vista and Ubuntu Natty side by side.  When he has gone to turn his computer on today, he is getting the message

Error: unknown file system 
grub rescue <

on the screen. I have trawled various search engines and most of what I find is suggesting re-installs etc.

As he has no disks with him, I am just wondering if there is anything else we can do to remedy his predicament....

Thank you in anticipation of your kind assistance.....

---

### Post by gonewriting on 2011-10-12
I recommend looking [here]("https://help.ubuntu.com/community/Grub2#Boot_a_Specific_Kernel_Manually").  There are steps that will tell you how to boot into Linux and reinstall GRUB.  Good luck!

---

### Post by Skyline911 on 2011-10-12
Thank you for the response :) That looks seriously technical to me but I will see if I can make head or tail of it.......

---

### Post by Skyline911 on 2011-10-12
I am really grateful for your answer, gonewriting, but I don't understand most of the information you have linked to........

---

### Post by cryptotheslow on 2011-10-12
Can he boot into Vista?

If not does he have access to a working PC that he can download the Ubuntu installer iso file and burn it to CD?

It would be most useful to people trying to help if you could get him into a running LiveCD/USB instance (use the "Try Ubuntu" option _[COLOR=Red]**not **[/COLOR]_[COLOR=Red][COLOR=Black]the "Install" option). And then download and run the bootinfoscript here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Posting up the contents of the results.txt file that the script creates will really assist in understanding what is where on the drive(s).
[/COLOR][/COLOR]

---

### Post by drs305 on 2011-10-12
> **Skyline911 said:**
> I am really grateful for your answer, gonewriting, but I don't understand most of the information you have linked to........

The information in the Grub 2 community documentation can look overwhelming. In the grub-rescue section, the commands in bold are what is typed. There is a lot of documentation but the actual commands are very simple to enter and execute. 

The TAB completion feature - typing the first part of an entry and then TAB-ing to complete the entry - makes entering some of the information even easier. It really isn't too difficult to type the entries; understanding what is happening in the background admittedly is not quite as easy to comprehend for those not used to command line operations. Thankfully there is a chance that the system will boot by following the procedures even if you don't understand the concepts.

It *becomes* more difficult if the procedure doesn't work, since the reasons for failing are varied and sometimes difficult to analyze without information provided from sources such as the boot info script. 

Don't forget that there are lots of helpers here who can assist in decrypting those instructions if necessary.

---

### Post by drs305 on 2011-10-12
> **Skyline911 said:**
> I am really grateful for your answer, gonewriting, but I don't understand most of the information you have linked to........

The information in the Grub 2 community documentation can look overwhelming. In the grub-rescue section, the commands in bold are what is typed. There is a lot of documentation but the actual commands are very simple to enter and execute. 

The TAB completion feature - typing the first part of an entry and then TAB-ing to complete the entry - makes entering some of the information even easier. It really isn't too difficult to type the entries; understanding what is happening in the background admittedly is not quite as easy to comprehend for those not used to command line operations. Thankfully there is a chance that the system will boot by following the procedures even if you don't understand the concepts.

It *becomes* more difficult if the procedure doesn't work, since the reasons for failing are varied and sometimes difficult to analyze without information provided from sources such as the boot info script. 

Don't forget that there are lots of helpers here who can assist in decrypting those instructions if necessary.

There is also a companion thread in these forums that discusses the same recovery procedures, written in a slightly different style, which includes questions and solutions by forum members:
[Grub Rescue Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by Skyline911 on 2011-10-13
Thank you all for your help.  I have fallen at the first fence I'm afraid, as I don't understand what

set root=(hdX,Y)
Use the correct X,Y results from the ls command and ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. For example, if the Ubuntu system is on sda5, enter: set root=(hd0,5)

means!!!  Sorry if that sounds a bit stupid :(

I am going to see him in a couple of week's time so I think I will just need to reformat his computer for him and pray that all his valuable stuff is on external storage!!

---

### Post by drs305 on 2011-10-13
Skyline911,

It means at the grub prompt you would type: set root (hd

Then you would need to know the drive and letter. The first drive on the machine is 0. If you have two drives, they would be 0 and 1. If you don't know which drive the Ubuntu partition is on, you can run "ls" at the Grub prompt. This will produce output showing all the drives (hd0), (hd1), etc and all the partitions (hd0,1), (hd0,2), (hd1,1), etc. For these last three (hd0,1) would be the first partition on the first drive. (hd0,2) would be the second partition on the first drive; (hd1,1) would be the first partition on the second drive.

If you aren't sure which drive contains the Ubuntu partition, you could run variations of the following: (hd0,1)/  and try the combinations you saw in the "ls" command. The "ls (hd0,1)/" command would display the main system files/folders in the / partition. For Windows, you would probably see "windows", and other familiar folders. If you find the correct Ubuntu partition, you would be entries like "boot", "etc", "dev", "home".

Of course, it you don't understand drives or what a partition is, none of this is still going to make sense.

I wouldn't reformat anything until you get his permission and can determine that there is nothing irreplaceable on it. Just because you can't access it at the moment doesn't mean that it would be hard to do given the correct guidance. It may take someone physically looking over your/his shoulder, or maybe a 'live chat' on one of the support channels. Just don't be in a big rush to erase everything until you are sure that's what you both want to do.

---

### Post by Skyline911 on 2011-10-22
Good evening All.

I am now in possession of the aforementioned laptop. 

I have attempted a fresh install of Ubuntu with a live CD with no success :(

I am greeted with much whirring of the drive followed by a momentary glimpse of the purple screen then a blank black screen.....

Starting to lose hope now.....................

UPDATE: Just trying the CD again and I think it may be doing something... all be it very slowly........I will keep you updated.....

---

### Post by Skyline911 on 2011-10-22
Failed..............

Have now attempted all previous suggestions to no avail.

Next option appears to be to take laptop to PC repair shop to see if there is any hope for it, I think.......

---

