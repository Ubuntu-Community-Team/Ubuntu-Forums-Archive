---
title: "Load windows on computer startup and not ubuntu"
date: 2009-11-07
forum: General Help
---

### Post by jcdavies on 2009-11-07
So just installed the new ubuntu with windows vista and am loving it so far. the only problem i have is that when ever i start the computer it instantly loads ubuntu. to go in to windows i have to push f12 at the dell screen to load the boot menu. is there any way so that i can change this around or at the very least just have it so that the boot menu automatically opens when i start the computer so i can choose which one i want. 

the computer i am using is a dell inspiron530, with a intel 2140 @ 1.60ghz and 1 gig of ram

thanks for all your help 
[]("http://forums.cnet.com/5208-4_102-0.html?threadID=367632%20&tag=unsubscribeForm;tracked-disc#")

---

### Post by x33a on 2009-11-07
edit your /boot/grub/menu.lst to point to windows instead of ubuntu.

do
```
gksudo gedit /boot/grub/menu.lst
```look for a line with ```
default 0
``` or similar.

change that 0 to the number pointing towards windows (4 most likely) (counting starts from 0).

---

### Post by jcdavies on 2009-11-07
[quote=x33a;8268792]edit your /boot/grub/menu.lst to point to windows instead of ubuntu.

do
```
gksudo gedit /boot/grub/menu.lst
```look for a line with [code]/quote]


i typed that in to the terminal, is that correct and another window opened named menu.1st(/boot/grub) - gedit

but nothing apperared in this window to change what am i doing wrong

---

### Post by nisix on 2009-11-07
menu.lst - .lst - that's lower case 'L' not the number 1

---

### Post by jcdavies on 2009-11-07
same thing happening just with a l instead of a 1 this time

---

### Post by nisix on 2009-11-07
grep menuentry /boot/grub/grub.cfg

Starting from 0, find the menuentry choice number of your windows os.

gedit /etc/default/grub

Change GRUB_DEFAULT=0  to GRUB_DEFAULT=saved, save it.

sudo grub-set-default X

Where X is the menuentry number of your windows os.

---

### Post by NFblaze on 2009-11-07
I'm curious as why you have to press F12 to change what you boot into, are you sure you took the LiveCD out of the CD tray.

---

### Post by ranch hand on 2009-11-07
Don,t do any of those things.  Menu.lst does not exist in grub2.  /boot/grub/grub.cfg is a read only file for root and over writen every time update-grub is run.

Go to /etc/default/grub and change the default number there.  Remember that counting starts at 0.  You can use your /boot/grub/grub.cfg file to count down the entries to get the right number.

After changing the number, run "sudo update-grub" and you will be all set.

It might be good to read the link in my sig.  The links within it are great and by people who actually know how to use grub2.

---

### Post by jcdavies on 2009-11-07
> **nisix said:**
> grep menuentry /boot/grub/grub.cfg

Starting from 0, find the menuentry choice number of your windows os.

gedit /etc/default/grub

Change GRUB_DEFAULT=0  to GRUB_DEFAULT=saved, save it.

sudo grub-set-default X

Where X is the menuentry number of your windows os.

thanks for your help i greatly appreciate it please bare with me this is all new to me so this is how far i got

jenna@jenna-desktop:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Dell Utility Partition (on /dev/sda1)" {
menuentry "Windows Vista (loader) (on /dev/sda3)" {

wasnt sure what u meant by teh 0 thing so i then enetered 

gedit /etc/default/grub

a new window opened with this in it

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


i tried to change the 0 to saved as u said but it wont let me save it as its a read only file. so sorry but stuck again your help is very much appreciated though, is there another way to do it through windows or is this the only way?

---

### Post by jcdavies on 2009-11-07
> **NFblaze said:**
> I'm curious as why you have to press F12 to change what you boot into, are you sure you took the LiveCD out of the CD tray.

jkust the way i think this computer is set up even when the cd is in the tray i have to go to the boot menu to load the cd

---

### Post by jcdavies on 2009-11-07
> **ranch hand said:**
> Don,t do any of those things.  Menu.lst does not exist in grub2.  /boot/grub/grub.cfg is a read only file for root and over writen every time update-grub is run.

Go to /etc/default/grub and change the default number there.  Remember that counting starts at 0.  You can use your /boot/grub/grub.cfg file to count down the entries to get the right number.

After changing the number, run "sudo update-grub" and you will be all set.

It might be good to read the link in my sig.  The links within it are great and by people who actually know how to use grub2.

do i need to put anythign in front of the /etc/default/grub

sorry really new to this

---

### Post by nisix on 2009-11-07
Try gksudo gedit /etc/default/grub

What I mean is start counting from 0 starting at the top of the menuentries.

menuentry 0
menuentry 1
menuentry 2
...

---

### Post by jcdavies on 2009-11-07
> **nisix said:**
> Try gksudo gedit /etc/default/grub

What I mean is start counting from 0 starting at the top of the menuentries.

then got this again as a read only file

 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by nisix on 2009-11-07
Oops I was answering too fast.

You're good to go that's edited already.

Go ahead to the next step.

---

### Post by jcdavies on 2009-11-07
is there a way to maybe do this in windows?

---

### Post by nisix on 2009-11-07
You could also try the other guy's advice.

Just change GRUB_DEFAULT=saved / 0 to GRUB_DEFAULT=X, where X is the menuentry of your windows

You could find it out using grep menuentry /boot/grub/grub.cfg (Remember count from 0 starting at the top)

Just save it then run

sudo update-grub

---

### Post by jcdavies on 2009-11-07
> **jcdavies said:**
> then got this again as a read only file

 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

sorry it didnt have the saved in it it was # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by nisix on 2009-11-07
Like I said change GRUB_DEFAULT=0 

Change '0' to the menuentry of your windows os, save it then run sudo update-grub

---

### Post by jcdavies on 2009-11-08
> **nisix said:**
> Like I said change GRUB_DEFAULT=0 

Change '0' to the menuentry of your windows os, save it then run sudo update-grub

ok so think im there how do i find out the menuentry for windows?

---

### Post by ranch hand on 2009-11-08
You are dealing with a system file.  You need root powers.  Try'
```

gksudo gedit /etc/default/grub

```

---

### Post by x33a on 2009-11-08
sorry guys, i haven't upgraded to karmic and didn't know that it has grub2. sorry for the confusion.

---

