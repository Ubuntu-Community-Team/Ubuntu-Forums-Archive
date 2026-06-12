---
title: "New to linux trying to use Ubuntu 9.10"
date: 2010-04-02
forum: General Help
---

### Post by bekor on 2010-04-02
Hi, I am new .and trying to use Ubuntu for the first time.I have an older machine.It is a Dell Latitude c800.I have a ATI Technologies, Inc. Rage Mobility M4 video card,and I can not find a driver for it.Do I need the driver for my videos to work right?Is their some alternative root I can take if their is no available driver in Ubuntu?

---

### Post by NightwishFan on 2010-04-02
Hello and welcome to Ubuntu Forums!

Ubuntu includes an open source ATI driver. Try Ubuntu from the live CD and see if your video card works. ;)
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Chances are it will just work.

---

### Post by c3ntur10n on 2010-04-02
yap! that is the first thing i did, i tried the live cd first... everything is working great with my laptop, now i'm using ubuntu for the first time. :)

---

### Post by NightwishFan on 2010-04-02
Good, then it should work out for you if display performance was appropriate from the live cd. Did you notice if you had desktop effects by any chance?

If you have any other questions please feel free to ask me.

Here are some links for Ubuntu beginners.
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by bekor on 2010-04-03
> **NightwishFan said:**
> Hello and welcome to Ubuntu Forums!

Ubuntu includes an open source ATI driver. Try Ubuntu from the live CD and see if your vid eo card works. ;)
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Chances are it will just work.

hi, i  am not sure what you mean.Are you saying it will work if i boot from the cd?is that the only way i can have a working video card or does  it repair my non-working problem.be patient with me i am new and have little understaning yet.

---

### Post by NightwishFan on 2010-04-03
Did you already try Ubuntu and it did not work? I as assuming you were wondering about hardware compatibility. If it does not work, check the restricted drivers manager (System -> Administration -> Hardware Drivers) inside Ubuntu to see if you have a driver available.

You can use the live cd (which runs on its own without installing, like a test drive) and see if your video works or not from there.

---

### Post by lidex on 2010-04-04
Can you post the output of this command:
```
lspci -nn | grep VGA
```

Use the terminal: "Applications>Accessories>Terminal"

---

### Post by 3rdalbum on 2010-04-04
> **bekor said:**
> Hi, I am new .and trying to use Ubuntu for the first time.I have an older machine.It is a Dell Latitude c800.I have a ATI Technologies, Inc. Rage Mobility M4 video card,and I can not find a driver for it.

There is exactly one driver for that graphics card - and it's included with Ubuntu and enabled by default. In other words, problem solved - there's nothing more you need to do!

---

### Post by Dayofswords on 2010-04-04
found the computer full spec sheet

[http://support.dell.com/support/edocs/systems/latc800/en/ug/specs.htm](http://support.dell.com/support/edocs/systems/latc800/en/ug/specs.htm)

just so you guys know

standard(from oem) ram is 64mb, thats not enough for ubuntu

---

