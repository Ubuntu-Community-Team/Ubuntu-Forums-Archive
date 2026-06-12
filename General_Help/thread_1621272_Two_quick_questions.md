---
title: "Two quick questions"
date: 2010-11-14
forum: General Help
---

### Post by chippy_250 on 2010-11-14
New to Ubuntu :)

1. Ubuntu logs me out after a few mins of inactivity (which is fair enough) but when I log back in it's closed down all my apps and browser etc. How do I stop it from either forgetting what I was doing or logging me out in the first place?

2. When I try to configure 'Wine' it logs me out and won't let me do it (I'm the Admin) 

Thanks

---

### Post by 3rdalbum on 2010-11-14
It shouldn't log you out unless you tell it to. I think your problem are related to your graphics card - maybe X is crashing when your screensaver kicks in, and also when Wine attempts to discover if it can use OpenGL.

Try turning off the screensaver as a quick workaround. But also, what graphics card do you have and what driver are you using? Can you run 3d programs or desktop effects?

---

### Post by matt_symes on 2010-11-14
Hi

To test open gl open a terminal and type glxgears. You should see an animation if all is well.

To turn off screensaver: System->Preferences->Screen saver. Uncheck Activate screen saver when computer is idle.

Kind regards

---

### Post by Goldfissh on 2010-11-14
Are you sure that you're running as root when you're trying to configure Wine?

---

### Post by chippy_250 on 2010-11-15
> **matt_symes said:**
> Hi

To test open gl open a terminal and type glxgears. You should see an animation if all is well.

To turn off screensaver: System->Preferences->Screen saver. Uncheck Activate screen saver when computer is idle.

Kind regards

I tried what you said and it came up with this message "sudo apt-get install mesa-utils"

I also can only run the basic visual effects. I did try to run the normal mode but the screen went black for a while and then it said it couldn't run so went back to basic mode.

---

### Post by matt_symes on 2010-11-15
Hi

What version of Ubuntu are you using?

mesa-utils is the package the contains glxgears.

Typing at sudo apt-get install mesa-utils at the command line will install this package on your machine. However it was included in my install of 10.04 by default or at least one of the updates.

Package details here:
[http://www.ubuntuupdates.org/packages/show/243066](http://www.ubuntuupdates.org/packages/show/243066)

When was the last time you updated your packages?

What is your graphics card?

Kind regards

---

### Post by chippy_250 on 2010-11-17
> **matt_symes said:**
> Hi

What version of Ubuntu are you using?

mesa-utils is the package the contains glxgears.

Typing at sudo apt-get install mesa-utils at the command line will install this package on your machine. However it was included in my install of 10.04 by default or at least one of the updates.

Package details here:
[http://www.ubuntuupdates.org/packages/show/243066](http://www.ubuntuupdates.org/packages/show/243066)

When was the last time you updated your packages?

What is your graphics card?

Kind regards


I've only just got Ubuntu 10.10 about 2 weeks ago. 
How do I find out what graphics card I got? I know how to find it on Windows Xp but where's the system info on Ubuntu?

---

### Post by matt_symes on 2010-11-17
Hi

Open a terminal and type 

lspci | grep VGA

The command line is case sensitive. This will tell you your graphics card model.

Also at the terminal type.

sudo apt-get update
Then enter your password (you will see nothing as you type it, dont worry this is normal). Then type

sudp apt-get upgrade.

This will ensure you have all the latest packages (at least for the sources you have enabled).

Go to System->Administration->Hardware drivers (in the menu). Does it specify any drivers you need for your video controller?

At the terminal type

sudo apt-get install mesa-utils

This will install glxgears. Try to run it and see what happens.

BTW. I just want to ask for clarification. When you say it logs you out, do you mean it takes you to the very first logon screen with the nice background and the option to login yourself or another, or does it have a black background with a window that just asks you to enter your password.

The reason i ask is because the default in Ubuntu when the screen saver kicks in is to ask you for your password to unlock the screen saver and to get back into Ubuntu. This is different than the initial logon screen.

Kind regards

---

### Post by chippy_250 on 2010-11-18
> **matt_symes said:**
> Hi

Open a terminal and type 

lspci | grep VGA

The command line is case sensitive. This will tell you your graphics card model.

Also at the terminal type.

sudo apt-get update
Then enter your password (you will see nothing as you type it, dont worry this is normal). Then type

sudp apt-get upgrade.

This will ensure you have all the latest packages (at least for the sources you have enabled).

Go to System->Administration->Hardware drivers (in the menu). Does it specify any drivers you need for your video controller?

At the terminal type

sudo apt-get install mesa-utils

This will install glxgears. Try to run it and see what happens.

BTW. I just want to ask for clarification. When you say it logs you out, do you mean it takes you to the very first logon screen with the nice background and the option to login yourself or another, or does it have a black background with a window that just asks you to enter your password.

The reason i ask is because the default in Ubuntu when the screen saver kicks in is to ask you for your password to unlock the screen saver and to get back into Ubuntu. This is different than the initial logon screen.

Kind regards

I've tried to do everything you told me. I don't seem to have 'Hardware drivers' in the Administration menu...
So I clicked on 'Additional drivers' but there's nothing in there.

I also typed: 'sudo apt-get install mesa-utils' into the terminal and it asked me if I wanted to download 2 software packages, so I said yes, they downloaded but then nothing happened after that.

I found out what graphics card I've got though...

VGA compatible controller: S3 Inc.VT375 (ProSavage8 KM266/KL266)

In answer to your question about
 "When you say it logs you out, do you mean it takes you to the very first  logon screen with the nice background and the option to login yourself  or another, or does it have a black background with a window that just  asks you to enter your password."

The first one - with the option of login you/another user with the colorful background.

So what do I do now?

---

### Post by matt_symes on 2010-11-18
Hi

Open a terminal and type 

glxgears

What happens?

Kind regards

---

### Post by chippy_250 on 2010-11-18
> **matt_symes said:**
> Hi

Open a terminal and type 

glxgears

What happens?

Kind regards

Screen went black, when it came back on it had logged me out and I had to log back into my user account. The same happens when I try to configure Wine. 
What does this mean then?

---

### Post by matt_symes on 2010-11-18
Hi

It means you have a problem with your graphics card and OpenGL and x windows . Glxgears uses openGL and is a little test application to ensure everything is working. In your case it is not.

Unfortunately, i have to pop out for a while. If no one else helps, i will speak later.

Kind regards

---

