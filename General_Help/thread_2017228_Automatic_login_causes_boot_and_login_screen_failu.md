---
title: "Automatic login causes boot and login screen failure"
date: 2012-07-04
forum: General Help
---

### Post by 4ebees on 2012-07-04
Hi all,

Very strange problem here.

I have three machines, identical boxes (literally), same motherboards, with one one machine having an Intel video chip while the other two have ATI cards.

All machines:

CPU: Intel(R) Core(TM)2 Duo CPU E7400 @ 2.80GHz

RAM: 2G DDR2 800 MHz

Two machines have the following video card:
Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450]

The third has a stock Intel card.

All have fresh installs of Ubuntu 12.04. All were installed on the same day (long day :))

After creating the admin user as me, I created accounts for each of the kids on their respective machines. I created an automatic login for the youngest and this is what started the problem.

That machine would start to boot, would then drop to a shell and show me that it was frozen at battery check.

After some reading that this was a problem with some Intel cards (and failing to be able to fix it) I reinstalled, didn't select auto login for the child account and all was well with the universe. 

Today, the middle child asked me to change their machine to auto login. When we then went to start the machine we got the same problem as the first machine.

I accessed a shell and changed the user back to non-auto login (for those interested, the actions are posted at the bottom) and when we restarted the machine, all was fine.

The first machine we had the problem on has an Intel card, the second has an ATI card.

I'm curious as to:

1. Does anyone have a clue as to why this would happen?
2. Has anyone else had the same problem?

I've checked the forums but not found a similar issue. Most people are writing that they've had problems getting auto login to work but none appear to relate to booting to the login screen.


***********
[U][B]Recovering from problem
[/B][/U]

Use alt-F2 to access a shell.

Login

Type

[B]sudo mount -o remount,rw /
[/B]
to mount the file system

([http://askubuntu.com/questions/120153/how-to-change-read-only-file-at-root-prompt](http://askubuntu.com/questions/120153/how-to-change-read-only-file-at-root-prompt))

Then do the following:

Change directory to the **gdm** directory

**cd /etc/gdm/**

Type 

[B]sudo cp custom.conf custom.conf.orig
[/B]

This saves a copy in case you wreck the one you're working on :)

Then type

[B]sudo vi /etc/gdm/custom.conf
[/B]

This allows you to edit the custom.conf file 

Change

**AutomaticLoginEnable=True **

to  

[B]AutomaticLoginEnable=False
[/B]

If you're not familiar with Vi you need to press the **i** key  to modify the text.

When finished hit **Esc**. This will cease your editing. You then type the following:

**:w**

which writes the changes 

Then type

[B]:q
[/B]
Which quits the process.

Then type

[B]sudo reboot
[/B]

and you should be good to go at the login

([http://www.unixmen.com/how-do-i-disable-auto-login-in-ubuntu/](http://www.unixmen.com/how-do-i-disable-auto-login-in-ubuntu/))

---

### Post by dino99 on 2012-07-05
why are you using gdm, as ubuntu now use lightdm instead (with unity-greeter) ?

---

### Post by dino99 on 2012-07-05
oops

---

### Post by 4ebees on 2012-07-05
> **dino99 said:**
> why are you using gdm, as ubuntu now use lightdm instead (with unity-greeter) ?

No particular reason.

---

### Post by apollo777 on 2012-10-18
I am experiencing the same issue.

I have the PC set up to run mythTV and my wife and kids will veto the whole setup if there's a login involved. They want to be able to turn the TV on, pick up the remote, and start watching. If they need to login after any reboot, that's not going to fly.

Your description describes my situation exactly.

Can anyone offer a solution. Please avoid irrelevant questions like, "why are you using gdm, as ubuntu now use lightdm instead (with unity-greeter) ?" ... although, maybe I'll try lightdm to see if it makes any difference (doubtful).

Apollo

---

### Post by apollo777 on 2012-10-18
Well, I guess I'll eat my hat now. Lightdm worked. That's the solution.

Please keep the irrelevant questions coming.

Apollo

---

