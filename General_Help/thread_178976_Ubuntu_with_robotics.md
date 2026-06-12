---
title: "Ubuntu with robotics"
date: 2006-05-18
forum: General Help
---

### Post by eshubu on 2006-05-18
Here is my situation.  I have an embedded pc running Ubuntu that will be mounted on an autonomous robot platform.  The pc will be connected to a wireless router (also on the robot) and will run an ssh server.  I need to be able to have shell access to the computer by connecting to the router that is on the robot.  Since there will be no monitor on the robot, I need to be able to simply turn on the computer and have the ssh server start (the computer will be routinely turned on and off since it will be battery powered).  Is there anything special I need to do to be able have the ssh server start silently without having any user interaction (i.e logging in...)?

Also I would appreciate a description of what I need to do to get the ssh server up and running (installation, configuratation, starting / restarting the server etc.).  Thanks!

---

### Post by soce_32 on 2006-05-18
update-rc.d ssh 20 1 2

This command basically says update the rc.d links so that ssh will start early in the boot process for runlevels 1 and 2.

HTH

---

### Post by RFScheer on 2006-11-26
eshubu,

I'm working on a robomagellan autonomous robot and it sounds like we're probably covering some of the same ground, although hopefully you're much further along than I am.

Currently, I've installed player/stage/gazebo and am trying to install a python based control framework from pyrorobotics.org.  You'd think the python part would be the easy part but I'm struggling a bit with the install.

Anyway, get in touch if you want to cooperate or just share issues.

---

### Post by bee4 on 2007-04-26
I have had some problems with the installation of Gazebo, what are the minimum requirements to install Gazebo with a standard Graphics Environment? Because I have been a little confused! Thanks

---

