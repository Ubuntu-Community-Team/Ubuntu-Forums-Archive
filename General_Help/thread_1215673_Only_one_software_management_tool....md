---
title: "Only one software management tool..."
date: 2009-07-17
forum: General Help
---

### Post by JTmas on 2009-07-17
Hello folks,

I've just started using Ubuntu 9.04 -Jaunty Jackalope, being a long time OS X user, and sick of windows running on my older laptop. 

So first thing I had to do was download Flash Player 10, and Skype. Flash Player downloaded fine, I double clicked on the .deb file to install it, and got an error message.
> [B]
Only one software management tool is allowed to run at the same time[/B]

Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first.Since this is the first .deb package I've launched, and since previous to this I haven't had any other windows such as Update Manager, I'm puzzled as to what it could be. To be sure it wasn't just some sort of problem with the installer, I ran the skype.deb one too, but it gave the same error.

Now I'm a complete Ubuntu Newbie, but I've had loads of tech experience with Windows and OS X.

Any Ideas?

---

### Post by TeoBigusGeekus on 2009-07-17
Perhaps the update manager was working in the background - checking for updates.
Have tried again?

---

### Post by michy99 on 2009-07-17
There are several software managements tools: Synaptic Package Manager, Add/Remove, Gdebi, Update Manager, aptitude, apt-get. Only one of these can run at a time.

---

### Post by JTmas on 2009-07-17
> Perhaps the update manager was working in the background - checking for updates.
Have tried again? 	

Yeah, tried again, rebooted, tried once more, and still the same error.

> There are several software managements tools: Synaptic Package Manager, Add/Remove, Gdebi, Update Manager, aptitude, apt-get. Only one of these can run at a time.

Yeah, I assumed it could have been something like that, so I ran System Monitor, and as far as I can see, none of those mentioned are there....

---

### Post by michy99 on 2009-07-17
Do you get an error if you run this from a terminal?```
sudo apt-get update
```

---

### Post by JTmas on 2009-07-17
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


And so I ran that, and then got:

> Setting up hddtemp (0.3-beta15-45) ...

Processing triggers for python-support ...
Setting up nullmailer (1:1.04-1.1) ...
 * Starting mail-transfer-agent:                                         [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


And now, I am truly confused.

---

### Post by ddrichardson on 2009-07-17
Dpkg is run by aptitude and actually installs packages.  As it said it was interrupted, when it runs it places a file in /var/tmp/lock that stops other package managers running, because it exited abnormally, that file is still there.  Running the command given makes all installed packages re-configure and removes (hopefully) any issues.

ldconfig is _always_ deferred until last, otherwise it would be run after each package and would take forever.

You should now be able to double click your deb file.

---

### Post by michy99 on 2009-07-17
Run```
sudo apt-get update
``` again and see if you get errors this time.

As to installing software, installing through the repositories is usually the best way to go. Here's an overview of installing software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ddrichardson on 2009-07-17
Its also well covered in Help.  Skype is not available in the repositories AFAIK.

---

### Post by JTmas on 2009-07-17
ddrichardson, Thank you so immensely much. Both Flash Player 10 and Skype are now installed and running fine. 

Once again, thanks.

---

### Post by ddrichardson on 2009-07-17
No worries, as the chap above is getting at, using the repos is advantageous as it provides automatic updating.

---

