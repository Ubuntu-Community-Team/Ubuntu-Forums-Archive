---
title: "Mic not working"
date: 2011-03-25
forum: General Help
---

### Post by J_Wales on 2011-03-25
My mic isn't working in ubuntu10.10. I tried  just testing it in ubuntu and no sound comes out. All I here is static  when I raise and lower the mic output volume under sound  options/preferences. I tried changing around the audio type but nothing. I get sound from playing videos and when ubuntu loads, so my output works fine.  Any ideas?

---

### Post by luceerose on 2011-03-25
I would open either alsamixer or gnome-alsamixer (if installed) & check the 'mic boost' settings.
I don't know if that will help you. It's just a wild stab in the dark.

---

### Post by J_Wales on 2011-03-25
No, unfortunately.
I have an asus p5gv-mx motherboard which uses the ADI AD1986A audio. The output works fine but I get nothing on microphone/input. Anyone know what i can do?

I tried downloading the drivers from asus/linux version, but I really have no idea how to install it. I read the installation guide the provided. Extracted to a temp directory in my home folder. ran per installation guide 
./configure
make
make install

all i got was a wall of text confirming something happened on all cmds but with a lot of errors. So obviously it didn't install correctly. I'm familiar with PC hardware but, I'm a total noob at this so I really don't know what to do.

I retried using sudo but the same thing.

Any ideas?

---

### Post by luceerose on 2011-03-25
Ok, I didn't even know Asus had Linux drivers on their site. I'm having a problem with an Asus M4A89TD board where I can't any output other than the front channel working.
So, I'll get onto those drivers & let you know how I go installing them.

---

### Post by luceerose on 2011-03-25
Sorry, no such animal for my motherboard.
The download I got from the Asus site is a .zip file & It's contents - 1 .txt file.
The following is the entire contents of the text file;
"Note: Please update to the latest Linux Kernel for motherboard chipset and components support."

---

### Post by J_Wales on 2011-03-25
It must mean your board is pre-canned support in most linux flavors. My board works fine except the stinking mic. You can also look up the hardware and go directly to the chipset manufacture for drivers.

---

