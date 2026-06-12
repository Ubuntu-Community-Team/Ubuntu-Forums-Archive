---
title: "&gt;&gt; Some problems; plz advice :)"
date: 2009-09-04
forum: General Help
---

### Post by echo9 on 2009-09-04
Hi to all! :)

Am a newbie to ubuntu 

1. whenever(most of the time) i switch on my notebook and select the ubuntu boot option from grub's menu; the boot process hangs and i need to repeatedly push the enter/return key till the nvidia's driver splash screen comes up.. :( 

why is it so..? why is the boot process requires user's input (any button..to be pressed including space-bar etc.)

2. i am not able to save any files/folders on other ntfs partitions

suppose i make a new folder..rename it..and then copy some files from my /home dir
this goes all the way right..but when i restart and boot into windows (have windows vista basic ed.) ..the folders gone..it isn't there..!? :(

i think i need to install ntfs-config and sudo it??

3.  while trying to put my notebook into standby mode it goes into the mode but while waking it up it doesn't comes out of it (most of the time..) i get a blank black coloured screen.. :'(

and yea.. if my speakers are not in mute mode then whenever i try to go into standby/sleep mode i get a sharp click sound from my speakers for about a fraction of a second

is it goin to damage my speakers?

my notebooks is having a nVidia nforce 630M chipset; has a 7150M GPU onboard

my proc is a AMD turion 64x2; using ubuntu 9.04 32 bit ed.


thanks in advance~
Regards

---

### Post by echo9 on 2009-09-05
is there anyone who can solve my problems..?:(

anyone....?

---

### Post by Liolikas on 2009-09-05
1)  something wrong with nvidia drivers try update etc.

2) you have ntfs-3g installed right?

---

### Post by P4man on 2009-09-05
> 1. whenever(most of the time) i switch on my notebook and select the ubuntu boot option from grub's menu; the boot process hangs and i need to repeatedly push the enter/return key till the nvidia's driver splash screen comes up.. :( 

Do you get any messages ? If you dont, then try this, to make the boot process more verbose, and we can figure out whats going on: in grub, don press enter on the ubuntu line, but press "e" to edit. Then select the third line that looks somehwat like this:

kernel	/boot/vmlinuz-2.6.28-11-generic root=UUID=a438d590-7b75-44eb-8bb6-0765f7c8f82c ro **splash quiet**

Press E again to edit. Remove the the "splash" and "quiet" options at the end. Then press enter to confirm, and B to boot. This will output a lot of text on your screen during the boot process, see what its asking you..

> 
2. i am not able to save any files/folders on other ntfs partitions

suppose i make a new folder..rename it..and then copy some files from my /home dir
this goes all the way right..but when i restart and boot into windows (have windows vista basic ed.) ..the folders gone..it isn't there..!? :(

Can you browse your windows drive ? Are you sure you are putting those files on the windows drive and not on the ubuntu partition (which windows can't read) ?

Try opening the file manager (nautilus) and open the windows drive from the left menu. If you see folders like "windows" "program files" "users" etc, then its your vista drive. Try making a new folder in there. Do you get any errors? 


> 3.  while trying to put my notebook into standby mode it goes into the mode but while waking it up it doesn't comes out of it (most of the time..) i get a blank black coloured screen.. :'(


Can you give the exact type of laptop you have, rather than the specs? Also, did you run all updates?

> and yea.. if my speakers are not in mute mode then whenever i try to go into standby/sleep mode i get a sharp click sound from my speakers for about a fraction of a second

is it goin to damage my speakers?

I doubt that very much.

---

### Post by echo9 on 2009-09-06
i really appreciate u guys..have finally come to the rescue :) :)
thanks~

@ [Liolikas]("http://ubuntuforums.org/member.php?u=67515")

>  			 		   		 		 		1)  something wrong with nvidia drivers try update etc.

2) you have ntfs-3g installed right?


1> well my nvidia driver is working just fine..nothing seems to be wrong on that part..

2> yup..ntfs-3g was installed by default

am able to browse the windows partitions

also am able to create some new folders and put data into that but when i restart the system..whoosh.. its gone

not able to see the data as well as the new folder both from inside the windows as well from ubuntu :(

@[P4man]("http://ubuntuforums.org/member.php?u=412374")

1> > Do you get any messages ? If you dont, then try this, to make the boot process more verbose, and we can figure out whats going on: in grub, don press enter on the ubuntu line, but press "e" to edit. Then select the third line that looks somehwat like this:

kernel	/boot/vmlinuz-2.6.28-11-generic root=UUID=a438d590-7b75-44eb-8bb6-0765f7c8f82c ro **splash quiet**

Press E again to edit. Remove the the "splash" and "quiet" options at the end. Then press enter to confirm, and B to boot. This will output a lot of text on your screen during the boot process, see what its asking you..

well i generally switch to the verbose mode by pressing alt+f1 to see whats wrong..

and all it stops at is: some image not found..doing normal boot 

2> > Can you browse your windows drive ? Are you sure you are putting those files on the windows drive and not on the ubuntu partition (which windows can't read) ?

Try opening the file manager (nautilus) and open the windows drive from the left menu. If you see folders like "windows" "program files" "users" etc, then its your vista drive. Try making a new folder in there. Do you get any errors?

yes am browsing the right drive(s) and am able to see all the data present..the only thing which bugs me is why i am not able to save any files/folders on ntfs partitions..?

am able to create some new folders and put data into that but when i restart the system..whoosh.. its gone

after restart i am not able to see the data as well as the new folder both from inside the windows as well from ubuntu :(

3>>  	 	 Can you give the exact type of laptop you have, rather than the specs? Also, did you run all updates?

there you go :) ...

i have a compaq presario 6608AU

Specs:

AMD turion 64x2 1.9Ghz
2.5GB DDR2 RAM
nvidia 7150M onboard GPU
nvidia MCP67M chipset
dual boot vista basic 32 bit edition+ubuntu 9.04 32 bit edition
grub v.1.5

broadcom wireless 4311  :( but works classy in ubuntu 9.04 (thanx ubuntu) :popcorn:

---

### Post by P4man on 2009-09-06
> **echo9 said:**
> 
well i generally switch to the verbose mode by pressing alt+f1 to see whats wrong..

and all it stops at is: some image not found..doing normal boot 

Can you be a bit more precise :) ?
You can check the log files after booting by running dmesg
copy/paste the appropriate parts here, or save the entire log by typing
dmesg>log.txt and attach the log here. Id like to see exactly what it prompts you for when you need to press enter to continue.

> am able to create some new folders and put data into that but when i restart the system..whoosh.. its gone

after restart i am not able to see the data as well as the new folder both from inside the windows as well from ubuntu :(


that sounds very bad. Check the drive from within windows, the only thing I can think of is that the ntfs volume got corrupted.

---

### Post by echo9 on 2009-09-06
heres my log file

pastebin URL >

[http://pastebin.com/f810678c](http://pastebin.com/f810678c)

sorry but forum's attahcment method din't worked for me :( way too slow

---

### Post by echo9 on 2009-09-09
actually i am facing the "stopping at boot-up" problem from many days..so i generally switch to verbose mode by pressing alt+f1  to see whats going on inside :D

can anybody..help me out?
would appreciate much~ :)

---

### Post by P4man on 2009-09-09
dont have much time, I quickly glanced at your logfile.. and Ill do a wild guess: go in to your bios and disable the hardware firewall for your nforce network card.

---

### Post by echo9 on 2009-09-10
> **P4man said:**
> dont have much time, I quickly glanced at your logfile.. and Ill do a wild guess: go in to your bios and disable the hardware firewall for your nforce network card.
sorry but theres no option for hardware firewall in my BIOS.. :(

uhh..i would like to ask is the issue of ubuntu hanging during boot up an issue of something related to some disabling a feature through which we get those messages of whats going on..during boot up..?

or is have something to do with user's interference during boot up process? an option which could enable the kernel to not to require user's intervention during boot up sequence??

---

### Post by P4man on 2009-09-10
> **echo9 said:**
> sorry but theres no option for hardware firewall in my BIOS.. :(

Then can you try disabling the onboard network card all together? Just to test.

> uhh..i would like to ask is the issue of ubuntu hanging during boot up an issue of something related to some disabling a feature through which we get those messages of whats going on..during boot up..?

I don't know, Ive never ever seen it (except in the case where a disk needs checking, but then its clearly mentioned).

Now you posted your log, but you still haven't pointed out where (in that log) it hangs ? Whats on the screen when you need to press something to continue. (And are you sure you have to?)

> or is have something to do with user's interference during boot up process? an option which could enable the kernel to not to require user's intervention during boot up sequence??

I dont know if its the kernel (i kinda doubt it), but again, Ive never seen it, so i wouldn't know. For sure its not normal.

---

### Post by echo9 on 2009-09-13
gee thanx for replyin..

ya, i checked it out finally where the boot-up hangs: 

kinit: no resume image found, doing normal boot

this is where it hangs unless i press a key n then if i press it then too it takes much time to get it through this phase.. and finally i have to kee pressing akey (say the return key) to keep up my booting process reach the login page :(

---

### Post by P4man on 2009-09-13
> **echo9 said:**
> gee thanx for replyin..

ya, i checked it out finally where the boot-up hangs: 

kinit: no resume image found, doing normal boot

this is where it hangs unless i press a key n then if i press it then too it takes much time to get it through this phase.. and finally i have to kee pressing akey (say the return key) to keep up my booting process reach the login page :(

The message you get there is normal, its just checking if the system is waking up from a hibernate, it doesn't find a hibernate image to resume from (since you did a shutdown) and therefore, it does a regular boot. thats completely normal.

If you don't press anything, what happens exactly ? Please be patient :p. No other messages on screen ? (still boot with the "splash" and "quiet" removed).

---

### Post by echo9 on 2009-09-14
> **P4man said:**
> The message you get there is normal, its just checking if the system is waking up from a hibernate, it doesn't find a hibernate image to resume from (since you did a shutdown) and therefore, it does a regular boot. thats completely normal.

If you don't press anything, what happens exactly ? Please be patient :p. No other messages on screen ? (still boot with the "splash" and "quiet" removed).
if i don't press anything the boot process does not even move a single line ahead and it keeps stucked at the same line (i checked it by switching to verbose mode by pressing the Alt+F1)

i waited for around 20 minutes..isn't that enogu for the kernel to laod my normal ~nux image..? ;) hehe..

well, may the splash and quiet mode both of them are still mentined in my menu.lst file 

should i tremove them and then test it?? but i want a splash at least :(

---

### Post by P4man on 2009-09-14
> **echo9 said:**
> if i don't press anything the boot process does not even move a single line ahead and it keeps stucked at the same line (i checked it by switching to verbose mode by pressing the Alt+F1)

Well, since my very first post, Im trying to find out exactly what line that is that is needing your input.. what does it say?

---

### Post by echo9 on 2009-09-14
> **P4man said:**
> Well, since my very first post, Im trying to find out exactly what line that is that is needing your input.. what does it say?
don't know.. all it stops at is: 
knit: no resume image found, doing normal boot..

:(

---

### Post by P4man on 2009-09-14
> **echo9 said:**
> don't know.. all it stops at is: 
knit: no resume image found, doing normal boot..

:(

Ok, and then you press a key, and it starts spitting out lines from the kernel and it boots without further intervention, is that correct ?

---

### Post by echo9 on 2009-09-14
hey..i did some googling on this issue and what i think is i should install "[tuxonice]("http://tuxonice.net")" 

will it solve my problem..??

---

### Post by echo9 on 2009-09-14
absolutely correct..but i have to press a key(any key) for many times so generally i keep pressing return till i reach login window :'(

---

### Post by P4man on 2009-09-14
> **echo9 said:**
> hey..i did some googling on this issue and what i think is i should install "[tuxonice]("http://tuxonice.net")" 

will it solve my problem..??

No. Tuxonice is an app to help hibernate (suspend to disk) work. Last guy that I tried helping here tried installing it and ruined his setup. Not that I think the app is to blame, but I fail to see how it relates to what you're having. 
edit: scratch that, messages crossed

---

### Post by P4man on 2009-09-14
> **echo9 said:**
> absolutely correct..but i have to press a key(any key) for many times so generally i keep pressing return till i reach login window :'(

Maybe Im not smartest kid around, but its still not clear to me... Im sorry :(

You have that "normal boot" message, it stalls there, so you hit enter key (several times, you sure one doesnt work?) , until it continues booting.. then I suppose you stop pressing enter.. does it stall again before reaching the login, or not ? If it does, at what lines?  Any line ?

---

### Post by echo9 on 2009-09-14
> **P4man said:**
> No. Tuxonice is an app to help hibernate (suspend to disk) work. Last guy that I tried helping here tried installing it and ruined his setup. Not that I think the app is to blame, but I fail to see how it relates to what you're having. 
edit: scratch that, messages crossed
sorry but i din't got the last line..
"..messages crossed..?"

---

### Post by echo9 on 2009-09-14
> **echo9 said:**
> sorry but i din't got the last line..
"..messages crossed..?"
hehe..for sure guys at ubuntu forum are the smartest of all~ :) i have heard much about this forum..

yes..i have to again press a key because if i don't then the boot up process again it hangs at the next line and keeps hanging until i reach the login window..so a scenario can be:

i have to press a key at every line to reach the login window. if i press a key one time at this line: 

knit: no resume image found, doing normal boot..

then too i have to press a key again to let the process go to the next line..
well its a whole long list of processes i can't remember them all..but they all definitely give me a tinkle that the various system services are being initialized one-by-one

---

### Post by P4man on 2009-09-14
Ok, now its clear :)

(as for the line you didn't understand, ignore it. I had written something there asking to reply to my previous question, but before I had posted it, you had already replied, so i removed the question)

Now, I think its time for some possible solutions. Im pretty sure you're having a compatibility problem with your bios. You can try this; open a terminal, and type
```

gksudo gedit /boot/grub/menu.lst
```

(Im assuming you have normal grub 1, not grub2. If you dont know, then you have grub 1)

find your most recent kernel. It will look something like this:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

with different numbers obviously (thats a very old one). Now add something to the line starting with kernel:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash **acpi=noirq**
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Save, reboot, cross fingers.

---

### Post by echo9 on 2009-09-14
> **P4man said:**
> Ok, now its clear :)

(as for the line you didn't understand, ignore it. I had written something there asking to reply to my previous question, but before I had posted it, you had already replied, so i removed the question)

Now, I think its time for some possible solutions. Im pretty sure you're having a compatibility problem with your bios. You can try this; open a terminal, and type
```

gksudo gedit /boot/grub/menu.lst
```

(Im assuming you have normal grub 1, not grub2. If you dont know, then you have grub 1)

find your most recent kernel. It will look something like this:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

with different numbers obviously (thats a very old one). Now add something to the line starting with kernel:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash **acpi=noirq**
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Save, reboot, cross fingers.
hey~hey.. :D acpi=noirq ??

am i going to disbale my acpi ? will my suspend/hibernate features work?  what will be the known after effects of acpi=noirq 
 parameter?
will do it.. :) but still just asking hehe..

---

### Post by P4man on 2009-09-14
> **echo9 said:**
> hey~hey.. :D acpi=noirq ??

am i going to disbale my acpi ? will my suspend/hibernate features work?  what will be the known after effects of acpi=noirq 
 parameter?
will do it.. :) but still just asking hehe..

No, to disable acpi, you'd need "acpi=off".
Setting noirq only disable interrupt routing feature on ACPI, something you don't really need. You should not lose any real performance or capability on a desktop (or laptop) system. As I understand it, its only somewhat needed in servers with high I/O load and tons of cpu's.

---

### Post by echo9 on 2009-09-15
> **P4man said:**
> No, to disable acpi, you'd need "acpi=off".
Setting noirq only disable interrupt routing feature on ACPI, something you don't really need. You should not lose any real performance or capability on a desktop (or laptop) system. As I understand it, its only somewhat needed in servers with high I/O load and tons of cpu's.
hey..gee thanks for the input :)

and one more thing, i am not able to suspend/hibernate my system 
i searched the forum+googled for it and i think i should use APM instead of ACPI ?

whats the basic difference? and will i be able to solve my problem? 
my laptop's model: Compaq Presario 6608AU

---

### Post by P4man on 2009-09-15
> **echo9 said:**
> hey..gee thanks for the input :)

You're welcome, but is it actually working now?
> 
and one more thing, i am not able to suspend/hibernate my system 
i searched the forum+googled for it and i think i should use APM instead of ACPI ?

whats the basic difference? and will i be able to solve my problem? 
my laptop's model: Compaq Presario 6608AU

What isn't working? Suspending, hibernating or "only" the resuming for one or both ?

Either way, before trying anything else, see if you can't find a more recent BIOS for your machine. Everything points to a particularly crappy bios implementation. Also check your bios for ACPI settings you can change.

Other than that, you could try "uswsusp":
[https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)
for hibernate.

And/or a lot more kernel switches:

[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

---

### Post by echo9 on 2009-09-18
> **P4man said:**
> You're welcome, but is it actually working now?


What isn't working? Suspending, hibernating or "only" the resuming for one or both ?

Either way, before trying anything else, see if you can't find a more recent BIOS for your machine. Everything points to a particularly crappy bios implementation. Also check your bios for ACPI settings you can change.

Other than that, you could try "uswsusp":
[https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)
for hibernate.

And/or a lot more kernel switches:

[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)
sorry for this late reply :(

n am very thankful to you.. my boot up process int's hanging anymore! yipeee! :)

my suspend isn't workin as it should..the computer goes into the standby mode but when i wake it up the light stops blinking the hard rive shows some i/o n then screen goes blank; nothing shows up.

also when hibernating..i get to see some errors (will definitely post them here; they ar related to the same term u told refered to in the above reply: "usb.." this thing shoed up with some code) but the system hibernates after that message output n recovers easily from the hibernate :)

so the final sttand is like this: resume from a standby doesn't works (previously it was not workin!)  hibenates works perfectly but prints some error messages to console before going itno hibernate mode.

---

### Post by echo9 on 2009-10-04
anybody plz help me out~

---

