---
title: "Odd login screen display, unable to login (10.04 LTS)"
date: 2010-05-05
forum: General Help
---

### Post by gcpitts on 2010-05-05
I recently upgraded to Ubuntu 10.04 LTS and at first, everything was just fine. This issue came about yesterday, as far as I know, while my screen was locked.

The login screen now displays only half of the original login screen (left side) and the other half (right side) is an odd view of a black background with a white box in the center (see [this mock up]("http://twitpic.com/1l4pqo/full")).

Another note of interest is that the right side pans as I move the mouse around the screen, as if the right-side view were a second view port to the login screen without displaying it properly.

I am not able to log in whatsoever. An incorrect password results in the standard error message. A correct password results in a temporary black screen, as if to load to the desktop, but then redisplays the login screen as if I hadn't logged in at all.

I'm not sure where to begin, as I cannot login to run any commands and the grub menu does not give options to start in safe mode--it just loads directly to the latest instance of Ubuntu.

---

### Post by rodh on 2010-05-05
Try using the Live CD

---

### Post by gcpitts on 2010-05-05
The live cd works fine, but I'm not sure how to correct the issues from there.

---

### Post by gcpitts on 2010-05-06
Still no resolution. I did manage to install ubuntu 10.04 again along side the corrupted version, so I may end up transferring old files and erasing the old install.

---

### Post by Eycks on 2010-05-14
I am having the same trouble with my 10.04 login screen. Does anyone know how the login screen works or can supply a link? I have tried startx from the rescue login but that just produces a background screen with nothing on it.  I also tried deleting the password from my login by changing my passwd file.

---

### Post by gcpitts on 2010-06-05
I reinstalled 10.04 again successfully and deleted the problem partition. What I did to "fix" it was set it to automatic login so that it goes directly to the graphic user interface.  However, my kids were playing around on the computer and creating a ton of miscellaneous files and folders by randomly clicking and typing, so I decided to set it to require a password at login and now the exact same issue has returned.  Fortunately the grub menu was installed properly this time, so I am able to get to the command line and login, then use startx to get to the GUI. This bypasses the login screen altogether.  Although, logging in this way each time is less than desirable, so if anyone has a solution, I'd really appreciate it.  To the previous poster, when I use startx, the GUI loads my background first, but eventually the rest of the interface loads in, too. Try waiting for a few minutes to see if that works. It's one option until this issue can be resolved.

---

### Post by lol768 on 2010-06-05
Just wondering, are you trying to login to GNOME or KDE?
Does fail-safe GNOME work at all and can you login by pressing Ctrl + Alt + F2?

---

### Post by mark_s_robinson on 2010-06-07
I've had a similar problem, only I also get the "onboard" keyboard displayed as well (this is on an old T43 IBM ThinkPad)

Although the mouse worked, I couldn't type in the password to log on - maybe there was a problem detecting the keyboard which is why the "onboard" keyboard is started. (*Although I was not actually able to use this "onboard" keyboard to log in either*).


After a bit of hackery and heavy hammering I managed to get the "normal" login window by:
```

mkdir -p /var/tmp/usr/share/gdm/autostart/LogInWindow # Just so I can move the files out of the way
cd /usr/share/gdm/autostart/LogInWindow
mv gnome-settings-daemon.desktop \
   onboard.desktop \
   gnome-mag.desktop \
   /var/tmp/usr/share/gdm/autostart/LogInWindow/

```Its not really a fix, my problem appears to be with```
 gnome-settings-daemon.desktop
```- but I don't know why.

All the above does is stop the gdm process from running some features. How problematic this might be in the future I'll probably find out shortly. :(


**NOTE**: This happened whilst my son was "working/playing" on his account - he and I have no idea if he did something - he's 5 and can't quite articulate what had happened :)



_Footnote_
As I was not able to use [FONT=Courier New]alt-f1/f2/f3[/FONT] etc - I had to use the Live CD and then edit the ```
/etc/X11/default-display-manager
``` to remove the ```
/usr/sbin/gdm
``` entry.

I was then able to get logon to my laptop using the console and manually started gdm (which showed the same symptom).

Not knowing how the login works, or anything, I used a bit of crude scripting to try and diagnose where I thought the problem might be.
I created a cronjob to kill the gdm process after a couple of minutes (given that I couldn't log on or use Alt-f2).
```
*/2 * * * * pkill gdm
```I also used pstree to see what processes got spawned .
```
/usr/sbin/gdm & sleep 5 && pstree -al `ps -ef | grep gdm | grep -v grep | awk '{print $2}' | head -1`
```([FONT=Courier New]pgrep[/FONT] didn't quite work, so I had to list all the "gdm" processes and hope the top one was the base one. I then let the cron job kill the process so I could see all the spawned processes in the console again. Previously, I had tried [FONT=Courier New]strace[/FONT], but that did not seem to show any of the sub-processes being kicked off).


I found myself "investigating" the gnome-session and the [FONT=Courier New]*.desktop[/FONT] files in [FONT=Courier New]/usr/share/gdm/autostart/LogInWindow[/FONT]
By deleting (or moving the file elsewhere) the *.desktop files in turn, I found that I could get rid of the "split" screen by removing  [FONT=Courier New]gnome-mag.desktop[/FONT], I could also could get rid of the [FONT=Courier New]onboard.desktop[/FONT] to stop the "onboard" keyboard and eventually found that [FONT=Courier New]gnome-settings-daemon.desktop[/FONT] was "stopping" me from typing in the password.

However, why this stopped me, I don't know - I only know that by removing it, I was able to log on again. (I removed [FONT=Courier New]onboard.desktop[/FONT] and [FONT=Courier New]gnome-mag.desktop[/FONT] because the screen was still magnified and the "onboard" was still displayed).



Anyone have any thoughts on what might have happened? I couldn't find any "saved" sessions that might have caused this and I had uninstalled/reinstalled gdm but that did not solve the problem.

---

### Post by Sianegad on 2010-07-04
Mark S Robinson

Well thank you, that worked for me as well.  My two and a half year old son managed to do the same trick on his computer.  It's pretty safe once he is logged-in.  I kept the log-in menu for easy access to the admin user, but i guess i better change to auto log-in.   No idea how he managed  to start those two services, but two kids breaking it the same is not coincidence. something is weak...

---

### Post by spschiebel on 2010-09-08
I'm having the exact same problem.  My 4 year old daughter was using her account, which should have been fairly secure.  When my wfie sat down to log her off and log onto her own account she said there was an error message of some kind that kept popping up when she closed it.  When she got to the login screen it was as described previously, the right side was some sort of magnified version that scrolled when the mouse was moved.  The "onboard" keyboard was displayed at the top of the left hand side and she couldn't get anything to type into the password field.  After some investigation of my own I have observed the following.
 
1) I can login to both my daughters accounts as they are set up without passwords, so just a mouse click on the gdm screen will do it.
2) I cannot login to either my wife's or my account because they require keyboard inputs and keyboard is not responding.  "Onboard" keyboard also doesn't work for inputting passwords.
3) I noticed that a "Welcome to Orca" message is played when the GDM screen appears.
4) I tried disabling and removing Orca and Onboard, now the audio message "Welcome to Orca" does not play and the "Onboard" keyboard is no longer displayed, but the right side of the screen remains magnified and the keyboard doesn't work.
 
I haven't tried what was mentioned by mark yet as I don't fully understand the consequences of these actions.
 
I find this a very peculiar bug/problem resulting from four seperate instances of children doing something that results in the same behaviour.  I tried thinking about what a child could do, but came up with nothing.
 
Anyone had any luck finding out what is going on here and how to reverse it?

---

### Post by dcstar on 2010-09-09
> **spschiebel said:**
> 
..........
3) I noticed that a "Welcome to Orca" message is played when the GDM screen appears.
4) I tried disabling and removing Orca and Onboard, now the audio message "Welcome to Orca" does not play and the "Onboard" keyboard is no longer displayed, but the right side of the screen remains magnified and the keyboard doesn't work.
 
I haven't tried what was mentioned by mark yet as I don't fully understand the consequences of these actions.
 
I find this a very peculiar bug/problem resulting from four seperate instances of children doing something that results in the same behaviour.  I tried thinking about what a child could do, but came up with nothing.
 
Anyone had any luck finding out what is going on here and how to reverse it?

[https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)
[http://ubuntuforums.org/showthread.php?t=786327](http://ubuntuforums.org/showthread.php?t=786327)

---

### Post by Atallcostsky on 2010-12-07
> **gcpitts said:**
> I recently upgraded to Ubuntu 10.04 LTS and at first, everything was just fine. This issue came about yesterday, as far as I know, while my screen was locked.

The login screen now displays only half of the original login screen (left side) and the other half (right side) is an odd view of a black background with a white box in the center (see [this mock up]("http://twitpic.com/1l4pqo/full")).

Another note of interest is that the right side pans as I move the mouse around the screen, as if the right-side view were a second view port to the login screen without displaying it properly.

I am not able to log in whatsoever. An incorrect password results in the standard error message. A correct password results in a temporary black screen, as if to load to the desktop, but then redisplays the login screen as if I hadn't logged in at all.

I'm not sure where to begin, as I cannot login to run any commands and the grub menu does not give options to start in safe mode--it just loads directly to the latest instance of Ubuntu.

After researching the problem a little bit I think I might have found the solution here (not a long-term solution for the distribution, but a way to fix the problem).

The bug report [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/594145](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/594145) seems to describe this problem. In comment #3, Svein Tore Seljebotn writes, "...I just logged into another console (Alt+Ctrl F1) while in GDM. There I wrote "sudo killall magnifier", and after that I could access the settings again and turn it off."

I tried this and it worked well for me. So, the instructions:

[LIST]
[*]At the login screen, switch to a terminal (Ctrl+Alt+F1).
[*]Log in to your normal user account. For example, if your user name is 'toby' with the password 'iamtoby', when the terminal pops up, enter 'toby', then 'iamtoby' when it asks for your password.
[*]Type ```
sudo killall magnifier
```.
[*]Switch back to your normal login window (for me this was Ctrl+Alt+F7, but I'm not positive on if it's F7 or a different function key for everyone else.
[*]*Click the Accessibility icon and un-check the magnifier option.
[/LIST]
This worked for me after a restart, running Ubuntu 10.10. Hope it helps!

---

### Post by shatadru on 2011-01-12
> **Atallcostsky said:**
> After researching the problem a little bit I think I might have found the solution here (not a long-term solution for the distribution, but a way to fix the problem).

The bug report [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/594145](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/594145) seems to describe this problem. In comment #3, Svein Tore Seljebotn writes, "...I just logged into another console (Alt+Ctrl F1) while in GDM. There I wrote "sudo killall magnifier", and after that I could access the settings again and turn it off."

I tried this and it worked well for me. So, the instructions:

[LIST]
[*]At the login screen, switch to a terminal (Ctrl+Alt+F1).
[*]Log in to your normal user account. For example, if your user name is 'toby' with the password 'iamtoby', when the terminal pops up, enter 'toby', then 'iamtoby' when it asks for your password.
[*]Type ```
sudo killall magnifier
```.
[*]Switch back to your normal login window (for me this was Ctrl+Alt+F7, but I'm not positive on if it's F7 or a different function key for everyone else.
[*]*Click the Accessibility icon and un-check the magnifier option.
[/LIST]
This worked for me after a restart, running Ubuntu 10.10. Hope it helps!

Thanks a ton! solution worked for me!!!

---

### Post by dislocated on 2011-03-14
Came back to the computer after my 4 yr old son had been randomly clicking on the log-in screen. Had the same problem posted above, and the solution here fixed it.

Thank you!

---

### Post by sreesha.c.n on 2011-04-24
simple solution:

enter as root user in terminal..

then..

cd /usr/bin
rm -r magnifier

---

### Post by Atallcostsky on 2011-05-28
> **sreesha.c.n said:**
> simple solution:

enter as root user in terminal..

then..

cd /usr/bin
rm -r magnifier

Are you sure it would be good to go about solving this problem in this way? It looks like running rm on magnifier would remove the program itself from the user's system, rather than just stop it.

---

