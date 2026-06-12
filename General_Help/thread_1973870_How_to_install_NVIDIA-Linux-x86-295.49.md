---
title: "How to install NVIDIA-Linux-x86-295.49"
date: 2012-05-05
forum: General Help
---

### Post by garyzw on 2012-05-05
Could someone please explain to me how to install the 295.49 drivers in Ubuntu 12.04?

---

### Post by Abrer on 2012-05-05
-Download drivers
-Make the file executable
-Stop X ('sudo lightdm stop' without quotes should work)
-Ctrl + F1 or so to get to a shell if yours is goofy looking after stopping lightdm
-cd to the directory the file is located
-Execute file with ./FILENAME
-Install

---

### Post by garyzw on 2012-05-05
Thanks for the reply. When I use "sudo lightdm stop" I get this message "Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?"



> **Abrer said:**
> -Download drivers
-Make the file executable
-Stop X ('sudo lightdm stop' without quotes should work)
-Ctrl + F1 or so to get to a shell if yours is goofy looking after stopping lightdm
-cd to the directory the file is located
-Execute file with ./FILENAME
-Install

---

### Post by Abrer on 2012-05-05
hrm... could try 'sudo service lightdm stop'.

Btw, I'm assuming you already know that stopping lightdm will drop you into a terminal setting. So in the event that you don't know this and stop lightdm anyways, ctrl + alt + f1/f2/f3/we will change your shell screens and running sudo lightdm start or sudo service lightdm start will relaunch lightdm.

---

### Post by garyzw on 2012-05-05
Thanks for bearing with me--'sudo service lightdm stop' worked.

Trying to cd to the directory the file is located does not work-- ctrl + alt + f1/f2/f3/ brings up a TTY and asks for Login and password.

I know my password but what about log in?

> **Abrer said:**
> hrm... could try 'sudo service lightdm stop'.

Btw, I'm assuming you already know that stopping lightdm will drop you into a terminal setting. So in the event that you don't know this and stop lightdm anyways, ctrl + alt + f1/f2/f3/we will change your shell screens and running sudo lightdm start or sudo service lightdm start will relaunch lightdm.

---

### Post by Abrer on 2012-05-05
Your login is your username. If your username was Bob, you'd type Bob at the username prompt. Running ```
whoami
``` in a terminal displays your username.

To clarify, you're using the same name as you do in your GUI. It's still the same system, just in text mode.

Edit#2: I gotta get going, hope you got the drivers installed.

---

### Post by garyzw on 2012-05-05
I am now using the live CD to post to this forum-- the driver seemed to instll fine but  sudo service lightdm start does not seem relaunch lightdm. Even when I re-boot I am back to the TTY is does not go in to the Unity desktop

HELP!!

---

### Post by Abrer on 2012-05-05
What is the message you get when you try to restart lightdm?

---

### Post by garyzw on 2012-05-05
I would have to exit the live CD and write it down but it I think it put me back in to the TTY asking for user name and password

> **Abrer said:**
> What is the message you get when you try to restart lightdm?

---

### Post by garyzw on 2012-05-05
I would really hate to have to re-install Ubuntu!

---

### Post by Abrer on 2012-05-05
Well since you're in a livecd session, can you tell me the contents of your main install's /etc/X11/default-display-manager file? Should just be able to open it up with gedit or so.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
if you install the driver via the run file you will have to reinstall it ever time the kernel updates

once you download the driver
ctrl+alt+f1
login 
[FONT=Courier New]sudo service lightdm stop
sudo sh Downloads/NVIDIA-Linux-*-295.49.run[/FONT] the tab key does autocomplete
if you get a error about "nouveau"
you need to edit /etc/default/grub ([FONT=Courier New]gksudo gedit /etc/default/grub[/FONT])
locate the line with "[FONT=Courier New]quit splash[/FONT]" in it and make it "[FONT=Courier New]quit nomodeset splash[/FONT]"
save it 
run [FONT=Courier New]sudo update-grub[/FONT]

to get the gui back run [FONT=Courier New]sudo service lightdm start[/FONT]

---

### Post by garyzw on 2012-05-05
> **Abrer said:**
> Well since you're in a livecd session, can you tell me the contents of your main install's /etc/X11/default-display-manager file? Should just be able to open it up with gedit or so.

How do I open the /etc/X11/default-display-manager with gedit??

---

### Post by garyzw on 2012-05-05
I got it 

It says /usr/sbin/lightdm

---

### Post by Abrer on 2012-05-05
Let me see if I got this right:

You installed the drivers, but boot back into the computer and it takes you to a login screen. Are you not able to login into the computer because you don't know your username? If that's the case, you should be able to check the /etc/passwd file to find usernames.

Once you login, run sudo service lightdm start.

---

### Post by Cavsfan on 2012-05-05
Try this. It should work with any version of Ubuntu although I keep seeing problems with nVidia drivers on 12.04.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

It should pull up 295.48 I see it just came out on 1012.05.03

I am going to install using this method my self but, I am on Lucid Lynx.

---

### Post by Cavsfan on 2012-05-05
I just updated my driver! It takes just a few minutes once you have done it a couple of times.
Now, I have to move the new driver into the place that How to mentions so that the next kernel install picks up the new driver.

---

### Post by garyzw on 2012-05-05
I am able to log in and all I get is a blinking _

> **Abrer said:**
> Let me see if I got this right:

You installed the drivers, but boot back into the computer and it takes you to a login screen. Are you not able to login into the computer because you don't know your username? If that's the case, you should be able to check the /etc/passwd file to find usernames.

Once you login, run sudo service lightdm start.

---

### Post by garyzw on 2012-05-05
Thanks Cavsfan-- the first time around I messed up my installation but after re-install and following these direction everything worked.

> **Cavsfan said:**
> Try this. It should work with any version of Ubuntu although I keep seeing problems with nVidia drivers on 12.04.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

It should pull up 295.48 I see it just came out on 1012.05.03

I am going to install using this method my self but, I am on Lucid Lynx.

---

### Post by Cavsfan on 2012-05-05
> **garyzw said:**
> Thanks Cavsfan-- the first time around I messed up my installation but after re-install and following these direction everything worked.


You are welcome! Glad I could help. It is pretty simple after a few times.
Once you do it once, the next time you just start at step 4. 
Just boot into recovery and drop into root console and enter** telinit 3** wait 20 seconds or so and then login.

I messed my system up a couple of times and had to re-install before I got a bit more knowledgeable about this stuff.
One time my compiz went crazy and re-installing the driver is what fixed it.

Oh, please mark this thread as solved by clicking on **thread tools** at the top and then **mark this thread as solved** at the bottom of the list.

---

### Post by garyzw on 2012-05-05
When the linux  kernal updates does it still recognize the new driver?

> **Cavsfan said:**
> You are welcome! Glad I could help. It is pretty simple after a few times.
Once you do it once, the next time you just start at step 4. 
Just boot into recovery and drop into root console and enter** telinit 3** wait 20 seconds or so and then login.

I messed my system up a couple of times and had to re-install before I got a bit more knowledgeable about this stuff.
One time my compiz went crazy and re-installing the driver is what fixed it.

Oh, please mark this thread as solved by clicking on **thread tools** at the top and then **mark this thread as solved** at the bottom of the list.

---

### Post by kelvin spratt on 2012-05-05
> **Abrer said:**
> What is the message you get when you try to restart lightdm?
You need to reboot to load the nvidia driver

---

### Post by Cavsfan on 2012-05-06
> **garyzw said:**
> When the linux  kernal updates does it still recognize the new driver?

When you get a kernel "update" you will see a message that the driver is already installed.
But, when a new kernel is installed, it will be added to the kernel if you went by this How To  
[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

When I do it, I just copy the commands to a text file (gedit) and modify them as needed.
Then copy and paste them one at a time back into the terminal.

Once you have completed the bottom part of creating the script and creating the directory and moving the script to that directory,
all you will need to do the next time you update the driver is delete the driver and **nvidia-driver** from** /usr/src**.
Then complete the 2 steps in the top (this has been updated to the newest version):

```
sudo mv NVIDIA-Linux-x86_64-295.49.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-x86_64-295.49.run /usr/src/nvidia-driver
```

When I mention "you will see the driver is already installed", you will see that if you use CLI commands to get your updates.
When a new kernel is installed, you will also see from the script 
**Building NVIDIA driver for kernel XXX** and after that you will hopefully see **SUCCESS: Driver installed for kernel XXX**.

**ranch hand** a friend in this forum, taught me to use these commands and not Update Manager. He called it Update Mangler.
I use it to view the updates but, I only get my updates with:
```
sudo apt-get update 
sudo apt-get upgrade
```
That will get most updates but, if there is a new kernel to be installed, that kernel will be held back. First apply the updates and then enter this to get the kernel:

```
sudo apt-get dist-upgrade
``` 
These commands allow you to see any error messages or anything like that.

If you want, you can also make these into scripts called "ud" and "ud2" by entering 
**gksu gedit /home/cavsfan/.bashrc**
and adding these 2 lines towards the bottom (I add mine above where it says **# Alias definitions.**

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```

You will need to logout and back in before these will work.
You will just need to enter **ud** in a terminal and your password to get updates.
If there is a kernel held back after getting those updates just enter **ud2**.

---

