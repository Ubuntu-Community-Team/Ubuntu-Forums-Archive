---
title: "installing lubuntu on top of ubuntu causes problems in unity"
date: 2011-09-18
forum: General Help
---

### Post by doogiekd on 2011-09-18
i followed the instructions on the lubuntu wiki for installing lubuntu on top of ubuntu. after doing so, the following errors occurred in unity:

more information regarding this problem:

1. selecting anything but lubuntu in the session menu on the login screen always gives the following message:

"xsession: unsupported number of arguments (2) falling back to default session.

2. regardless if you pick unity, unity 2d, or ubuntu classic from the session menu on the login screen, the above message appears (clicking "okay" makes it dissapear - but unity ALWAYS starts, even if you picked ubuntu classic.

3. in unity, the mouse left button does not work.

4. in unity, the unity menu bar does not autohide and is always on top.

5. in unity, when starting synaptic, the following message appears:
"a malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus. try again.

the system usually freezes at this point.

6. when attempting to correct the menu autohide problem in config settings manager, clicking the plugins option displays a message that plugins are in conflict and asks if you want to correct.

i have always clicked "no" - and would like clarification if i should resolve those plugin issues by clicking "yes."

it appears that gnome (unity) is conflicting with lxde (lubuntu) - although i dont know why this happening because selecting either session from the login screen should only start the appropriate desktop mgr.

i installed lubuntu from the synaptic in unity because there are some times when i want to run things in lowest memory possible because i have an old computer. (512mb compaq i386). I really was hoping that i could choose between unity (or more preferably gnome classic) or lubuntu from the login screen. also searches on the forums indicate many people would like to install lubuntu on top of ubuntu to try lubuntu out before making the switch permanently. 

any suggestions?

---

### Post by amjjawad on 2011-09-20
> **doogiekd said:**
> i installed lubuntu from the synaptic in unity because there are some times when i want to run things in lowest memory possible because i have an old computer. [COLOR=Red]**(512mb compaq i386)**[/COLOR]. I really was hoping that i could choose between unity (or more preferably gnome classic) or lubuntu from the login screen. also searches on the forums indicate many people would like to install lubuntu on top of ubuntu to try lubuntu out before making the switch permanently. 

any suggestions?

Hi there,

I admit there is a little mess over here but that should **not** be a problem.
First thing first, could you please confirm that the machine you are running Ubuntu 11.04 on and then you installed Lubuntu-Desktop from Synaptic is the same one that you mentioned? 
If yes, then I recommend NOT to use Unity on such machine. 

Lubuntu 11.04 is your best choice with that machine, period.
Better to do clean installation. If you need any further info, please do let me know and I'll be more than glad to help :)

---

### Post by doogiekd on 2011-09-26
hi, thanks for your reply.

yes, the same machine mentioned has ubuntu 11.04 with lubuntu installed from synaptic.

(compaq presario 5000 512mb ram)

i was was really hoping to go back and forth between ubuntu and lubuntu - but installing lubuntu from synaptic has caused the above problems in unity.

ubuntu did work before installing lubuntu from synaptic, it was slow, but there were no problems. i could live with that, as long as i have the option to go back and forth between lubuntu & ubuntu. these problems also make it difficult for people to try out lubuntu without the need for a clean install. the lubuntu wiki even says you can try lubunu on ubuntu by installing lubuntu from synaptic. 

k.

---

### Post by amjjawad on 2011-09-27
> **doogiekd said:**
> hi, thanks for your reply.


Hi,
You most welcome :)


> yes, the same machine mentioned has ubuntu 11.04 with lubuntu installed from synaptic.

(compaq presario 5000 512mb ram)

Ok, thanks for confirming :)


> i was was really hoping to go back and forth between ubuntu and lubuntu - but installing lubuntu from synaptic has caused the above problems in unity.
There are many other ways to do that but apparently, you chose the easiest way but unfortunately, it caused lots of problems.

Could you please try to remove "lubuntu-desktop" form Synaptic (Right Click and Choose Completely Remove) and report back? 
Once you remove it, I suggest to reboot your machine and login again.
Not sure if that will fix the issue but let's try to fix it with whatever possible :)


> these problems also make it difficult for people to try out lubuntu without the need for a clean install. the lubuntu wiki even says you can try lubunu on ubuntu by installing lubuntu from synaptic. 

You are right specially if a new comer is trying Lubuntu for the first time and did the same that you did.

I might update the wiki but I'll first talk to The Lubuntu Team about that.

Personally, I have my own way to try new things. LiveCD or LiveUSB, install on VirtualBox, install on external HDD, install on USB Drive or install it on a Test PC.


Will wait for your reply :)

Thank you!

---

### Post by doogiekd on 2011-09-27
hi, 

per your instructions, i completely removed lubuntu along with all packages marked lubuntu using synaptic.

the problems continue:

1. the login screen did not return to the normal gnome login screen. the login screen is blue and looks very much like the lubuntu login screen, although it does not say lubuntu. instead, it just says "Login:"

2. Entering unity 2d after login screen a black screen appears with a white box that says:

"xsession: unsuported number of arguments (2) falling back to default session."

3. the same message appears when selecting ubuntu classic from the login screen, the above message appears and (instead of ubuntu classic) the unity 2d session is loaded.

4. the unity 2d menu panel (on the left) does not autohide when another app is started. the unity menu panel remains on top of whatever app is started.

5. everything else seems to work fine.

this is a very strange problem.

i am really hoping (praying actually), that i dont have to reinstall ubuntu to fix this. i would really like to have the ubuntu back before i installed lubuntu on top of it.

any suggestions to how to fix this?

i was also thinking i could reinstall ubuntu using the "keep current configuration" option on the live cd.perhaps this would correct the above problems.

if i can fix the ubuntu machine, i was thinking about installing lubuntu next to ubuntu on a separate partition.

thanks for your help, 

k.

ps. yes, i would definitely change the wiki and indicate that lubuntu should not be installed on top of ubuntu from synaptic until these problems are corrected.

---

### Post by doogiekd on 2011-09-27
other example of a user with similar problem:

[http://ubuntuforums.org/showthread.php?p=11256463](http://ubuntuforums.org/showthread.php?p=11256463)

---

### Post by amjjawad on 2011-09-27
I'm not a fan of Unity nor an expert but I hope these links will be helpful:

[http://askubuntu.com/questions/31849/how-do-i-restart-unity](http://askubuntu.com/questions/31849/how-do-i-restart-unity)

[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal)



Yes, better to learn how to fix things instead of re-install :)

---

### Post by amjjawad on 2011-09-27
> **doogiekd said:**
> other example of a user with similar problem:

[http://ubuntuforums.org/showthread.php?p=11256463](http://ubuntuforums.org/showthread.php?p=11256463)

Thanks a lot for reporting this issue. I got 3 cases so far.
I already sent to Lubuntu Team and hope we can work to fix that.

Will keep you posted :)

---

### Post by phillw on 2011-09-27
Hi,

the current recommended way of adding lubuntu to an existing installation is via [upgrade to Lubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu). That section also includes additional notes on having 2 sets of apps available and tidying up things.

With the new build of 11.10 system, this will quite likely change as we're depreciating the 'no-recommeds install' from 11.10, but the instructions do work for all current releases.

Regards,

Phill.

---

### Post by doogiekd on 2011-09-28
well, i've tried every suggestion mentioned above and the same problem continues.

anyone have any more suggestions for getting ubuntu back after deleting lubuntu?

---

### Post by amjjawad on 2011-09-28
> **doogiekd said:**
> well, i've tried every suggestion mentioned above and the same problem continues.

anyone have any more suggestions for getting ubuntu back after deleting lubuntu?

I do have an Ubuntu 11.04 installed and don't mind to mess with it. I could help you with that. However, I haven't experienced such issue before so you need to be patient, otherwise someone else hopefully needs to step-in and help :)

Sorry that all the previous suggestions didn't fix the issue.

Don't give up :)

---

### Post by doogiekd on 2011-10-06
well, i decided to redo my computer and reinstalled with lubuntu only. 

it is awesome.

marking this as solved with recommendation that lubuntu and ubuntu not be installed together - at least for now.

---

### Post by amjjawad on 2011-10-06
> **doogiekd said:**
> well, i decided to redo my computer and reinstalled with lubuntu only. 

it is awesome.


I was so busy and couldn't try that as promised, sorry.

Well, anyway, good job and congratulation for setting it up :)


> marking this as solved with recommendation that lubuntu and ubuntu not be installed together - **at least for now**.
And until otherwise, I guess you do have a point :)

---

