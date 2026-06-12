---
title: "Ubuntu 8.04.4 LTS won't boot"
date: 2011-09-13
forum: General Help
---

### Post by Michael4 on 2011-09-13
[CENTER]***Intro***
[/CENTER]
 Hello dear ubuntu forum users. I am Michael, I am a complete newbie in  this world and am not very familiar with the usual terms, so I might be a  little slow, and might be giving you a lot of useless information.

Yesterday I discovered I could not boot into kubuntu and since then I've  been searching the web for information. As a newbie I am not very  comfortable by changing stuff, as such I have far from followed every  suggestion I found, since the threads I found were similar to my  problem, but I did not if they were sufficient identical.

Therefore, I have decided to write here.

[CENTER]***Info***
[/CENTER]
 I have dual boot windows xp and kubuntu. I believe 108 gb for windows and 12 gb for kubuntu.
I have set kubuntu to what is usually booted into, but there's 3 seconds where I can choose.
If kubuntu is selected, a 10 seconds count down begins, which will boot into kubuntu unless escape is pressed.
If I press escape, I get to choose between:

[LIST=1]
[*]Ubuntu 8.04.4 LTS kernel 2.6.24-28 generic
[*]Ubuntu 8.04.4 LTS kernel 2.6.24-28 generic (recovery mode)
[*]Ubuntu 8.04.4 LTS kernel 2.6.24-19 generic
[*]Ubuntu 8.04.4 LTS kernel 2.6.24-19 generic (recovery mode)
[*]Ubuntu 8.04.4 LTS memtest+
[/LIST]
 Windows xp [if pressed, this will just bring me back to the place where I choose among the two options, kubuntu and windows xp].

I have had Kubuntu for a long time, and it's worked without problems  until yesterday, though it was yesterday I found out about this problem,  I am not familiar with how long it has been there. Though I'm confident  that at most a week could have passed without me finding out about the  booting problem.

I installed kubuntu using a cd, which I cannot find.

The problem occurs when I choose kubuntu, and either let the timer run  out, in which case it chooses Ubuntu 8.04.4 LTS kernel 2.6.24-28  generic, if I press escape and choose this option myself and finally if I  choose Ubuntu 8.04.4 LTS kernel 2.6.24-28 generic (recovery mode).

Ubuntu 8.04.4 LTS kernel 2.6.24-19 generic seems to work fine however.

When I boot into Ubuntu 8.04.4 LTS kernel 2.6.24-28 generic, the  computer only get to the point where it writes [linux-initrd  @0x1f823000, 0x7ccd3b bytes]. Nothing follows from this line and I've  tried to wait it out, without success. Further more everything freezes  and ctrl + alt + del, ctrl + alt + f2, ctrl + alt + backspace, alt +  sysrq + r (followed by the previous three commands) and finally alt +  sysrq + r + e + i + s + u + b doesn't reboot the machine. [All these  commands did I find yesterday and I've only tried them today].

I've tried to run something called chkdsk /r in windows xp, which took  quite a lot of time, but didn't change anything. Likewise I've tried to  run system recovery, but despite having given maximum memory space for  this process, I could only choose between 12/09-11 and 11/09-11. I  recovered to 11/09-11, but it didn't help.

The only unusual process I can think of, which have taken place in the  period of the last week, where I suspect the problem occoured, was a  system clean up done by windows xp, due to lack of space. This happened  on 11/09-11..

Through searching on the web, I found the following suggestions:
Defragment in Win XP - I did this a couple of months ago.
Run chkdsk /r - I did this without success.
In boot\grub\menu.lst append to every line which begins with kernel  "acpi=off" - I haven't done this, as I'm not very comfortable doing so.  Though if it's necessary to change files, should I just use notepad to  do so, eventhough it's not a txt file?

Any help will be appreciated! Thank you. Have a nice day.

---

### Post by searchfgold6789 on 2011-09-13
I can help you by saying this: Windows XP has nothing to do with linux. Whatever you do in windows XP will have no effect whatsoever on the linux side of your computer because XP cannot even recognise the part of your hard disk that linux is installed on. However there are two exceptions to this rule:

[LIST=1]
[*]There are utilities out there for Windows XP that can delete the partition on your hard disk that linux is installed on.
[*]If you run "fixboot", "fixmbr", or some other commands from the recovery console, those will delete or mess up your boot menu and be unable to access linux.
[/LIST]
So, watch out for that.
Also, all the different entries you have in the boot menu for linux boot to the *same* system with exactly the same files, documents, and settings. The only difference between them is the kernel that they load, which you can probably think of as being the "core of the system", so which one you choose does not matter much as long as it works.
Another thing: the current version of Ubuntu that you have installed is 8.04, which means that it was released in April (04) of 2008. A new version of Ubuntu comes out every 6 months and you can continue to receive updates for it until the next version comes out, except for Long-Term Support releases (you have one) which will last for 2 years until they "expire" and the ethernet cable leading to the website where the updates for software can be found is unplugged. ([http://xkcd.com/908/](http://xkcd.com/908/)) The latest version of Ubuntu is 11.04, and 11.10 is about to be released in a month and a half. I highly recommend booting from the kernel selection that works and following the official instructions [here]("https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04") to upgrade to newer releases one by one until you reach the latest version, which I can say is the best and mot stable version yet. You can also go to kubuntu.org to download the latest release to a CD.
Good luck,
 - search

---

