---
title: "Error on disk where /home is lcated"
date: 2010-04-29
forum: General Help
---

### Post by chisle on 2010-04-29
i have my /home folder located on a seperate HDD than my boot folder and the rest of the OS. Lately i been getting an errror screen when i boot up. is says some errors where found on my disk where my /home folder is located. then from there i am givwen the option to hit I to ignore, S to skip or M to manually mess with it. the only way for me to get around this is usually just to a hard restart and it boots up fine. but i dont understand what errors are being found on the HDD so i can render this situation.

---

### Post by chisle on 2010-04-29
Someone might know better than i do, but i think the problem is when i do a cold boot. My OS boot files are running on a SSD, while my /home is running on a HDD. and therefore when it goes to boot the OS, the HDD hasnt gotten the disk spinning at full speed yet. and therefore it finds no /home folder and then reports the problem. Thats why when i restart the computer, since the HDD is still spinning it starts up fine. The only thing i dont get is when i first built this computer, about two weeks ago this wasnt happening, does that mean the HDD i got is already starting to show some slowing down from when i first got it? Does this hypothesis make sense or am i completely a noob?

---

### Post by chisle on 2010-04-29
bump anyone?

---

### Post by dino99 on 2010-04-29
call a console with:

alt+F2 then run: sudo apt-get install -f && sudo dpkg --configure -a

(validate with "enter")

---

### Post by chisle on 2010-04-29
ok i did that and then nothing happened, the terminal just closes. Is that all thats suppose to happen?

---

### Post by chisle on 2010-04-29
that didnt seem to work, i turned on my computer when i got home and the same thing. the first start up it gives me the screen which says errors  while trying to locate /home on the disk, then i restart and it boots fine. any ideas?

---

### Post by chisle on 2010-04-30
any other ideas appreciated, only other option i can think of is a fresh install, but really want to do this as a last resort.

---

### Post by mechro on 2010-04-30
> **chisle said:**
> My OS boot files are running on a SSD, while my /home is running on a HDD. and therefore when it goes to boot the OS, the HDD hasnt gotten the disk spinning at full speed yet. and therefore it finds no /home folder and then reports the problem. Thats why when i restart the computer, since the HDD is still spinning it starts up fine. 

I don't know if it would help but you could try enabling/increasing the Grub Timeout in **/etc/default/grub**. Run **sudo update-grub** after editing this file.

---

### Post by chisle on 2010-04-30
Assuming i am correct as to why it does that, that may work. will try and post results. thanks

---

### Post by mechro on 2010-04-30
> **chisle said:**
> Assuming i am correct as to why it does that, that may work. will try and post results. thanks

I'm assuming too! :D

---

### Post by P4man on 2010-04-30
> **chisle said:**
> Someone might know better than i do, but i think the problem is when i do a cold boot. My OS boot files are running on a SSD, while my /home is running on a HDD. and therefore when it goes to boot the OS, **the HDD hasnt gotten the disk spinning at full speed yet**. and therefore it finds no /home folder and then reports the problem. Thats why when i restart the computer, 

this sounds imminently reasonable to me. I know how to add a parameter to have grub wait a few seconds before mounting the root partition, but I cant really find how to do that for any other partition. Ill keep looking, but maybe someone else knows?

---

### Post by chisle on 2010-04-30
Unfortunately that was a no go. Did not work so maybe i was wrong. I attached some pics to see if that helps at all. the second screen comes up when i hit esc. i can toggle back and forth from the graphical screen to the text based.

---

### Post by P4man on 2010-04-30
as a test/workaround, can you try setting your bios so it boots from the hdd first? Since its not bootable ( I assume) it will then proceed to boot from the ssd, but it might have "woken" the hdd by just trying to boot from it.

---

### Post by chisle on 2010-04-30
Not able to set it up like that. my bios only allows for the first boot device to be a hard drive, and the second boot device an optical drive. When i set the HDD as my boot device it just goes to a black screen and i am unable to do anything from there and forces a restart. :(

---

### Post by P4man on 2010-04-30
You could install grub on the hdd perhaps?

---

### Post by chisle on 2010-04-30
i am at a loss, it does say about trying to run: e2fsck -b 8193 in the text screen

---

### Post by P4man on 2010-04-30
just to be clear, if you do a warm reboot, everything is ok? it may check your filesystem because you didnt shut it down nicely, but its not like its actually a hdd problem other than it probably not spinning up fast enough with a cold boot?

---

### Post by chisle on 2010-04-30
i dont know, it has been a little hit and miss. everytime from a cold boot it does it for sure, but then when a do a restart sometimes it will boot up normally and others it goes back to that screen. but after a few restarts i am always able to somehow get it booted up fine. it varies to how many times i have to restart it though.

---

### Post by chisle on 2010-04-30
well i have to head into work for a couple hours, be back later. if you come up with anything else let me know. thnx

---

### Post by P4man on 2010-04-30
well I still think your own analysis is the most probable, and I would try curing it by installing grub on the hdd and setting the bios to boot from it. 

But it wouldnt be a bad idea to boot a livecd or stick and run disk utility in system > administration and test the drive for errors and check the smart status.

also, if you do have to reboot, dont hit the reset switch but use reisub:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

---

### Post by chisle on 2010-04-30
So i did a complete reinstall hoping to fix everything... unfortunately it was not so. i restarted my computer probably about 5 times after i had the reinstallation done, and one of those times i still got screen that has been haunting me. what is really disappointing is that i just built this computer maybe three weeks ago. and the other thing is i never even see thr grub menu in the begining when i start my computer, even if i put the grub timeout to 30 seconds+, so i dont know what that is about either

---

### Post by mechro on 2010-05-01
If you hold down the Shift key when booting the Grub menu should appear... This is the Hidden-Timeout setting rather than the Timeout setting in /default/grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by spoon_ on 2010-05-01
Hey did you install the 2.6.33 kernel by any chance? I just installed lucid on an SSD, and I decided to install the 2.6.33 kernel for TRIM support. With it I got the exact same errors you're describing. The 2.6.32 kernel works fine though.

In my case, both / and /home are on the SSD, but some other storage partitions are on an HD. The HD partitions are the ones it complains about.

---

### Post by chisle on 2010-05-01
> **spoon_ said:**
> Hey did you install the 2.6.33 kernel by any chance? I just installed lucid on an SSD, and I decided to install the 2.6.33 kernel for TRIM support. With it I got the exact same errors you're describing. The 2.6.32 kernel works fine though.

In my case, both / and /home are on the SSD, but some other storage partitions are on an HD. The HD partitions are the ones it complains about.

Nope installed kernel 2.6.32-21 :(, but yea it is the partition on my HDD that it gets fussy with.

---

### Post by P4man on 2010-05-01
setting a grub time out may not help if nothing is querying the disk, it wont spin up.

try this instead. Go to a grub shell (press c in grub menu) and run some commands there:

```
ls
``` 

shows all drives

then have it access your harddrive by entering:

```
ls (hd1,2)
```

replace 1 with the harddisk drive number and 2 with the partition number (remember grub stats counting at zero)

The idea here is to make the drive spin up. Once that is done, press escape and try booting. If that works without error, we have the cause, and the solution wont be far.

---

### Post by chisle on 2010-05-01
> **P4man said:**
> setting a grub time out may not help if nothing is querying the disk, it wont spin up.

try this instead. Go to a grub shell (press c in grub menu) and run some commands there:

```
ls
``` 

shows all drives

then have it access your harddrive by entering:

```
ls (hd1,2)
```

replace 1 with the harddisk drive number and 2 with the partition number (remember grub stats counting at zero)

The idea here is to make the drive spin up. Once that is done, press escape and try booting. If that works without error, we have the cause, and the solution wont be far.

This is probably a a huge noob question but how do i get to the grub shell? and if the partition that /home is on is sdb6 would i enter it as (hd2,6)? also is that a "one" or an "ell" in 1s

---

### Post by chisle on 2010-05-01
ok ignore last post. i held down shift while booting, this got me into grub, and then i hit "c" to get into command line. i hit ls and it showed me all available partitions and hd's. i then hit ls (hd1,6) i am pretty sure that is the /home folder partition. below are pictures. the one thing i didn't understand though is it recognizes it as ext 2 but i formatted everything in ext 4.

---

### Post by chisle on 2010-05-01
rebooted 5 times. one time from a cold start. doing the above mentioned method with the grub shell. saddly enough, it was to no prevail. infact the cold boot was the only one, minus the last restart that booted with no problems. back to square one i suppose. ubnless i am wrong about the partition being (hd1,6) of course.

---

### Post by P4man on 2010-05-02
No you did it right. The actual partition doesnt even matter as long as its on the correct drive, the drive must spin up. Grub calls it ext2, because it mounts it as ext2, it doesnt know ext3/4 (but doesnt need to, as ext is foreward and backward compatible)

I think this is where you file a bug report on launchpad.

One last question though, this is not by any chance a WD caviar green hardddrive?

---

### Post by chisle on 2010-05-02
> **P4man said:**
> No you did it right. The actual partition doesnt even matter as long as its on the correct drive, the drive must spin up. Grub calls it ext2, because it mounts it as ext2, it doesnt know ext3/4 (but doesnt need to, as ext is foreward and backward compatible)

I think this is where you file a bug report on launchpad.

One last question though, this is not by any chance a WD caviar green hardddrive?

It is a  500Gb WD caviar blue hdd. why do you ask?

---

### Post by P4man on 2010-05-02
> **chisle said:**
> It is a  500Gb WD caviar blue hdd. why do you ask?

Because I recall reading of a similar issue with WD caviar green (that supposedly saves energy, and I guess by sleeping more than other drives?) and i googled on it and remember reading about a firmware issue with those drives. Certain revisions had that problems, others did not. Just going by vague memory here.

---

### Post by P4man on 2010-05-02
cant find that particular link anymore, but you may want to read through these:

[http://chbits.blogspot.com/2009/07/fixing-wd-gps-drives-with-wdtler-and.html](http://chbits.blogspot.com/2009/07/fixing-wd-gps-drives-with-wdtler-and.html)
[http://ubuntuforums.org/showthread.php?t=1297342](http://ubuntuforums.org/showthread.php?t=1297342)

---

