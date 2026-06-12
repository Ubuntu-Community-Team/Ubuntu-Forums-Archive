---
title: "Santa Claus Detection System"
date: 2010-12-19
forum: General Help
---

### Post by SteveDee on 2010-12-19
Does Father Christmas really come down your chimney on Christmas Eve and deliver all those presents? There's only one way to find out...

In less than 10 minutes (by following 10 easy steps) you can install, configure and run your own Santa Claus detector using the excellent application "motion". This will allow you to capture video clips on a host machine, which also acts as a live webcam server for other computers on your network.

So if you have a webcam attached to your computer, let's go!

1. Run Synaptic Package Manager, search for "motion" and install it.
2. Using your file manager, create a new directory to store your captured video (e.g. /home/steve/motionVideo).
3. Also create a new hidden directory called ".motion" (e.g. /home/steve/.motion) for your configuration file.
4. You now need to run your file manager as root (see note below), navigate to /etc/motion, and copy the motion.conf file to the .motion hidden folder in your home directory (e.g. /home/steve/.motion/motion.conf)
5. Change permissions for this new copy of motion.conf for user "Other" to "Read and Write".
6. Open this file in a text editor, and search the file for "target_dir" and change location to suit (e.g. target_dir /home/steve/motionVideo)
7. Search the file again for "webcam_motion" and change this to "webcam_motion on"
8. Search the file for "webcam_localhost" and change this to "webcam_localhost off"
9. Open a terminal to run motion by typing:-
```
 motion -n 
```
10. Open your web browser and enter the local address and port: [http://127.0.0.1:8081](http://127.0.0.1:8081)

You should now be able to see a jerky video image through your webcam. You can also view this remotely by opening a web browser on a networked computer and entering the IP address & port of the host machine (e.g. [http://192.168.0.99:8081](http://192.168.0.99:8081)).

To stop the motion app, just use <ctrl> c in the terminal.

When motion detects "change" it will save jpeg images and short video clips in the target file (e.g. /home/steve/motionVideo). The format of the video can be changed via the motion.conf file. Just search for "ffmpeg_video_codec" and use one of the formats shown in the motion.conf file.

If your web browser just shows streams of text, its probably because it does not support the video format (try Firefox, or change the video format).

By default, motion expects the webcam to be /dev/video0. For any other device just edit the motion.conf file.

To use your file manager as root:-
 - Ubuntu: open a terminal and type gksu nautilus
 - Lubuntu: open file manager (PCManFM) and navigate to the required folder, then select menu "Tools" > "Open Current Folder as Root"

More info on motion configuraion options: [http://www.lavrsen.dk/foswiki/bin/view/Motion/ConfigFileOptions](http://www.lavrsen.dk/foswiki/bin/view/Motion/ConfigFileOptions)

This procedure tested using motion 3.2.12 on Lubuntu 10.10 & Ubuntu 10.10.

Merry Christmas!

---

### Post by P1C0 on 2010-12-19
> **SteveDee said:**
> Does Father Christmas really come down your chimney on Christmas Eve and deliver all those presents? There's only one way to find out...

In less than 10 minutes (by following 10 easy steps) you can install, configure and run your own Santa Claus detector using the excellent application "motion". This will allow you to capture video clips on a host machine, which also acts as a live webcam server for other computers on your network.

So if you have a webcam attached to your computer, let's go!

1. Run Synaptic Package Manager, search for "motion" and install it.
2. You need to run your file manager as root(see note below) for the next 3 steps.
3. Create a new directory to store your captured video (e.g. /home/steve/motionVideo) and a new hidden directory ".motion" (e.g. /home/steve/.motion)
4. Now navigate to /etc/motion, and copy the motion.conf file to the .motion hidden folder in your home directory (e.g. /home/steve/.motion)
5. Change permissions for this new copy of motion.conf for user "Other" to "Read and Write".
6. Open this file in a text editor, and search the file for "target_dir" and change location to suit (e.g. target_dir /home/steve/motionVideo)
7. Search the file again for "webcam_motion" and change this to "webcam_motion on"
8. Search the file for "webcam_localhost" and change this to "webcam_localhost off"
9. Open a terminal to run motion by typing:-
```
 motion -n 
```10. Open your web browser and enter the local address and port: [http://127.0.0.1:8081](http://127.0.0.1:8081)

You should now be able to see a jerky video image through your webcam. You can also view this remotely by opening a web browser on a networked computer and entering the IP address & port of the host machine (e.g. [http://192.168.0.99:8081](http://192.168.0.99:8081)).

To stop the motion app, just use <ctrl> c in the terminal.

When motion detects "change" it will save jpeg images and short video clips in the target file (e.g. /home/steve/motionVideo). The format of the video can be changed via the motion.conf file. Just search for "ffmpeg_video_codec" and use one of the formats shown in the motion.conf file.

If your web browser just shows streams of text, its probably because it does not support the video format (try Firefox, or change the video format).

By default, motion expects the webcam to be /dev/video0. For any other device just edit the motion.conf file.

To use your file manager as root:-
 - Ubuntu: open a terminal and type gksu nautilus
 - Lubuntu: open file manager (PCManFM) and navigate to the required folder, then select menu "Tools" > "Open Current Folder as Root"

More info on motion configuraion options: [http://www.lavrsen.dk/foswiki/bin/view/Motion/ConfigFileOptions](http://www.lavrsen.dk/foswiki/bin/view/Motion/ConfigFileOptions)

This procedure tested using motion 3.2.12 on Lubuntu 10.10 & Ubuntu 10.10.

Merry Christmas!I also had to change permission for others in folder motionUser to read, write, execute, because the owner of the folder was root and running motion -n could not write any video or images in to it.

Other than that, it works great!! Thanx!!

---

### Post by SteveDee on 2010-12-22
> **P1C0 said:**
> ...I also had to change permission for others in folder motionUser to read, write, execute, because the owner of the folder was root and running motion -n could not write any video or images in to it....

Many thanks P1C0 for pointing that out.

I have now modified the procedure in post#1 so that the folders are created running file manager as "user" and only the motion.conf copying is done as root.

---

