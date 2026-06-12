---
title: "Login Broken"
date: 2011-12-31
forum: General Help
---

### Post by alladnsane on 2011-12-31
I can't login as my main admin account. From main gdm login menu I choose me account name, enter password and I end up back on the login menu.

I am running Ubuntu 10.04 on a desktop with integrated intel video and integrated sound. 

In my main admin account I just installed Skype and went into Preferences-->Startup Applications-->Options and clicked remember currently running applications to make Skype start at login.   then got my PS3 Eye to work with video and audio after some googling. I plugged it in and rebooted then changed pulseaudio input device to analog output and digital input with PS3 Eye selected as default input device. So far so good.  Tested in Skype options and sound recorder...all good.

I then unplugged USB cable for EYE and my screen went blank...nothing worked. I did a hard reset and got to login screen, but after typing my password there is a pause, screen goes black as if about to login and then right back to login screen.  All my other accounts will let me login with no problem but not my main admin account.  Have tried failsafe session and xterm session..same thing - right back to login screen.

---

### Post by alladnsane on 2011-12-31
UPDATE:
So I have been playing around and have been able to get into my account in console.  
After failed login attempt ctr+alt+F7 shows a few lines of code on screen, the last few of which are:

*(in red) PulseAudio configured for per-user-session                 [OK]
     *Enabling additional executable binary formats binfmt-support   [OK]
*checking batter state...                                            [OK]
     ^ (pointing at the ] after ok

the screen is frozen at this point but allows keyboard input (which doesn't do have any effect on anything).

ctrl+alt+F8 at this point brings me back to the login screen. ctrl+alt+F1 brings me to TTY1 and I can login to my main account in text only. So at least the account is still there and accessible, just apparently not through gdm.  Again, all other accounts are working normally.

Now that I have access I am still at a loss as to how to fix the problem or what to do next.

---

### Post by alladnsane on 2012-01-02
Does anyone have any ideas of what I should try or any information (and how to get it) I should post to receive some help? I am completely at a loss and really don't want to reinstall. I have a lot of time spent installing and customizing and don't want to go through it all again, but really need to get into that account (the only one with su rights not to mention all my stuff).
Any suggestions are welcome as I am at my wits end.
Thank-you

---

### Post by dozdozez on 2012-01-02
I would try in tty1:
sudo dpkg-reconfigure gdm

Emm... I have read your question more carefully and don't think this would fix your problem.

try to login as your default admin account again, then go to tty1 type:
dmesg
and paste the output here.

if you need access to your graphical configuration tools, you can run (as root or any other user):
xinit
and then in the grafical console
gnome-session
this will start a session with gnome, and if it fails to load it will be an error message that can give us the clue.

---

### Post by alladnsane on 2012-01-02
Thank you dozdozez...dont know yet if it worked but any response is good  :)

ok, I logged into tty1 as the broken user (only one with su privileges) and entered 
```
sudo dpkg-reconfigure gdm
```
(is there anyway to copy and paste from one user to another user in tty1 by the way??)  

EDIT:
So I then logged out from TTY1 and tried to login by switching users...no dice. Right back to this user unlock screen ( I assume from login menu it would have brought me back there).  I am getting sad :(

---

### Post by robsoles on 2012-01-02
before  you exit the terminal you may need to restart gdm, it used to be
```
 service gdm restart
```and should still restart gdm (if the dpkg command you ran didn't restart it). It shouldn't be a problem to remain logged in to the tty terminal as you use the keyboard combo to go back to GUI and try your login there.

That may not work, if it doesn't it may be that carefully editing one (or two files) in your home directory (or just deleting it/them outright) will "un-break" your login, probably the one to do with Skype, especially if you set that sucker to start with your login.

---

### Post by alladnsane on 2012-01-02
> **dozdozez said:**
> 
try to login as your default admin account again, then go to tty1 type:
dmesg
and paste the output here.

How do I copy and paste to and from TTY1? Print screen doesnt seem to be workin either.  I did get an error (this is a transcription bc unable to copy/paste)

```
restart: rejected send message, 1 matched rules;
 type="method_call", sender="1.80"(uid=1000 pid=6340 common="restart)
 interface=com.ubuntu.Upstart 8_6. Job" member="Restart" error name="(unset)"
 requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 com="/sbin/init"))
```

also errors with xinit, (again a transcription)
```
Fatal server error:Server is already active for display 0

ddxSigGiveUp: Closing log
No Protocol specified
giving up
xinit
```

> **robsoles said:**
> before  you exit the terminal you may need to restart gdm, it used to be
```
 service gdm restart
```and should still restart gdm (if the dpkg command you ran didn't restart it). It shouldn't be a problem to remain logged in to the tty terminal as you use the keyboard combo to go back to GUI and try your login there.
I did get an error with gdm restart 
(this is a transcription bc unable to copy/paste)
```
restart: rejected send message, 1 matched rules; type="method_call", sender="1.80"(uid=1000 pid=6340 common="restart) interface=com.ubuntu.Upstart 8_6. Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 com="/sbin/init"))
```

> That may not work, if it doesn't it may be that carefully editing one (or two files) in your home directory (or just deleting it/them outright) will "un-break" your login, probably the one to do with Skype, especially if you set that sucker to start with your login.

Should I apt-get purge skype (I did set it to start at login, or at least tried to, one of the last things I did before kaos?

---

### Post by dozdozez on 2012-01-02
I edited my last post to say another thing and didn't notice you had posted your answer.
Try to login as your default admin account again, then login as a normal user, open a terminal, type:
dmesg
and paste the output here.

---

### Post by alladnsane on 2012-01-02
> **dozdozez said:**
> I edited my last post to say another thing and didn't notice you had posted your answer.
Try to login as your default admin account again, then login as a normal user, open a terminal, type:
dmesg
and paste the output here.


Sorry not new to ubuntu but new to the consoles as I havent really had many problems before.  Did do that but don't know how to copy and paste from the console (see above)

---

### Post by fdrake on 2012-01-02
login in the console as the admin and type:
```
dmesg >> /home/regular_user/Desktop/dmesg.txt
sudo chmod 777 /home/regular_user/Desktop/dmesg.txt
```
login as regular user and look for that file in your desktop folder.

also can you tell su what kind of ubuntu are you using? you can run these commands as a regular user:

```
cat /etc/lsb-release && uname -a
```

---

### Post by fdrake on 2012-01-02
can you also try this if it works... login in recovery mode:
at boot time at the grub menu select recover > login as root prompt> and enter these commands: where USER = ise the admin username which you have issues to login with.

```

rm -R /home/USER/.pulse
mkdir /home/USER/.pulse
chown USER:USER /home/user/.pulse
reboot now

```

---

### Post by alladnsane on 2012-01-02
Sorry, I screwed up earlier, the error I mentioned was for the gdm restart...still transcribing it, was like 4 lines long including stuff like ...member="Restart" error name="(unset)"...

> **fdrake said:**
> login in the console as the admin and type:
```
dmesg >> /home/regular_user/Desktop/dmesg.txt
sudo chmod 777 /home/regular_user/Desktop/dmesg.txt
```
login as regular user and look for that file in your desktop folder.

tried this...permission denied

> **fdrake said:**
> also can you tell su what kind of ubuntu are you using? you can run these commands as a regular user:

```
cat /etc/lsb-release && uname -a
```

```
jay@alladnsane-desktop:~$ cat /etc/lsb-release && uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux alladnsane-desktop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
jay@alladnsane-desktop:~$ 
```

---

### Post by fdrake on 2012-01-02
> Quote:
Originally Posted by fdrake View Post
login in the console as the admin and type:
Code:

dmesg >> /home/regular_user/Desktop/dmesg.txt
sudo chmod 777 /home/regular_user/Desktop/dmesg.txt

login as regular user and look for that file in your desktop folder.
tried this...permission denied
I should have told you to run instead
```
dmesg | sudo tee /home/regular_user/Desktop/dmesg.txt 
```

that's ok, can you try my suggestion in post #11 and see if that solves the problem..

---

### Post by alladnsane on 2012-01-02
> **fdrake said:**
> I should have told you to run instead
```
dmesg | sudo tee /home/regular_user/Desktop/dmesg.txt 
```

that's ok, can you try my suggestion in post #11 and see if that solves the problem..


uploaded dmesg as attach. (in 3 parts...was too big for 1 or 2). about to try the reboot to root thing


THANK-YOU all very much

I also just apt-get purged skype   :)

---

### Post by dozdozez on 2012-01-02
In the console ^C doesn't works for copy paste, but if you can select the text, right click, copy and then you can paste.

But i would prefer the output you get following frdake's post above, it creates a text file in the regular_user's desktop called dmesg.txt that you can edit and make copy-paste in the usual way here.

---

### Post by alladnsane on 2012-01-02
> **fdrake said:**
> can you also try this if it works... login in recovery mode:
at boot time at the grub menu select recover > login as root prompt> and enter these commands: where USER = ise the admin username which you have issues to login with.

```

rm -R /home/USER/.pulse
mkdir /home/USER/.pulse
chown USER:USER /home/user/.pulse
reboot now

```


ok, I apparently have forgotten my root login password. I did however follow these commands in TTY1 under the broken user (as well as purging skype).

Same thing not fixed :(

---

### Post by alladnsane on 2012-01-02
> **dozdozez said:**
> In the console ^C doesn't works for copy paste, but if you can select the text, right click, copy and then you can paste.

I cannot select text and xinit returned
```
Fatal Server error: Server is already active for display 0
...
ddxSigGiveUp: Closing log

No Protocol specified
giving up.
xinit
```

that is my transcription and not a copy

EDIT:
I just came off nights and have been at work for 16 hrs.  Appreciate everyones help but need to sleep now. will continue tomorrow morning after work. Thank-you

---

### Post by robsoles on 2012-01-02
Forgotten root password: When you use 'sudo' your regular login password should allow you to proceed/action your commands - 'root' is best not granted a password.

If you really want to be root for a while then use```
sudo bash
```enter your regular password and then be pretty darn careful in whatever terminal you take root in until you type exit into that terminal, it will not close the terminal but will drop you back to being the user you logged in as in the first place.


The only way you'll have copy and paste is in the(/a) GUI - if you have another computer then you could setup (if not already running) openssh-server ("sudo apt-get install openssh-server") on the machine with the problem and then ssh into the problem machine using a GUI terminal from your other machine - if you have a second computer we could boot from the LiveCD (or is already running an OS capable of SSH in a terminal);

Please tell us if you have a second computer, all sorts of handy being able to keep a window open on the terminal while you try to login again, assuming you haven't second computer I am going to move on to getting some decent clues using your single computer.

(I am in Australia, it's 6.52am here, I have just gotten up and will have to go to work in a couple of hours - I can check in from work but if you have second computer and say so soon then I may not be the one who describes how to log into the problem one from the good/other one using SSH.)


I reviewed your dmesg files and the problem blocking your GUI login to your main account doesn't seem apparent in it to me, the problem may be indicated in one of the other logs the system keeps and the easiest way to find the problem is to watch relevant logs as you log in.


If you go to  TTY1 and login using any user (prefer user allowed to sudo) including the problem user and execute this command:```
tail -f /var/log/syslog
```and then return to the GUI screen (would I assume correctly you know that is [CTRL]+[ALT]+[F7]?) and attempt login again, sit through failure and then return to TTY1 - some messages relating to the error may have scrolled off the top of the screen but, if /var/log/syslog is the log with the clues, there will be a (better) clue on display on the screen.

If there doesn't seem to be a clue in the syslog file then there might be a usable clue in the xorg.0.log so try the same thing against that log:```
tail -f /var/log/Xorg.0.log
``` in TTY1 and make GUI logiin attempt with broken user again.

Once you find a log that is giving any clues at all you can use the following to get us a look at the clues```
tail -f /var/log/[COLOR=Blue]log-with-clues-filename[/COLOR] > /home/regular_user/Desktop/[COLOR=Blue]show-log-with-clues-filename[/COLOR].txt
``` repeat GUI login attempt to make it copy all the given clues into the file, return to TTY1 and press [CTRL]+[C] to make it stop writing new entries to our file. Login as "regular user" and the file I want to see should be sitting on your desktop, it shouldn't be ridiculously big and you might be able to just copy and paste it into some [noparse][code][/noparse] tags rather than having to attach it.

There are thousands of people on UF who can make out as well as me with decent clues and there are hundreds of us heaps better at it than me :)

Edit: If there are no (obvious) clues in any of the logs don't fret, just say so - plenty other fish in that barrel to take potshots at.

---

### Post by alladnsane on 2012-01-02
> **robsoles said:**
> Forgotten root password: When you use 'sudo' your regular login password should allow you to proceed/action your commands - 'root' is best not granted a password.

If you really want to be root for a while then use[code]sudo 
I do know to use sudo but was asked to login to recovery root prompt which then asked for root password...assumed it was same as my sudo password but apparently not.  

> Please tell us if you have a second computer, all sorts of handy being able to keep a window open on the terminal while you try to login again, assuming you haven't second computer I am going to move on to getting some decent clues using your single computer.
No second computer but do have a smartphone to follow instructions and post short replies.


I just woke up and need to leave for work (nights. bleh!) I will be home around 7:30 EST  (its 6pm here now), and will follow the log instructions.

Thanks again to you all (maybe there are people who know more than you but they aren't the ones responding to me so thank-you)

---

### Post by robsoles on 2012-01-03
> **alladnsane said:**
> I do know to use sudo but was asked to login to recovery root prompt which then asked for root password...assumed it was same as my sudo password but apparently not.

To be sure it is understood: To act as root for a series of terminal commands without  re-typing "sudo" at the start of each command you can become root by sudo'ing BASH, not a brilliant thing to do too regularly, or all that drunk, but worth it if you've more than three in a row to bother with.


Ahh, yes, soz, didn't read close enough - tricky: When I last checked it was still being touted as inappropriate to assign root a password (enabling common login for root) so I've always made the assumption that if I was challenged for (specifically) root's password I should enter nothing and expect the goods (recovery modes/LiveCD) - to be flat out honest the only thing I have ever accessed the recovery mode menus for was to have it try to repair installed packages before re-booting to whatever level of usability that gave me for another hack at it and this was only when I was convinced I could get solution easier booted from the problem OS itself as opposed LiveCD.

(I doubt having recovery mode attempt to repair broken packages will get this for us, keep reading, soz)

The command to give root a password is straightforward and simple but I won't post it publicly (even though a bit of man'ning up and/or Googling should put anybody in the picture (anybody who really wants to be in the picture)) because I reckon it is a bit malicious to advise anybody to assign root an actual password.

If you really want to assign root a password I will publicly advise that you that you want a minimum of 16 alpha-num digits which form no recognisable word or element you know of - if you take an eight letter word and convert it to hex then that 16 character string might be enough but if we can think of this as a method for choosing more complex passwords (that we have an easy token to remember by) then crackers (who are only too thrilled to try more and more complex stuff) can think of coding their crap to make that brute force attack as well.

I will PM you the command line to assign root his password if you insist to know. Most people with 6 months experience in Linux (including 5 minutes in terminal) will :face-palm: when they see the line. Many with more than a couple of years experience in Linux know the line and won't immediately share it with beginners nor are they in any hurry to run around using it on any systems they run a GUI in...

If you ever do assign root a password then the biggest mistake you could make is to get used to (or even really bother) logging into any GUI as that particular deity.


FYI (@fdrake also) there was no need to login any more specially than TTY (as the user in question) to remove the ~/.pulse file and restore a blank, the following instructions execute flawlessly for me in terminal both in GUI and in TTY logged in as [COLOR=Blue]<me!>[/COLOR] repeatedly.
(login as specified user)```
sudo rm -Rf ~/.pulse
sudo mkdir ~/.pulse
sudo chown [COLOR=Blue]<me!>[/COLOR]:[COLOR=Blue]<me!>[/COLOR] ~/.pulse
```Of course [COLOR=Blue]<me!>[/COLOR] is actually rob on my system(s). Just in case any reader doesn't know; In terminal (any Linux terminal) "~/" translates to /home/[COLOR=Blue]<me!>[/COLOR] where [COLOR=Blue]<me!>[/COLOR] is specifically the logged in user.

I doubt the pulse entries are the problem. I want to bet that it is the Skype config file(s) that are borking this but it may just be my hatred and loathing of the people who acquired it last - to be honest it will be the first config files I try to help alladnsane **move** out of the way to attempt login again with quite some expectation of success.


@alladnsane: Since this debacle began; Have you tried plugging the device back in and rebooting with it plugged in? Just occurs that a script relating to the device might be borking your login when it cannot communicate with that device - chances are the foolish line in the reasonable .config file isn't that foolish when that thing is plugged in.


@all: If you can possibly spare the extra time it will take it is well worth your while to restart your computer after every major change (that you have never performed on specific OS before) before any consecutive change because solving problems when it is only one major step you took before a restart is a lot easier than alladnsane is facing ATM. IMHO (H is for humble.) any software that Canonical hasn't included in your repository (excludes "device drivers" delivered using the other mech) *is* a major change to install and warrants restarting to check it hasn't broken anything about your preferred system behaviour for your login.

Soz, I can make long posts coz I type too fast (n stuff) in general and some topics just inspire me :roll: #-o

---

### Post by alladnsane on 2012-01-03
> **robsoles said:**
> I doubt the pulse entries are the problem. I want to bet that it is the Skype config file(s) that are borking this but it may just be my hatred and loathing of the people who acquired it last - to be honest it will be the first config files I try to help alladnsane **move** out of the way to attempt login again with quite some expectation of success.
I did follow the commands to rmove the pulse entries in tty1 as my sudo user. Pretty sure it worked.

> @alladnsane: Since this debacle began; Have you tried plugging the device back in and rebooting with it plugged in? Just occurs that a script relating to the device might be borking your login when it cannot communicate with that device - chances are the foolish line in the reasonable .config file isn't that foolish when that thing is plugged in.
Yes, the first thing I tried was to reboot with the EYE cam plugged in..guess I should edit my original post to include that.  I have since apt-get purged skype as well.

Ok, I tried the tail command to my other user but permission denied so I followed the same command but to a flashdrive. I think the syslog has NB stuff (shows some errors relating to gdm anyway. Don't know about the Xorg log, don't think anything there but will attach it anyway.

results of syslog during login attempt:
```

Jan  3 08:06:02 alladnsane-desktop kernel: [  540.631123] sd 7:0:0:0: [sdi] 8232960 512-byte logical blocks: (4.21 GB/3.92 GiB)
Jan  3 08:06:02 alladnsane-desktop kernel: [  540.634119] sd 7:0:0:0: [sdi] Write Protect is off
Jan  3 08:06:02 alladnsane-desktop kernel: [  540.634123] sd 7:0:0:0: [sdi] Mode Sense: 03 00 00 00
Jan  3 08:06:02 alladnsane-desktop kernel: [  540.634126] sd 7:0:0:0: [sdi] Assuming drive cache: write through
Jan  3 08:06:02 alladnsane-desktop kernel: [  540.651127] sd 7:0:0:0: [sdi] Assuming drive cache: write through
Jan  3 08:06:03 alladnsane-desktop kernel: [  540.653237]  sdi: sdi1
Jan  3 08:06:03 alladnsane-desktop kernel: [  541.010320] sd 7:0:0:0: [sdi] Assuming drive cache: write through
Jan  3 08:06:03 alladnsane-desktop kernel: [  541.012410] sd 7:0:0:0: [sdi] Attached SCSI removable disk
Jan  3 08:06:49 alladnsane-desktop kernel: [  587.830023] FAT: Unrecognized mount option "fmask-137" or missing value
Jan  3 08:10:59 alladnsane-desktop kernel: [  837.410804] FAT: Unrecognized mount option "fmask-137" or missing value
Jan  3 08:14:25 alladnsane-desktop acpid: client 1149[0:0] has disconnected
Jan  3 08:14:25 alladnsane-desktop acpid: client connected from 1149[0:0]
Jan  3 08:14:25 alladnsane-desktop acpid: 1 client rule loaded
Jan  3 08:14:25 alladnsane-desktop kernel: [ 1043.666948] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jan  3 08:14:30 alladnsane-desktop gdm-session-worker[1490]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  3 08:14:33 alladnsane-desktop gdm-session-worker[1490]: pam_sm_authenticate: Called
Jan  3 08:14:33 alladnsane-desktop gdm-session-worker[1490]: pam_sm_authenticate: username = [alladnsane]
Jan  3 08:14:33 alladnsane-desktop gdm-session-worker[1490]: pam_sm_authenticate: /home/alladnsane is already mounted
Jan  3 08:14:34 alladnsane-desktop gdm-simple-slave[2024]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan  3 08:14:34 alladnsane-desktop acpid: client 1149[0:0] has disconnected
Jan  3 08:14:34 alladnsane-desktop acpid: client connected from 2026[0:0]
Jan  3 08:14:34 alladnsane-desktop acpid: 1 client rule loaded
Jan  3 08:14:35 alladnsane-desktop gdm-session-worker[2062]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan  3 08:14:36 alladnsane-desktop gdm-simple-greeter[2061]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jan  3 08:14:36 alladnsane-desktop gdm-simple-greeter[2061]: WARNING: Unable to lookup user name alladnsa: Success
```
don't know if it matters or not but in regards to the last line the user name is actually alladnsane (it is shown missing the final "ne" in the log)


Xorg.0.log included as attachment. I also edited message 7 to include transcriptions of the full error messages when i tried xinit and gdm restart.

---

### Post by robsoles on 2012-01-03
(good morning :))

Clue: custom.conf

Please log into TTY as alladnsane and;```
grep -R 'custom.conf' *
```

If that gives you one and only one result (a filename followed by a snippet of text showing how 'custom.conf' is used) then please attach (a copy of) that file to your next post.

If more than one result use "> results.txt" to get me a look at those please.


Sorry our time doesn't align better.

---

### Post by alladnsane on 2012-01-03
Good Morning :)

I tried ```
grep -R 'custom.conf' *
```
but it didn't seem to do anything. I hit ctrl+c and then got messages about ```
[184.945036] ecryptfs_decrpt_page: Error attempting to read lowerpage; rc=[-4]
```

Also, how would I copy the results to graphical user after I get them?

---

### Post by fdrake on 2012-01-03
from your previous logs it looks like that the error is:
> 

[48756.480602] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[48828.894834] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[48846.545255] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[48867.082118] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[48881.315363] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[48941.896674] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[49564.974817] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[49584.568022] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[49604.371103] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50079.372279] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50141.320977] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50291.862006] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50311.570889] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50354.107881] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50505.249443] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50568.949650] SysRq : HELP : loglevel(0-9) reBoot Crash terminate-all-tasks(E) memory-full-oom-kill(F) kill-all-tasks(I) thaw-filesystems(J) saK show-backtrace-all-active-cpus(L) show-memory-usage(M) nice-all-RT-tasks(N) powerOff show-registers(P) show-all-timers(Q) unRaw Sync show-task-states(T) Unmount force-fb(V) show-blocked-tasks(W) dump-ftrace-buffer(Z) 
[50599.905151] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50664.198688] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50717.974718] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[50771.807756] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[51074.754010] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[51238.104388] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[51509.719951] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[51996.450166] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[52066.551706] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[52319.734433] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[52811.273284] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[53124.005096] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
from your last log (syslog)
> Jan  3 08:14:25 alladnsane-desktop kernel: [ 1043.666948] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
searching online i found out that is a problem with the kernel
[https://bugs.archlinux.org/task/22228](https://bugs.archlinux.org/task/22228) present in different distributions.

do you have an older kernel present in your system? older than 2.6.32-37-generic (you should have available at least 2.6.32-36-generic or older). Try to boot into that kernel and check if you encounter the same issue. You can try to reinstall your kernel but it looks like it doesn't give any positive results... to reinstall:

```
sudo apt-get install --reinstall linux-image-2.6.32-37-generic linux-headers-2.6.32-37-generic
```


@robsoles
> FYI (@fdrake also) there was no need to login any more specially than TTY (as the user in question) to remove the ~/.pulse file and restore a blank, the following instructions execute flawlessly for me in terminal both in GUI and in TTY logged in as <me!> repeatedly.
(login as specified user)
Code:

sudo rm -Rf ~/.pulse
sudo mkdir ~/.pulse
sudo chown <me!>:<me!> ~/.pulse

Of course <me!> is actually rob on my system(s). Just in case any reader doesn't know; In terminal (any Linux terminal) "~/" translates to /home/<me!> where <me!> is specifically the logged in user.
the reason i told to the OP to use the root user in recovery mode to delete the files is that some of those files (at login) may start running and once they are open they cannot be deleted even if you use sudo. but off corse i couldn't be sure of that so i just played safe ;)

---

### Post by alladnsane on 2012-01-03
> **fdrake said:**
> from your previous logs it looks like that the error is:
from your last log (syslog)

searching online i found out that is a problem with the kernel
[https://bugs.archlinux.org/task/22228](https://bugs.archlinux.org/task/22228) present in different distributions.

do you have an older kernel present in your system? older than 2.6.32-37-generic (you should have available at least 2.6.32-36-generic or older). Try to boot into that kernel and check if you encounter the same issue. You can try to reinstall your kernel but it looks like it doesn't give any positive results... to reinstall:

Just tried 2.6.32-36 generic...same thing.  Everything was working fine with 2.6.32-37 up to now and is still working with other users

---

### Post by robsoles on 2012-01-03
@fdrake: I don't think that is the problem because most of those entries occur in systems that don't block a user from accessing their GUI login.


Howto write to other user's folder:

OK, making the assumption that you have chosen encrypted home folder for every user you have made on this system you need to make a new user with a **non**-encrypted home folder so that 'alladnsane' can become root (in tty1) and write files to their desktop or where-ever and chown them to the new user so you can log in and attach or open or whatever the files as that new user.```
sudo bash
grep -R 'whatever-you-are-looking-for-in-text-config-files' .* > /home/[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]/Desktop/results.txt
chown [COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]:[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR] /home/[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]/Desktop/results.txt
exit
```


Mmmh, didn't turn up the file referencing that custom.conf thing using grep, poop.

So, you executed "sudo apt-get purge skype" if I understand? Chances are that that didn't remove per-user config files etc so lets have a quick look for a couple of different config files might be slinking around your home folder: (login as alladnsane)```
find -name *kype*
find -name *eye*
```If you get a response from either of those indicating Skype or that Eye thing you have then we can rename those to something like "original.filename[COLOR="blue"].dont[/COLOR]" and try your GUI login again.

Ask for specific instructions on renaming the files (show us the resulting files that are returned for those 'find' instructions as well please) if you are not sure how to safely move them out of the way using the advice in the above paragraph.

---

### Post by alladnsane on 2012-01-04
> **robsoles said:**
> (good morning :))

Clue: custom.conf

Please log into TTY as alladnsane and;```
grep -R 'custom.conf' *
```So I figured out the reason this didn't work the first time... there was no"." before the *.

> Howto write to other user's folder:

OK, making the assumption that you have chosen encrypted home folder for every user you have made on this system you need to make a new user with a **non**-encrypted home folder so that 'alladnsane' can become root (in tty1) and write files to their desktop or where-ever and chown them to the new user so you can log in and attach or open or whatever the files as that new user.```
sudo bash
grep -R 'whatever-you-are-looking-for-in-text-config-files' .* > /home/[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]/Desktop/results.txt
chown [COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]:[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR] /home/[COLOR="Blue"]that-new-user-with-unencrypted-home-folder[/COLOR]/Desktop/results.txt
exit
```Yes my accounts are encrypted but do have my daughters account not encrypted. However I am using a flashdrive instead so I used:```
sudo bash
grep -R 'custom.conf' .* --exclude-dir=\.Private --exclude-dir=\.wine > /media/flashlogs/grepresults.txt
```So the results of the grep came up with nothing (I blocked /.Private because that was all the ecryptfs errors, and blocked /.wine because it returned a Warning about a recursive loop.  I waited until the drive stopped running and then ctrl+c.)

> So, you executed "sudo apt-get purge skype" if I understand? Yes I did

> find -name *eye*[/code]If you get a response from either of those indicating Skype or that Eye thing you have then we can rename those to something like "original.filename[COLOR="blue"].dont[/COLOR]" and try your GUI login again.

Ask for specific instructions on renaming the files (show us the resulting files that are returned for those 'find' instructions as well please) if you are not sure how to safely move them out of the way using the advice in the above paragraph.
Came up with nothing for eye, cam, ps3, sony. Skype returend this:```
./.config/ubuntu-tweak/sourcecenter/sourcecenter/logo/skype-logo.png
./.config/ubuntu-tweak/sourcecenter/sourcecenter/logo/skype-icon.png
./.config/ubuntu-tweak/appcenter/appcenter/logo/skype-logo.png
./.config/ubuntu-tweak/appcenter/appcenter/logo/skype-icon.png
./.local/share/gnome-do/plugins/addin-db-001/addin-data/1/Do.Skype,1.2.maddin
./.Skype
```
I renamed .Skype using ```
mv .Skype .Skype.dontuse
```
Rebooted and same thing happened. ctrl+alt+F7 showed frozen bootup screen```
* .....                     [OK]
[COLOR="Red"]* [COLOR="Black"]PulseAudio configured for per-user session
                *Enabling additional exucatable binary formats binfmt support    [OK]
* checking battery state                          [OK] [/COLOR][/COLOR]
```
Where * .....    refers to first few lines on screen
Which other ones should I change?

---

### Post by robsoles on 2012-01-04
Can you look for ```

./.local/share/gnome-do/plugins/addin-db-001/addin-data/1/Do.Skype,1.2.maddin
```In your Daughter's home folder please?

If you cannot find it in her home folder then would you please move it from there in your own home folder ```
./.local/share/gnome-do/plugins/addin-db-001/addin-data/1
```to somewhere like a sub-folder of any personal folder (Desktop, Documents, Videos etc etc).


If you are saying that after you moved .skype to .skype.dontuse the computer doesn't even make it to the GUI login prompt then I gotta say that's very unusual but if it is so then you had best use tty1 to rename it back (???)

---

### Post by alladnsane on 2012-01-04
> **robsoles said:**
> Can you look for ```

./.local/share/gnome-do/plugins/addin-db-001/addin-data/1/Do.Skype,1.2.maddin
```In your Daughter's home folder please?I found it in the account that I am using right now (my other account "jay"- encrypted with no sudo priveleges). What would you like me to do with it??  Should I still move in my own home folder?

> If you are saying that after you moved .skype to .skype.dontuse the computer doesn't even make it to the GUI login prompt then I gotta say that's very unusual but if it is so then you had best use tty1 to rename it back (???)It makes it to the GUI login menu, but then after I attempt to login and comes back to login menu that is the code I see at ctrl+alt+f7...login prompt is now at ctrl+alt+F8.  This is the same thing that has been happening so no change at all.

---

### Post by robsoles on 2012-01-04
If 'jay' can login then it seems pointless to me to move the file out of the way in your 'alladnsane' home folders.

Is teabreak where I work - I will think on it some more.

If you can bare it I would really love to see the resulting file from:
(must login as alladnsane, in TTY for this to have chance of finding it)```
sudo bash
cd /
grep -R 'custom.conf' .* > /<somewhere-you-can-write-as-root-read-as-GUI-user>/search-custom-conf.txt
exit
```
It will take forever to finish and may make a very ugly file of output (all sorts of errors, denieds and so forth, I don't care - only a matter of sifting through them for better clues) but it should find whatever is trying to access that custom.conf file when alladnsane tries to login to the GUI.


As a quick test to make sure it is worthwhile to sit through that grep command, open tty1 login and set off tail -f /var/log/syslog in it - try to login as anybody but alladnsane and if the syslog mentions that custom.conf thing but doesn't block the other user's login then custom.conf isn't worth pursuing as the culprit either.

(I'll be checking you out for a per-user xorg config file next if that custom.conf error is there for other users who can login to GUI.)

---

### Post by alladnsane on 2012-01-04
> **robsoles said:**
> As a quick test to make sure it is worthwhile to sit through that grep command, open tty1 login and set off tail -f /var/log/syslog in it - try to login as anybody but alladnsane and if the syslog mentions that custom.conf thing but doesn't block the other user's login then custom.conf isn't worth pursuing as the culprit either.
OK, I think this is really weird but am not sure.  I rebooted the computer, went to tty1 and logged in as jay (figured it would be easier to send logs straight to desktop :) ), sent the syslog to my desktop, switched to gdm login (ctrl+alt+F7), and logged in as jay. Logged in no problem, switched back to tty1, ctrl+c to kill the tail, logged out of tty1, ctrl+F7 back to jay GUI. 

There is no mention of custom.conf but there are other errors. That's when things get weird. Logged out and now the gdm login at ctrl+alt+f8 and ctrl+alt+f7 shows the same thing as after I try unsuccessfully to log in as alladnsane;
>  ```
* .....                     [OK]
[COLOR="Red"]* [COLOR="Black"]PulseAudio configured for per-user session
                *Enabling additional exucatable binary formats binfmt support    [OK]
* checking battery state                          [OK] [/COLOR][/COLOR]
```
Where * .....    refers to first few lines on screen



Switched back to tty1, logged in as jay again and same routine except ctrl+alt+f8 to get to gdm login. Logged in no problem as jay but a totally different syslog now showing the same error with /etc/gdm/custom.conf

I will attach both logs and begin the grep. (any idea how long it should take or how to tell when it's done bc doesn't seem like it's doing anything?)

Thank-you again for all time and effort. It is really appreciated.

---

### Post by robsoles on 2012-01-04
I can review those logs closer in about 4 hours when I go home.


The grep command will take a fair while to complete and how long entirely depends on how much data is 'openable' for grep to search in your system because the instruction I gave you told it to look at every last thing throughout any mounted file-system you have.

Soz, on the other hand tho -: if you logged in as alladnsane (as I requested) to start the grep command then you can go back to GUI and log in as one of the users who hasn't been blocked in GUI and play mostly everything available to you at that point as the other user.


If you do log in as another user (in GUI) then you can open terminal and pop```
sudo ps aux | grep 'grep'
```into it - if you get two responses relating to root running grep then the other command is still executing, if there is only one reference to root running grep there then it is this instance of "sudo ps aux | **grep** 'grep'" that is being reported.


If I get a better clue from them logs, when I get home, I will post again without prompting.

---

### Post by robsoles on 2012-01-05
If there is a file in /etc/X11/ on this machine named xorg.conf then I would like to see a copy of it.


Sorry, if that silly grep command is still running system wide then please stop it and switch to the /etc directory to reissue it (as root) and without the period - dunno how I missed '/etc/gdm/' as a good place to look closer before (indicated as location of 'custom.conf'), drop the '.conf' in the query, forgive my re-issue of the commands:```
sudo bash
cd /etc
grep [COLOR=Blue]-R[/COLOR] custom *
exit
```After grinning at the result you can repeat for us with the > somefile bit please ;)

---

### Post by robsoles on 2012-01-05
Just in case you are working from emails or something I have reposted to let you know I have edited above to include the 'recursive' switch in the grep command as I should have in the first place.


Edit: Been meaning to ask; syslog makes it look like 'jay' made it to a usable desktop in the GUI - is that right?

---

### Post by alladnsane on 2012-01-05
> **robsoles said:**
> 
Edit: Been meaning to ask; syslog makes it look like 'jay' made it to a usable desktop in the GUI - is that right?That is correct. Jay made it to usable desktop both times.

> If there is a file in /etc/X11/ on this machine named xorg.conf then I would like to see a copy of it.There was no xorg.conf in /etc/X11/ so I expanded the search;```
./usr/lib/X11/xorg.conf.d
./usr/share/man/man5/xorg.conf.5.gz
./etc/X11/xorg.conf.failsafe
find -name *org.con*
```The contents of xorg.conf.failsafe;```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I have attached the results of;```
sudo bash
cd /etc
grep -R custom 
```
EDIT: The original grep command never did finish ;)

---

### Post by robsoles on 2012-01-05
I wish something would turn up as the thing pointing at this custom.conf file but it seems it won't so never mind, let's make a custom.conf file that is pretty much empty and get on with something else:```
sudo nano /etc/gdm/custom.conf
```Type '#' into the start of the file (in nano) and then press [CTRL]+[X] - program prompts if you want to save or not so hit [Y], program (may) prompt with filename so just hit [Enter].

Login to tty1 as alladnsane:```
sudo bash
tail -f /var/log/syslog > /home/<unencrypted-users-folders>/see-login-syslog-again.txt

```Switch back to GUI login screen and attempt using alladnsane again please - wait fully for login screen back on display and then [CTRL]+[C] to break that tail command and attach this new log please.

Remaining logged in (and root) as alladnsane please ```
cd ~/
ls .* > /home/<unencrypted-place-again>/show-short-form-list-config.txt
ls -R .* > /home/<unencrypted-place-again>/show-long-form-list-config.txt
exit
```(TIP: Always don't remain root when you can't think why it is necessary)


Sorry we haven't found the problem (and made it go away) yet - if you get sick of allowing me to pursue the problem remotely like this then it is possible to spawn a new user, give them sudo privileges and copy/move all the personal data from alladnsane to the new user. Another alternative is to scrub all of 'alladnsane's personal configuration files with the expectation that all the really required ones will be re-written on the fly as required.

---

### Post by alladnsane on 2012-01-05
First off, if YOU are sick of trying then I understand. You have gone above and beyond for some guy on the other side of the world (who really does appreciate it - success or not).  I am getting close to calling it myself.

-I made the blank /etc/gdm/custom.conf  -- didn't help for the record.
-rebooted
-tty1 -> alladnsane login
-sudo bash
-tail -f /var/log/syslog > ....
-back to gdm and login and the winner is;```
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.977710] sd 5:0:0:0: [sdh] Write Protect is off
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.977713] sd 5:0:0:0: [sdh] Mode Sense: 03 00 00 00
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.977716] sd 5:0:0:0: [sdh] Assuming drive cache: write through
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.980132] sd 5:0:0:0: [sdh] Assuming drive cache: write through
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.980193]  sdh: sdh1
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.985883] sd 5:0:0:0: [sdh] Assuming drive cache: write through
Jan  5 21:11:33 alladnsane-desktop kernel: [   44.985922] sd 5:0:0:0: [sdh] Attached SCSI removable disk
Jan  5 21:11:47 alladnsane-desktop sudo: pam_sm_authenticate: Called
Jan  5 21:11:47 alladnsane-desktop sudo: pam_sm_authenticate: username = [alladnsane]
Jan  5 21:11:47 alladnsane-desktop sudo: pam_sm_authenticate: /home/alladnsane is already mounted
Jan  5 21:13:07 alladnsane-desktop acpid: client connected from 1097[0:0]
Jan  5 21:13:07 alladnsane-desktop acpid: 1 client rule loaded
Jan  5 21:13:07 alladnsane-desktop kernel: [  139.790877] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jan  5 21:13:20 alladnsane-desktop gdm-session-worker[1136]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  5 21:13:29 alladnsane-desktop gdm-session-worker[1136]: pam_sm_authenticate: Called
Jan  5 21:13:29 alladnsane-desktop gdm-session-worker[1136]: pam_sm_authenticate: username = [alladnsane]
Jan  5 21:13:29 alladnsane-desktop gdm-session-worker[1136]: pam_sm_authenticate: /home/alladnsane is already mounted
Jan  5 21:13:30 alladnsane-desktop acpid: client 1097[0:0] has disconnected
Jan  5 21:13:30 alladnsane-desktop acpid: client connected from 1917[0:0]
Jan  5 21:13:30 alladnsane-desktop acpid: 1 client rule loaded
Jan  5 21:13:31 alladnsane-desktop gdm-simple-greeter[1952]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jan  5 21:13:32 alladnsane-desktop gdm-simple-greeter[1952]: WARNING: Unable to lookup user name alladnsa: Success
```

I also found some other threads with similar issues...[[COLOR="Blue"]_Ubuntu 10.04 GDM/Gnome Login Loop_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1433987")
> **axi0n said:**
> ...On reboot, I would be presented with the GDM login screen but when I clicked on a user and entered a password.. it would look like it was logging in, then kick me straight back out to the login screen...

Looking at the logs, I eventually figured I would attempt to re-install the complaining packages with....

sudo apt-get install xxx --reinstall --force-yes

I had done a bunch when I tried to re-install gnome... It was already installed but said it couldn't re-install because of a missing dependency...  Empathy...

sudo apt-get install empathy

It also had a recommendation to install "gnome-desktop-environment"  (well duh.. ) ;-)

Installed that... Plus the bonus 112Mb of dependency packages, and now I am fully into the system GUI...This is referring to a beta 10.04 patched installation so not sure how relevant.

[[COLOR="Blue"]_Login problem (the login screen shows again)_[/COLOR]]("http://askubuntu.com/questions/5956/login-problem-the-login-screen-shows-again")> I had a problem with GDM restarting (once) each time when trying to log in after upgrading to Maverick Alpha, upon installing GDM on top of an existing ubuntu Server install.

The solution for me was to remove GDM and GDM configuration files and reinstall.

ONLY RECOMMENDED if you can't get another solution.

EDIT: forgot this one
[[COLOR="Blue"]_Login Loop problem with 10.10_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9959525")

> **moonguide said:**
> RESOLVED

(For each of the following I chose to boot into recovery mode from GRUB.)

Alas, I did not keep notes on where I got the answer (it was on this forum, I think in one of the 10.04 threads), but here's the steps I took to get my 10.10 install working:

I renamed ~.ICEauthority and ~.Xauthority, prefixing them with "old" so I could change them back if I needed to. I did them one at a time. Neither change made any difference -- I still had the login loop.

One recommendation said to add the following to /etc/X11/xorg.conf:

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

I rebooted, letting GRUB make the default choice, and successfully logged in to 10.10.

I didn't have an xorg.conf file, so I created one with nano. (If you are like me you might not know about nano. It's a text file editor like vi or vim.)



Also I have attached an annotated mixed log. From clean boot I tried to login to alladnsane, successfully logged in to jay, and logged in to alladnsane in tty1.

---

### Post by alladnsane on 2012-01-05
I edited the last message and pm'd you.  Should I try any of those solutions??

---

### Post by robsoles on 2012-01-06
> **alladnsane said:**
> I edited the last message and pm'd you.  Should I try any of those solutions??

PM understood, I made some little response. We'll get back to that longer list if we need to later.


Those situations don't seem to show that they fixed an individuals GUI login in a system where other individuals were still able to login to the GUI while that individual had the problem. I can't see one to pursue based on that lacking similarity.


You made a fairly unique problem with the sequence of steps you took, I will review the short-list of config files and see if there are any that I would either instruct you to simply **m**o**v**e out of the way or specifically request a squiz at. Of course I am going to look at that log of yours - I gotta go shops and make dinner too so next post could be couple (or more, soz got a bit of reading to do in this) hours away.



Re: Sick of it
My concern in mentioning that was that you might be less fascinated by getting to the bottom of this than I am (or at least "... than I can make myself be, once I've posted to a thread and appear to be the (*gulp*) leader") so I thought I should probably let you know that there are shortcuts back to just getting on with your computing life (so to speak) if you wanted to just skip it and are willing to have a 'factory reset' to your own desktop.

Chances are if we stick at it there might not be any need for your next logical thread "how to get 'eye' working with skype in 10.04 without borking GUI login" but remaining chances we make 10 pages of posts each and one of us cracks and begs for one of the shortcuts :roll:

---

### Post by robsoles on 2012-01-06
> **alladnsane said:**
> ...

-I made the blank /etc/gdm/custom.conf  -- didn't help for the record.
...

It helped confirm my new suspicion it was nothing to do with the overall issue blocking alladnsane from logging in.


It is hard to be sure from the snippets of logs (forgive me if more of Jay's login is in earlier posted log(s)) whether or not syslog (or any other) ever mentioned```
/build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
```If it is not mentioned as the other GUI users login successfully to a usable desktop then we are after a couple of details regarding this file: We need to find its true address and we need to find what package it belongs to and what is trying to include it as part of alladnsane's startup.

Oh, wait - I'll leave that there just in case we end up going back to it but **here is something I wish I had thought of a couple of days ago:**


Mmmh. You got everything just how you wanted it and then told it to remember running programs for start time didn't you! Let's pop that out of the way:
(login to tty as alladnsane please)```
mkdir ~/Documents/old-autostart
mv -R ~/.config/gnome-session/saved-session/* ~/Documents/old-autostart/
```I don't expect so but just upgrade yourself to root if it denies permission to move those, downgrade yourself but you don't need to logout of tty1 before jumping to GUI for yet another login attempt.

I'm almost holding my breath to hear back about this one :)

---

### Post by robsoles on 2012-01-06
> **robsoles said:**
> ...

Mmmh. You got everything just how you wanted it and then told it to remember running programs for start time didn't you! Let's pop that out of the way:
(login to tty as alladnsane please)```
mkdir ~/Documents/old-autostart
mv -R ~/.config/gnome-session/saved-session/* ~/Documents/old-autostart/
```I don't expect so but just upgrade yourself to root if it denies permission to move those, downgrade yourself but you don't need to logout of tty1 before jumping to GUI for yet another login attempt.

I'm almost holding my breath to hear back about this one :)

Good thing I didn't hold my breath :)

Just in case you can see the potential short-short-cut that instruction is (to making alladnsane able to reach usable GUI desktop), you can take it that way but otherwise if it does fix the login problem then we can find a pathway to the problem element(s) by looking at the contents of ~/Documents/old-autostart; It wouldn't surprise me if that 'alladnsa' reference I have purposefully ignored is in there.

I have ignored that 'alladnsa' reference to date because looking for that one reference where (potentially) thousands of references to 'alladnsane' exist would be even more nightmarish than wading through the result of 'ls -R .*' from anybody's home directory would be.

What have you got for me Pal? Please tell me what happens when...

---

### Post by alladnsane on 2012-01-07
> [Good thing I didn't hold my breath :)

Sorry if you were turning blue ;) Working rotating 16 hour shifts and juggling a young daughter. 

> (login to tty as alladnsane please)```
mkdir ~/Documents/old-autostart
mv -R ~/.config/gnome-session/saved-session/* ~/Documents/old-autostart/
```I don't expect so but just upgrade yourself to root if it denies permission to move those, downgrade yourself but you don't need to logout of tty1 before jumping to GUI for yet another login attempt.

I'm almost holding my breath to hear back about this one :)

And...no good. No change.

> **robsoles said:**
> It is hard to be sure from the snippets of logs (forgive me if more of Jay's login is in earlier posted log(s)) whether or not syslog (or any other) ever mentioned```
/build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
```If it is not mentioned as the other GUI users login successfully to a usable desktop then we are after a couple of details regarding this file: We need to find its true address and we need to find what package it belongs to and what is trying to include it as part of alladnsane's startup.

It is mentioned for other persons, but only at logout. For alladnsane it is mentioned at same time as login, but the login loops back to gdm so fast its hard to say. Got more snippete for you, sorry. I clean booted, logged in as jay, logged out, logged in as jay again, logged out, logged in as another user with no password, logged out and tried to (but failed to login as alladnsane. I spaced all events out and kept track of times.
```
/var/log/syslog

#### 8:22  reboot 
Jan  6 20:22:59 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[1148]: [COLOR="Red"]Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow[/COLOR][/COLOR]
Jan  6 20:22:59 alladnsane-desktop avahi-daemon[996]: Registering new address record for fe80::21b:fcff:fe73:bcc2 on eth0.*.
Jan  6 20:22:59 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[1148]: WARNING: Unable to lookup user name alladnsa: Success[/COLOR]

#### 8:29 successfull login as jay 
an  6 20:29:34 alladnsane-desktop gdm-session-worker[1149]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 20:29:48 alladnsane-desktop gdm-session-worker[1149]: pam_sm_authenticate: Called
Jan  6 20:29:48 alladnsane-desktop gdm-session-worker[1149]: pam_sm_authenticate: username = [jay]
Jan  6 20:29:48 alladnsane-desktop gdm-session-worker[1642]: Passphrase file wrapped
Jan  6 20:29:49 alladnsane-desktop kernel: [  423.758469] padlock: VIA PadLock not detected.
Jan  6 20:29:52 alladnsane-desktop rtkit-daemon[1757]: Sucessfully called chroot.
Jan  6 20:29:52 alladnsane-desktop rtkit-daemon[1757]: Sucessfully dropped privileges.
Jan  6 20:29:52 alladnsane-desktop rtkit-daemon[1757]: Sucessfully limited resources.
Jan  6 20:29:52 alladnsane-desktop rtkit-daemon[1757]: Running.

#### 8:34 logout
Jan  6 20:35:01 alladnsane-desktop kernel: [  735.449263] __ratelimit: 21 callbacks suppressed
Jan  6 20:35:01 alladnsane-desktop kernel: [  735.449268] python[1763]: segfault at 0 ip (null) sp bfa9420c error 4 in libcrypto.so.0.9.8[110000+138000]
Jan  6 20:35:02 alladnsane-desktop acpid: client connected from 2269[0:0]
Jan  6 20:35:02 alladnsane-desktop acpid: 1 client rule loaded
Jan  6 20:35:03 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[/COLOR][2304]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jan  6 20:35:03 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[/COLOR][2304]: WARNING: Unable to lookup user name alladnsa: Success
Jan  6 20:35:21 alladnsane-desktop [COLOR="Red"]pulseaudio[1755]: core-util.c: Failed to create secure directory: Permission denied[/COLOR]

#### 8:37 successful login as jay again
Jan  6 20:37:21 alladnsane-desktop gdm-session-worker[2305]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 20:37:33 alladnsane-desktop gdm-session-worker[2317]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 20:37:43 alladnsane-desktop gdm-session-worker[2317]: pam_sm_authenticate: Called
Jan  6 20:37:43 alladnsane-desktop gdm-session-worker[2317]: pam_sm_authenticate: username = [jay]
Jan  6 20:37:43 alladnsane-desktop gdm-session-worker[2321]: Passphrase file wrapped
Jan  6 20:37:45 alladnsane-desktop rtkit-daemon[1757]: Sucessfully made thread 2412 of process 2412 (n/a) owned by '1002' high priority at nice level -11.
Jan  6 20:37:45 alladnsane-desktop rtkit-daemon[1757]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 20:37:45 alladnsane-desktop [COLOR="Red"]pulseaudio[2412]: pid.c: Stale PID file, overwriting.[/COLOR]

#### 8:49 logout
Jan  6 20:39:41 alladnsane-desktop kernel: [ 1015.764402] python[2415]: segfault at 0 ip (null) sp bfb6ff9c error 4 in libz.so.1.2.3.3[110000+13000]
Jan  6 20:39:42 alladnsane-desktop acpid: client 2269[0:0] has disconnected
Jan  6 20:39:42 alladnsane-desktop acpid: client connected from 2748[0:0]
Jan  6 20:39:42 alladnsane-desktop acpid: 1 client rule loaded
Jan  6 20:39:43 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[2783]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow[/COLOR]
Jan  6 20:39:43 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[2783]: WARNING: Unable to lookup user name alladnsa: Success[/COLOR]
Jan  6 20:40:02 alladnsane-desktop [COLOR="Red"]pulseaudio[2412]: core-util.c: Failed to create secure directory: Permission denied[/COLOR]

####8:40-8:42 other user in and out
##showed same thing as above

#### 8:46 fail to login as alladnsane
Jan  6 20:46:19 alladnsane-desktop gdm-session-worker[3045]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 20:46:25 alladnsane-desktop gdm-session-worker[3045]: pam_sm_authenticate: Called
Jan  6 20:46:25 alladnsane-desktop gdm-session-worker[3045]: pam_sm_authenticate: username = [alladnsane]
Jan  6 20:46:25 alladnsane-desktop gdm-session-worker[3054]: Passphrase file wrapped
Jan  6 20:46:27 alladnsane-desktop acpid: client 3009[0:0] has disconnected
Jan  6 20:46:27 alladnsane-desktop acpid: client connected from 3127[0:0]
Jan  6 20:46:27 alladnsane-desktop acpid: 1 client rule loaded
Jan  6 20:46:28 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[3162]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow[/COLOR]
Jan  6 20:46:29 alladnsane-desktop [COLOR="Red"]gdm-simple-greeter[3162]: WARNING: Unable to lookup user name alladnsa: Success[/COLOR]
```
I have attached the completes syslog, as well as contents of old-autostart just in case.  

Also, found this in /var/log/gdm/:0-greeter.log after a fresh boot and attempt to login as alladnsane;```
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/1015829a5ba0e00908132590937294575700000017350005.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/1015829a5ba0e00908132590937294575700000017350005.ms': No such file or directory
** (process:1746): DEBUG: Greeter session pid=1746 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-ifBuft/database

(gnome-power-manager:1745): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9cdde20'
gdm-simple-greeter[1746]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x100003f (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x100003f (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
gdm-simple-greeter[1746]: WARNING: Unable to lookup user name alladnsa: Success
```

Seemed kinda interesting.

Sorry again, for taking so long to get back with this, as well as how long the message is. :P

---

### Post by robsoles on 2012-01-07
If the the saved-session files are not setting off the problem then we may as well move them back, a couple in particular seem a better idea to be starting for a healthy session. I will encourage you to move two entries out of the way, being Skype (xxx046) and the HP Systray (xxx044) before moving the rest back to their usual place.```
mv ~/Documents/old-autostart/*21590046.desktop ~/Documents
mv ~/Documents/old-autostart/*21590044.desktop ~/Documents
mv ~/Documents/old-autostart/* ~/.config/gnome-session/saved-session
```Just my own preference about the HP thing but Skype is supposedly uninstalled due to being one of the suspects here.


Well, that brings us back to the per user configuration files then and trying to search them using the terms we can see isn't going to get us an easy hint at the culprit(s) by looks of things.

That gtkwidget error occuring on logout is a bit of a confirmation for me that the element routing alladnsane straight through to logout isn't reporting it anywhere we are looking (/var/log/) so far.

It makes me conclude that the gtkwidget error itself is irrelevant and alladnsane is simply being logged out before ever (apparently) really being logged in to the GUI.

How does bundling up all of the xorg/X11/gnome related configuration files (anything alsa or pulse if present (not '~/.pulse' please) as well) which are in alladnsane's ~/ folders (and subfolders :roll:) and sending them to me sound to you?

Mmmh, sounds like a (potential) nightmare of reading for me if you do that; Maybe you can have a hunt around through those config files and see if you can find anything remotely (prefer very, actually) suspicious for us to pick through?

---

### Post by alladnsane on 2012-01-07
Ok, I moved the files back from old-autostart (minus Skype and HP).

Looked as best I could and didn't find anything I thought wsa important anywhere in alladnsane's home folder (but not really sure what I am looking for so might possibly have missed something). And yes a nightmare of reading ;) 

I did have a discovery and got excited about it - I logged in to recovery console, resume normal boot, logged in console as alladnsane.
I then typed startx and got the following error;```
xauth: error in locking authority file /home/alladnsane/.Xauthority.

waiting for X server to begin accepting connections.
..
No Protocol specified
..
```and that just kept repeating and scrolling down screen.

Checked  the ~/.Xauthority file and the permissions were -rw------ root:root. In account jay it was owned by user (googled and found that is proper!). I used ```
sudo chown alladnsane:alladnsane .Xauthority
```.  Unfortunately it didn't help. It got rid of that message at recovery console startx to be replaced by one about xkeyboard or something (said not fatal to xserver) followed by "ddxSigGiveUp".

About ready to bull through it.  Was thinking, could I make a new sudo user, and begin copying folders one at a time over from alladnsane until boot failed there?? I would then have a stable sudo user and still able to troubleshoot the problem as I went.  Might isolate the trouble area or eliminate  home folder altogether. Would that work??


EDIT:
Happy First Saturday of 2012  :)

---

### Post by robsoles on 2012-01-07
Thanks very much re: Saturday (but it's Sunday! :p)

Occurs to me: Have you checked ownership of the files in alladnsane's home folders?

Would you try logging into tty1 as alladnsane and issuing the following command for your home folder (should be a prompt ending "~$")```
ls -Ral | grep root
```Here is the response on a VM system I initialised yesterday (with 10.04, all my other instances of Ubuntu are either 11.x or text only at this point) and have done some testing in regarding this problem:```
rob@rob-vmtop:~$ ls -Ral | grep root
drwxr-xr-x  4 root root 4096 2012-01-08 15:28 ..
rob@rob-vmtop:~$
```So, if much shows up for the command for you then I might have finally dug up a reasonable culprit at last.

(Soz if the first thing you did (and then second or third thing mentioned in thread :roll:) was checking the ownership of your config/home_folder files!)



On the other hand; Would you like the terminal sequence for spawning a new user and making them a sudo-er or are you pretty right with that?

---

### Post by alladnsane on 2012-01-08
> **robsoles said:**
> 
Occurs to me: Have you checked ownership of the files in alladnsane's home folders?
```
# sudo ls -Ral | grep root > /media/flashlogs/query-grep.txt

drwxr-xr-x   9 root       root         4096 2011-01-15 15:15 ..
drwxr-xr-x   2 root       root         4096 2011-01-11 23:30 .ure
-rwxr-xr-x 1 alladnsane alladnsane   94 2011-01-11 22:13 Browse as root
-rwxr-xr-x 1 alladnsane alladnsane  271 2011-01-11 22:13 Open with your favorite text editor (as root)
-rwx------  1 alladnsane alladnsane   465000 2009-09-16 17:56 bitdefender_antirootkit-beta2.exe
drwx------  2 alladnsane alladnsane    12288 2011-01-14 20:56 rootrepealinstr.showthread.php_files
-rwx------  1 alladnsane alladnsane    59927 2009-09-21 23:15 rootrepealinstr.showthread.php.htm
./Documents/desktop old/flash drive/pc cleanup/rootrepealinstr.showthread.php_files:
-rwxr-xr-x  1 root       root         34198 2011-09-24 18:32 hpmudext.soT
-rwxr-xr-x  1 root       root        342096 2011-09-24 18:32 libsane-hpaio.so.1.0.0T
-rw-------  1 alladnsane alladnsane 10576 2011-11-24 14:55 root
-rw-r--r--  1 alladnsane alladnsane 32768 2011-11-24 14:55 root-81c021fe.log
-rw-r--r-- 1 alladnsane alladnsane  176 2011-12-30 11:38 root_node_id
-rw-r--r-- 1 alladnsane alladnsane  176 2011-12-30 11:23 root_node_id.old
drwxr-xr-x   2 root       root        4096 2011-01-11 23:30 .
-rw-r--r--   1 root       root        1469 2011-01-11 23:30 javasettings_Linux_x86.xml
```I am attaching the relevant files.

Before I start with new user I think for shits and giggles I want to to try purging gdm and reinstalling. ```
# sudo apt-get remove gdm
# sudo apt-get install gdm
```  Is there anything else I need to do to make the entire login process and configs be fresh and new?? 
Also I read a couple things which said that completely reinstalling gnome might fix whatever is broken or installing kde can give gui access to alladnsane?!?

EDIT: or should I try the new sudo user thing first??```
# sudo useradd username    # Replace "username" with the username you want to create.

# sudo passwd username   #  assign a password for this new user

# sudo mkdir /home/username   #Create now a home directory for this new user

# sudo chown username /home/username   # change the owner of /home/username to this new user

# sudo chgrp username /home/username   # grant access to this new user to /home/username

# sudo adduser username admin   # grant this user root (sudo) privileges

-- borrowed and edited from [[COLOR="Blue"]_UpUbuntu_[/COLOR]]("http://www.upubuntu.com/2011/07/how-to-create-new-user-account-from.html")
```  Anything else needed??

---

### Post by robsoles on 2012-01-08
I'll have to review your attachment when I knock off from work.


Reinstall gdm - "anything else you can do?"
AFAICT reinstalling the majority of packages doesn't kill per user configs and is likely to leave alladnsane unable to login - alternatively just leaving gdm and going and deleting the obvious config files for (anything to with) gnome/gdm in alladnsane's home folder would be more likely to yield the effect desired by purging and reinstalling gdm (over alladnsane's login at least).

Doing that (killing alladnsane's gnome related config files) will either make it capable of giving alladnsane a working gnome desktop or it will reveal that gnome isn't the actual problem.


Installing KDE?
Can't see why (aside little things, less likely) KDE wouldn't just ignore the gnome configs and get alladnsane all the way to a usable desktop (provided gnome config is the problem) - of course just installing it (without uninstalling gnome) won't be enough; alladnsane will need to select it as the environment to login to at GUI login prompt.


New sudo-ing user:
Needn't take that many commands, last I checked the adduser command will make a home directory (and new group for new user) when invoked fairly plainly:```
sudo adduser mynewusername
```created a new group, new home folder and prompted for a new password for the new user. Granting them sudo privilege was just your bottom line so the entire sequence of commands I would expect to have to enter for that task is two:```
sudo adduser meagain
sudo adduser meagain admin
```(Where the first command will inform me of the new group and new home folder and then prompt me (twice) for a new password and the second command will just return).


I will post again unprompted if I see anything worth pursuing in your attachment but taking the assumption you pulled out and listed everything that returned for 'grep root' I don't expect a critter to chown to turn up.

---

### Post by robsoles on 2012-01-09
OK, I see attachment was just contents of files returned for the command "ls -Ral | grep root" and they are not, AFAICT (As Far As I Can Tell), causing (nor even part of) the problem.


There are other ways of attaching certain system items to users, with specific settings, that don't occur in ~/.* but I am not up on those items (just know it can be done and is done from time to time) and if it is one of those items it will screw us that much longer to find it if I remain the best source of ideas to work from against this problem.

A quick(~ish) test against that is to identify and **move** all configuration files from alladnsane's home folders to an unusable (simply to have other filename, in same location, is usually enough) place - no shortcut to doing this (AFAICT, without threatening personal data) and the reward/benefit against the effort may actually be meaningless; Ie., alladnsane makes it to a usable desktop but it is "factory reset" and we've got no **extra** clue how we can have 'eye' work with Skype under 10.04 without making the problem...


Soz, nothing worth pursuing in the attachment but I posted anyway :roll:

---

### Post by robsoles on 2012-01-09
alright: Would you please go through alladnsane's home folder and collect every last file you could concievably consider being part of the per-user configurations for gnome, alsa and pulse.


I expect this sequence can make it easier for you but I haven't tried a couple of specifics about the advice I am about to dish out so please inform where it goes completely opposite to my specs here:

Please log into TTY/tty1 as 'alladnsane' and then switch back to GUI login and log in as 'jay'; Operating as 'jay' open a terminal "Accessories->Terminal", type in```
gksudo nautilus
```wait for the prompt, look at the prompt and should see drop down to select SUDO user, select alladnsane and then type his password, browse to alladnsane's home folders - if you can access files in alladnsane's home folders this way it will be a lot more convenient, than by terminal alone, to collect appropriate files to zip up to send to me.

(Note: Personal reasons I hate tar, if I can encourage you to grab the zip binaries (software centre, or just 'sudo apt-get zip' (pretty sure) and use that format for compressing, if you've intention **I** open it, I won't be as dubious about unpacking them at work!!! - gz is fine, tar (tarball) is something my mother would prefer I didn't share my thoughts on (ie., if you ain't got nuthin nice to say....))


The reason I am asking for these files is because you might look at some obfuscated thing within and decide perhaps it belongs where if I can't unobfuscate it and determine its worth and value to making alladnsane have a usable desktop then I will ask it be moved out of the way for another shot at full GUI login for alladnsane.



Edited in: If 'jay' cannot select a different user to 'gksudo', using the graphical prompt that opens, then consider adding 'jay' to the 'admin' group at which point you can let me know how miserably attempts are failing to get a nautilus (file-browser) window open on alladnsane's home folders using 'jay' and I should (with a little testing of my own) have s sequence for terminal that will open that nautilus bugger on alladnsane's home folders under 'jay's GUI login for you :)
(Either that or my apology that three different pathways, I can think of right now, that should work all fail.)

---

### Post by alladnsane on 2012-01-09
WOOHOO. I finally have some good news (sort of) I am sending this from my 'broken' account!!!
> **robsoles said:**
> 
A quick(~ish) test against that is to identify and **move** all configuration files from alladnsane's home folders to an unusable (simply to have other filename, in same location, is usually enough) place - no shortcut to doing this (AFAICT, without threatening personal data) and the reward/benefit against the effort may actually be meaningless; Ie., alladnsane makes it to a usable desktop but it is "factory reset" and we've got no **extra** clue how we can have 'eye' work with Skype under 10.04 without making the problem...
There is kinda a shortcut...I moved EVERYTHING in alladnsanes home folder into ~/test-brokenness/ , rebooted and voila I can log in to factory reset alladnsane. And I don't care about getting the EYE working with skype anymore...just bought a Logitech webcam instead..hopefully not as many headaches!
> consider adding 'jay' to the 'admin' group at which point you can let me know how miserably attempts are failing to get a nautilus (file-browser) window open on alladnsane's home folders using 'jay'
I can't believe I never did this before;
```
sudo adduser jay admin
```
Having graphical access for someone who is comfortable, but not super used to or fast at console (although getting better this last week lol), is a godsend!!

> Personal reasons I hate tar, if I can encourage you to grab the zip I will use zip from now on ;)

> Would you please go through alladnsane's home folder and collect every last file you could concievably consider being part of the per-user configurations for gnome, alsa and pulse.
I will, but not tonight. My new guitar and ps3 Rocksmiths is BEGGING me to pick it up. Have barely played it since xmas bc of this stupid computer!! Also I am going to begin moving folders back into alladnsane's /home/alladnsane/ from /home/alladnsane/test-brokenness

I also have 2 logs. ~/.xsession-errors both before and after being able to login. Makes me think ```
/home/alladnsane/.gnupg/
``` might be the culprit but haven't tested yet. I will begin tomorrow morning (9pm here now in Ontario, Canada) collecting config files and testing adding folders back to alladnsane 1 at a time.

---

### Post by robsoles on 2012-01-10
> **alladnsane said:**
> .... I will begin tomorrow morning (9pm here now in Ontario, Canada) collecting config files and testing adding folders back to alladnsane 1 at a time.

Excellent work Pal!!! But don't worry about bundling files up for me to have a squiz at because the methodology you describe means that you will know which file(s) bork your login, when they bork it again it will be the last file(s) you put back and that identifies them as the files that really need to be reviewed.

Due what I think lives in (and is done in) ~/.gnupg it is pretty weird (to me at least) that it seems to be where the trail breaks in xsession errors - basic upshot, I would very much appreciate a squiz at the contents of the gpg-agent-info-alladnsane-desktop file indicated by that log.


Repeat: Please disregard previous request/advice to bundle up all possibly relevant config files, just show me the ones that re-break your login when you put them back :)

(Well done on spotting shortcut btw - dunno why it didn't occur to me that everything could be moved together (config and personal files) safely enough.)

---

### Post by alladnsane on 2012-01-10
> **robsoles said:**
> Excellent work Pal!!! But don't worry about bundling files up for me to have a squiz at because the methodology you describe means that you will know which file(s) bork your login, when they bork it again it will be the last file(s) you put back and that identifies them as the files that really need to be reviewed.
Well looks like all is good. After a bit of finagling got everything copied back to /home/alladnsane. Nothing killed it again which is really wierd unless I missed something.  
The only things I can think of are :
  - I missed something when copying back to home
  - ~/.pulse/ but copied the old one over (which was empty b/c of #sudo rm -R ~/.pulse). 
  - libsane-hpaio.so.1.0.0T and hpmudext.soT were chowned from root:root to user:user (not a likely culprit)
  - made blank /etc/gdm/custom.conf 
  - my possible incompetence at following directions earlier in the thread and later fumbling ineptitude :)
I am about to start changing the above back to their original states (other than the .pulse and thing b/c never made a copy of the original)

@all ALWAYS #cp /path/to/filename /path/to/filename.saved-myself-a-lot-of-grief-by-having-a-copy-of-original  BEFORE you #rm /path/to/filename

> I would very much appreciate a squiz at the contents of the gpg-agent-info-alladnsane-desktop file indicated by that log.
I have attached this. I am now getting a whole bunch of new errors in ~/.xessions-errors file.  Maybe I'll let you off the hook and start a new thread although I attached it anyway ;)

> Repeat: Please disregard previous request/advice to bundle up all possibly relevant config files, just show me the ones that re-break your login when you put them back :) I figured as much

> (Well done on spotting shortcut btw - dunno why it didn't occur to me that everything could be moved together (config and personal files) safely enough.)Thank-you, but I don't know if safely is accurate. Yes I got it to work and everything seems ok (fingers crossed) but using #gksudo nautilus to copy other users home folder turned everything to owned by root. I fixed this by #sudo chown -R user:user ~/test-brokenness, and for some reason everything copied into the new folder but several files wouldn't copy back out to home folder with "cannot copy special file" error. These I had to move directly instead of copying back;```
~/.config/gxine/socket
~/.config/xpad/server
~/.MultiGet
~/.gvfs  ##this one was busy so had to move and chown from other user
```


Well I have reinstalled Skype and timidity via synaptic, and added the saved sessions for skype and hp-systray back into ~/gnome-sessions/saved-sesions. I also renamed the folder ~/.recently-used.xbel bc ~/.xsession-errors was complaining about not being able to write to it because it was a directory. 
All seems to be working ok with no clue whatsoever as to what killed it in the first place

Thank-you very much for all your time and effort (and patience for my learning curve in console ;) )  Would never have gotten here without your help. Unless you think otherwise I am going to mark this thread as solved. Solved in a very ugly way but nonetheless working.  Hopefully when I attempt to plug my new logitech webcam in it doesn't break again ;)
EDIT:Logitech c270 webcam works great out of the box for both audio and video. Wish I had used it in first place ;)

---

### Post by robsoles on 2012-01-10
Oh, yeah, that rooted nautilus idea was just to collect files to give me a squiz - if I had realised you used that to move alladnsane's folders I would have been able to let you know that some of the config files may not go back too easily etc etc.

When I used the words "safely enough" before I was thinking more of your personal data rather than config files (config & such come from installers and the like - personal files come from *you*).

Due encryption alladnsane must login for root to (have a chance) be able to see his files but to manipulate alladnsane's files (specifically config files) it would be better to boot from a LiveCD but the process for mounting a user's encrypted home folders is uglier again so the risk that certain files would be in use (by alladnsane) as you try to put them back is high, especially if logged into GUI as alladnsane as more of the config files are in use when that is so.

The 'problem' file probably got 'mashed' out of contention (as a problem) by the system using a copy of it (which was working) while you move/copied it back - system could have written the good copy (which it made as you logged in) back over the bad copy in reaction to some event, such as you logging out and back in again.

~/.gvfs is special to the point of (in a way) not really existing.



I do not think otherwise, it isn't the best way a thread/problem I got involved in got solved but (as far as is sensible to invest time in, yours and mine) the title of this thread has been satisfied so...

---

