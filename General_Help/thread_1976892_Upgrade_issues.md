---
title: "Upgrade issues"
date: 2012-05-09
forum: General Help
---

### Post by bobipod on 2012-05-09
I upgraded to the 12/04 edition of ubuntu but i have a couple of issues.

1 ubuntu 1 fails every time on start up and generates an error report.

2 shut down is not shutting the laptop down it is just putting it into a kind of sleep mode.  I have to hold the power button for a few seconds in order to fully shut down.

---

### Post by zvacet on 2012-05-09
Boot in recovery mode and type

```
dpkg --configure -a
sudo apt-get -f install
```

Run one command at the time.

---

### Post by bobipod on 2012-05-14
now that i have installed ubuntu as my sole os i am ready to sort these glitches out.

Is booting in safe mode possible in ubuntu alone?

If so how do i do it? Is it hardware specific, such as F2 / F12?

---

### Post by bobipod on 2012-05-16
^^^^^^ anybody advise?

---

### Post by bobipod on 2012-05-17
no one?

---

### Post by Cavsfan on 2012-05-17
It should be listed on the grub menu when you boot up. Or do you boot directly into Ubuntu?

---

### Post by Cavsfan on 2012-05-17
If it goes straight into Ubuntu, enter this
**gksu gedit /etc/default/grub**
Then change uncomment out or add **GRUB_TIMEOUT=60**
60 is seconds, you can enter 10 or whatever -1 will pause it until you enter a key.
Also, if you see this **GRUB_DISABLE_LINUX_RECOVERY=true** add a # before it to comment it out or change it to **false**.

Then enter **sudo update-grub** to make the changes stick.
And reboot, you should see a list and recovery should be one of them.

---

### Post by bobipod on 2012-05-18
> **Cavsfan said:**
> If it goes straight into Ubuntu, enter this
**gksu gedit /etc/default/grub**
Then change uncomment out or add **GRUB_TIMEOUT=60**
60 is seconds, you can enter 10 or whatever -1 will pause it until you enter a key.
Also, if you see this **GRUB_DISABLE_LINUX_RECOVERY=true** add a # before it to comment it out or change it to **false**.

Then enter **sudo update-grub** to make the changes stick.
And reboot, you should see a list and recovery should be one of them.

My system does go staright into ubuntu load up.  From the above I assume you mean open a terminal window and enter the above in that window?

I have tried but nothing happens it just goes to another command line.

---

### Post by Cavsfan on 2012-05-18
> **bobipod said:**
> My system does go staright into ubuntu load up.  From the above I assume you mean open a terminal window and enter the above in that window?

I have tried but nothing happens it just goes to another command line.

You enter **gksu gedit /etc/default/grub** in a terminal and it should ask for your password.
Then open up the file for editing with gedit.

---

### Post by bobipod on 2012-05-19
Ok, i got past the password and i'm not quite sure where to get the correct "gedit" file from to edit it.

If i enter gedit after i have entered my password it opens up a blank new document.  Is this correct or is the file hidden somewhere and i need to access it somehow?  I searched using dash home but nothing but the above blank file again.

---

### Post by waperboy on 2012-05-19
> **bobipod said:**
> Ok, i got past the password and i'm not quite sure where to get the correct "gedit" file from to edit it.

If i enter gedit after i have entered my password it opens up a blank new document.  Is this correct or is the file hidden somewhere and i need to access it somehow?  I searched using dash home but nothing but the above blank file again.

You do not just enter "gedit" and press enter, you type:

gksu gedit /etc/default/grub

and press enter. If it asks you for a password, you enter your password.

---

### Post by Cavsfan on 2012-05-19
> **waperboy said:**
> You do not just enter "gedit" and press enter, you type:

gksu gedit /etc/default/grub

and press enter. If it asks you for a password, you enter your password.

> **bobipod said:**
> Ok, i got past the password and i'm not quite sure where to get the correct "gedit" file from to edit it.

If i enter gedit after i have entered my password it opens up a blank new document.  Is this correct or is the file hidden somewhere and i need to access it somehow?  I searched using dash home but nothing but the above blank file again.

Yes, when you enter **gksu gedit /etc/default/grub** and it asks for your password and you enter it, 
it should edit the file **/etc/default/grub** with the text editor gedit.

If it gets an error about gedit not existing, enter **sudo apt-get install gedit**.
If it opens the file on a white background with "gedit" in the middle of the bar at the top, you are there.

I don't know what version of Ubuntu you have. I am on 10.04 Lucid Lynx LTS and this is what my /etc/default/grub file looks like:```


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
[COLOR=Red]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]GRUB_TIMEOUT=60[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#backup monitor size
#GRUB_GFXMODE=1366x768-24
GRUB_GFXMODE=1920x1200-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```My default line is windows 7 (2) as all I have is (the first line is 0):

```
     0    Ubuntu Lucid Lynx
     1    Ubuntu Lucid Lynx (Recovery Mode)
     2    Windows 7
```You would just want to make sure the 1st red line is commented out if it is not already with an # as the 1st character.
Then make sure the 2nd red line is not commented out and if it does not exist, add it.
60 on my file is the number of seconds the grub selection screen will display.
You can change this to 10, 20, 30 or whatever you want. If you set it to -1, it will stay there until you select an option on the screen.

Then save the file and in terminal enter **sudo update-grub** to make those changes stick.
Any time you make a change to grub, you must enter sudo update-grub or else when you reboot, your changes will be lost.

Let us know what happens after you change that and reboot. You should see a menu.
The reason my grub menu is just 3 lines is because I went through the blue How to in my signature and customized it.

---

### Post by bobipod on 2012-05-26
now i'm getting nothing except below, i'm sure it must be me doing something wrong 

[IMG]http://i147.photobucket.com/albums/r298/Cabble/gedit.png[/IMG]

---

### Post by linuxman94 on 2012-05-26
You're missing a space between gedit and the file path.  It should be this:
```
gksu gedit /etc/default/grub
```

Also, gedit is just a text editor, grub is the file you are editing.

---

### Post by bobipod on 2012-05-26
finally got the file to display and the file now looks like this

[IMG]http://i147.photobucket.com/albums/r298/Cabble/currentgrub.png[/IMG]

yet still the laptop sits in a "sleep" state instead of shutting off.

---

### Post by Cavsfan on 2012-05-26
> **bobipod said:**
> finally got the file to display and the file now looks like this

[IMG]http://i147.photobucket.com/albums/r298/Cabble/currentgrub.png[/IMG]

yet still the laptop sits in a "sleep" state instead of shutting off.

The time it currently displays the menu is set to 1 second. In a terminal enter **gksu gedit /etc/default/grub**
and where you see it says **GRUB_TIMEOUT=1** change it to **GRUB_TIMEOUT=60**.
Then enter **sudo update-grub** to make the changes stick. If you do not do this, it will be the same as before.
Reboot and the menu should display for 60 seconds and the 2nd line down should be recovery mode.
Select that and when it comes up scroll the options to the bottom and select root shell. At the prompt if it not already asking for your userid enter login and enter your userid and password.
Then enter the commands that **zvacet** recommended in post #2 one at a time.
Then enter **sudo reboot** and see what you have.

---

### Post by bobipod on 2012-05-28
I give up on this as nothing is working, thanks for help though!

---

### Post by bobipod on 2012-05-31
OK a fresh glimmer of positivity and a solution to my wifi issue means i'm ready to give this another go.

---

