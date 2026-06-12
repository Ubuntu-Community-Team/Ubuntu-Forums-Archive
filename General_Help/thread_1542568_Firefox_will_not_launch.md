---
title: "Firefox will not launch"
date: 2010-07-30
forum: General Help
---

### Post by elohnah on 2010-07-30
Hello,

A new linux user--very, very much a newbie.:neutral:

I have Ubuntu 10.4 installed, which dual boots alongside Windows Xp Home Edition.
The Firefox web browser will not launch. i have googled this problem, & tried everything that was posted in different forums, & Firefox still wont launch. Could this be a bug in Ubuntu 10.4?

Have 180 GB of disk space left on Sata hard disk.
two GB of memory

Thank You
elohnah

---

### Post by lovinglinux on 2010-07-30
First, try to start Firefox in safe mode. to do that you will need to run a command in a terminal. Go to "Applications >> Accessories >> Terminal" and paste (CTRL+SHIFT+V) or type the following command:

```
firefox -safe-mode
```

Then choose the option to continue in safe mode.

If that doesn't work, try to create a new user profile, just to test to see of you have an issue with your current profile. To do that, use the command below to open the Profile Manager, then create a new profile and start it:

```
firefox -P
```

Please report the results.

---

### Post by elohnah on 2010-07-30
Lovinglinux,

first code bought up this: "could not launch application. failed to execute child process, "firefox.exe" (no such file or directory)

second code brought up this: run-mozilla.sh: Cannot execute /usr/lib/  firefox-3.6.8/firefox-bin.pure.

elohnah

---

### Post by elohnah on 2010-07-30
Is there a way of downloading another linux web browser in Ubuntu without using firefox--since it will not launch?
This is probably a stupid question.

---

### Post by lovinglinux on 2010-07-30
First you need to understand that applications in Linux are provided from a central repository, from where you can install all the software you need (mostly), not search on the web like on Windows. Secondly, although there are ways of running software designed for Windows, exe files are not intended to work with it.

Looks like you have installed a Firefox version designed for Windows, hence the **firefox.exe** error message.

To remove all Windows applications that you might have installed, open the file manager, go to your home directory, then press CTRL+H to show hidden files and folders, then locate the folder **.wine** and delete it.

Then run the following command to re-install firefox properly:

```
sudo apt-get install --reinstall firefox
```

Logout and login again, then start Firefox from the applications menu.

Keep in mind I'm giving you commands because it's easier for us to give instructions with commands, but that doesn't mean you can't do stuff on Ubuntu using only the mouse.

---

### Post by elohnah on 2010-07-31
i could not find .wine folder in file manager. Tried the code to reinstall firefox--invalid command.

---

### Post by elohnah on 2010-07-31
LovingLinux,

Firefox is now working, i am using  firefox  in Ubuntu now. Thanks for your help in solving this problem.

elohnah

---

### Post by lovinglinux on 2010-07-31
> **elohnah said:**
> LovingLinux,

Firefox is now working, i am using  firefox  in Ubuntu now. Thanks for your help in solving this problem.

elohnah

You are welcome.

How did you solve the problem?

---

