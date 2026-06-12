---
title: "NEWBIE HELP NEEDED in installing Ubuntu remix and keeping win xp (simple issue)"
date: 2009-09-04
forum: General Help
---

### Post by ryansdistrict on 2009-09-04
Hello
i got TOshiba NB100 with windows xp sp3 previously installed 
Please i need help in backupup what a previously got so that i can return anytime to it in the future 
then i would like to install ubuntu netbook remix to my netbook and make it to dual boot with my win xp

What i've done so far 
is i downloaded and had the .img of ubuntu ready on a bootable flash 
i need safe  way to backup my win xp then install ubuntu next to xp 
my netbook hardisk is made up of 1 partition


Your support is appreciated 

Thank you

---

### Post by P4man on 2009-09-04
do you have an external drive thats big enough to hold a backup of your entire windows setup ? If so, we can make a drive image that you can restore later.

If not, you can do 2 things: first try out ubuntu just from the stick, and see if you like it. If you don't, then you've saved yourself a lot of time :p. If you do want to install it, a regular install will make a dual boot system, it will resize the partition and leave your XP intact. Not that its a bad idea to make a backup, but *normally* its not needed.

One caveat though: if later you  decide to remove ubuntu, you'll be stuck with the grub bootloader, and without windows cd (or disk image), it might be tricky to restore the windows bootloader. I guess you could make a backup from the windows bootloader with "dd" and put it on a usb stick, but Id have to google for that.

---

### Post by ryansdistrict on 2009-09-04
i have an external portable Hardisk that i can copy the files to
How can i make an image ?

I loved ubuntu i am already using it in its desktop version and i would like to install the remix on my netbook too because am fedup of virii and windows 
the 

if i boot the setup from Flash will there be an option in the settup that allowes me to resize/ create partitions in my 1 partition win xp hd without loosing data ?

by the way an important issue am worried about is that when i booted ubuntu form USB its now showing me what am expecting after 1 minute loading files it shows me the no partition error :S 
WHy is this ?

---

### Post by P4man on 2009-09-04
> **ryansdistrict said:**
> i have an external portable Hardisk that i can copy the files to
How can i make an image ?

with dd from a terminal:

dd if=/dev/yourhardisk of=/media/yourexternaldisk/image.img

(no output will appear until its done).

If you like a more graphical solution, have a look at clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

> if i boot the setup from Flash will there be an option in the settup that allowes me to resize/ create partitions in my 1 partition win xp hd without loosing data ?


Yes. During the install it will ask you where to install to and offer to resize the XP partition to make room for ubuntu. Just make sure you dont keep the default size for the ubuntu partition, which is like 2.5 GB. Make it bigger :)

> by the way an important issue am worried about is that when i booted ubuntu form USB its now showing me what am expecting after 1 minute loading files it shows me the no partition error :S 
WHy is this ?

Can you elaborate? I dont know what "the" no partition error is. ? Can you boot ubuntu from the stick?

---

### Post by ryansdistrict on 2009-09-04
when the boot starts the stuff starts to load until the details below ppea

---

### Post by ryansdistrict on 2009-09-04
hold on i will attach a screen shot

---

### Post by ryansdistrict on 2009-09-04
here is the error am getting 
i tried it on 2 laptops here is the result

---

### Post by nothingspecial on 2009-09-04
You are obviously having a problem with netbook remix and unetbootin.

If I were you, I would use unetbootin to download regular ubuntu-9.04.

You can install the netbook remix interface later.

---

### Post by ryansdistrict on 2009-09-04
i did what u sugested and copied an iso image of the desktop version and boooted from it 
what i got is the same error i tried it on another pc same error :S :(

---

### Post by nothingspecial on 2009-09-04
Download your distribution and launch unetbootin.

Choose disk image, iso (see screenshot 1)

Click on the box thingy to the right of that line and navigate to the iso (see screenshot2)

Screenshot 3 shows you how it should now look. Unfortunately I dont have a usb drive on me at the moment but you have to select it in the second box at the bottom where it says drive. It could be your usb stick that is at fault. I do this all the time.

---

### Post by ryansdistrict on 2009-09-04
mmmm the 3 steps i did them and clicked write 
i wated like 3 4 minutes and it said done and asked me to close or to reboot  
i rebooted from usb and got that error 
have i missed otu anything ?

---

### Post by nothingspecial on 2009-09-04
Are you doing this from linux or windows?

I use the version that "comes with" ubuntu but maybe the latest version of unetbootin has a bug. You could try installing an earlier version from [[COLOR="Magenta"]here[/COLOR]]("http://sourceforge.net/projects/unetbootin/files/").

Or like I said it might be your usb stick.

You would have to remove the version you have now.

---

### Post by nothingspecial on 2009-09-04
Or as you have tried this a number of times maybe unetbootin and the stick have got them selves in a mess. It might be an idea to completely remove everything from the stick and trying again.

---

### Post by ryansdistrict on 2009-09-04
am now on windows 
i tried by another usb stick i got still same problem 
i formated the stick several times and started plan 
i feel ive hit a dead end

---

### Post by nothingspecial on 2009-09-04
Then like I said, maybe try an earlier version of unetbootin (See pinky purple link a couple of posts up)

I`m at a loss, it works for me, every time.

And I`m sorry, I have to bow out now and go to bed, I`m sorry I couldn`t help you resolve your issue.



.......or borrow a usb disk thingy and try to do it that way.

---

### Post by ryansdistrict on 2009-09-04
dont worry buddy nity 
ill try to get old version if it didnt work ill borrow a 16gb flash drive maybe because its 1gb its not working

---

### Post by ryansdistrict on 2009-09-04
NO LUCK 
ill have to try by getting a new flashj drive 

anyone got a simpler possible sollution ?

---

### Post by P4man on 2009-09-04
You got to be doing something wrong. Can you post a screenshot of unetbootin just before you make it write the stick?

Other thought: you got a windows virus messing up your sticks?


closing thought: your screen is upside down :p

---

