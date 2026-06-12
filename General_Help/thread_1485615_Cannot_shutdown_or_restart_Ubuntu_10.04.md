---
title: "Cannot shutdown or restart Ubuntu 10.04"
date: 2010-05-17
forum: General Help
---

### Post by blakdogg on 2010-05-17
Hi

I have a recently new, less than 2 weeks old, Ubuntu 10.04 LTS installl. It is a clean install since the prior install of 10.04 LTS decided it would no longer allow me to login.

My problem is that I cannot shutdown or restart my machine. And I have no idea why it happened.

Has anyone experienced a similar problem? Does anyone know where I should start looking?

Thanks

---

### Post by CountMeIn on 2010-06-01
Hi,

Lots of people with problem like this inc. me.

I noticed this problem happened whenever I started Ubuntu 10.04 and had problems with mounting USM sticks, partitions or even CDs. I would get 'permission denied' . When that happened, I couldn't shutdown or restart from the GUI - it just brought me back to the login screen. I've found that this bug has been reported, but there is no solution yet:

[https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139](https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139)

hope that helps.

---

### Post by 98cwitr on 2010-06-01
i concur...APTonCD did not work right when I went to 10.04. Thankfully I didn't have too much to install.

---

### Post by taufiqbanua on 2010-06-01
:)
my friends and i experienced same thing like that. i hope there will be a solution.
if it happens, the final action is only opening terminal:
sudo init 6 =to restart or init 0=to shutdown
however, it isn't easy anymore if i must always open the terminal to restart or shutdown
thank u

---

### Post by Ozor Mox on 2010-06-01
I just had this happen at the same time as my sound crapped out. I had to shut down from the terminal. After starting back up everything seems to be ok again.

---

### Post by JS_Prom on 2010-06-02
> **blakdogg said:**
> Hi

I have a recently new, less than 2 weeks old, Ubuntu 10.04 LTS installl. It is a clean install since the prior install of 10.04 LTS decided it would no longer allow me to login.

My problem is that I cannot shutdown or restart my machine. And I have no idea why it happened.

Has anyone experienced a similar problem? Does anyone know where I should start looking?

Thanks

I report the same problem. This is a fresh Ubuntu 10.04 install on an HP COmpaq nx6115 notebook computer. THe restart and shutdown buttons don't restart and shutdown. Although, there is a message box saying that the system will restart/shutdown, it does not. Alternative is to start and terminal and do sudo halt.

Intermittently, the buttons may decide to obey you and actually shutdown sometimes when pressed! But not as a rule.

---

### Post by ChristopherB on 2010-06-27
> **blakdogg said:**
> Hi

I have a recently new, less than 2 weeks old, Ubuntu 10.04 LTS installl. It is a clean install since the prior install of 10.04 LTS decided it would no longer allow me to login.

My problem is that I cannot shutdown or restart my machine. And I have no idea why it happened.

Has anyone experienced a similar problem? Does anyone know where I should start looking?

Thanks

One thing I found out in Ubuntu 6.04 is that when logout doesn't work then press: [Alt]+[Ctrl]+[F4] will give me a terminal then I press [Alt]+[Ctrl]+[Delete] and pc rebooted.

This works even for the latest version

It works for me every time I mess something up :cry: which I do at times as I "play" with Ubuntu. :D

Christopher

---

### Post by aimwin on 2010-09-18
> **CountMeIn said:**
> Hi,

Lots of people with problem like this inc. me.

I noticed this problem happened whenever I started Ubuntu 10.04 and had problems with mounting USM sticks, partitions or even CDs. I would get 'permission denied' . When that happened, I couldn't shutdown or restart from the GUI - it just brought me back to the login screen. I've found that this bug has been reported, but there is no solution yet:

[https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139](https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139)

hope that helps.

Yes I have the same problems, 
my notebook is Oem asusek main board
Subsystem: ASUSTeK Computer Inc. Device 1297
and nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
Subsystem: ASUSTeK Computer Inc. Device 1212

I have the latest updated software, as reported in sysinfo attached.

I don't have this problem in other previous Ubuntu 8.04->till 10.04.
All other version did hung up now and then but not the same pattern as it did with 10.04 now.

---

### Post by Flos Headford on 2010-09-21
Yes,I have the same prolblem. The euro-standard On-Off buton takes me to a dialogue box - if I click on Restart, it closes a few window-frsmes, but then stalls.
I can open a terminal and type:
sudo shutdown -r now
and that works fine, but it's hardly the kind of behaviour one would want to parade in front of a Linux skeptic looking over one's shoulder.
If anyone finds a fix for this, do email me, please.
Oh dear, I've just realised how stupid it would be type in my email address.. nonetheless, I shall keep a careful eye on this thread.
Thanks to all who contribute,
Yours Faithfully,
Flos

---

### Post by Flos Headford on 2010-09-24
I have sent thanks to linuxishard on this thread
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-not-closing-down-827685/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-not-closing-down-827685/)

I had previously tried altering an /etc/default/grub line to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

But, following the advice in the link above, by right-clicking on the panel Shutdown button, then selecting Remove, I got rid of the button. Then I right-clicked in a blank area of the panel, selected Add to Panel, then chose the Shut Down... icon from the displayed list. That restored the button. The first time I tried it, it didn't work. But, after using a terminal to do
sudo shutdown -r now
The Shutdown button now works. Thanks to linuxishard, and all others who contributed!
I leave it to the discetion of the Original Poster whether to mark this thread SOLVED.
Phil

---

### Post by Zeblue on 2010-09-27
Flos, so far from what I've read, the "sudo shutdown -X now" command allows just about everyone's system to operate normally on the following reboot. Have you turned your machine on and off several times, now, to ensure that the method you used has actually fixed the problem?

So far, I've noticed that using this terminal command is only part of a workaround procedure, not an actual fix.

I too have posted an addendum on a previously reported bug concerning this issue, though different than the one posted by the OP: [Bug #518533]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/518533")

---

