---
title: "Permission"
date: 2011-04-27
forum: General Help
---

### Post by Don DeGregori on 2011-04-27
Running 10.10

I have 2 ifconfig bash scripts that work from command line.
First one called internetup and other internetdn

#!/bin/bash

sudo ifconfig eth0 down
sudo ifconfig eth0 up

and 

#!/bin/bash

sudo ifconfig eth0 down

I really need the first one for the EB1007 computer will not bring the net card up automatically. I have never seen this before. Using 10.10 on other boxes with no problem. So, I need to do it manually and click an icon in top panel. I made such an icon, but doesn't work.

On terminal, I do sudo ./internetup  This works. I guess I need a script that asks for root password and then continue with the internetup portion. Is there another easier way, for the computer is for a non-Linux friend, and surely does not want to run a script just to get connected!
donde

---

### Post by michaelb28 on 2011-09-01
Is eth0 set to auto in /etc/network/interfaces?

---

