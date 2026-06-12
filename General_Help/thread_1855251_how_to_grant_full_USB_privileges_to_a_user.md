---
title: "how to grant full USB privileges to a user?"
date: 2011-10-05
forum: General Help
---

### Post by bcrowell on 2011-10-05
How do I grant full privileges to a user to do whatever they want to do to USB devices? For example, I have software ( [https://github.com/bcrowell/freelab](https://github.com/bcrowell/freelab) ) that needs to claim a USB interface, and I get this error:

```
/usr/lib/ruby/1.8/usb.rb:401:in `usb_claim_interface': Operation not permitted - usb_claim_interface (Errno::EPERM) from /usr/lib/ruby/1.8/usb.rb:401:in `claim_interface' from ./vernier.rb:246:in `initialize' from -e:1:in `new' from -e:1
```

Can I do this by editing /etc/group? By doing something with udev? This post [http://ubuntuforums.org/showthread.php?t=1851620](http://ubuntuforums.org/showthread.php?t=1851620) describes a failed attempt to do it with udev; I don't know anything about udev, and just based that attempt on what I found by googling.

This is on lucid.

Thanks in advance!

---

### Post by mikejonesey on 2011-10-05
i'd do this in the fstab if it prooved to every be a problem for me, but I've never had a problem with usb permissions before...

just add a line with no auto and user priv so user can mount and it wont auto mount at boot (cause it wont be there)...

---

### Post by bcrowell on 2011-10-05
Thanks for the reply -- but it isn't a device with a filesystem on it. It's an interface to a sensor.

---

### Post by mikejonesey on 2011-10-05
blowing all security out the window...

edit the /etc/sudoers file to enable user to run your prog or whaterver uses the interface without a password, you can then setup an alias to call the sudo so the commands run the same...

ps... obviously make the binary read and execute only to regular users for some security...

---

### Post by JKyleOKC on 2011-10-05
Try adding the user to the "plugdev" group, which is GID 46 on my Lucid system. You can do this by using the GUI's user administration tools (I use Xubuntu which has a different GUI than plain Ubuntu) or by editing the /etc/group file with sudo privilege as you prefer...

---

### Post by mikejonesey on 2011-10-05
for [JKyleOKC]("http://ubuntuforums.org/member.php?u=374258")'s suggestion;

```
sudo usermod -a -G plugdev USERNAME
```

---

### Post by bcrowell on 2011-10-05
Aha! Thanks, folks, I'll try that.

---

### Post by bcrowell on 2011-10-06
Thanks, all, for the help!

Adding the user to the plugdev group did not turn out to help. The solution using the sudoers file did work. I would prefer not to have to do it that way, for security reasons, but if that's the way it is, at least it works :-)

---

### Post by wt8008 on 2011-10-06
I was reading this thread [http://ubuntuforums.org/showthread.php?t=880550](http://ubuntuforums.org/showthread.php?t=880550)

and someone did say they had to have write permissions on the particular device in /dev/bus/usb to be able to claim it.

---

### Post by bcrowell on 2011-10-07
Thanks, wt8008, changing write permissions could be a much better solution.

---

