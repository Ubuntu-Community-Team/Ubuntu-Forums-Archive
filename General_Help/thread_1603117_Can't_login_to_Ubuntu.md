---
title: "Can't login to Ubuntu"
date: 2010-10-22
forum: General Help
---

### Post by sorinu26 on 2010-10-22
Hi, I have a problem. I can't login to my account on Ubuntu 10.10. After I enter my login details, a black screen appears for like 2 seconds and after that it redirects me back to login screen. I try to login with ALT + CTRL + F1 and after i entered my login details, I wrote "startx" but it gave me an error. What could be the prob. and how can i solve it? Thanks a lot! :)

---

### Post by praveenthivari on 2010-10-22
In tty1 (Ctrl+Alt+F1), login there.
```
sudo stop gdm
``` followed by ```
sudo start gdm
```. Hope tht helps u to find out the problem.

---

### Post by sorinu26 on 2010-10-22
> **praveenthivari said:**
> In tty1 (Ctrl+Alt+F1), login there.
```
sudo stop gdm
``` followed by ```
sudo start gdm
```. Hope tht helps u to find out the problem.

I tried like you said and it don't gives me error. After I enter the second command it shows me the login page and near my name its written "currently logged in". If i press on my username, I need to write my password again, but when i press login nothing happends. :(

---

### Post by AmiloLinux on 2010-10-23
> **sorinu26 said:**
> Hi, I have a problem. I can't login to my account on Ubuntu 10.10. After I enter my login details, a black screen appears for like 2 seconds and after that it redirects me back to login screen. I try to login with ALT + CTRL + F1 and after i entered my login details, I wrote "startx" but it gave me an error. What could be the prob. and how can i solve it? Thanks a lot! :)

I have the exact same problem in 10.10 as Sorinu26. After I enter my password and press enter, Ubuntu returns to the login prompt.

This seemed to happen after I installed Google Earth on the system, and needed to open a folder as root to change a filename.

Due to this problem I decided to to reinstall the system.

Regards

---

### Post by kentpend on 2010-10-24
I'm having the exact same problem, an I also have google earth.  But I've had that installed for some time, so I have no idea if that has anything to do with it.

I've given up on trying to fix it...  and am downloading a clean iso of 10.04 right now.

---

### Post by krzychw on 2010-10-25
I have the same problem but I didn't install Google Earth. I just installed system updates yesterday and I can't login today.
I hope reinstall is not the only solution!

---

### Post by DooM55 on 2010-10-25
after i update sis ubuntu 10.10 cann't login

when i press alt+ctrl+f7


the massege error said :

skipping profile  :confused::confused::confused:

---

### Post by DooM55 on 2010-10-25
how i can rapir the system


the problem slove tnx 

:)

---

### Post by sorinu26 on 2010-10-26
> **DooM55 said:**
> how i can rapir the system


the problem slove tnx 

:)

how u solved the prob? :)

---

### Post by arpad9 on 2010-10-26
Have you checked your /home/<user>/.xsession-errors file for clues?

---

### Post by sorinu26 on 2010-10-26
> **arpad9 said:**
> Have you checked your /home/<user>/.xsession-errors file for clues?

how can i check it? i can't login

---

### Post by krzychw on 2010-10-26
> **arpad9 said:**
> Have you checked your /home/<user>/.xsession-errors file for clues?

Solved! Thanks for tip, arpad9! In .xsession-errors I found precise error message - it was my mistake in .profile file.


> **sorinu26 said:**
> how can i check it? i can't login

Sorinu26, you can login: press Ctrl+Alt+F1 to get to console with login prompt.

---

### Post by D.J.H. on 2010-10-27
How did you solve it?

I have the same problem.
I already tried CTRL+ATL+F1: I can login there however I cannot seem to  open the /home/<user>/.xsession-errors file it says access is  denied.

Is there any way I can change this or that I can solve the login problem?
I'm totally new to linux, so a more comprehensive explanation would bne appreciated?:)

---

### Post by Yondergod22 on 2010-10-27
try 
```

sudo nano /home/<user>/.xsession-errors

```
(I probably wont be any help past that but it's a start :P)

---

### Post by cgroza on 2010-10-27
Hope the OP will post his solution. Thats why forums like this exist.

---

### Post by bond17_007 on 2010-10-27
I have a similar but little different issue. 
I upgraded my system to 10.10 from 10.04. I use to have "auto-login" in my 10.04 system. 
After I boot up when I see the home screen, I get prompts for the keyrings unlock password. Recently, I have been getting that keyring prompt at least 3 times before I can fully use the system. (defeats the purpose of auto-login). 
So I decided to remove the auto-login, but when i do, after my system boots up, I see the login screen but when I click on a user name, I don't see the place to put a password. the system just shows me the list of user name and I am stuck in that screen.

In order to get rid of that I ended up enabling the auto-login again.
It would be nice to figure out why I am seeing the issue. 

It would be great if someone could help me with this. 

Anyways, for others seeing this issue, you may try enabling the auto-login so they can completely by-pass the login screen. to do so follow the steps below:

1. While you are on the login screen Press Alt+ Ctrl+ F1 
2. You should see a terminal screen
3. login to the system by providing your user name and password 
4. type "sudo stop gdm"
5. vi /etc/gdm/custom.conf 
6. copy the following code  (replace YOUR_USER_ID):
```

[daemon]

TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=YOUR_USER_ID
AutomaticLogin=YOUR_USER_ID
TimedLoginDelay=30

DefaultSession=gnome

[security]

[xdmcp]

[gui]

[greeter]




GraphicalTheme=SpaceList




DefaultWelcome=false

Welcome=Welcome




[chooser]

[debug]

[servers]

```
7. restart gdm by doing "sudo /etc/init.d/gdm start"
8. press "Alt+Ctrl+F7" you should be logged into the system automatically
  (Note try Alt+Ctrl+F8) sometimes it might be opened in tty8

---

### Post by D.J.H. on 2010-10-28
Thanks for the replies, unfortunately they didn't get me much further.

I now managed to get into the /.xsession-errors file. than the screen shows:
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US
Start IM through /etc/X11
/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.:34:Can't open /home/<user>/.profile

Can I do anything with that? Does it explain anything??

With regard to an attempt to enable auto-login:

I am writing this on a different computer, how am I supposed to copy it onto my laptop?I tried typing it, but when I try to change what is already written, or try to insert something there is an error message and my keybord goes, mad.

Sooooo, any other ideas?

---

### Post by bond17_007 on 2010-10-28
Hi, 
  Sorry to hear that, I basically copy pasted the entire content of the file for reference.
 Only line you may need to add/change would be:
```

....
AutomaticLoginEnable=true

...
AutomaticLogin=YOUR_USER_ID
....

```

hope this helps..

> **D.J.H. said:**
> Thanks for the replies, unfortunately they didn't get me much further.

I now managed to get into the /.xsession-errors file. than the screen shows:
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US
Start IM through /etc/X11
/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.:34:Can't open /home/<user>/.profile

Can I do anything with that? Does it explain anything??

With regard to an attempt to enable auto-login:

I am writing this on a different computer, how am I supposed to copy it onto my laptop?I tried typing it, but when I try to change what is already written, or try to insert something there is an error message and my keybord goes, mad.

Sooooo, any other ideas?

---

### Post by keithspg on 2010-10-31
same here. I upgraded last night from 10.04. Was going fine. I was trying to get the iphone tethering running again and when I rebooted, I cannot log into ubuntu. something about 'cannot read /home/user/.profile so I renamed the .profle and now it logs in but I get only the desktop background and no toolbars or anything.

???

KeithG

---

### Post by bond17_007 on 2010-11-01
Hi Keith,
  I suggest that you "change the owner" of your original ".profile" file using "chown" command.
You may do so by running following command:
```

  $ chown YOURID .profile

```

Good Luck!

---

### Post by parsim on 2010-11-07
My **workaround**: First, login via a terminal with [Control] + [Alt] + 1. Then:
```

sudo service gdm stop
startx
```
Then I'm in to the desktop. But I need to do this every boot, which is driving me crazy.

There are many people reporting this issue, and many solutions that work for some (but not me):
[list][*]Delete $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml (I have no such file)
[*]Check permissions of ~/.ICEauthority and ~/.profile (mine are fine -- I even did a chown -R $HOME $USER:$USER to be sure)
[*]Inspect ~/.xsession-errors for problems (mine simply says "/etc/gdm/Xsession: Beginning session setup...")
[*]sudo dpkg-reconfigure gdm (nothing happens)
[*]sudo apt-get --purge --reinstall install gdm gnome-session (no difference)
[*]Set user to automatic login (I already have -- gdm still pops up and asks for a login. Tried changing it to manual and back, no difference.)
[*]Create a new user, try logging in as that (no difference)
[*]Replace nvidia driver with open-source one (no difference)
[/list]
I've also combed through every log file I can think of looking for an error message. The closest I can find is that when running "Login Screen Settings" (in System -> Administration, or "gdmsetup" from the command line), I can't unlock it. Clicking "Unlock" just produces the message:
```
** (gdmsetup:4895): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files
```

---

### Post by parsim on 2010-12-06
Four weeks later I still can't find a fix. :(

---

### Post by sawjam on 2010-12-12
Well this is what I did lacking in finesse but did the job.

[http://ubuntuforums.org/showthread.php?t=1504682](http://ubuntuforums.org/showthread.php?t=1504682)


log in by alt+ctrl+f1

sudo aptitude install gnome-desktop-environment

sudo stop gdm
sudo start gdm

---

### Post by parsim on 2010-12-12
Thanks very much for the reply! But no dice for me. Same issue following "sudo aptitude install gnome-desktop-environment".

The thread you reference has an actual error in the user's ~/.xsession-errors. Mine just says "/etc/gdm/Xsession: Beginning session setup..."

---

### Post by Kamikun on 2011-01-18
> **bond17_007 said:**
> I have a similar but little different issue. 
I upgraded my system to 10.10 from 10.04. I use to have "auto-login" in my 10.04 system. 
After I boot up when I see the home screen, I get prompts for the keyrings unlock password. Recently, I have been getting that keyring prompt at least 3 times before I can fully use the system. (defeats the purpose of auto-login). 
So I decided to remove the auto-login, but when i do, after my system boots up, I see the login screen but when I click on a user name, I don't see the place to put a password. the system just shows me the list of user name and I am stuck in that screen.

In order to get rid of that I ended up enabling the auto-login again.
It would be nice to figure out why I am seeing the issue. 

It would be great if someone could help me with this. 

Anyways, for others seeing this issue, you may try enabling the auto-login so they can completely by-pass the login screen. to do so follow the steps below:

1. While you are on the login screen Press Alt+ Ctrl+ F1 
2. You should see a terminal screen
3. login to the system by providing your user name and password 
4. type "sudo stop gdm"
5. vi /etc/gdm/custom.conf 
6. copy the following code  (replace YOUR_USER_ID):
```

[daemon]

TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=YOUR_USER_ID
AutomaticLogin=YOUR_USER_ID
TimedLoginDelay=30

DefaultSession=gnome

[security]

[xdmcp]

[gui]

[greeter]




GraphicalTheme=SpaceList




DefaultWelcome=false

Welcome=Welcome




[chooser]

[debug]

[servers]

```7. restart gdm by doing "sudo /etc/init.d/gdm start"
8. press "Alt+Ctrl+F7" you should be logged into the system automatically
  (Note try Alt+Ctrl+F8) sometimes it might be opened in tty8

I had a problem where I could log in but after i started to log in, it would promptly kick up a message and then kick me back to the log in screen. I tried what you said above and it worked perfectly, until i restarted my computer. Then when i tried to run "sudo /etc/init.d/gdm start" it would say: 
"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service dgm start
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start gdm"

Going back to the log in screen, i tried to copy down the error that popped up when i tried to log in which read something like this:
"Enabling additional binary formats binfmt-support[ok] speech–dispatcher configured for user sessions
 checking battery state... starting Common unix[ok]
 g System: cupsd [ok]
 PulseAudio configured for per-user session"

I am using Ubuntu 10.04 on the Archos 9 tablet

---

### Post by Roxez on 2011-01-18
Same problem here, btw you can enter in no graphic card mode and in safe mode but not in normal mode so i thing is a graphic card problem, do you people have nvidia?

---

### Post by bond17_007 on 2011-01-18
> **Kamikun said:**
> I had a problem where I could log in but after i started to log in, it would promptly kick up a message and then kick me back to the log in screen. I tried what you said above and it worked perfectly, until i restarted my computer. Then when i tried to run "sudo /etc/init.d/gdm start" it would say: 
"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service dgm start
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start gdm"

Going back to the log in screen, i tried to copy down the error that popped up when i tried to log in which read something like this:
"Enabling additional binary formats binfmt-support[ok] speech–dispatcher configured for user sessions
 checking battery state... starting Common unix[ok]
 g System: cupsd [ok]
 PulseAudio configured for per-user session"

I am using Ubuntu 10.04 on the Archos 9 tablet

Hi Kamikun,
  After you followed my steps, you should have not have to do it every time. After the file is changed, even after the computer is rebooted, the login screen should have worked okay. 
Anyways, the solution for the issue you are seeing is that
instead of running "sudo /etc/init.d/gdm start" you could do "service dgm start" or "sudo service dgm start".
let me know if that works.

Thanks,

---

### Post by parsim on 2011-01-18
> **Roxez said:**
> Same problem here, btw you can enter in no graphic card mode and in safe mode but not in normal mode so i thing is a graphic card problem, do you people have nvidia?

I do have nvidia, but have the same problem in safe mode (and even recovery console).

Btw, when I was first searching for info on this problem, it took me forever to figure out how to boot into safe mode, so for the record, the option appears at the bottom of the GDM login screen once you have selected a user.

---

### Post by Roxez on 2011-01-18
so is nvidia then, you can start in normal mode, but you need to stop the nvidia graphics i did that, but i dont want to be like that t.t no graphip card means no games t.t
i thing an update do this

---

### Post by Kamikun on 2011-01-19
> **bond17_007 said:**
> Hi Kamikun,
  After you followed my steps, you should have not have to do it every time. After the file is changed, even after the computer is rebooted, the login screen should have worked okay. 
Anyways, the solution for the issue you are seeing is that
instead of running "sudo /etc/init.d/gdm start" you could do "service dgm start" or "sudo service dgm start".
let me know if that works.

Thanks,
When I tried to log in again, it was the same problem, thus why i tried them again and got those errors. Anyways, regarding the to suggestions, neither worked. the first gave the message:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3646 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
the second message said:
start: Job is already running: gdm

---

### Post by bond17_007 on 2011-01-19
> **Kamikun said:**
> When I tried to log in again, it was the same problem, thus why i tried them again and got those errors. Anyways, regarding the to suggestions, neither worked. the first gave the message:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3646 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
the second message said:
start: Job is already running: gdm

Hi Kamikun,
   Can you quick check this setting:

In the terminal please type:
$ sudo cat /etc/pam.d/gdm

can you see if you can find a line that reads:
@include common-pamkeyring

if you find it, then comment it out by putting # so the line should look like
#@include common-pamkeyring

---

### Post by Kamikun on 2011-01-19
> **bond17_007 said:**
> Hi Kamikun,
   Can you quick check this setting:

In the terminal please type:
$ sudo cat /etc/pam.d/gdm

can you see if you can find a line that reads:
@include common-pamkeyring

if you find it, then comment it out by putting # so the line should look like
#@include common-pamkeyring

I don't see the line that you mentioned.

---

### Post by Kamikun on 2011-01-19
> **bond17_007 said:**
> Hi Kamikun,
   Can you quick check this setting:

In the terminal please type:
$ sudo cat /etc/pam.d/gdm

can you see if you can find a line that reads:
@include common-pamkeyring

if you find it, then comment it out by putting # so the line should look like
#@include common-pamkeyring

I don't see the line that you mentioned.

---

### Post by Kamikun on 2011-01-19
> **bond17_007 said:**
> Hi Kamikun,
   Can you quick check this setting:

In the terminal please type:
$ sudo cat /etc/pam.d/gdm

can you see if you can find a line that reads:
@include common-pamkeyring

if you find it, then comment it out by putting # so the line should look like
#@include common-pamkeyring

I don't see the line that you mentioned.

---

### Post by engr_sav on 2011-01-19
I have the same problem. I am running 10.10 on a Dell Netbook. However, it always catches on the third login and boots up. What's up?

Thanks,

---

### Post by Roxez on 2011-01-21
Damm still no ansewer T.T whe need help, no one know the answer? the only thing i know it is a nvidia xserver error :S

---

### Post by Kamikun on 2011-01-22
well, that doesn't sound like the same problem as me... mine is on the first log in and won't let me log in.

I'm thinking of taking my tablet to my on campus computer help and pray that someone there knows more about linux than i do and can help me.

Also, sorry about the triple post before.

---

### Post by Roxez on 2011-01-24
update jan 24, did nothing :s

---

### Post by eriro on 2011-01-29
I don't know if this helps someone else. 

I also had the problem of not being able to login. After entering my details and hitting enter the screen went black for about 2 seconds and then threw me back to the login screen.

I could fix this by allocating more memory to my onboard graphics card in the bios. 

I don't know why it worked though, but maybe 10.10 needs more video memory than earlier versions of ubuntu.

Hope this useful to anyone!

---

### Post by Kamikun on 2011-02-02
> **eriro said:**
> I don't know if this helps someone else. 

I also had the problem of not being able to login. After entering my details and hitting enter the screen went black for about 2 seconds and then threw me back to the login screen.

I could fix this by allocating more memory to my onboard graphics card in the bios. 

I don't know why it worked though, but maybe 10.10 needs more video memory than earlier versions of ubuntu.

Hope this useful to anyone!
Could you explain how to do what you did? I want to try it for 10.04

---

### Post by parsim on 2011-02-03
Well, I have now at least discovered an error log: although my ~/.xsession-errors is always empty, there is this in /var/log/gdm/:0-greeter.log:
```
$ sudo more /var/log/gdm/:0-greeter.log
** (process:1564): DEBUG: Greeter session pid=1564 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-UKuzeR/database
gdm-simple-greeter[1564]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-settings-daemon:1550): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```
Which is very similar to what other people see in ~/.xsession-errors.

---

### Post by Roxez on 2011-02-06
Well, now whe know where is the error, someone know how to fix it?

---

### Post by mockingbird on 2011-02-09
I got this error after I installed subversion (SVN).

Here is what's in my .xsession-errors file:

Xsession: X session started for username at Wed Feb  9 18:25:48 EST 2011
tempnam: Permission denied

I will try some of the suggestions here.

Maybe it's because I enables xhost + before but I forgot to revert to xhost - before I rebooted.

---

### Post by mockingbird on 2011-02-09
Ok typing this fixed it for me:

sudo chown <username> /tmp

---

### Post by mockingbird on 2011-02-09
Ok scratch that.  Chowning /tmp only allowed me to run startx after I had shutdown KDE with /etc/init.d/kdm stop.

But it seems to me this problem has something to do with a script messing with some of the folder permissions.

---

### Post by xubno on 2011-03-06
Hey, I just installed xubuntu 10.10 on a clean system except my /home partition was from another system and have the exact same problem.  It's been a while.  Has anyone figured this out?  What gives??

---

### Post by Amber2011 on 2011-03-06
I have been trying to work on this problem for 2 days now. I did not want to see anyone go through what I have been going through but at the same time I am glad I am not alone. I will read through all this. I can only get on-line in safe mode or root mode, neither of which allows me to download anything or make changes.

I also noticed after I type in my password the screen I want flashes for a second, then that stupid log in screen redirects.

---

### Post by ssuuddoo on 2011-03-07
on some of my computers (10.10) it sometimes refuses to login and sais that
gdm-simple-greeter is not responding and offers three possibilities:
lock screen; cancel; log out anyway.

when choosing any of these three choices, the graphic terminal (tty7 or tty8) gets lock up and I have to restart it through other terminal.

in the :0-greeter.log ...
gdm-simple-greeter: Fatal IO error 11 (Source is temporarily unavailable) on X server :0.0.

it only happens sometimes, but now I had to restart it twice to succesfully log in.
(problem is that regular users can't do it and cannot therefore log in anyway). 
grrr

---

### Post by Amber2011 on 2011-03-07
I have not seen that on my screen.

---

### Post by xubno on 2011-03-07
I think ssuuddoo means it's in one of the log files somewhere.  I don't think he's talking about the screen.  Hey suuddoo, could you please explain about that log?

---

### Post by xubno on 2011-03-07
Hey, just a thought, try logging in by selecting a different desktop on the login screen.  There may be a problem with just the desktop you are trying to use.

I think you'll get some choices after you type/select your user name.

---

### Post by parsim on 2011-05-01
I never managed to fix this, but after upgrading to 11.04 it has fixed itself.

Hallelujah.

---

### Post by ssuuddoo on 2011-05-05
it was fixed with the dist. upgrade. thnx folks :D

---

### Post by hitchhiker_42 on 2011-05-18
Hey guys, I have a somewhat similar problem.
I had version 10.10 working perfectly, but after updating to 11.04 my user logs off randomly and the user login page reappears. It doesn't seem to matter what I'm doing at the moment the session is closed: sometimes it happens when I open Firefox or documents, sometimes when the computer is just resting.

Is anyone having a similar issue?

---

### Post by parsim on 2011-05-18
> **hitchhiker_42 said:**
> Hey guys, I have a somewhat similar problem.
I had version 10.10 working perfectly, but after updating to 11.04 my user logs off randomly and the user login page reappears.

That sounds like a completely different problem; you might want to start a new thread.

---

### Post by hitchhiker_42 on 2011-05-19
> **parsim said:**
> That sounds like a completely different problem; you might want to start a new thread.


Thanks, I'll do that =)

---

### Post by Enter t'Ibex on 2011-05-30
Dont know why,but out of the blue this infinite login loop hit me last night (failed hibernate restore???? or last update????)....

When I looked at the .xsession-errors it said this:

home/logan/.gnupg/gpg-agent-info-logan-laptop :1 :syntax error "unexpected word"

That is from my notes and it probably not 100% correct...

so I nano'd that file and it was full of junk.  
sorry I don't have the file but it was full of *, $, and lots of diamonds in the string. Corrupted file full of hex crap....

I inserted a # as the first character to comment out the line, wrote out the file and rebooted.

That worked, login working.  Now the files are completely fixed and that line now looks like this.....

GPG_AGENT_INFO=/tmp/gpg-Sw2AVB/S.gpg-agent:1232:1

Hope this helps.. very strange indeed...

---

### Post by pdiefend on 2011-06-23
Hello all,

I am having trouble with the login now too and I was hoping that maybe one of you may have a possible fix.  When I try to login using the regular mode (quiet splash in grub settings) I get a login screen, I type in the password, the screen goes blank like it's resetting and then I get the login again asking for password and it loops forever. 

Then trying to get around the problem, it will not work in failsafe mode, same thing, and I tried to login using text setting at grub and that logged in fine at text, then when I type "startx" I get errors: 
```
"Could not update ICEauthority file /home/username/.ICEauthority"
``` and
```
"The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet". Do you wnat to delete the applet from you configuration?"
```Before I can even type startx I do have to go to /home/username/ and delete the files .xAuthority, .xAuthority-c, and .xAuthority-l.

[EDIT]
I did forget to add that x is working, but not properly, meaning I have the desktop, but some applications will not start.

---

### Post by Rolandmaffia on 2011-07-15
I had same error as it is described, I couldt log in, and .xsession-error said, that it can't open .profile, but it was OK...

Before this problem, I forced a remove of gconf2... it was a mistake... now I ran:

> **parsim said:**
> 
[list]
[*]sudo apt-get --purge --reinstall install gdm gnome-session (no difference)

than, I could log in...

---

[I](Otherwise, I have an problem with an applet after the reinstalls: 
> Error during loading OAFIID:GNOME_FastUserSwitchApplet. Delete it?

but it is a small problem only, now I can use my computer; thanks  **parsim** the idea.)[/I]

---

### Post by SDSL on 2012-02-05
I've fixed this error on 11.10 and 12.04
by logging from other laptop through ssh to the stucked laptop
then i've executed these commands

```

/etc/init.d/gdm stop
/etc/init.d/lightdm stop

```
You'll notice the login screen has been turned off and now you see the console.

from the ssh console do the following command
```

/etc/init.d/gdm start

```

now, you'll get the other login window which is not similar to the previous one,  then put your password and you're in.

---

### Post by bond17_007 on 2012-02-06
@SDSL, 
   You could also do it on the same computer by Pressing "Ctrl+Alt+F1" to start TTY1 (You can use F2.. F6) F7 is the one that has GDM. 
after you press the combo above, you will get a terminal where you should be able to login and execute the command you mentioned. Then by pressing "Ctrl+Alt+F7" go to the login screen.

---

### Post by xile101 on 2012-04-12
had the same problem: trying to login but displays a black screen with some text and then goes back to login screen.

i fixed it by typing this:
```
sudo chmod 777 /home/<username>/.Xauthority
```

now i can login like normal even after i log out and after i restart.
hope this helps.

---

### Post by pressse on 2012-04-12
Ïðèêîëüíîå âèäåî ïðî [íàðêîìàí ïàâëèê](http://presently.ru/narkoman-pavlik-chajka-22-9-seriya)

---

### Post by pressse on 2012-04-12
Ïðèêîëüíîå âèäåî ïðî [íàðêîìàí ïàâëèê ñìîòðåòü îíëàéí](http://presently.ru/narkoman-pavlik-chajka-22-9-seriya)

---

