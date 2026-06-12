---
title: "Rdesktop &quot;Thin client&quot; redux."
date: 2009-09-29
forum: General Help
---

### Post by Beltaine on 2009-09-29
Ok, I've gotten Ubuntu Desktop running on our netbooks.

I've gotten rdesktop to successfully connect to our Windows Terminal Server.

What I need to know now is the following, in order of importance:

1. How do I make Ubuntu automatically execute my rdesktop command to connect to our terminal server when Ubuntu loads?

2. Can I make it run a script that starts rdesktop then shuts down the machine when the user logs out of and closes rdesktop?

3. How can I remove all non-essential applications, games, widgets and whatnot from my ubuntu installation? All it needs to do is run rdesktop with sound and usb support.

All of the above needs to be done on a bone-stock install from the .iso

---

### Post by Brandon Williams on 2009-09-30
Here's the first approach that comes to mind.

1. configure gdm for autologin of the correct user with no delay

2. setup the autologin user to use ~/.xsession as the session startup method; e.g.
```
echo "Session=default" > ~/.dmrc
```

3. create a ~/.xsession script for the autologin user that runs rdesktop with the appropriate arguments and then runs 'sudo halt' when rdesktop exits

4. set up sudoers to allow the autologin user to run halt without a password


Please post questions if you're not sure about any of the individual steps above, or if it just doesn't appear to work.

---

### Post by Beltaine on 2009-09-30
Yeah, I'm going to need more details on the steps above.

I'm Linux dumb.

Some of this may be going already? I've just used the default Ubuntu Jaunty desktop install.

It boots up and logs in automatically as a user called "Student" that was created during the install.

---

### Post by ubun_two on 2009-09-30
> **Beltaine said:**
> 
3. How can I remove all non-essential applications, games, widgets and whatnot from my ubuntu installation? All it needs to do is run rdesktop with sound and usb support.


You could start with this: [http://eeebuntu.org/index.php?page=base](http://eeebuntu.org/index.php?page=base)

---

### Post by Brandon Williams on 2009-09-30
I already specified the command line to user for step 2. If you look at that file now, it probably says "Session=gnome". You just want it to sat "Session=default" instead.

For step 3, create a file called ~/.xsession in the account of user "Student". It will look something like this:
```
#!/bin/sh
rdesktop ...
sudo halt
```
The line that says "rdesktop ..." should be the rdesktop command line that you would use to startup rdesktop in fullscreen mode. This script must be executable, so run this command after creating the file:
```
chmod u+x ~/.xsession
```

Step 4 is just to allow user Student to run the command /sbin/halt without entering a passphrase. Open /etc/sudoers by running the following command:
```
sudo visudo
```
and then add the following line to the end:
```
Student ALL=NOPASSWD: /sbin/halt
```
Save the file and exit.

Now, reboot the machine and see if it works.

In addition to the above, you might also have to configure the system so that it gets a dhcp address automatically, without requiring the network manager applet to be running. Do this by adding the following text to /etc/network/interfaces:
```
auto eth0
iface eth0 inet dhcp
```

This sample assumes that the device name of your network interface is eth0 and that it's an ethernet interface with a cable. If it's wireless, you will probably need to add a few more config setting to get it to work.

---

