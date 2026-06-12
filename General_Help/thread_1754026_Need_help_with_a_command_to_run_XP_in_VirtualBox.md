---
title: "Need help with a command to run XP in VirtualBox"
date: 2011-05-09
forum: General Help
---

### Post by gh0stpirate on 2011-05-09
Hey guys, been reading/messing around all day trying to get this to work... simply, i CAN'T figure this out. I apologize that i need this SOOO baby fed to me, but heres the deal, i need a this command ran at startup. AS ROOT.

"$sudo virtualbox --startvm xp"

this starts a vm of xp that has my magic jack perfectly config'd

no matter what i try, it will NOT work. running as non-root isn't an option either, as i NEED USB support.

im on ubuntu 10.10

i really need line by line command-prompt goodness xD im usually awesome at google-foo, but this one really has me vexed. :( thanks in advance guys.

---

### Post by 3 frags left on 2011-05-09
I would not like to be rude but... your title could be more explanatory. It also would be hard to know what would happen without knowing what kind of error is it displaying; could you post it here for us?

---

### Post by 3 frags left on 2011-05-09
Oh, I already realizied what it is.

It may sound odd, but the VirtualBox saved VMs are [COLOR="Red"]per user[/COLOR], which means that the user *root* can't visualize your VM named xp because it was set at another user profile. If you type *virtualbox* without *sudo*, you'll load it easily, as you previously did. So, you have two solutions for this issue:

1. Install VirtualBox Guest Additions, which allows you to resize the window easily (with Windows adjusting its resolution along), transit your mouse from both screens without having to press the escape key, and most important, detect your USB drives and other devices. It's pretty easy, all you need to do is on the window of your opened VM, get to the Devices menu and select *Install Guest Additions* option. Reboot your VM and there you go.

2. Create a new VM configuration, but selecting the same Virtual Disk. I don't know if this will be possible, however, but it's worth a shot, although doing the method 1 is much more practical.

---

### Post by gh0stpirate on 2011-05-09
Hey, sorry i was out for a walk to take in the sunshine ;) i think you miss-understand my problem. it doesnt matter what user executes the VM's, (you can just chown the user and group easily) i experimented with that quite a bit. all of the VM end executes flawlessly. i just need to run:

"virtualbox --startvm xp" as ROOT

it needs to be started as root so i can get all the juicy extras (proper usb support etc) so again, is there anyway this can be done? (i know it can but no idea how) if it didn't require root privs. this would be a breeze, but alas, im not that lucky xD. im surprised the "start-up applications" under system wouldnt have a checkbox to run as root with supplied credientials.... hmmm

---

### Post by collisionystm on 2011-05-09
> **gh0stpirate said:**
> Hey guys, been reading/messing around all day trying to get this to work... simply, i CAN'T figure this out. I apologize that i need this SOOO baby fed to me, but heres the deal, i need a this command ran at startup. AS ROOT.

"$sudo virtualbox --startvm xp"

this starts a vm of xp that has my magic jack perfectly config'd

no matter what i try, it will NOT work. running as non-root isn't an option either, as i NEED USB support.

im on ubuntu 10.10

i really need line by line command-prompt goodness xD im usually awesome at google-foo, but this one really has me vexed. :( thanks in advance guys.


Dude....

```
VBoxManage startvm xp
```your welcome!

And it does not need to be started as root. Add yourself to the vbox users group

```
usermod -G vboxusers -a username
```

Reboot your computer

---

### Post by 3 frags left on 2011-05-09
Digging up a little in the old archives, I found this:
[http://ubuntuforums.org/showthread.php?t=642394](http://ubuntuforums.org/showthread.php?t=642394)

Give it a shot!

---

### Post by doas777 on 2011-05-09
> **gh0stpirate said:**
> Hey, sorry i was out for a walk to take in the sunshine ;) i think you miss-understand my problem. it doesnt matter what user executes the VM's, (you can just chown the user and group easily) i experimented with that quite a bit. all of the VM end executes flawlessly. i just need to run:

"virtualbox --startvm xp" as ROOT

it needs to be started as root so i can get all the juicy extras (proper usb support etc) so again, is there anyway this can be done? (i know it can but no idea how) if it didn't require root privs. this would be a breeze, but alas, im not that lucky xD. im surprised the "start-up applications" under system wouldnt have a checkbox to run as root with supplied credientials.... hmmm
if it did, since that applet does not require root to add new apps, would be a major vulnerability for teh sudo system.

I do add apps and scrpts to startup applications to run with 'gksu' so they prompt me for a password. would that be acceptable? just replace sudo with gksu.

---

### Post by gh0stpirate on 2011-05-09
> **collisionystm said:**
> Dude....

```
VBoxManage startvm xp
```your welcome!

And it does not need to be started as root. Add yourself to the vbox users group

```
usermod -G vboxusers -a username
```

Reboot your computer

](*,) that does NOT have super user privs, and is just a different command to do what im already doing. thank you for your input though man! (just tried to MAKE SURE) and the entire issue over and over again....

it needs to be executed by ROOT at start-up not $USER.

---

### Post by collisionystm on 2011-05-09
..... you sir need to do a little more reading. You DO NOT need root to use usb or other 'juicy' features on virtualbox. All you need to do is add yourself to vboxusers.

But, you can travel your own path. I only offered wisdom from someone who has done this 10,000 times. Have a good day

---

### Post by gh0stpirate on 2011-05-09
thank you very much for that, i added myself.

.....

..
 and it still didn't work xD (love your avatar btw) 
why is it such an insane question to people that i just want to run it as root for my own purposes? why so much resistance!

---

### Post by aysiu on 2011-05-09
> **gh0stpirate said:**
> why is it such an insane question to people that i just want to run it as root for my own purposes? why so much resistance! Because you already stated in the first post that running as root doesn't work for you, and because others who have responded have no problems running it without root.

---

### Post by gh0stpirate on 2011-05-09
im saying running as root is the ONLY way it works xD

---

### Post by aysiu on 2011-05-09
> **gh0stpirate said:**
> im saying running as root is the ONLY way it works xD
Probably you ran it with *sudo* once and then accidentally changed ownership of a user configuration file so it can't be run as user any more.

Change ownership back: ```
sudo chown -R gh0stpirate:gh0stpirate /home/gh0stpirate
``` Then add yourself to the right group, install the Guest Additions and never run it with *sudo* again.

---

### Post by gh0stpirate on 2011-05-09
> **aysiu said:**
> Probably you ran it with *sudo* once and then accidentally changed ownership of a user configuration file so it can't be run as user any more.

Change ownership back: ```
sudo chown -R gh0stpirate:gh0stpirate /home/gh0stpirate
``` Then add yourself to the right group, install the Guest Additions and never run it with *sudo* again.

thank you for your untiring patience. i think in order for me to REALLY cut the fluff from this issue to get to the meat of it. let me try and re-word this as a challenge or something.

run this command **_as root_** when you start your computer or log in:

virtualbox --startvm xp

********
that is all.

my vm's are perfectly fine in everyway, i understand chown, groups, ownership etc. hence why i can play with my vms under any user. its simple chown commands. just ignore anything having to do with vm configurations etc... forget i even mentioned them xD

i just need the command above to be ran by ROOT on BOOT :P

there is nothing incorrect in my vbox configs whatsoever. it acts like this due to the nature of this magic jack, however, when its executed as root, no problems. so why bother with everything else? i just want to run that command as root, on boot. :confused:

***
another quicky example, say i wanted to run Sudoku as root (for whatever reason) once i log in or start my computer. i.e// i turn my computer on, log in, and sudoku is open automatically, with root privs.


**** same thing, just instead of sudoku, substitude, THAT above command :)

---

### Post by aysiu on 2011-05-09
I wouldn't recommend running Sudoku as root either. The problem isn't "How can I run this as root?" but "How can I run this?" Running programs as root that don't need root access is not a good idea.

If you check out this thread ([Using magicJack on Linux](http://www.magicjacksupport.com/magicjack-on-virtualbox-t7984.html) you'll see there's no references to having to run it as root in order to get it to work.

What I'm saying is if you have to run it as root to get it to work, then you have to fix that problem first. If you really do understand *chown* and all that, I shouldn't have to tell you this twice.

---

### Post by gh0stpirate on 2011-05-09
i give up.


If i want to make my computer unsafe, run my HDD without a cover on it, balance my monitor on toothpicks above an egg, its my business. simple question, 0 direct answers, i know what i ask is very possible. who cares if my vbox install is a "giant security risk"? is it on your network? i understand the risks, and have weighed them in favour for this method. I just want to know how to run a damn command as root when i log in. Thats all. This is insane. If fedora had synaptic..... (haven't checked in a while) id be off this OS. Community has NEVER been the same since anything after 7.10

---

### Post by JKyleOKC on 2011-05-09
> **gh0stpirate said:**
> my vm's are perfectly fine in everyway, i understand chown, groups, ownership etc. hence why i can play with my vms under any user. its simple chown commands. just ignore anything having to do with vm configurations etc... forget i even mentioned them xD

i just need the command above to be ran by ROOT on BOOTPut the command in your /etc/rc.local file, just above the line that says "exit 0" and you'll have what you're asking for.

However it still won't work, because your VMs are in your home directory, not that of root. They are located in one of two directories: .VirtualBox for those created before vbox version 4, and a non-hidden subdirectory for those created by version 4. It might work if you copy the entire vbox directory set from your home directory over to that of root, however. If you do so, you may have to chown all of the files as well -- but it's quite possible that there may be some integrity checks in the VM's xml file to detect such changes and keep them from working.

EDIT: Incidentally, your lack of security DOES affect my network. Have you ever heard of botnets? Contrary to popular opinion, Linux systems CAN be invaded and pwned; the very first worm was written on a Unix system! And as others have told you, it's not necessary to run as root. I have five VMs on this box, all with full USB support, and all running as my own user ID. Another box has a VM that handles my Email, which starts automatically at boot time and is saved before shutdown, again using my ID, not root. It **can** be done.

---

