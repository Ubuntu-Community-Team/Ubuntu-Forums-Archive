---
title: "Problem with .ICEauthority"
date: 2011-09-12
forum: General Help
---

### Post by Nemo103 on 2011-09-12
After logging in, an error message appears:
```
Could not update ICEauthority file /home/alistair/.ICEauthority
```
then another ```
There us a problem with the configuration server: (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 226)
```
then, after a pause, ```
Nautilus could not create the following required folders: /home/alistair/Desktop, /home/alistair/.nautilus.
``` and ```
GConf error: No database available to save your configuration: Unable to store a value at key '/apps/nautilus/preferences/clutter_test', as the configuration server has no writable databases. [...]
```

I've tried most of the advice [here]("http://ubuntuforums.org/showthread.php?t=1423233"), including creating a new user, who also had the same problem on logging in. 
When I run *ls -a* in a terminal in the GUI, it shows Access-Your_private-Data.desktop, README.txt, .cache, .ecryptfs, and .Private.

Please help!

---

### Post by ubudog on 2011-09-12
Did you recently change your password as root?

To log in and fix this:
Restart your computer, but DON'T log in.  At the log in screen, press CTL>ALT>F1.  You will be presented with a console.  Type:

```
ecryptfs-mount-private
``` <enter key>

And enter your previous password.  Then press CTL>ALT>F7 or CTL>ALT>F8 if F7 doesn't work.  Now, log in.

Once logged in, open a terminal.  Type:
```
passwd
``` 

Set up a new password. 

Reboot.  You should be able to log in like normal. 

Hope this helps!  If not, let us know.

---

### Post by Nemo103 on 2011-09-12
Hi,
I hadn't changed it.
I tried doing what you said, but it wasn't having me put ecryptfs-mount-private as my login in tty1. I logged in as normal and changed my password as advised, but the problem persisted when rebooted.
Thanks

---

### Post by Nemo103 on 2011-09-12
Update:
Having logged on in tty1 as well, I can open firefox, evince and gedit from the terminal, but not nautilus. Also, my home folder now contains all the things it should (I think). Unity still doesn't work (when I run unity --replace, it gets stuck halfway through).
Anyone?

---

### Post by ubudog on 2011-09-12
> **Nemo103 said:**
> Update:
Having logged on in tty1 as well, I can open firefox, evince and gedit from the terminal, but not nautilus. Also, my home folder now contains all the things it should (I think). Unity still doesn't work (when I run unity --replace, it gets stuck halfway through).
Anyone?

So, when you run the command ls you can see your stuff?

And does unity --replace give an error?

---

### Post by lkjoel on 2011-09-12
[FONT=Verdana]To fix the .ICEauthority problem:
```
sudo chmod -R 0777 ~/.ICEauthority
```[/FONT][FONT=Verdana]
It should fix the problem. If it doesn't fix it, try this:
```
sudo mv ~/.ICEauthority ~/.ICEauthority.BAK

```[/FONT]

---

### Post by Nemo103 on 2011-09-12
ubudog,
Yeah, after I log in on tty1 I can see my files in home, and use some programs, but not before.
unity --replace does a lot of window loading and initalising, then just runs out of steam at "Setting Update "fullscreen_visual_bell"

lkjoel, 
the chmod didn't fix it. I did something along the lines of the renaming before, but I'll do it again and see.

Thanks guys

---

### Post by ubudog on 2011-09-12
Can you access the login screen?  Try selecting Ubuntu Classic and see if you can login now.

---

### Post by lkjoel on 2011-09-12
Try this:
```
sudo chmod 0600 /home/alistair/.ICEauthority
sudo chown alistair /home/alistair/.ICEauthority

```

---

### Post by Nemo103 on 2011-09-12
ubudog,
I can see the login screen but the option to use Classic isn't there...

lkjoel,
still no luck ):

---

### Post by lkjoel on 2011-09-12
OK. Could you try this?
```
sudo mv ~/.ICEauthority.BAK ~/.ICEauthority
sudo chmod 0600 /home/alistair/.ICEauthority
sudo chown alistair /home/alistair/.ICEauthority

```
And if it still doesn't work, could you give me the output of this Terminal command?
```
stat ~/.ICEauthority

```

---

### Post by Nemo103 on 2011-09-12
Nope.

Here it is:
alistair@Gizmo:~$ stat ~/.ICEauthority
  File: `/home/alistair/.ICEauthority'
  Size: 7548          Blocks: 32         IO Block: 4096   regular file
Device: 14h/20d    Inode: 4194344     Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/alistair)   Gid: ( 1000/alistair)
Access: 2011-09-12 18:47:37.315199996 +0100
Modify: 2011-09-12 18:47:34.920397996 +0100
Change: 2011-09-12 18:47:34.920397996 +0100

---

### Post by lkjoel on 2011-09-12
Try this:
```
sudo mv ~/.ICEauthority ~/.Noth.ingTo55Do3W.ithIC1Eau9th.ori8ty

```
Then reboot.
The system will be forced to re-generate ICEauthority.

---

### Post by ubudog on 2011-09-12
> **Nemo103 said:**
> ubudog,
I can see the login screen but the option to use Classic isn't there...

lkjoel,
still no luck ):

At the bottom of the screen, there should be a drop down menu with Ubuntu Classic in it.  Do you see where it says "Ubuntu"?

---

### Post by Nemo103 on 2011-09-12
Same error messages. In home there's the .Nothing... file and a new .ICEauthority:

-rw-------  1 alistair alistair   314 2011-09-12 19:07 .ICEauthority
...
-rw-------  1 alistair alistair  7548 2011-09-12 18:47 .Noth.ingTo55Do3W.ithIC1Eau9th.ori8ty

---

### Post by paccamura on 2011-09-12
Hi,
I get the same message:
Could not update ICEauthority file /home/mario/.ICEauthority

but I only had some problem with the sound volume controller (which I don't have anymore)

what is this ICEauthority? if my system works shall I just ignore it?

(meanwhile I tried some of the solution proposed in this discussion but without success)

thanks

---

### Post by ubudog on 2011-09-12
> **paccamura said:**
> Hi,
I get the same message:
Could not update ICEauthority file /home/mario/.ICEauthority

but I only had some problem with the sound volume controller (which I don't have anymore)

what is this ICEauthority? if my system works shall I just ignore it?

(meanwhile I tried some of the solution proposed in this discussion but without success)

thanks

Hi, what version of Ubuntu are you using?

---

### Post by Nemo103 on 2011-09-12
(I'm on 11.04 [but I did something before that brought up the GUI of an older one])

---

### Post by ubudog on 2011-09-12
> **Nemo103 said:**
> (I'm on 11.04 [but I did something before that brought up the GUI of an older one])

Did you go on Ubuntu Classic?  That has the old GUI.

---

### Post by Nemo103 on 2011-09-12
ubudog,
it was "sudo /etc/init.d/gdm restart" 
or "sudo /etc/init.d/gdm stop startx"
from within the noticeably broken GUI.

---

### Post by paccamura on 2011-09-12
> **ubudog said:**
> Hi, what version of Ubuntu are you using?

I'm on ubuntu 11.04 with unity 2D

---

### Post by Nemo103 on 2011-09-12
_mostly FIXED_

I just idly did ```
chmod a+rwx ICEauthority
``` and rebooted. Unity is back.
But [LIST]
[*]all the original personal changes to the GUI seem to have reverted to default
[*]there is still a message at the top of the terminal telling me how to use sudo
[*]the files in home are not coloured (and I'm not sure whether some things are missing...)
[*]still no option for Ubuntu Classic at login
[/LIST]
So essentially fixed, minus a few unimportant details.

---

### Post by ubudog on 2011-09-12
> **Nemo103 said:**
> _mostly FIXED_

I just idly did ```
chmod a+rwx ICEauthority
``` and rebooted. Unity is back.
But [LIST]
[*]all the original personal changes to the GUI seem to have reverted to default
[*]there is still a message at the top of the terminal telling me how to use sudo
[*]the files in home are not coloured (and I'm not sure whether some things are missing...)
[*]still no option for Ubuntu Classic at login
[/LIST]
So essentially fixed, minus a few unimportant details.

Great! 

1. That is probably due to unity --replace

2. Not sure what that is, but probably due to replacing .ICEauthority

3. Not sure what that could be... weird

4. Very strange, are you sure you just don't see it?  Can you upload a picture of your login screen?

---

### Post by Nemo103 on 2011-09-12
Here.
The only things to click on are the accessibility button and the power button.

---

### Post by ubudog on 2011-09-12
What about after you click on "Alistair"?

---

### Post by Nemo103 on 2011-09-12
Ahaa! If I click on newuser (not automatic login, while alistair is) the options appear.

---

### Post by ubudog on 2011-09-12
> **Nemo103 said:**
> Ahaa! If I click on newuser (not automatic login, while alistair is) the options appear.

Yep, so automatic login was the problem.

So, if you want it to start Gnome even with auto login enabled, login as Alistair, and open your "System Settings" control panel.  Click on the "System" button, and then on the "Login Screen" button.  Change it to "Ubuntu Classic".

---

### Post by Nemo103 on 2011-09-12
Thank you!

---

### Post by ubudog on 2011-09-12
Not a problem.  ;-)

---

### Post by Nemo103 on 2011-09-13
Update:

I noticed there was still something wrong when all the saved settings on chromium had gone. Having read that ecryptfs does something wrong when automatic login is set, I stopped automatic login. Then the original problem (no Unity) came back.

[Removing ecryptfs]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup") from terminal fixed it.

---

