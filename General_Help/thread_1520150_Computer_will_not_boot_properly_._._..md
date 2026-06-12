---
title: "Computer will not boot properly . . ."
date: 2010-06-29
forum: General Help
---

### Post by ThePossum on 2010-06-29
Tried restarting my netbook with Karmic on it this morning.  Got the login screen and an error message as follows:

Install Problem
The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your computer Administrator.

Then when I click on my user name the system just comes back to the login screen and the same error message.  Does this each time I try to login.  Can't get it to boot.

---

### Post by justleen on 2010-06-29
go into a terminal (ctrl-alt-F2), and login in there.
See if you can reinstall the package
```

sudo apt-get install --reinstall gnome-power-manager 
```

---

### Post by kalistona on 2010-06-29
justleen, can you explain why i have had the same problem when on ubuntu 9.1, on usb,
**after update**s the same messages was appeared ?
before, all was ok.
thank you for your answer, i would like to know where was the problem.

---

### Post by justleen on 2010-06-29
The error message says it has problems with its config.
reinstalling or reconfiguring the package _should_ restore this default config.

reconfig:
```

sudo dpkg-reconfigure  <package-name>

```

---

### Post by kalistona on 2010-06-29
thank you.

---

### Post by ThePossum on 2010-06-29
> **justleen said:**
> go into a terminal (ctrl-alt-F2), and login in there.
See if you can reinstall the package
```

sudo apt-get install --reinstall gnome-power-manager 
```

Thanks,

Now how do I get to the terminal if the machine will not boot?  Just use the ctrl-alt-F2 while it is booting?

---

### Post by ThePossum on 2010-06-29
Got to the terminal and used the command that you suggested.  Got the following message

It seemed to be working and it came to the following line

[I]Need to get 1,101kB of archives  Do you want to continue?

[/I]I said y and hit enter and go the following

[I]Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main gnome-power-manager 2.30.0-0ubuntu1
Could not resolve 'us.archive.ubuntu.com
Failed to fetch [http://us.archive/ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.30.0-0ubuntu_i386.deb](http://us.archive/ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.30.0-0ubuntu_i386.deb)
Could not resolve 'us.archive.ubuntu.com
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/I]Sounds to me like[I] it is not connected to the internet with the built in wireless feature and my wireless network.  I am quite a bit lost on this can anyone help me out?
[/I]

---

### Post by ThePossum on 2010-06-29
Got the computer hooked to the internet.  Ran the command you gave me to reinstall the gnome-power-manager and it seemed to work as it brought me back to the command prompt.

Shut the netbook down and restarted and still get the same error message at the login screen about the gnome-power-manager being install incorrectly.

Is there any hope other than a reinstall of karmic.  I hope I don't need to do that.

---

### Post by ThePossum on 2010-06-29
Can anyone help with my problem?  Please!

---

### Post by ThePossum on 2010-07-07
I got this problem fixed.  Seems that my HD was full.  Once I went to the terminal and deleted a directory with a few music file in it I was able to reboot the computer.

Thanks for the suggestions guys.

---

