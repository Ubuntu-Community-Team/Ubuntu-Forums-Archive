---
title: "Could not log in after crash (no prompt to enter password)"
date: 2011-05-11
forum: General Help
---

### Post by nd.trixiebunt on 2011-05-11
Hi guys ! I hope someone can help me out with this desktop issue with Ubuntu 10.10 ...

My Ubuntu desktop crashed last night after I accidentally bumped into the CPU box. Right after I bumped into it, it restarted automatically ... then it ran disk integrity check, also automatically ... 

The issue is that I can NOT log into it. There is no way that I could enter my password. Though I could telnet into it using my laptop (I have set up telnetd into this desktop before).

I am trying to search for similar issues in this forum but I could not find one that is really like this. So if someone could help me out, I have all 5 years of work in the hard drive. Thank you very much in advance !!!

The two images below shows the issue it had done. 


This is my login screen (note: whenever I click "nd-desktop", it doesn't give me prompt for password.

[[IMG]http://img685.imageshack.us/img685/1310/img3060t.th.jpg[/IMG]]("http://img685.imageshack.us/i/img3060t.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is just the screen it gives me when I click "nd-desktop" above. Also, take note there are no usual options below that could change my preferred desktop etc. 

[[IMG]http://img833.imageshack.us/img833/6194/img3061g.th.jpg[/IMG]]("http://img833.imageshack.us/i/img3061g.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by sikander3786 on 2011-05-11
Welcome to the forums :-)

I am not definitely positive what has happened there and what should be done to fix it.

As a workaround, we can try to set GDM to login automatically and don't ask for a password. Lets see if you can get to the desktop then.

From your Login Screen (messed), press Ctrl + Alt + F1. tty should appear. Login using your credential and edit the gdm conf files.

```
sudo nano /etc/gdm/custom.conf
```

Find the line similar to this.

```
AutomaticLoginEnable=false
```

And change the 'false' part to 'true' so it looks like,

```
AutomaticLoginEnable=true
```

Save the file and restart gdm.

```
sudo service gdm restart
```

Any progress?

---

### Post by sweetleaf on 2011-05-11
You've tried restarting the machine, right? (Power menu in lower-right corner.) And gdm looks the same after restart?

---

### Post by nd.trixiebunt on 2011-05-11
@sikander3786
Hey, thank you for your help. It seems like I don't have the file custom.conf on /etc/gdm ... I guess it was corrupted. 

@sweetleaf
yup. still the same screen after reboot.

---

### Post by nd.trixiebunt on 2011-05-11
should I reinstall gdm ?

---

### Post by nd.trixiebunt on 2011-05-11
Found something on the net and tried this ... This gave me "No valid session found"

Anyone, please help ?

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=nd
AutomaticLogin=nd
TimedLoginDelay=30
DefaultSession=gnome

---

### Post by nd.trixiebunt on 2011-05-11
By the way, this issue happened while I was updating ubuntu (the usual updates). Then it crashed.

---

### Post by sikander3786 on 2011-05-11
Here is my gdm conf file.

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=username
TimedLoginEnable=true
TimedLogin=username
TimedLoginDelay=10

```

Replace username with your user name and place it in the gdm folder.

And yes, you can try re-installing gdm.

```
sudo apt-get install --reinstall gdm
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

The last 2 commands to make sure there are no broken packages.

---

### Post by nd.trixiebunt on 2011-05-11
1. I tried copying your conf file but still got the same message "No valid session found."

2. I also tried "sudo apt-get --reinstall gdm" and this is what I get:

nd@nd-desktop:~$ sudo apt-get install --reinstall gdm
[sudo] password for nd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gdm : Depends: udev (>= 166-0ubuntu4) but 162-2.2 is to be installed
 libdrm-dev : Depends: libdrm2 (= 2.4.23-1ubuntu6) but 2.4.21-1ubuntu2.1 is to be installed
              Depends: libdrm-intel1 (= 2.4.23-1ubuntu6) but 2.4.21-1ubuntu2.1 is to be installed
              Depends: libdrm-radeon1 (= 2.4.23-1ubuntu6) but 2.4.21-1ubuntu2.1 is to be installed
              Depends: libkms1 (= 2.4.23-1ubuntu6) but 2.4.21-1ubuntu2.1 is to be installed
 plymouth : Depends: libplymouth2 (= 0.8.2-2ubuntu22) but 0.8.2-2ubuntu5.1 is to be installed
            Depends: udev (>= 166-0ubuntu4) but 162-2.2 is to be installed
 plymouth-label : Depends: libplymouth2 (= 0.8.2-2ubuntu22) but 0.8.2-2ubuntu5.1 is to be installed
 plymouth-x11 : Depends: libplymouth2 (= 0.8.2-2ubuntu22) but 0.8.2-2ubuntu5.1 is to be installed
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-10
                              Depends: xserver-xorg-core (>= 2:1.10.0-0ubuntu1~) but 2:1.9.0-0ubuntu7.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by nd.trixiebunt on 2011-05-11
I finally got my box to reinstall gdm. Now, it stalls on splash screen. :(

---

### Post by sikander3786 on 2011-05-11
There were some unmet dependecy problems...

If there is not a lot of configurations/customizations involved, I would recommend to do a fresh install as it would be less effort and time consuming.

For backing up your important files, you can boot an Ubuntu Live CD and then mount your intended partition from the Places menu and copy over your data to a safe location.

For the files that don't let you copy without root access, you can press Alt + F2 from the Live Session mode and start nautilus as root.

```
gksudo nautilus
```

---

### Post by VAran22 on 2011-06-27
Hi guys!
I have Dell Vostro V13 laptop with "Ubuntu 10.10 desktop" on it, and exactly the same trouble that threadstarter had: no prompt to enter password on logon screen.
Maybe somebody can help me to find solution?
You can say, that fresh install might save my time, but what about others who can face same issue?
Once founded solution will help us all :)

I can successfuly login in recovery mode and launch xserver.
Reconfiguring or reinstalling gdm brings no effect :(
I don't know where to look and what else can I try? I'm a newbie :-[
What else information can I provide for you?
Appreciate any help.

---

