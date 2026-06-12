---
title: "bash:  No such file or directory"
date: 2011-09-19
forum: General Help
---

### Post by DancesWithRobots on 2011-09-19
A few weeks ago I installed ROS diamondback.  Part of the first tutorial configuration process is the creation of a bash script called setup.sh:

(from the ros beginner tutorials. This is for ros electric.  The diamondback instructions were the same except for the word "diamondback" instead of "electric")

> [B]mkdir ~/ros_workspace

[/B]Now create a bash script for configuring your ROS workspace environment. Create a setup file named setup.sh 

[B] #!/bin/sh 
 source /opt/ros/electric/setup.bash  
 export ROS_ROOT=/opt/ros/electric/ros
 export PATH=$ROS_ROOT/bin:$PATH  
 export PYTHONPATH=$ROS_ROOT/core/roslib/src:$PYTHONPATH
 export ROS_PACKAGE_PATH=~/ros_workspace:/opt/ros/electric/stacks[/B]

The above setup.sh adds the ros_workspace to your ROS_PACKAGE_PATH. 

Now source setup.sh:  

**. setup.sh**A week or so later, ros updated to electric, and I uninstalled the old package
Everything works, except, now whenever I open a terminal window I get the message 

**bash: /opt/ros/diamondback/setup.bash: No such file or directory**

I've researched bash and shell startup scripts, but I still can't figure out where whatever I have to change is.
Can someone point me towards a noob level explanation or tutorial that will get this error out of my terminal windows?

---

### Post by DancesWithRobots on 2011-09-19
OK, so I don't know why I was unable to find ~/bashrc, but, when I tried opening it directly into an editor, there it was and at the bottom was the line I needed to remove.  Also, the commands that caused my problem was actually a bit further back in the installation procedure:

**echo "source /opt/ros/electric/setup.bash" >> ~/.bashrc . ~/.bashrc**

---

