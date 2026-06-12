---
title: "Velleman k8055 USB permissions help"
date: 2011-01-05
forum: General Help
---

### Post by captomner on 2011-01-05
I recently assembled a Velleman k8055 kit. I installed this library:

[http://libk8055.sourceforge.net/]("http://libk8055.sourceforge.net/")

I can control the kit by running the included command line tool as sudo, but I don't know enough about udev to change the permissions. I'd like to set access for everyone (or at least for me) to be read/write.

I tried following the advice in this post, but no luck:
[URL="http://www.uluga.ubuntuforums.org/showthread.php?t=1342955"]
http://www.uluga.ubuntuforums.org/showthread.php?t=1342955[/URL]

I have found a few references to pages discussing this topic, but they're either out of date or broken links. If I missed another thread on this topic, I apologize, but I sure looked!

---

### Post by SteveDee on 2011-01-05
Have you successfully created a "k8055" group by adding the Velleman.rules file to the /etc/udev/rules.d directory?

---

### Post by captomner on 2011-01-05
Wow, that was much easier than I expected. It worked great. Thanks for the help.

If you're willing, I'd like to understand how the permissions work a little better- why does adding this file fix it?

Thanks again!

---

### Post by SteveDee on 2011-01-06
I'm glad you got it working. My only experience with the K8055 was 3 or 4 years ago when I created a test rig to test an auto-weighing machine. I wrote the software for Windows using VB. I thought about buying one for myself recently to "play" with on Linux. What are you doing with yours?

I know next to nothing about udev, except that it is the current device manager for Linux. I just downloaded the K8055 package that you have, and read the README file. The velleman.rules file specifies a new group ("k8055") and sets permissions to 660, which basically means that group members have read/write access to the device/files needed to control the K8055.

Linux "users" can only access or run files: 1) that they own, 2) where they belong to the file's group, or 3) where access is granted to "other".

If you open a terminal window and type:-
```

ls -l

```
...you should see output like this, with permissions displayed as rwx:-
```

-rwxr-xr--  1 steve family         193 2010-11-05 21:08 SilverSurfer.sh
-rw-r--r--  1 steve family           0 2010-11-24 21:16 webcam_shot.png

```
...so for the SilverSurfer.sh file, -rwx part means that the owner (steve) can read, write & execute the file (a script).
The r-x bit means any member of the group (family) can read or execute the script.
And finally, the r-- means that any other user can only read the file.

These permissions can be represented as a binary or decimal number, where each group of 3 is a digit. So:-
rwx r-x r-- is binary: 111 101 100, which is 754

There are plenty of good explanations on file & device permissions. I suggest you take a look at this: [http://dsl.org/cookbook/cookbook_9.html](http://dsl.org/cookbook/cookbook_9.html)  (...or maybe someone can suggest alternatives).

As for udev, you could start with this: [http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev) ...and if you are still interested, check out the links at the bottom of that page.

I hope this helps.

---

### Post by captomner on 2011-01-20
Thanks for the great detailed response! Sorry I didn't respond sooner- I thought I was subscribed to the thread but apparently I wasn't.

I'm not entirely sure what I'm going to do with it yet. I am thinking something along the lines of home automation and/or security, although it might not be perfectly suited for the latter. For now, I am trying to figure out how to write a daemon that will perform output functions when it receives an input.

My wife bought me the kit- I probably wouldn't have tried to tackle it unless it was placed in front of me, but I'm glad I am working on it now. I'm teaching myself C++ and figuring out the hardware side of wiring up relays, but I'm learning a lot through trial and error. I'm hoping I'll come up with a more concrete idea of what I want to do after I am more comfortable with the programming.

What are you thinking about using yours for?

---

### Post by SteveDee on 2011-01-24
> **captomner said:**
> ...My wife bought me the kit...What are you thinking about using yours for?

Well, having just failed in my plan to capture video via 2 Ezcaps connected to an old computer ([http://ubuntuforums.org/showthread.php?t=1672938](http://ubuntuforums.org/showthread.php?t=1672938)), I've decided to get an assembled K8055 and use it to switch between cameras.

This may sound like "...a sledge hammer to crack a nut..." but hey! my wife couldn't think what to get for my birthday!

I have a headless pc (on a wifi network) in the garage monitoring a robin's nest via "motion". Recordings are accessed by avi files over the network, live video can be viewed via Firefox, and the pc can be controlled via VNC.

I now need to be able to remotely switch between cameras. This could be done via a printer parallel interface (which this pc does NOT have) but I would still need to construct a circuit with a relay and driver.

Using the K8055 will give me additional options, so I am considering using the A-D inputs (with bead thermistors) to monitor nest box temperatures, and maybe a couple of digital outputs to control lighting.

But I won't be using the same programming language as you, as I promised myself never to look at another line of C++ code after slipping into semi-retirement 2 years ago.

I much prefer the quick-fix RAD languages like VB, Delphi and (for Linux) Gambas.

---

### Post by SteveDee on 2011-01-29
> **SteveDee said:**
> Have you successfully created a "k8055" group by adding the Velleman.rules file to the /etc/udev/rules.d directory?

Hi captomner,
although my suggestion in post #2 seems to have solved your permissions problem, it did not work for me. In fact I turned my pc on the following day and was completely baffled to find the system would not boot.

On a Lubuntu system I could reach the login screen, but it would keep asking for name/password. On Ubuntu I couldn't even get that far.

**Removing Velleman.rules solves that problem, and I can use the k8055 as root. So I wonder how your install procedure differs from mine?**

This is what I did:-
> 
 * install libusb-dev via Synaptic
 * download libk8055
 * Added velleman.rules to: /etc/udev/rules.d directory
 * in libk8055 makefile; change "PREFIX = ?/usr/local" to "PREFIX = /usr/local"
 * in libk8055/src folder run:-
 * make all
 * ...then...
 * sudo make install

I think I also manually created a "k8055" group at some point, but this did not help.

I'm not too impressed with the initial performance using libk8055. When I ran some simple Gambas code to control the k8055, the cpu usage was very high. So I just ran this from a terminal:-
```

sudo k8055 -p:0 -num:20 -delay:500

```
...which resulted in about 90%cpu on my 1.4GHz laptop.

When/if time permits, I'd like to look at: [http://sourceforge.net/projects/k8055d/](http://sourceforge.net/projects/k8055d/)
...and also try to get the Velleman VB code running under Wine, at least to compare %cpu figures.

---

### Post by Jafo1957 on 2011-02-01
Hello SteveDee,
I had exactly the same problem after the same operation.
And ofcourse, I had to remove the velleman.rules to have my laptop properly working again.
I would like to spend some time on analyzing this velleman.rules to see if there's something that may cause the machine to hang-up.
Maybe there's another way to grant permissions for the k8055 to regular users ?

---

### Post by SteveDee on 2011-02-02
> **Jafo1957 said:**
> ...I would like to spend some time on analyzing this velleman.rules to see if there's something that may cause the machine to hang-up....

OK, here is an alternative to the velleman.rules file which seems to work for me:-
```

# udev rules file for Velleman K8055 USB Experiment Interface Board
# from: http://www.clan-elite.info/forum.asp?action=view_thread&id=896

SUBSYSTEMS!="usb", ACTION!="add", GOTO="k8055_rules_end"

# The K8055 device, including all jumper configurations             
ATTRS{idVendor}=="10cf", ATTRS{idProduct}=="5500", GROUP="k8055", MODE="0660"
ATTRS{idVendor}=="10cf", ATTRS{idProduct}=="5501", GROUP="k8055", MODE="0660"
ATTRS{idVendor}=="10cf", ATTRS{idProduct}=="5502", GROUP="k8055", MODE="0660"
ATTRS{idVendor}=="10cf", ATTRS{idProduct}=="5503", GROUP="k8055", MODE="0660"

LABEL="k8055_rules_end"


```

This should allow you to run commands in a terminal like this:-
```

k8055 -p:0 -num:25 -delay:500

```

So it looks like the answer is to specify the Group & Mode for each of the 4 possible board numbers.

I'm still concerned about the cpu% load when polling the device using the command above, but I guess it is just only an "experimenters board".

---

### Post by Jafo1957 on 2011-02-03
@SteveDee :

>  OK, here is an alternative to the velleman.rules file which seems to work for me:-...Running flawlessly for me too !
Now I can go on installing the graphical interface and continue testing.

I would like to use this card only for experiments,
More professional material is a lot better but also pretty expensive, like the cards sold by

[ http://www.decision-computer.de/default-e.html]("http://www.decision-computer.de/default-e.html").

These are good quality, I used them before for automation applications. Don't know if those are also available in the UK, but there surely are other alternatives.

Thank you for your help !  

      ):P

---

