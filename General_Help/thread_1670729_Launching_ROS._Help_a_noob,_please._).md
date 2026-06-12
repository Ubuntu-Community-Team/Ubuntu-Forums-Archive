---
title: "Launching ROS. Help a noob, please. :)"
date: 2011-01-19
forum: General Help
---

### Post by Squiggler on 2011-01-19
Let me start by saying this is my second day using Ubuntu and I'm having trouble with just one program.
I can't seem to launch ROS.  I know where it is, but I don't know the name of the directory or how to launch it.  Can anyone help?  It's probably really simple, but ti's been frustrating me for a few hours. 
Please help! :)

---

### Post by Fire_Chief on 2011-01-19
Can you give a little more description please? What kind of application is ROS?
You mentioned that you know where it is but don't know the name of the directory? This seems contradictory since if you know where it is then you know the name of the directory containing the application.

The more info you can provide, the faster we can get to a resolution. :)

Cheers!

---

### Post by Fire_Chief on 2011-01-19
Oops...double posted :(

---

### Post by Squiggler on 2011-01-19
ROS is a robot operating system (aptly named).  I'm trying to launch the interface but I can't seem to get it.
If I browse my HDD It's located in opt/ros/cturtle  From there I don't know what I'd be looking for, and as I'm new to Ubuntu I don't know how to find that directory through the terminal.
I've found roslaunch, but again, I'm not sure how to put that into the terminal.

---

### Post by Fire_Chief on 2011-01-19
From a Linux command line, you can run applications by specifying the path to the executable (including the name of the application).

The important part to note here is that you can start an application from anywhere if you use the full path when you want to start the program.
If your ROS executable is named ROSLaunch and is in the /opt/ros/cturtle directory, then to start it, you would give the path to the application.
```
/opt/ros/cturtle/ROSLaunch
```


If you happen to already be in the /opt/ros/cturtle directory, you can just use a local path to start the application. ```
./ROSLaunch
```

There are several directories in the filesystem that have most of the programs you use on a linux system. Most often, these directories are included in a system variable called the PATH. The path variable allows you to run a program without having to give the full path each time you want to run it. Several examples include the commands ls, pwd, chmod, and mv. It feels like these commands are built-in but really, the directories which contain these applications are simply in the PATH.

You can modify the PATH variable to suit your needs. It is stored per user. To see what your PATH currently has defined:```
echo $PATH
```
To add new directories to your PATH:```
PATH=$PATH:/new/directory/target/location
```
Where the directory location has the applications you want to run.

Lastly, a file is considered executable if it has the execute bit set on it. If your terminal shows you different colored files, typically a light green colored file is executable. The other way to confirm that a file is executable is to do an ls command on the file and look at the details. This page explains the details on this quite well. [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

Cheers!

---

