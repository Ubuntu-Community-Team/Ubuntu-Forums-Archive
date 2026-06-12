---
title: "Installed kde on a gnome ubuntu"
date: 2010-09-03
forum: General Help
---

### Post by Adrienk on 2010-09-03
I used the ubuntu software center which i have never used before to install KDE on Ubuntu which by default is gnome. it gives me (at login) the ability to switch between KDE and Gnome, can i move files between the two? 

Does KDE get updates for the desktop if installed this way?

---

### Post by harrismh777 on 2010-09-03
The answer to your first question depends on what you mean by "move files between the two".

KDE and Gnome are desktops (over window managers over X11). They are two unique interfaces over the same system. The interface looks and behaves differently, but the system is the same. You can access all of your files from either interface. 

If you mean specific kde or gnome configuration files then the answer is no; although, there are migration tools that you can use ymmv that will aid in configuring one mailer to another, for instance. 

Depending on how you have the update manager configured your new kde packages should update automatically like all the other packages on your system.

---

### Post by Adrienk on 2010-09-04
I havent done any configuration to the update manager, is there something specific i should do?

---

### Post by zadehas on 2010-09-04
As long as you installed KDE using the software center, you don't need to do anything, the KDE packages will get updated along with all the others. Like harrismh777 said, it's the same system, but with a different graphic interface.

---

### Post by cwwilson721 on 2010-09-04
Your confusion comes from a slight lack of knowledge about the way Ubuntu/Linux works.

There is GNU/Linux, the Operating System. The guts, you might say.

Then there is the **G**raphical **U**ser **I**nterface (GUI), which in the case of Ubuntu, is Xserver. It is the 'framework' for the various desktops work. 

And then, there are the Desktop Environments, like Gnome, and KDE. They provide the actual 'eyecandy'. They also have some minor program differences, but if they were installed through the Ubuntu Software Repos, you can use most programs from either desktop in either desktop. (Example, you can run knetwalk in gnome, and gmines in KDE)

In a nutshell, the GUI only provides a way for you to run programs by using a mouse, instead of typing everything in. Technically, you don't even need it for most tasks the OS needs to do. But it sure is easier to just click an icon rather than type in a long line of text to just copy a data cd.

Think of your system as an automobile. The drivetrain is Linux, the body is xserver, and the paint color is the Desktops. No matter what color you choose to paint your car, the trunk will still have the same contents. So if you put a box in the trunk, and then repaint the car, the trunk will STILL have the same box in it, and the motor will still run the same. The paint shop might have added a chrome piece here or there, just to make it go with the paint color, but by and large, mostly it's just color. Changing the paint color does not change the engine, does it? So in Ubuntu, all programs still do the same job, but just look different. (There ARE performance differences between desktop environments, but for the sake of this discussion, and brevity, we'll leave those out, because that's a whole other discussion.)

Changing from gnome to KDE doesn't change the way things work, just the way they look. Updates, etc, will work fine

All of the above assumes that you installed KDE/Kubuntu from the Ubuntu repositories.

---

