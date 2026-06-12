---
title: "keybord prferences on startup"
date: 2011-05-24
forum: General Help
---

### Post by meredith_fer on 2011-05-24
hi everyone!

I have this problem: keybord preferences keep appearing every time I start ubuntu. It shows two option for the keyborad, I picked one (the same, always) and then close it.

But it is annoying do it everytime

any ideas?

thx guys!

---

### Post by hwttdz on 2011-05-25
Appears at the login screen or after you login?  I wonder if it's an autostart file either in 
/usr/share/gdm/autostart/
or
~/.config/autostart

---

### Post by meredith_fer on 2011-05-26
> **hwttdz said:**
> Appears at the login screen or after you login?  I wonder if it's an autostart file either in 
/usr/share/gdm/autostart/
or
~/.config/autostart

thank you for your response... this is what I got:

/usr/share/gdm/autostart/LoginWindow$ dir

at-spi-registryd-wrapper.desktop  libcanberra-ready-sound.desktop
gdm-simple-greeter.desktop	  metacity.desktop
gnome-mag.desktop		  onboard.desktop
gnome-power-manager.desktop	  orca-screen-reader.desktop
gnome-settings-daemon.desktop

---

### Post by hwttdz on 2011-05-29
It doesn't seem to be any of those, and what are the contents of ~/.config/autostart/ ?

---

### Post by meredith_fer on 2011-05-30
> **hwttdz said:**
> It doesn't seem to be any of those, and what are the contents of ~/.config/autostart/ ?

bluetooth-applet.desktop	 ubuntuone-launch.desktop
deja-dup-monitor.desktop	 vino-server.desktop
evolution-alarm-notify.desktop	 wicd-tray.desktop
libcanberra-login-sound.desktop

thank you for helping me

---

### Post by hwttdz on 2011-05-30
By "keyboard preferences" do you mean "gnome-keyboard-properties" i.e. run "gnome-keyboard-properties" and let us know if it's the same window.  

What is the output of the command:
find / -xdev -iname gnome-keyboard-properties* 2>/dev/null

---

### Post by meredith_fer on 2011-05-30
> **hwttdz said:**
> By "keyboard preferences" do you mean "gnome-keyboard-properties" i.e. run "gnome-keyboard-properties" and let us know if it's the same window.  

What is the output of the command:
find / -xdev -iname gnome-keyboard-properties* 2>/dev/null

the output is:

/usr/share/man/man1/gnome-keyboard-properties.1.gz
/usr/share/gnome-control-center/ui/gnome-keyboard-properties-dialog.ui
/usr/share/gnome-control-center/ui/gnome-keyboard-properties-a11y-notifications.ui
/usr/share/gnome-control-center/ui/gnome-keyboard-properties-options-dialog.ui
/usr/share/gnome-control-center/ui/gnome-keyboard-properties-layout-chooser.ui
/usr/share/gnome-control-center/ui/gnome-keyboard-properties-model-chooser.ui
/usr/bin/gnome-keyboard-properties

thank youuuu

---

### Post by hwttdz on 2011-05-31
You never answered, does it appear at the login window or after you have logged in and reached the desktop?

An inelegant workaround would be to "sudo chmod -x /usr/bin/gnome-keyboard-properties" and then just remember to undo that if you need to change keyboard properties later.  

It doesn't seem to be started by an autostart file or the gnome session.  

Could you run (where meredith_fer should be your username on the box) after boot, when the gnome-keyboard-properties is still open: 
ps -ww -eo pid,ppid,user,command|grep `ps -ww -eo pid,ppid,user,command -u meredith_fer|grep gnome-keyboard-properties|grep -v grep|awk '{print $2}'`

This is a hackjob way of telling us which process is starting the keyboard preferences thing.

---

### Post by meredith_fer on 2011-06-01
> **hwttdz said:**
> You never answered, does it appear at the login window or after you have logged in and reached the desktop?

An inelegant workaround would be to "sudo chmod -x /usr/bin/gnome-keyboard-properties" and then just remember to undo that if you need to change keyboard properties later.  

It doesn't seem to be started by an autostart file or the gnome session.  

Could you run (where meredith_fer should be your username on the box) after boot, when the gnome-keyboard-properties is still open: 
ps -ww -eo pid,ppid,user,command|grep `ps -ww -eo pid,ppid,user,command -u meredith_fer|grep gnome-keyboard-properties|grep -v grep|awk '{print $2}'`

This is a hackjob way of telling us which process is starting the keyboard preferences thing.

it appears after I log in, when I see the desktop. I ran the command you suggest:

ps -ww -eo pid,ppid,user,command|grep `ps -ww -eo pid,ppid,user,command -u meredith_fer|grep gnome-keyboard-properties|grep -v grep|awk '{print $2}'`

and I got:
Use: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

don't know what this means

---

### Post by hwttdz on 2011-06-01
Ok, why don't you just run the command in two parts, first we need to find the pid of gnome-keyboard-properties, which we can do with:
"ps -ww -eo pid,ppid,command|grep gnome-keyboard-properties"

I get:
  487 30844 user  grep --color=auto gnome-keyboard-properties
30900 30844 user  gnome-keyboard-properties

Ignore the line beginning with grep in it, and look at the other, the first number is the process id of gnome-keyboard-properties.  The second is the process id of the parent process.  We're now going to look for the parent process by id (here mine is 30844):
"ps -ww -eo pid,user,command|grep 30844"

This tells me: 
"30844 jhb2147  bash", because I launched gnome-keyboard-properties from the bash shell.  I'm hoping that the process that is launching gnome-keyboard-properties stands out as unusual.  If so we'll be able to make a change there and that'll be it.

---

### Post by meredith_fer on 2011-06-03
> **hwttdz said:**
> Ok, why don't you just run the command in two parts, first we need to find the pid of gnome-keyboard-properties, which we can do with:
"ps -ww -eo pid,ppid,command|grep gnome-keyboard-properties"

I get:
  487 30844 user  grep --color=auto gnome-keyboard-properties
30900 30844 user  gnome-keyboard-properties

Ignore the line beginning with grep in it, and look at the other, the first number is the process id of gnome-keyboard-properties.  The second is the process id of the parent process.  We're now going to look for the parent process by id (here mine is 30844):
"ps -ww -eo pid,user,command|grep 30844"

This tells me: 
"30844 jhb2147  bash", because I launched gnome-keyboard-properties from the bash shell.  I'm hoping that the process that is launching gnome-keyboard-properties stands out as unusual.  If so we'll be able to make a change there and that'll be it.

again THANK YOUUU!!!

I got this:

for the first command:
3425  3402 grep --color=auto gnome-keyboard-properties

for the second:
3402 maria12 bash
3467 maria12 grep --color=auto 3402

Right know I haven't close the keyboard preferences. It has two languages to choose... it is getting on my nerves!

---

### Post by hwttdz on 2011-06-06
That output shows that gnome-keyboard-properties is not running.  You're sure you ran that command while it was open (having been launched automatically?)?

---

