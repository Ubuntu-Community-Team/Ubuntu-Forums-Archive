---
title: "I accidently deleted UBUNTU 11.04 - URGENT HELP!!!"
date: 2011-09-20
forum: General Help
---

### Post by RAIDa23 on 2011-09-20
Crap. I was getting frustrated at how slow Ubuntu was on my computer, and I wanted to change to Xubuntu. So I got a little too excited, and entered the code to remove Ubuntu found on this site: [http://www.psychocats.net/ubuntu/purexfcem](http://www.psychocats.net/ubuntu/purexfcem) (I didn't even have Xubunu downloaded yet. I just typed in the code for no damn reason)

into the Terminal. I press enter, and I said yes, and then yes again. Next minute, computer reboots, and goes to the Login screen and the only options for desktop avaliable is Recovery Mode and User Interface Mode. If I enter either one of these modes, all that shows up is the terminal command box in the left corner.

Ive got the cd to installing Ubuntu, so I turned off the computer, turned it on again, and put in the CD into the computer's CD drive. Nothing happens, all it does is go to the login screen.

SOMEONE PLEEEEAAAASSSSE HELP ME. I just want Ubuntu back. :(:(:confused::(:(:confused:

P.S Im on my mate's laptop. Thats how I'm on the net right now.

---

### Post by RAIDa23 on 2011-09-20
How do you remove ubuntu 11.04 from a computer with Ubuntu as it's primary OS? I bought a computer a while back without a OS so I installed Ubuntu on it, and I wanna get rid of it.

---

### Post by rickygarg on 2011-09-20
I'm no expert but I think that the installation issues with Ubuntu should not interfere with your BIOS' ability to boot from CD. Please ensure that you've set up your BIOS to boot from Disc. If that's a non issue, I am sure some smarter folks will be here to help.

---

### Post by rollinsmoke on 2011-09-20
start whatever os you want to install from disc to do that you need to go through your bios and go over to boot then select you cd drive as your main  restart saving changes then just go through what ever the formating and partitioning procedures are

---

### Post by rollinsmoke on 2011-09-20
otherwise if you just wanted a clean system with no os then just run off a linux live cd and format the drive with whatever disc manger is on the os

---

### Post by staticd on 2011-09-20
Hey if you get an X terminal just insert the same command with "sudo apt-get install" instead of "apt-get remove".
You could save the line on your pendrive as command.txt and do cat command .txt to get it into your terminal. Though it might be best to just reinstall ubunu. 

As rickygarg pointed out, its just that you have not set you bios to boot from the CD. Press Del/Esc/F1/F2/F3/F9/F10/F12 to get a boot menu. If you are not sure which one is for your computer, try all of them for good measure as your computer is booting. You should then be able to select the CD as you boot device and reinstall. 

How many partions do you have? Tell us if you need instrucions in backing up data on your ubuntu home.

---

### Post by nothingspecial on 2011-09-20
Hi,

get a wired connection.

Log in and type ```
sudo apt-get install ubuntu-desktop
```

---

### Post by coffeecat on 2011-09-20
@RAIDa23, is this question anything to do with this thread which you started only an hour or so previous to this one?

[http://ubuntuforums.org/showthread.php?t=1847041](http://ubuntuforums.org/showthread.php?t=1847041)

---

### Post by RAIDa23 on 2011-09-20
> **coffeecat said:**
> @RAIDa23, is this question anything to do with this thread which you started only an hour or so previous to this one?

[http://ubuntuforums.org/showthread.php?t=1847041](http://ubuntuforums.org/showthread.php?t=1847041)

Yes it is. After I reinstall Ubuntu, I woud like to get rid of it completely, and install Bodhi Linux.

---

### Post by nothingspecial on 2011-09-20
Threads merged

---

### Post by RAIDa23 on 2011-09-20
Ok so now what? I entered in the code, it did its thing, it asked me if i was sure If i wanted to continue, I said yes, and then all of this stuff came up, and its just stuck on one thing now. Did you want me to put the CD in as well? Cos I didnt.

---

### Post by eddier on 2011-09-20
Reboot with your Ubuntu live cd, activate your networking if it isnt allready up.

Download Bodhi.
Burn it to cd.
Shut down Ubuntu.
reboot with the Bodhi cd and install.

Think very carefully about using random code you have found on the internet.

eddie

---

### Post by RAIDa23 on 2011-09-20
I dont have CD burner, is there any other way to put Bodhi on USB?

---

