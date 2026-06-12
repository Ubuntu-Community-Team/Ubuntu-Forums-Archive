---
title: "Quick question- typing issues"
date: 2010-02-10
forum: General Help
---

### Post by radtek on 2010-02-10
Hi all-

Just a quickie question and I know it'll be easily solved.

**When I type on my laptop I keep losing the cursor to another part of the sentence, paragraph or page.**

I know there's [COLOR="Blue"]a way to disable the touch-pad while typing[/COLOR] but for the life of me I can't find it or remember where I read how to do it.

Could someone please help?

TIA

radtek

---

### Post by audiomick on 2010-02-10
If there is nothing in
System> preferences 
to change it, look at this
[http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

---

### Post by jamesisin on 2010-02-10
I found this through Google:

[http://www.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/](http://www.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/)

There were several related results (search terms: ubuntu disable touchpad).

---

### Post by radtek on 2010-02-10
Thanks Guys!

I also found this:

```
Touchpad

The AAO touchpad is quite easy to bump whilst typing. 
The best fix is to disable all scroll and tap commands for 1 second after each keystroke.

Go to Preferences and select "Sessions". Click the add button and add an entry:

[CODE]Name: Syndaemon
Command: syndaemon -d -t -i 1
Comment: Disable trackpad while typing

```
The '1' can be changed to any decimal number, 
and defines the amount of time to lock the trackpad after each keystroke. 
See the Syndaemon man page for full details.[/CODE]

I'll be looking into it!! Obviously, that is for the Acer but it gives some good pointers with Syndaemon.

---

### Post by jamesisin on 2010-02-10
Probably you can clean up the arguments:

```
syndaemon -dti 1
```

---

### Post by radtek on 2010-02-10
All that stuff isn't working for me.

```
radtek@radtek-laptop:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?
radtek@radtek-laptop:~$ syndaemon -d -t -i 1
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
radtek@radtek-laptop:~$ synclient TouchPadOff=1
Can't access shared memory area. SHMConfig disabled?

```

Think it's running under HAL and not xorg.conf

---

### Post by jamesisin on 2010-02-10
Sounds like you need to use sudo:

```
sudo syndaemon -dti 1
```

---

### Post by radtek on 2010-02-10
I tried that earlier. No luck.

```
radtek@radtek-laptop:~$ sudo syndaemon -dti 1
[sudo] password for radtek: 
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
radtek@radtek-laptop:~$ 

```

---

### Post by jamesisin on 2010-02-11
In the article I linked above it says to use simply:

```
syndaemon -d
```

Test that and see if that works.  If it does than we can sort out those other arguments later.

---

### Post by radtek on 2010-02-11
Sorry....:confused:

```
radtek@radtek-laptop:~$ syndaemon -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
radtek@radtek-laptop:~$ sudo syndaemon -d
[sudo] password for radtek: 
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
radtek@radtek-laptop:~$ 

```

Gee. This lappy has been great with the later distros. With edgy I had some config problems- mainly with wireless and sound. The peripherals all seem to run off of hardwired usb. Maybe this is the problem. Probably not...

Ran **lshw** but didn't see anything about "input".

This isn't a big deal that *has to be done*, but becoming more of a mystery LOL.

---

