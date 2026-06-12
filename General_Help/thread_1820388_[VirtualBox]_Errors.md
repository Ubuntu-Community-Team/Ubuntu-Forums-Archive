---
title: "[VirtualBox] Errors"
date: 2011-08-07
forum: General Help
---

### Post by AirSoma on 2011-08-07
I am trying to run VirtualBox on Ubuntu 11.04 Natty, and when I make a virtual machine it says it is successful. However when I try to run the machine I get this error box. [IMG]http://a2.sphotos.ak.fbcdn.net/hphotos-ak-snc6/262409_261210960572315_100000502408357_1013791_3383621_n.jpg[/IMG]
What did I do wrong? What can I do to fix this? I've deleted the virtual machine and made a new one. I've uninstalled and reinstalled virtualbox but nothing I've tried works. Please help.

---

### Post by lmarmisa on 2011-08-07
I recommend to use the version of VirtualBox of Oracle:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

If you install this other version, uninstall VirtualBox-OSE first.

---

### Post by AirSoma on 2011-08-07
Alright Alrgiht. Thanks, but bear with me now...How do I install the debian package?

---

### Post by lmarmisa on 2011-08-07
I recommend to follow the instructions for Debian-based Linux distributions of this page:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by AirSoma on 2011-08-07
Thank you, but now I have a new problem...heh [IMG]http://a8.sphotos.ak.fbcdn.net/hphotos-ak-snc6/198651_261235807236497_100000502408357_1013913_361163_n.jpg[/IMG]

---

### Post by lmarmisa on 2011-08-07
What Ubuntu version are you using?.

---

### Post by AirSoma on 2011-08-07
I am using 11.04 Natty. i386. I didn't have this problem back when I was on Maverick...

---

### Post by lmarmisa on 2011-08-07
Sorry. You told this detail in your first post. Try this command:

```

sudo apt-get install dkms

```

---

### Post by AirSoma on 2011-08-07
Haha alright. I am installing it as we speak. What next?

---

### Post by lmarmisa on 2011-08-07
If the packahe dkms was not installed, you could try to reinstall VirtualBox (use Synaptic for that). I thought that Ubuntu 11.04 included dkms. Maybe are you running xubuntu?.

---

### Post by AirSoma on 2011-08-07
It boots as Ubuntu...and I remember during the installation of the OS it said I was installing 11.04 Natty. It wasn't installed, but now it is.

---

### Post by lmarmisa on 2011-08-07
If your problem is solved, do not forget to add your user account to the user group vboxusers. Select System -> Admin -> Users and Groups -> Manage Groups -> vboxusers -> Add.

---

### Post by AirSoma on 2011-08-07
Oh it still has the second error box.. :(

---

### Post by lmarmisa on 2011-08-07
Reboot and try to run the proposed command:

```

sudo /etc/init.d/vboxdrv setup

```

Have you reinstalled VBox after the installation of dkms?.

---

### Post by AirSoma on 2011-08-07
Yes. When i run that command it says "/etc/init.d/... not a valid command"

---

### Post by lmarmisa on 2011-08-07
There is a space between vboxdrv and setup. Once you have installed dkms,  you could try to reinstall your current kernel using Synaptic. You can see the version of your current kernel typing the command:

```

uname -a

```

---

### Post by AirSoma on 2011-08-07
K it still didn't work... :( /etc/... isn't a command

---

### Post by lmarmisa on 2011-08-07
Use copy & paste. The command should work:

```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by AirSoma on 2011-08-07
It said >  musicly@musicly-Satellite-M505:~/Downloads$ sudo /etc/init.d/vboxdrv setup
[sudo] password for musicly: 
sudo: /etc/init.d/vboxdrv: command not found
 

---

### Post by lmarmisa on 2011-08-07
You can see the same command here:

```

luis@UB1010ZOTAC:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              
Error! There are no instances of module: vboxhost
4.0.12 located in the DKMS tree.
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS           [ OK ] 
 * Starting VirtualBox kernel modules                                    [ OK ] 
luis@UB1010ZOTAC:~$

```Did you install correctly VirtualBox?.

---

### Post by AirSoma on 2011-08-07
Maybe I didn't...I installed the debian package and uninstalled OSE virtualbox...

---

### Post by AirSoma on 2011-08-07
Nevermind! I got it to work. Thank you so much :)

---

### Post by lmarmisa on 2011-08-07
> **AirSoma said:**
> Nevermind! I got it to work. Thank you so much :)

Congratulations!!!. :-D

Could you give me some detail?.

Best regards,

Luis

---

### Post by zenben1126 on 2011-08-12
Hello, 

I've had some issues with vbox similar to this. I have installed the dkms package as well as the oracle vm full version (4.1). The problem is, though, that when I paste the /etc/init.d/vboxdrv setup command into the terminal, it says that the command is not found ^as stated by previous poster. Now on my home desktop this command worked fine and I had no issue installing vbox. But with the new vbox and the new laptop, it doesn't seem that the file /etc/init.d/vboxdrv exists. I am signed up as a user for vbox and still no success. Perhaps some assistance?

Thanks,
ben

---

