---
title: "New Install Duel Boot system Ub 10.10"
date: 2010-11-25
forum: General Help
---

### Post by Alpha99 on 2010-11-25
Hi there 
I am a new user to Ubuntu if i can get it to work 
Downloaded yesterday and spent last night and this morning going over it 

I have now made the jump - only to find it has locked me out of my other system all i can use is Ubuntu CD to gent online and contact you. After install it asked for reboot but during the install i chose run sids by side space give to Ubuntu was 60 G

Previously had Windows and Susse 10.3 in duel boot mode but was moving to Ubunto whwn this problem came up 
Can you help please.


System Amd 2400 2 G Ram 320 HDD Duel Core

---

### Post by dino99 on 2010-11-25
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Alpha99 on 2010-11-25
> **dino99 said:**
> here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

Hi Dino99
Thank you for your directions here.
But as i am very Green i will be having some diffeculties her, so far i am dowloading the partedmagic and will burn Cd  so once i re boot with CD i should follow your instructions  as above and create 3 partitions
But i am not too clear here what i will be doing as to size required by Windows, Suse and ubuntu as i do not want to loose the data within Suse. if at all, is it poss you may give a bit more detail for a novice to follow. 

Thanks.

---

### Post by apollothethird on 2010-11-25
> **Alpha99 said:**
> Hi there 
I am a new user to Ubuntu if i can get it to work 
Downloaded yesterday and spent last night and this morning going over it 

I have now made the jump - only to find it has locked me out of my other system all i can use is Ubuntu CD to gent online and contact you. After install it asked for reboot but during the install i chose run sids by side space give to Ubuntu was 60 G

Previously had Windows and Susse 10.3 in duel boot mode but was moving to Ubunto whwn this problem came up 
Can you help please.


System Amd 2400 2 G Ram 320 HDD Duel Core

Edit your /etc/default/grub file and command out "#" the line:

GRUB_HIDDEN_TIMEOUT=0

Then run "sudo update-grub".  Then restart the computer.  You should see your menu choice.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by dino99 on 2010-11-25
if your Suse installation already have both the "swap" and "/home" partitions, 
then you only need to create the "/" partition to install ubuntu (it will share the "swap" and "/home" with Suse, you dont need to do something special to use them)

Your data and settings are safe into /home (dont format that partition, but you can resize to widen it if neceessary)

About the winblows partition size, the partitioner (partedmagic) will show you the free space and let you shrink it if necessary.

About more help: look at links below if you need.

note about burning: the slower the better :)

---

### Post by Alpha99 on 2010-12-02
> **apollothethird said:**
> Edit your /etc/default/grub file and command out "#" the line:

GRUB_HIDDEN_TIMEOUT=0

Then run "sudo update-grub".  Then restart the computer.  You should see your menu choice.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Hi there, sorry to have taken so long in responding 

Many thanks for your ideas 
But to no avail as i had no access to the system for some unknown reason - No Xterm or command line

Could only boot up with the Cd. - So i gave up and have now resolved the issue with a clean system install from scratch.

Still have a lot to learn

Many Thanks any ways for your help.

---

### Post by apollothethird on 2010-12-03
> **Alpha99 said:**
> Hi there, sorry to have taken so long in responding 

Many thanks for your ideas 
But to no avail as i had no access to the system for some unknown reason - No Xterm or command line

[color=green]**Could only boot up with the Cd**[/color]. - So i gave up and have now resolved the issue with a clean system install from scratch.

Still have a lot to learn

Many Thanks any ways for your help.

Hi, Alpha.  I believe you made a rather drastic decision.  I’m sure you’ll have the issue again.  To start over so quickly might put a taste in your gut that Linux is fragile and you could easily lose your data.  It isn’t.  It’s very robust.

I don’t think you “had no access to the system”.  I believe you misunderstood the suggestions given.  To access the system was simple.  Apparently you accessed the system to perform your new installation.  We expected for you to use that same disk to perform your system recovery.  I’m sure had you clicking on “Try Ubuntu” rather than “Install Ubuntu” you would have had access to all the commands you needed included the terminal window.  If though some fluke you didn’t, we would have been glad to know why it was failing for you.  Maybe you have a bad install disk and might run into other problems.  But again, I don’t believe the latter I’m certain you misunderstood our suggestions.  Had you used the Install disk to log into this forum and tell us that you didn’t have access to the tools, we would have clarified what you have to do.

For most of us, our data on the drive is very important.  We wouldn’t be using an OS that we had to constantly install and start our personal data over.

Again, all the commands for recover were on the CD.  It appears from your message that you didn’t have problems booting to the CD.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by MamaWoll on 2011-01-04
> **dino99 said:**
> here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)



I have absolutely no idea what you are talking about.:confused:

I don't know much about computers. I know just enough to get by. Can I get you to translate that for the technologically challenge? 
I'm sorry lol

---

### Post by apollothethird on 2011-01-04
> **MamaWoll said:**
> I have absolutely no idea what you are talking about.:confused:

I don't know much about computers. I know just enough to get by. Can I get you to translate that for the technologically challenge? 
I'm sorry lol

Hi, MamaWoll.  It would be easier to decipher Dino99's message for you if we knew how it could apply to a problem you're having.

Dino99 was explaining install options that were directly related to the OP's immediate problem and question.  The application Dino99 was referring (gparted) is from prompts that will be displayed on the Advance install screen.  If you look at the advance options you'd see the application with various choices.  Dino99 was suggesting what to do with those choices.

A novice user trying to take that information in without looking at the menu options and without having an immediate need might be a bit lost, taking the message out of context.

If you're having a specific question or a specific problem we could probably easier assist by speaking relative based on your specific question or problem.

Are you having a specific problem are trying to do something specific?  You’re saying you know enough to get by.  That’s good.

The message speaks of applications for creating partitions on a hard drive.  The applications for making these partitions, referenced, are gparted and partedmagic.

A partition is like a virtual hard drive.  A hard drive is divided into partitions, each partition being able to function as if it were a separate hard drive.  Dino99 was suggesting making a partition devoted to Linux (the ext4 format) and using other space (partitions) for other things.

He also make a reference to various reference points on the hard drive for “/” which is known as the highest point, the root of the file system, and “/home” which is normally an area reserved for personal files and directories of the various users that logs into the Linux OS.

Without an immediate need, even that break down might appear complicated.  I believe it would be much easier if you made a reference to some type of objective and we could use that as a reference point.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Herman Munster on 2011-05-04
> **dino99 said:**
> here is how to install:
 
 
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings
 
[http://partedmagic.com/](http://partedmagic.com/)
 
The initial install of 10.04 LTS was performed within Windows using the Windows Installer.

---

### Post by apollothethird on 2011-05-04
> **Herman Munster said:**
> The initial install of 10.04 LTS was performed within Windows using the Windows Installer.

Herman.  In this case, you're running Wubi instead of Ubuntu.  It's a Windows install/compatible flavor of Ubuntu.  There are some major differences which include, it's not running on it's own partition.  It's running under Windows as a Windows application.

I haven't run that variety, so can't be much help except to suggest that you include the name Wubi when you're trying to get assistance.  This way people familiar with it's deviations will be aware of the differences, which in this case, will know that it won't show up as a partition option.

I believe that flavor was designed for users to test the Ubuntu and if they like it, give Ubuntu it's own partition go from there.

My suggestion, since you might have tested Ubuntu and may like it, to create a new partition and install Ubuntu on it an have full access to all the boot options and other components of the Ubuntu OS.

If you backup your Home directory, after installing Ubuntu on it's own partition freshly you can bring your Home directory back to that install and have your data and environment basically intact with a renewed available for full Ubuntu support.

If you decided to take this approach I can easily walk you thought the necessary steps of gparted to get it started.  Other than that, I'd kind of have to sit this one out and learn from tips given from the Wubi gurus.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

