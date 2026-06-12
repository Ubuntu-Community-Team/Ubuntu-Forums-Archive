---
title: "Can't log in"
date: 2011-10-22
forum: General Help
---

### Post by rasmus91 on 2011-10-22
Okay, so the UI on my Roomie's  Ubuntu 11.10 computer is acting up.

when he gets to the log in screen he enters his password, and hit login. Then it briefly shows a black screen where it says something like:

```
Stopping v run level compatibility
```

then it goes back to the log in screen.

I tried pressing ctrl+alt+f1 to go to the prompt, which it did right away. i though this might be a problem that there was made an update for, so i entered:

```
sudo apt-get update
```

here it failed loading ALL the archieves... I'm kinda stuck, any help would be much appreciated...

Started the computer in recovery, updated. It didn't help.

---

### Post by mikejonesey on 2011-10-22
hmm check the logs Ctrl+Alt+F1
login
sudo su
cd /var/log
tail -f syslog | less
Ctrl+Alt+F7
try login
Ctrl+Alt+F1
See what meesages  you got...

or just look at recent history with
tail -500 syslog | less
(Ctrl+F and Ctrl+B)

let us know what error messages you're facing...

---

### Post by rasmus91 on 2011-10-22
okay. Did the first thing you said this is what i get:

```

acpid: client 1515[0:0] has disconnected
acpid: client connected from 1515[0:0]
acpid: 1 client rule loaded
gnome-session[1885]: GDK-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
acpid: client 1515[0:0] has disconnected
acpid: client connected from 1950[0:0]
acpid: 1 client rule loaded
kernel: [  299.949355] [Hardware Error]: Machine check events logged
```

okay. "acpid" sounds like some hardware stuff to me, like some graphics has problems loading or something, but thats really nothing but a guess. 

Hopefully you have an idea? :)

---

### Post by mikejonesey on 2011-10-22
ok;
acpid: client 1515[0:0] has disconnected
means you have exited tty7

acpid: client connected from 1515[0:0]
means you went back to tty7

acpid: 1 client rule loaded
ignore

gnome-session[1885]: GDK-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
this is the problem...

acpid: client 1515[0:0] has disconnected
you left tty7

hmmm....
Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

try:
```
echo "export DISPLAY=:0.0" >> ~/.bashrc
```
(important to use two greater than signs or you wipe your bashrc file...)

also cat n grep ur bashrc n profiles to check what is going on...

X server :0.#012

seems wierd to me...

---

### Post by rasmus91 on 2011-10-23
> also cat n grep ur bashrc n profiles to check what is going on...

okay, what do you mean by this?

hmm. the command didn't really seem to help :-/

---

### Post by mikejonesey on 2011-10-24
cat = echo file contents to stdout
grep = filter stdout
```
cat ~/.bashrc | grep "DISPLAY"
```

somewhere your display env var seems to be getting messed up...

---

### Post by rasmus91 on 2011-10-25
give me this

```
export DISPLAY=:0.0
```

---

### Post by mikejonesey on 2011-10-25
hmmm i dunno  prob easyest way is to reinstall some x modules...

in the mean time from tty1 do useradd bob and login as bob on tty7... this will tell you if it's something in the user acount config or somthing bigger too...

---

### Post by matt_symes on 2011-10-25
Hi

This may be the .Xauthority issue some poeple have been having.

From the command line after logging into a console.

```
ls -l ~/.Xauthority
```

Make sure you are the owner and the permissions are rw only for you.

You can also try

```
xhost +
```

Kind regards

---

### Post by rasmus91 on 2011-10-25
Hi guys.

We tried the "useradd" command... theres just a password problem... and how do we remove the user again?

```
ls -l ~/.Xauthority
```

gives:

```
-rw------- 1 memborg memborg 58 2011-10-25 15:51 /home/memborg/.Xauthority
```

and ```
xhost +
```
gives us:

```
Invalid MIT-MAGIC-COOKIE-1 keyxhost: unable to open display ":0.0"
```

we tried logging in as a guest user, but it does the same as his own user account, (short time of black screen and then it returns us to the lightdm login screen) it may change nothing, but i believe that all of this happened after he had opened the Compiz manager (he didn't change anything though...)

Thanks for the help, we appreciate it :)

---

### Post by matt_symes on 2011-10-25
Hi

> Invalid MIT-MAGIC-COOKIE-1 keyxhost: unable to open display ":0.0"

This seems to suggest it does not like your xauthority cookie.

Log into the console and type

```
echo $XAUTHORITY
```

Is the path returned the path to your ~/.Xauthority file ?

You can get the same info from

```
xauth info
```

Kind regards

---

### Post by rasmus91 on 2011-10-26
```
echo $XAUTHORITY
```

give

```
 
``` (thats right, nothing -.^)

and 
```
xauth info
```

gives

```

Authority file:  /home/memborg/.Xauthority
File new:        no
File locked:     no
Number of entries: 0
Changes honored:  yes
Changes made:    no
Current input:   (argv):1

```

---

### Post by matt_symes on 2011-10-26
Hi

Let's try a quick test. At the lightDM login screen drop to a console by pressing ALT + F1. Enter user name and password for memborg.

Type

```
export XAUTHORITY=/home/memborg/.Xauthority
```

Press ALT + F7 to get back to LightDM login screen. Try to login as user memborg.

Kind regards

---

### Post by rasmus91 on 2011-10-26
```
export XAUTHORITY=/home/memborg/.Xauthority
```

Did it, still unable to log in... what really puzzles me is that logging in works fine under recovery mode...

---

### Post by matt_symes on 2011-10-26
Hi

> **rasmus91 said:**
> what really puzzles me is that logging in works fine under recovery mode...
[FONT=monospace]
[/FONT]```
xhost +
```Your above comment and the above xhost+ command  would tend to suggest it's not an X cookie issue as xhost+ should have allowed anybody to connect to the x server (xhost+ is dangerous but would have been rectified later).

I'm kind of scratching my head as the error message returned suggested that it was an x cookie problem.

Have you taken a  look in the logs ? They might cast some light on your problem.

Kind regards

---

### Post by rasmus91 on 2011-10-26
What logs exactly?

---

### Post by matt_symes on 2011-10-26
Hi

The first log i would post would be the LightDM log.

It can be found in

```
/var/log/lightdm/lightdm.log
```

If you can post it soon i will have a look tonight.

I do not have enough time for an IM session today though.

Kind regards

---

### Post by rasmus91 on 2011-10-27
```
[+0.05s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.05s] DEBUG: Starting Light Display Manager 1.0.1, UID=0 PID=1127
[+0.05s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.05s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.05s] DEBUG: Registered seat module xlocal
[+0.05s] DEBUG: Registered seat module xremote
[+0.05s] DEBUG: Adding default seat
[+0.05s] DEBUG: Starting seat
[+0.05s] DEBUG: Starting new display for greeter
[+0.05s] DEBUG: Starting local X display
[+0.05s] DEBUG: X server :0 will replace Plymouth
[+0.07s] DEBUG: Using VT 7
[+0.07s] DEBUG: Activating VT 7
[+0.07s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.07s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.07s] DEBUG: Launching X Server
[+0.07s] DEBUG: Launching process 1177: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.07s] DEBUG: Waiting for ready signal from X server :0
[+0.07s] DEBUG: Acquired bus name
[+0.07s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.59s] DEBUG: Got signal 10 from process 1177
[+0.59s] DEBUG: Got signal from X server :0
[+0.59s] DEBUG: Stopping Plymouth, X server is ready
[+0.61s] DEBUG: Connecting to XServer :0
[+0.61s] DEBUG: Starting greeter session
[+0.96s] DEBUG: pam_start("lightdm-autologin", "lightdm") -> (0x15e7800, 0)
[+0.96s] DEBUG: Starting session unity-greeter as user lightdm logging to /var/log/lightdm/x-0-greeter.log
[+0.96s] DEBUG: pam_authenticate(0x15e7800, 0) -> 0 (Success)
[+0.96s] DEBUG: pam_acct_mgmt(0x15e7800, 0) -> 0 (Success)
[+0.96s] DEBUG: Launching session
[+0.96s] DEBUG: pam_set_item(0x15e7800, 3, ":0") -> 0 (Success)
[+1.00s] DEBUG: pam_open_session(0x15e7800, 0) -> 0 (Success)
[+1.05s] DEBUG: Opened ConsoleKit session 52dceb39611c0b5b20bc24590000000b-1319696936.857391-187751974
[+1.07s] DEBUG: Dropping privileges to uid 113
[+1.07s] DEBUG: Adding session authority to /var/lib/lightdm/.Xauthority
[+1.27s] DEBUG: Restoring privileges
[+1.27s] DEBUG: Launching process 1388: /usr/lib/lightdm/lightdm-greeter-session 'unity-greeter'
[+1.27s] WARNING: Failed to open log file /var/log/lightdm/x-0-greeter.log: Permission denied
[+1.27s] DEBUG: pam_setcred(0x15e7800, PAM_ESTABLISH_CRED) -> 0 (Success)
[+1.27s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8 LANGUAGE=en_US:en'
[+1.38s] DEBUG: Read 8 bytes from greeter
[+1.39s] DEBUG: Read 9 bytes from greeter
[+1.39s] DEBUG: Greeter connected version=1.0.1
[+1.39s] DEBUG: Wrote 98 bytes to greeter
[+1.39s] DEBUG: Greeter connected, display is ready
[+1.39s] DEBUG: New display ready, switching to it
[+1.39s] DEBUG: Activating VT 7
[+1.92s] DEBUG: Read 8 bytes from greeter
[+1.92s] DEBUG: Read 15 bytes from greeter
[+1.92s] DEBUG: Greeter start authentication for memborg
[+1.92s] DEBUG: pam_start("lightdm", "memborg") -> (0x15f6470, 0)
[+1.92s] DEBUG: Prompt greeter with 1 message(s)
[+1.92s] DEBUG: Wrote 45 bytes to greeter
[+8.75s] DEBUG: Read 8 bytes from greeter
[+8.75s] DEBUG: Read 19 bytes from greeter
[+8.75s] DEBUG: Continue authentication
[+8.76s] DEBUG: pam_authenticate(0x15f6470, 0) -> 0 (Success)
[+8.76s] DEBUG: pam_acct_mgmt(0x15f6470, 0) -> 0 (Success)
[+8.76s] DEBUG: Authenticate result for user memborg: Success
[+8.76s] DEBUG: User memborg authorized
[+8.76s] DEBUG: Wrote 27 bytes to greeter
[+8.76s] DEBUG: Read 8 bytes from greeter
[+8.76s] DEBUG: Read 10 bytes from greeter
[+8.76s] DEBUG: Greeter requests session ubuntu
[+8.76s] DEBUG: Stopping greeter
[+8.76s] DEBUG: Dropping privileges to uid 113
[+8.76s] DEBUG: Removing session authority from /var/lib/lightdm/.Xauthority
[+8.81s] DEBUG: Restoring privileges
[+8.81s] DEBUG: Sending signal 15 to process 1388
[+8.81s] DEBUG: Process 1388 exited with return value 0
[+8.81s] DEBUG: pam_close_session(0x15e7800) -> 0 (Success)
[+8.81s] DEBUG: pam_setcred(0x15e7800, PAM_DELETE_CRED) -> 0 (Success)
[+8.81s] DEBUG: pam_end(0x15e7800) -> 0
[+8.81s] DEBUG: Ending ConsoleKit session 52dceb39611c0b5b20bc24590000000b-1319696936.857391-187751974
[+8.82s] DEBUG: Greeter quit
[+8.82s] DEBUG: Starting user session
[+8.82s] DEBUG: Dropping privileges to uid 1000
[+8.82s] DEBUG: Writing /home/memborg/.dmrc
[+8.92s] DEBUG: Restoring privileges
[+9.00s] DEBUG: Starting session ubuntu as user memborg logging to /home/memborg/.xsession-errors
[+9.00s] DEBUG: Launching session
[+9.00s] DEBUG: pam_set_item(0x15f6470, 3, ":0") -> 0 (Success)
[+9.00s] DEBUG: pam_open_session(0x15f6470, 0) -> 0 (Success)
[+9.01s] DEBUG: Opened ConsoleKit session 52dceb39611c0b5b20bc24590000000b-1319696944.814284-591265330
[+9.01s] DEBUG: Dropping privileges to uid 1000
[+9.01s] DEBUG: Adding session authority to /home/memborg/.Xauthority
[+9.09s] DEBUG: Restoring privileges
[+9.09s] DEBUG: Launching process 1606: /usr/sbin/lightdm-session 'gnome-session --session=ubuntu'
[+9.09s] DEBUG: pam_setcred(0x15f6470, PAM_ESTABLISH_CRED) -> 0 (Success)
[+9.09s] DEBUG: PAM returns environment 'GNOME_KEYRING_CONTROL=/tmp/keyring-9Fxkg5 GNOME_KEYRING_PID=1597 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8 LANGUAGE=en_US:en'
[+9.09s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
```

This is everything in the lightdm.log file...

It should be said that we logged in in recovery mode to see this...

---

### Post by MetallicM on 2011-10-27
Hi. I am the one my friend here has been trying to help.
The problem is that I can't log in, not in my own or guest user or other user. I had my labtop connected to an external screen using HDMI cable. I needed to work on a bigger screen. I don't know if that is where the problem is. It could also be after I entered the Compiz Manager. I just really wanted to learn to use linux and I still hope to get this to work.

---

### Post by mikejonesey on 2011-10-27
if you think the problem is compiz switch back to metacity...

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager gnome-wm
```

to make compiz default gain run:

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager compiz
```

also run;

```
compiz --replace &
```

to which to compiz on the fly....

if however it somthing in xorg, which is what i think... reinstalling packages will reset defaults...

try adding a new user and see if you can login to the gui with that user, if that is the case you know its a user specific option... in which case you can diff the xorg props...

otherwise reninstall a few xorg packs...

---

### Post by matt_symes on 2011-10-27
Hi

> **rasmus91 said:**
> This is everything in the lightdm.log file...

It should be said that we logged in in recovery mode to see this...

> **MetallicM said:**
> Hi. I am the one my friend here has been trying to help.
The problem is that I can't log in, not in my own or guest user or other user. I had my labtop connected to an external screen using HDMI cable. I needed to work on a bigger screen. I don't know if that is where the problem is. It could also be after I entered the Compiz Manager. I just really wanted to learn to use linux and I still hope to get this to work.

Your LightDM log file looks fine. 

I really don't think it's a Compiz issue as it affects both your user account and your guest account, but i may be wrong here. It's most definitely worth following mikejonseys instructions here.

Recovery mode loads X with failsafe options and that is why you can boot into recovery mode.

Personally, i think X is crashing when you log in. You can try to hunt this down and my next step would be to look at X's logs if you wanted to do this and post then back here.

```
/var/log/Xorg.0.log
~/xsession-errors
```

However, it may require quite a bit of detective work and, to make your life easier, i would agree with mikejonsey and reinstall X.

Kind regards

---

### Post by rasmus91 on 2011-10-30
what is the easiest way to (re)install X?

---

### Post by rasmus91 on 2011-10-31
Hi again.

we did this:

```
apt-get install --reinstall xserver-xorg
```

but it didn't help.

so we tried this:

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html")


didn't help either?

and I just cant help but wonder: What is wrong here? *scratching my head furiously* could it be the lightdm?

---

### Post by mikejonesey on 2011-10-31
try adding a new user and see if you can login to the gui with that  user, if that is the case you know its a user specific option... in  which case you can diff the xorg props...

---

### Post by rasmus91 on 2011-10-31
> try adding a new user and see if you can login to the gui with that user, if that is the case you know its a user specific option... in which case you can diff the xorg props...

i was asked to do this earlier and did. It was the same result.

---

### Post by matt_symes on 2011-10-31
Hi

Try deleting your .ICEauthority file in your home directory.

Boot into recovery mode and

```
rm /home/<your_user_name>/.ICEauthority
```

Then try to login.

That has also affected at least one other user.

Kind regards

---

### Post by rasmus91 on 2011-11-01
Guys, thanks for your help. well, my roomies patience ran out, so he reinstalled Ubuntu.

Its working now... strangely :P

Thanks for the help guys :)

---

### Post by mikejonesey on 2011-11-01
for future ref, as you had created a new user account and that did not work, then no user settings would be the cause, you would have needed to reninstall a few packages... 

which i'm not too sure about which... Could have got a list of all packages and reinstalled all packages instead of a full reinstall...

newhos good your all back up and running

---

### Post by rasmus91 on 2011-11-02
hehe, yeah. :)

---

