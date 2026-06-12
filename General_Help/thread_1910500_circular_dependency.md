---
title: "circular dependency"
date: 2012-01-17
forum: General Help
---

### Post by Penny_vdr on 2012-01-17
Hi,

I have only one package that I have created in ROS , I checked my manifest file and there is nothing wrong, the package depends on rospy, roscpp, and std_msgs. The command line roswtf just tells me that there is a circular dependency, nothing else, how can I fix this error? Is there a problem with the fact that we are 5 users on the computer and we all share ROS and its files?

---

### Post by Zill on 2012-01-17
> **Penny_vdr said:**
> Hi,

I have only one package that I have created in ROS , I checked my manifest file and there is nothing wrong, the package depends on rospy, roscpp, and std_msgs. The command line roswtf just tells me that there is a circular dependency, nothing else, how can I fix this error? Is there a problem with the fact that we are 5 users on the computer and we all share ROS and its files?
Welcome to Ubuntu forums.

Firstly, I am not familiar with ROS so maybe others will be more helpful.  However, as a starting point, I suggest it would be useful if you gave more information.

Presumably, you are running an Ubuntu system so please advise exactly which release you are using.

Generally, circular dependency errors occur when trying to install packages individually.  The apt-get system used by Ubuntu should resolve circular dependencies if all dependant packages are installed by a single command.  eg.
```
sudo apt-get install package1 package2 package3 etc.
```
Please try to install all relevant packages together and then post the output, with any error messages, back here.

ps.  I doubt if the number of users is at all relevant to dependency problems.

---

### Post by Neill_R on 2012-01-17
[LIST]
[*][Documentation]("http://www.ros.org/wiki/Documentation?action=fullsearch&context=180&value=linkto%3A%22Documentation%22")
[/LIST]
   
 
    **Wiki**

  
[LIST]
[*][ROS]("http://www.ros.org/wiki/ROS")
[*][StackList]("http://www.ros.org/wiki/StackList")
[*][RecentChanges]("http://www.ros.org/wiki/RecentChanges")
[*][Documentation]("http://www.ros.org/wiki/Documentation")
[/LIST]
  
  **Page**

 
[LIST]
[*]Immutable Page
[*][Info]("http://www.ros.org/wiki/Documentation?action=info")
[*][Attachments]("http://www.ros.org/wiki/Documentation?action=AttachFile")
[*]                                                           
[/LIST]
  
  **User**

 
[LIST]
[*][Login]("http://www.ros.org/wiki/Documentation?action=login")
[/LIST]
 
 
    *ROS  (Robot Operating System) provides libraries and tools to help software  developers create robot applications. It provides hardware abstraction,  device drivers, libraries, visualizers, message-passing, package  management, and more.  ROS is licensed under an open source, BSD  license.*

---

