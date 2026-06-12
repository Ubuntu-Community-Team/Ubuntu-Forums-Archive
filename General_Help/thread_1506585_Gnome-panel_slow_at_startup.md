---
title: "Gnome-panel slow at startup"
date: 2010-06-10
forum: General Help
---

### Post by aberg1990 on 2010-06-10
after an update gnome-panel is really slow , takes like a minute to start. i using ubuntu 10.04. can anyone help me to get it back to normal startup speed?

---

### Post by wolferl on 2010-06-10
> **aberg1990 said:**
> after an update gnome-panel is really slow , takes like a minute to start. i using ubuntu 10.04. can anyone help me to get it back to normal startup speed?

I am having exactly the same problem here...help!

---

### Post by pawanh on 2010-06-11
Me too

---

### Post by Djzn.BR on 2010-06-12
I am having the exact problem. There was an update for gnome-panel one or two times before, and now the panels are delaying something like 10 or 15 seconds to start up. ANNOYING!!! 

I am considering to move to Fedora... I haven't seen such buggy distro like Lucid Lynx!

---

### Post by aberg1990 on 2010-06-13
come on someone? help us

---

### Post by mpscheidt on 2010-06-14
I can also confirm this issue.

And the network manager applet is even slower; it only shows up after several minutes, even though network manager is running and working; just the icon delays to show.

Both delays, the gnome panel delay and the nm-applet delay, are user-specific. One user account leads to these delays after logging in, the other one not. Maybe something related to user account settings..

---

### Post by sant on 2010-06-14
I have tried uninstalling gnome-panel lucid updates and the problem persists.
If the folder panel at  /home/user/.gconf/apps is deleted gnome-panel starts correctly, but the issue is back on the next system boot.

---

### Post by aberg1990 on 2010-06-14
Of my experience the problem seems to only occur when you have automatic login or use fingerprint reader to login. the update i was talking about was a update for gnome-keyring... that update solved a issue that i had to write the wep key every time i login to my desktop but it created a new problem which i have described above

---

### Post by sant on 2010-06-14
You are right. 
No automatic login, gnome-panel loads correctly.

---

### Post by wolferl on 2010-06-14
> **aberg1990 said:**
> Of my experience the problem seems to only occur when you have automatic login or use fingerprint reader to login. the update i was talking about was a update for gnome-keyring... that update solved a issue that i had to write the wep key every time i login to my desktop but it created a new problem which i have described above

Hmm...seems that a lot of people are having the same issue. I have installed 10.04 on both my desktop and my netbook and the problem is exactly the same; both with the same updates. My desktop PC has 5 users and the netbook two...all of them present the problem. And no, I don't have automatic login nor fingerprint reader.

It is simply and plainly a BUG.

I tried to reverse to previous configurations (versions before the updates) but with no result :-(

---

### Post by suli8 on 2010-06-14
i'm having this issue also.
on both different computers! both on lucid!
between the password and the desktop it's taking time...like 10 seconds more than usual, and after desktop appears, it takes 3 seconds to the panel to jump down!

some1 reported a bug?

---

### Post by wolferl on 2010-06-14
Good news, I think.

I have it under scrutiny, but after testing it several times I think it is solved. This is what I have discovered and how I solved it (I hope).

The problem occurs with the latest version of GNOME KEYRING: files 'libpam-gnome-keyring' and 'gnome-keyring'.

I _downgraded_ them to the previous version, and then _blocked_ that version: **2.92.92.is.2.30.0-0ubuntu3** (instead of 2.92.92.is.2.30.1-0ubuntu2)

Can anyone check or confirm this solution please?

---

### Post by grege on 2010-06-14
There is a bug report for this.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/593226](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/593226)

@wolferl - perhaps you should add your findings there.

---

### Post by grege on 2010-06-14
I activated proposed updates in Synaptic, updated and it triggered a libpam upgrade that fixed (so far) the problem for me.

Thanks to wolferl

---

### Post by mpscheidt on 2010-06-15
As somebody suggested in this thread already, for me the problem only occurs when using the fingerprint reader (on a ThinkPad T60). Looging in typing the password is fine.

---

### Post by wolferl on 2010-06-15
> **grege said:**
> I activated proposed updates in Synaptic, updated and it triggered a libpam _upgrade_ that fixed (so far) the problem for me.
 
UPgrade?  What fixed it for me was a _DOWN_grade as I have explained. 
OK, anyway I confirm that it is still working fine on my both computers and tested several times with 7 different users.
 
[BTW I like Australia's Greg Egan's books ;-)]

---

### Post by grege on 2010-06-15
> **wolferl said:**
>  
[BTW I like Australia's Greg Egan's books ;-)]

No relation, but cool.

The discussion in the bug report has slowly reached pam as the culprit. I did fix it for me using an upgrade to the "proposed" version. It was an easy thing to try, given the info you provided and, for me, it did the job.

I was going to avoid proposed and backports and keep my install as standard as possible for a LTS release. But then I added a new kernel for my sound chip, and several PPAs and now it bears little resemblance to a standard install. Never mind.

---

### Post by realzippy on 2010-06-15
Here is someone with this issue;*removing the clock from panel* works for him.
maybe you can check this out also,might be interesting  for bugreports.

[http://ubuntuforums.org/showthread.php?t=1509151](http://ubuntuforums.org/showthread.php?t=1509151)

---

### Post by Frogs Hair on 2010-06-15
> **grege said:**
> I activated proposed updates in Synaptic, updated and it triggered a libpam upgrade that fixed (so far) the problem for me.

Thanks to wolferl

This also solved my issue . I had an 8 second delay before the panel and background loaded . I eliminated the video driver because the same thing occurred  without the driver. After the update all is well.

---

### Post by mjuhasz on 2010-06-15
I have removed the login keyring (Applications/Passwords and Encryption Keys) and that solved the issue.
I had this intuition because the gnome-keyring package update 2.92.92.is.2.30.1-0ubuntu1 had this in the changelog: "Remove accidental storage of user's login password in login keyring." I do not know if this has anything to do with the bug, but the keyring was empty anyway (all my passwords are stored in the default keyring).

---

### Post by wolferl on 2010-06-15
@ grege and @ frog's hair  > I'm happy to know that you have been able to solve the issue so easily, but could you please indicate what version of libpam-gnome-keyring have you running now? I am still a bit intrigued about why I needed to downgrade and you did an upgrade that fixed it.

---

### Post by grege on 2010-06-15
> **wolferl said:**
> @ grege and @ frog's hair  > I'm happy to know that you have been able to solve the issue so easily, but could you please indicate what version of libpam-gnome-keyring have you running now? I am still a bit intrigued about why I needed to downgrade and you did an upgrade that fixed it.

2.92.92 is 2.30.1-0ubuntu2

but other parts of pam maybe involved

libpam-modules  1.1.1-2ubuntu3
libpam-runtime  1.1.1-2ubuntu3
libpam0g        1.1.1-2ubuntu3
libpam-ck-connector 0.4.1-3ubuntu1

ps

My system is very non-standard - updated kernel and a swag of active PPAs.
It is not a simple thing. I have four Ubuntu machines, but only one was ever affected.

---

### Post by ELD on 2010-06-15
I also have the same very annoying issue - takes 22 seconds to load up the panels and desktop!

---

### Post by realzippy on 2010-06-16
I can confirm that simply downgrading *libpam-gnome-keyring* and
*gnome-keyring* to *2.92.92 is 2.30.**0**-0ubuntu3* solves/workarounds this issue.
Thanks,*wolferl* !

*aberg1990* should set this as solved.

---

### Post by grege on 2010-06-16
Go here and scroll to bottom for simple commands to fix the issue.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/593226](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/593226)

I would not call a downgrade problem solved, it is solved when the current version works. At least the devs now know the problem.

---

### Post by nanirandra on 2010-06-17
> **mjuhasz said:**
> I have removed the login keyring (Applications/Passwords and Encryption Keys) and that solved the issue.
I had this intuition because the gnome-keyring package update 2.92.92.is.2.30.1-0ubuntu1 had this in the changelog: "Remove accidental storage of user's login password in login keyring." I do not know if this has anything to do with the bug, but the keyring was empty anyway (all my passwords are stored in the default keyring).

That didn't do it for me. Just lost all stored passwords.:confused:

---

### Post by realzippy on 2010-06-17
> **nanirandra said:**
> That didn't do it for me. Just lost all stored passwords.:confused:


Again:

**downgrading** *libpam-gnome-keyring* and
*gnome-keyring* to *2.92.92 is 2.30.**0**-0ubuntu3* solves/workarounds this issue.

Can be done easily with synaptic or terminal,as suggested.

---

### Post by suli8 on 2010-06-17
nope!
downgraded both... no result...
removed the clock....no result
have no floppy... 
:(

---

### Post by wolferl on 2010-06-17
> **suli8 said:**
> nope!
downgraded both... no result...
removed the clock....no result
have no floppy... 
:(

That's strange, because it is sure that the origin of the issue was an update some 8 days ago, and by reversing the changes it should go back to normal behaviour. I tested one by one all the changes.

On the other hand, I have read your post #11 which I quote here:

>  i'm having this issue also.
on both different computers! both on lucid!
between the password and the desktop it's taking time...like 10 seconds  more than usual, and after desktop appears, it takes 3 seconds to the panel to jump down!And the sympthoms do not look like being the same. I experienced no delay in the desktop, it was normal, and the delay of the panel was never as short as 3 seconds to display, it took at last 30 seconds or more...every time. I really doubt it is the same issue :(

---

### Post by anantshri on 2010-06-17
one simple observation.

many people now-a-days are using conky for system information display

the recomended way for conky loading is to introduce a delay of 10-15 sec before loading it. so people are using shell script for the same.


general shell script are written as 

sleep 15 && conky -c ~/.conky/conky_config &

but the currect way would be 
(sleep 15 && conky -c ~/.conky/conky_config)  &

otherwise this introduces a delay of 15 seconds to the whole panel loading stuff.

hope this helps someone.

---

### Post by firesock on 2010-06-17
I have solved this issue with:

sudo aptitude install libpam-gnome-keyring=2.92.92.is.2.30.0-0ubuntu3
sudo aptitude install gnome-keyring=2.92.92.is.2.30.0-0ubuntu3

These lines solve the slow opening issue of the gnome-panel and the malfunctioning of the network-manager-gnome.

Thank you very much for your help. I hope this would be fixed in the future with an update. Please let us know :)

---

### Post by RikoW on 2010-06-18
I'm having the same problem, but unfortunately, none of the workarounds described here did help. Symptoms are:

- after login I see the default splash screen and the mouse pointer for "a long time"

- then my own wallpaer apears, but not much more is happening

- then screenlets appear

- finally the panel appears and I can finally work.

- during all this waiting, the hard disc is spinning constantly

All that feels like it takes at least a minute, which is highly annoying, especially since it's on a laptop.

Any other ideas?

Thanks and cheers,

               Riko

---

### Post by pawanh on 2010-06-27
> **RikoW said:**
> I'm having the same problem, but unfortunately, none of the workarounds described here did help. Symptoms are:

- after login I see the default splash screen and the mouse pointer for "a long time"

- then my own wallpaer apears, but not much more is happening

- then screenlets appear

- finally the panel appears and I can finally work.

- during all this waiting, the hard disc is spinning constantly

All that feels like it takes at least a minute, which is highly annoying, especially since it's on a laptop.

Any other ideas?

Thanks and cheers,

               Riko
Try *disabling* the **Screenlets Manager** at startup and try again. That worked for me.

---

### Post by RikoW on 2010-06-28
Hi,

> **pawanh said:**
> Try *disabling* the **Screenlets Manager** at startup and try again. That worked for me.

thanks for the hint, but unfortunately, that didn't make any difference :(

As in previous posts stated also, when I logout and log back in (so without a shutdown/reboot), the startup of gnome behaves just normal, meaning ~10 secs until a workable desktop is available.

Thanks again,
               Riko

---

### Post by RikoW on 2010-06-28
Okay! Solved! Seems my problems even though had the same symptoms were caused by something different.

I removed .gnome* .gconf* from my home dir and thus started with a fresh and default panel and desktop.

Since then login is as it used to be, don't ask me why, though. Took another half hour to reconfigure everything, but that's a small price compared to the annoyance of waiting each time for a minute or so before the desktop is ready.

Thanks and cheers,

  Riko

PS: it was not enough to to create a new panel and remove the old one. Tried that, too.

---

### Post by sandman3838 on 2010-07-04
Hello

If I'm reading it right, your issue here is from Sign-in to the desktop.
Correct?

My self I have one hell of a delay from the Plymouth splash screen to Sign-in?  

Now I have read a lot about Plymouth opening up in a bad resolution.....
thats not my issue.  It's after Plymouth.

Has anyone here come across other cases like this.  Could someone point me in the right direction.

Thank you

---

### Post by _demetri on 2010-10-30
For me, after reviewing .xsessions and /etc/gdm/* files (particularly files with "crash" suffix) I was able to determine it was my recent installation of afs causing the delay because my afs is behind a vpn. Disabling open-afs at startup did it. I am using Ubuntu 10.04

sudo update-rc.d -f openafs-client remove

---

### Post by sandman3838 on 2010-10-31
My fix was letting Ubuntu do its upgrade to 10.10.
No issues so far.

---

### Post by Chninkel on 2011-05-16
If it can be of any helps, in my case (Ubuntu 10.04, upgraded from 9.10 a few weeks ago), I removed all the applet from the top right corner (network/notification, clock, weather and login applets), restarted and from login prompt to usable desktop it suddenly took less than 5 seconds. Much better than before (about 1 minute doing ... nothing, just showing the wallpaper and the mouse pointer).

Weirder: I put all the applets back one by one with a computer restart between each and it is still less than 5 seconds.

(NB: before that I had tried various things to no effect: removing compiz, pulseaudio, dpkg-reconfiguring gdm, updating pam (didn't try downgrading), trying to understand bootchart, reading auth.log, messages, Xorg.0.log, ...)

Note that just after the 9.10 to 10.04 upgrade, the login time was fine, and I don't remember when the slowness appeared (I usually reboot once every week or so). So it may re-appear. If it does I'll try to remove the applets one by one to figure out which one is causing me this trouble.

---

### Post by Chninkel on 2011-05-27
There was an update of both dbus and networkmanager today and it's back ... about 1 minute between login and desktop actually showing up.

I tried to remove all the applets in the top-right corner and reboot, to no effect, it still takes ~ 1 minute to just login ... :(

(if i then logout and re-login it takes less than 5 seconds though, so this is clearly a first-login-after-boot problem with either dbus or the networkmanager/networkmanager-applet)

---

