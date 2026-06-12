---
title: "Another &quot;low-graphics mode&quot; issue"
date: 2010-09-23
forum: General Help
---

### Post by JustGus on 2010-09-23
A few days ago I tried to boot up and got a message "Ubuntu is running in low-graphics mode...Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself"

When I click OK and select the first option, to run in low-graphics for just one session, it doesn't fully boot (the last line of text left on the screen says "Checking battery state...")

If I try select the option to reconfigure the graphics, it goes nowhere.  If I select "Restart X" the machine hangs on the subsequent dialogue box "Stand by one minute while the display restarts".  

I can however exit to console login.

I'm not particularly savvy with the Terminal, but have tried a few things, including "sudo apt-get updates", sudo apt-get install", which both seemed to run, but didn't change anything.  I've tried "sudo service gdm restart" which didn't work.  I've tried (re?)installing xserver-xorg, which didn't work either. 

Interestingly, whenever I enter the console, I get the message that there's 26 updates, including 18 security updates.  I would have thought this message would have disappeared after I ran sudo apt-get update and install and restarted the machine (which I've done several times since).  Don't know if that sheds any light on the problem.

I'd also read that issue with NVIDIA drivers have been associated with the problem, but I don't think I've got a graphics driver installed.  I think the only graphics capability is what's on the Asus P5G41T-M LX motherboard (I checked the itemised receipt for the machine, which was custom built about 4 months ago and I can't see a graphics card listed).

I'd be very grateful if anyone out there can point me in the direction of a solution.  I've been 3 days without my music and need my audio fix  :(

---

### Post by dino99 on 2010-09-23
which ubuntu is used ?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1398377](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1398377)

---

### Post by JustGus on 2010-09-23
> **dino99 said:**
> which ubuntu is used ?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1398377](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1398377)

10.4 Lucid.  I've also had a look online and it looks as though the mobo comes with Integrated Intel GMA X4500 graphics.

EDIT - 
Oh, or if you mean server or desktop, I *think* it's desktop.

---

### Post by JustGus on 2010-09-24
Can anyone help?  Pretty please.

---

### Post by JustGus on 2010-09-26
A few images from my monitor, with further info...in the hopes this could clarify the problem.
[IMG]http://i56.tinypic.com/25urtyo.jpg[/IMG]
[IMG]http://i52.tinypic.com/2dj5su0.jpg[/IMG]
[IMG]http://i51.tinypic.com/mi2i4k.jpg[/IMG]
As I mentioned earlier, despite running > sudo apt-get update and > sudo apt-get install I'm still seeing this last image, showing the 25 updates aren't installing.

---

### Post by JustGus on 2010-09-28
In case it helps anyone with this problem, this issue has been resolved.  For more info, checkout this link:
[http://ubuntuforums.org/showthread.php?p=9897778](http://ubuntuforums.org/showthread.php?p=9897778)

---

### Post by JustGus on 2010-10-22
In case it's of use to anyone who encounters a similar issue, I found (after getting lots of help) a solution, with the problems associated with mysql software. Further details [here]("http://forums.slimdevices.com/showthread.php?t=82338&page=4"), with details on the fix actually starting around post #40.

---

