---
title: "Switch User &gt; Logout &gt; Black Screen of Death..."
date: 2010-09-21
forum: General Help
---

### Post by 2CV67 on 2010-09-21
*Edit: At this time, I was using 10.04 for my non-LTS Ubuntu*

I have been using Ubuntu for years, but only recently added a couple of other (non-admin) users.

Now, I have a frequent problem, the simplest scenario being:
Log-in User A (admin)
Switch Users to User B
Logout User B

Instead of a Login screen I get a black screen with no pointer or invite.
Num Lock is on & cannot be turned off.
There seems to be no way out except switching off.
I tried:
Ctrl/Alt/Backspace
Ctrl/Alt/Del
Ctrl/Alt/F8
Ctrl/Alt/F9
Alt/s
Password for A
Password for B

Visual Effects are OFF for all users.
Video card is ATI Radeon 9200 128Mo
No proprietary drivers.

There seem to be lots of similar(ish) reports on Ubuntu & Linux Mint forums, but mostly with Visual Effects ON &/or with NVidia.

Any ideas?

Thanks!

---

### Post by 2CV67 on 2010-09-24
I suppose I can assume that, since Num Lock & Caps Lock cannot be switched, then the Keyboard is dead & I don't need to look at any fixes or workarounds which involve keyboard input?

Including REISUB etc?

Trying to find leads from other threads, I found these which looked promising:

>  **Re: blank screen after log out. I.e.: switching user causes nonfunction.**
ok, I found another thread exploring this issue and tried the suggestion of uninstalling gnome-screensaver:

[http://ubuntuforums.org/showthread.p...08#post9387908](http://ubuntuforums.org/showthread.p...08#post9387908)

See my follow-up: I uninstalled and fixed the defect and then the defect remained fixed after I re-installed??
I tried uninstalling gnome-screensaver with no effect.
When I reinstalled it, I thought it had worked as I got as far as entering the login p/w before the screen greyed & everything froze.
Subsequent attempts get me straight back to the "usual" Black screen.

>  **Re: Black screen when log out or switch user**
If I can save someone the time of searching it out...

type this in a terminal:

sudo gedit /etc/X11/gdm/gdm.conf

find the line that begins with
#AlwaysRestartServer=false and change it to read
AlwaysRestartServer=true

reboot and you should now be able to log out.
As far as I can see, I don't have "/etc/X11/gdm/gdm.conf"
Is there an equivalent in 10.04?
Is it relevant?
Worth trying?

>  **Re: Blank screen after switch user/logout/inactivity**
I was having the same problem today when I was setting up Ubuntu for the rest of my family, and Ubuntu would always give me a white screen when I either logged off of a user, or when I would switch.
So I did some searching around the web, and I stumbled on a bug report from a couple years ago, someone posted a fix. It has worked for me, so far. I have logged off and switched users a couple times, without the "white screen of death". [https://bugs.launchpad.net/ubuntu/+s....17/+bug/48974](https://bugs.launchpad.net/ubuntu/+s....17/+bug/48974)
That's the bug report, and here is the fix they posted:



In /etc/gdm/gdm.conf-custom :

[daemon]
AlwaysRestartServer=true
RemoteGreeter=/usr/lib/gdm/gdmgreeter
[security]
AllowRoot=true

Not exactly my problem & again I don't have "/etc/gdm/gdm.conf-custom"
I do have "/etc/gdm/custom.conf" which looks pretty empty:
> .
.
.
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

AllowRoot=true

[xdmcp]

[gui]

[greeter]


Can anybody who understands this stuff suggest what is worth trying in 10.04?

Thanks!

---

### Post by 2CV67 on 2010-10-06
> **2CV67 said:**
> I have a frequent problem, the simplest scenario being:
Log-in User A (admin)
Switch Users to User B
Logout User B

Instead of a Login screen I get a black screen with no pointer or invite.
Num Lock is on & cannot be turned off.
There seems to be no way out except switching off.

This problem is a real nuisance.

No ideas?

Thanks!

---

### Post by Moozillaaa on 2010-10-06
I had a similar problem - log out as main user, and log in as system ROOT user, and the solution was to modify (in Hardy) the gnome configuration file that you've referred to.

I don't know the new file name in 9.10 or 10.04 for gnome configuration (or even if it still configures log in settings), but I bet your solution is in that file, whatever its' name.

See if you can find a line(s) with Allow[user/username/X]login=[True/False/limit], or something close to that...

---

### Post by 2CV67 on 2010-10-08
I have spent a long time looking for the appropriate 'gdm.conf' or similar file, with no success.

Terminal 'locate gdm.conf' gives:
> /etc/dbus-1/system.d/gdm.conf
/etc/gdm/gdm.conf.dpkg-bak
/etc/init/gdm.conf
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config

Only the dpkg-bak file refers to 'AlwaysRestartServer=' but that is just a backup file, so not operational, isn't it?

In gdm.conffiles, I found another list of potential files:
> /etc/gdm/gdm.schemas
/etc/gdm/PostSession/Default
/etc/gdm/Xsession
/etc/gdm/PostLogin/Default.sample
/etc/gdm/PreSession/Default
/etc/gdm/Init/Default
/etc/dbus-1/system.d/gdm.conf
/etc/pam.d/gdm
/etc/pam.d/gdm-autologin
/etc/X11/Xsession.d/60xdg_path-on-session
/etc/init/gdm.conf
But nothing there either.

I also started digging in Applications > System Tools > Configuration Editor, but gave up...

Any suggestions as to where I should be able to find the required file(s)?

---

### Post by 2CV67 on 2010-10-08
Further searching seems to suggest that 10.04 no longer uses gdm.conf files?

Replaced by /etc/gdm/custm.conf ?

Which is pretty empty.

Am I supposed to just add 'AlwaysRestartServer=true' or something else?
Where?

---

### Post by 2CV67 on 2010-10-08
In fixing another problem, it looks as though I have accidentally fixed this one too...

The other problem was that my non-administrator users, logged-in without password, were asked for the keyring password if I (admin) was not also logged-in.

I found this post: [http://ubuntuforums.org/showpost.php?p=7349479&postcount=7](http://ubuntuforums.org/showpost.php?p=7349479&postcount=7)
Suggesting that that one could be fixed, without fiddling with keyring manager, by setting the wireless as "Allow for all users" (They were already all allowed in User Settings!!)

That worked perfectly.

In my testing, I went through the usually-fatal routine of Switch User > Logout with no problem!

Well, there was a slight problem that everybody gets a p/w request before reaching their desk, but that's much better than the black screen!

I rechecked this a dozen times & it is OK so far.

Don't ask me...:confused:

---

### Post by 2CV67 on 2010-10-09
Spoke too soon!

Black screen of death is back again today whenever I try Switch User > Logout.

But I did notice that if I have several active users, I can logout OK until I get down to the last but one...
Schematically:
Login A (admin)
Switch to B 
Switch to C
Logout C (OK - to a black screen with p/w invite for B & option to Switch User > Switch to B)
Logout B > Black Screen Freeze

So still looking for any kind of help!

Thanks.

---

### Post by SentientFluid on 2010-10-12
For the nvidia related issue the fix was to either upgrade to 10.10 or to install the nvidia drivers used for 10.10. Perhaps something similar would work for you?

---

### Post by cojoco on 2010-10-19
I have four computers at home, and have this black screen of death on *ALL* of them.

I am using a mixture of KDE and Gnome, and nVidia and ATI, and wireless and ethernet, and Asus and Gigabyte motherboards, and single/multiple users.

The only common features are that all of them are AMD machines, and they are all running 10.04

I cannot log out on ANY of them!  I just get a black screen, with no keyboard input.  This has been true since I upgraded to 10.04.

I can SSH in and kill the X server, and I don't think this works: I think I always need to reboot.  I'm not going to try now though.

---

### Post by 2CV67 on 2010-10-19
I have to admit I am relieved to see I am not alone - sorry cojoko!

Following your post, I went to my 8.04 partition & created another user.
Absolutely no problem with Switching to that user & Logging out again...
Tried that 3 times OK.
Then came back to 10.04 & got black screen after first attempt.
I notice that before logging out in 10.04 you have to confirm first, which doesn't happen in 8.04.
So it looks like it is not just my hardware alone, but combination with 10.04.

Getting off the subject - how much better the 8.04 arrangements were for Switch/Logout/Restart etc!

---

### Post by SentientFluid on 2010-10-19
> **cojoco said:**
> I have four computers at home, and have this black screen of death on *ALL* of them.

I am using a mixture of KDE and Gnome, and nVidia and ATI, and wireless and ethernet, and Asus and Gigabyte motherboards, and single/multiple users.

The only common features are that all of them are AMD machines, and they are all running 10.04

I cannot log out on ANY of them!  I just get a black screen, with no keyboard input.  This has been true since I upgraded to 10.04.

I can SSH in and kill the X server, and I don't think this works: I think I always need to reboot.  I'm not going to try now though.

Try using to restart [REISUB]("http://kember.net/articles/reisub-the-gentle-linux-restart/") instead.

I had the same issue when using the nvidia driver and installed the nvidia driver from 10.10. I posted the steps [here]("http://ubuntuforums.org/showpost.php?p=9963115&postcount=35") that solved it for me.  I don't have any ATI cards so am not sure which driver might help but I'm guessing you could find it [here]("http://mirrors.kernel.org/ubuntu/pool/restricted/f/fglrx-installer/").

Another alternative is to upgrade to 10.10.

---

### Post by 2CV67 on 2010-10-20
> **SentientFluid said:**
> Try using to restart [REISUB]("http://kember.net/articles/reisub-the-gentle-linux-restart/") instead.

I had the same issue when using the nvidia driver and installed the nvidia driver from 10.10. I posted the steps [here]("http://ubuntuforums.org/showpost.php?p=9963115&postcount=35") that solved it for me.  I don't have any ATI cards so am not sure which driver might help but I'm guessing you could find it [here]("http://mirrors.kernel.org/ubuntu/pool/restricted/f/fglrx-installer/").

Another alternative is to upgrade to 10.10.

Thanks for the suggestions.

Actually I started this thread because my symptoms did not quite match those on other threads:
- No nvidia
- No proprietary drivers
- Keyboard dead so REISUB not available
- etc

I will upgrade to 10.10 in a couple of months, but not sooner, as upgrades always bring more new problems (like this one) & I like to see some fixes available before I jump in!

---

### Post by SentientFluid on 2010-10-20
> **2CV67 said:**
> - Keyboard dead so REISUB not available

Yeah, I thought the same thing (no response from any of the keys, not even Num or Caps Lock) but REISUB still worked. I hope you still tried it and didn't assume (like I did) that it just wouldn't work. :)

> **2CV67 said:**
> I will upgrade to 10.10 in a couple of months, but not sooner, as upgrades always bring more new problems (like this one) & I like to see some fixes available before I jump in!

Always a smart bet!

Good luck and I hope you find a solution!

---

### Post by ollesbrorsa on 2010-10-23
> I will upgrade to 10.10 in a couple of months, but not sooner, as upgrades always bring more new problems (like this one) & I like to see some fixes available before I jump in!

Hello,

I have the exact same problem. Unfortunately I am on 10.10 so an upgrade will not solve your problems... Ubuntu 10.10 64bit to be exact. Proprietary AMD/ATI video drivers.

At the moment the "workaround" is to logout each user before another logs on. Not really an ideal situation on a multi user system. :(

Br,
ollesbrorsa

---

### Post by e.meitner on 2010-10-27
> **2CV67 said:**
> Spoke too soon!

Black screen of death is back again today whenever I try Switch User > Logout.

But I did notice that if I have several active users, I can logout OK until I get down to the last but one...
Schematically:
Login A (admin)
Switch to B 
Switch to C
Logout C (OK - to a black screen with p/w invite for B & option to Switch User > Switch to B)
Logout B > Black Screen Freeze

So still looking for any kind of help!

Thanks.

You may want to take a look at this bug report and click "Does this bug  affects you" if you can reproduce it as described in the bug  description.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011)

---

### Post by 2CV67 on 2010-10-27
> **e.meitner said:**
> You may want to take a look at this bug report and click "Does this bug  affects you" if you can reproduce it as described in the bug  description.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011)
Thanks, but I can't reproduce that bug.
When I try, I get:
Login as A - OK
Switch to B - OK
Switch to C - OK
Switch to B - OK
Logout B > Black screen with no cursor & no keyboard actions.

So this is another one (of how many??)

Still looking...  :(

---

### Post by 2CV67 on 2010-10-28
Should I be able to find any diagnostic help, maybe in a log file or something?

---

### Post by tripmix on 2010-10-28
I get this "black screen of death" sometimes when I switch to console with ctrl+alt+f#, it's completely random on my system so I have no idea whats causing it but it's highly annoying. I don't use gdm nor do I log in with multiple users unless you count hts and stuff.

---

### Post by 2CV67 on 2010-12-31
Well - I just upgraded from 10.04 to 10.10 and the problem is still there.

To resume> Log-in User A (admin)
Switch Users to User B
Logout User B

Instead of a Login screen I get a black screen with no pointer or invite.
Keyboard is dead.
There seems to be no way out except switching off.
Visual Effects are OFF for all users.
Video card is ATI Radeon 9200 128Mo
No proprietary drivers.

Surely there should be some trace in a log file or somewhere, to help diagnose this significant problem?

Thanks for any pointers!

---

### Post by 2CV67 on 2011-02-26
Well - 5 months & one upgrade later - my problem is still there 100%.

I am quite surprised that the great Ubuntu community (I really mean that - not sarcasm!) has not come up with any decent diagnosis possibility.

I did notice that I can escape without a full hard shutdown if I just touch the shutdown switch.
Then I get the Ubuntu screen with 5 red/white buttons while the PC seems to do an orderly shutdown.
After that (as opposed to a full hard shutdown) then the PC does not automatically boot when power is next supplied & there is no disk checking.

Does that provide any clue?

Thanks for any suggestion applicable to 10.10 !

---

### Post by 2CV67 on 2011-02-26
I have been playing around with this problem today.

When it started, last year, I was running 10.04 as my main Ubuntu & also had 8.04 as my LTS backup version.
I had the problem in 10.04 but not in 8.04.

In the meantime, I have upgraded main Ubuntu from 10.04 to 10.10 & still have the problem.
I have upgraded LTS from 8.04 to 10.04 & still do NOT have the problem there!
So there is not any fixed incompatibility between my hardware/software & Ubuntu 10.04.
That is significant & reassuring!

When I have the problem (black screen) then the keyboard appears dead (can't change NumLock or CapsLock & Ctr/Alt/Backspace or Ctr/Alt/Del don't work).
Last year, I note that I tried REISUB without success, but today (maybe after some other fiddling??) REISUB does work to give me a reboot.

Surprisingly, if I initially login as user B or C (non-admin, but that may be coincidence) then I can do any amount of Switching & Logout between any combination of users A,B & C with absolutely no problem!

This includes the case which looks just like my usual problem case, where I am solely logged in as A (admin) then switch to B then logout of B...

Everything stays OK until the next reboot where I login first as A.
After which, Switch to B then logout B gives me the black screen again.

I really would like to beat this to death & would appreciate suggestions!

Thanks!

---

### Post by 2CV67 on 2011-02-27
Not surprising that Ctrl/Alt/Backspace did not work - it has been quietly disactivated in recent distros...

I have reactivated it like this:
[http://deviceguru.com/enabling-ctrl-alt-backspace-to-kill-the-x-server-in-ubuntu/](http://deviceguru.com/enabling-ctrl-alt-backspace-to-kill-the-x-server-in-ubuntu/)

Still looking for input on the black screen problem!

---

### Post by 2CV67 on 2011-03-02
Just found that I can provoke a similar freeze (but not black screen) by simply:
- Login A
- Switch user
- Select A
- Password for A
- Login
At that point, the login screen freezes (no mouse, no keyboard).
REISUB still works.

Again, if I initially Login as B or C then all combinations work OK!
For instance:
- Login B
- Switch user
- Select B
(no password for B - is that significant??)
- Straight to B

or:
- Login B
- Logout B
- Login A
- Switch user
- Select A
- Password for A
- Login OK...

I am sure there are lots of clues here for somebody who understands this stuff better than me!

---

### Post by trinitrotoluene on 2011-03-05
Hi 2CV67, I have the exact same problem as you but on Linux Mint 10. To continue without rebooting I ssh into the machine and restart gdm, which kills the user's sessions. Looking for a real solution as well.

---

### Post by 2CV67 on 2011-04-01
Bump...

If only for the simple case:
> - Login A
- Switch user
- Select A
- Password for A
- Login
At that point, the login screen freezes (no mouse, no keyboard).
REISUB still works.

---

### Post by 2CV67 on 2011-07-17
Just upgraded to 11.04 & this problem has totally disappeared.

Very good news, even if the reason remains a mystery! :)

---

### Post by marclar on 2011-07-18
Yes, same problem in 11.04. I enter user B's password and then it's a black screen. Any suggestions?

---

### Post by wildmanne39 on 2011-07-18
> **marclar said:**
> Yes, same problem in 11.04. I enter user B's password and then it's a black screen. Any suggestions?Hi, you should start your own thread this one is marked solved and is old so you will not get much help here.

---

