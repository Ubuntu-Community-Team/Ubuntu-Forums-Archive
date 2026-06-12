---
title: "Unable to install Startup disk  Creator"
date: 2010-09-27
forum: General Help
---

### Post by rmcellig on 2010-09-27
I am running 10.0.4 and am having problems installing Startup Disk Creator. what can I do to resolve the problem?

---

### Post by mikewhatever on 2010-09-27
It's a pity you didn't hit the +Details button. Can you do that.

---

### Post by hrickh on 2010-09-27
> **rmcellig said:**
> I am running 10.0.4 and am having problems installing Startup Disk Creator. what can I do to resolve the problem?
See the "+ Details" in your screencap? Click on it and it will tell you exactly what's gone wrong.

R.
==

---

### Post by rmcellig on 2010-09-27
When I do that, this isall I see:

usb-creator-gtk

What does  this mean?

---

### Post by C.S.Cameron on 2010-09-27
Are you sure that Startup Disk Creator is not already installed?
Look under System/Administration/Startup Disk Creator

---

### Post by rmcellig on 2010-09-27
I checked under System/Administration and it's not there. Is there any way of checking from the terminal?

---

### Post by mikewhatever on 2010-09-27
usb-creator-gtk should be installed by default. What's the output of 
**sudo apt-get install usb-creator-gtk**
?

---

### Post by rmcellig on 2010-09-27
This  is  what I see:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  usb-creator-gtk: Depends: usb-creator-common (= 0.2.22.1) but it is not going to be installed
E: Broken packages

---

### Post by C.S.Cameron on 2010-09-27
To launch usb-creator from terminal type:
```
usb-creator-gtk
```

---

