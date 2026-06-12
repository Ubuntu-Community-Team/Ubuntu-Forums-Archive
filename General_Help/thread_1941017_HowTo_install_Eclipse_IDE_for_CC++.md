---
title: "HowTo install Eclipse IDE for C/C++"
date: 2012-03-14
forum: General Help
---

### Post by linuxford on 2012-03-14
I am not an expert, so use at your own risk. However, I did spend some work getting eclipse for c++ and thought you guys may be interested in a simple newbie how-to.
--------------------------------------------------------------

USE ECLIPSE IDE for creating C/C++ programs on UBUNTU LINUX

If you are a Linux user, then you will want to download the Eclipse cockpit (note: if you already have downloaded Eclipse, you may need to download a plugin). This directions will assume a Ubuntu Linux distribution is installed on your computer (I am using Natty Narwhal but some of the earlier versions will be the same).

First go to the menu, Applications->Ubuntu Software Center

Once the Ubuntu software center menu is up
1. type 'eclipse' in the top right software search section

2. click Install

3. Go to the menu, Applications->Programming->Eclipse
You will get a Eclipse splash screen. Notice the version called "Galileo". Write down on some paper what version that you get because you will need this later.

4. And then a menu asking where to store your program stuff (workspace), just click OK

5. Then it will open up your basic workarea. Notice in the top left hand corner (or middle in some versions) it says JAVA. This means currently Eclipse is setup to create and run Java programs. We need to change this by getting what the call a plugin. 

A plugin is basically some additional computer code or capabilities that you get to plugin to your existing software application (Eclipse) that gives it additional functionality that it doesn't normally have. It is kind of like when you get a plugin for your Internet browser that allows you to play Flash games or animation, etc.

6. Go to the top of your Eclipse Menu, Help->Install New Software

7. You will need to click the Add... button to add a website from where it can download the plugin from.

8. Cut and past the following text:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo) 
into the Add menu.

You will need to substitute the portion that says "galileo" for whatever version you have (remember the Eclipse splash screen I mentioned earlier).

9. After you add the Galileo repository and click Ok, then you will have the menu (shown below) come up.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux08.gif/311161362/eclipseLinux08.gif[/IMG]


10. Check the CDT Main Features as shown below.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux09.gif/311161744/eclipseLinux09.gif[/IMG]


11. Click Next

12. Click Next.

13. Click the "I accept the terms of the license agreements" and then Finish.

14. And then it will began to download, be patient this could take awhile depending on your Internet connection.

After it finishes, it will ask you to restart Eclipse. Go ahead and restart it.
Then you will get the following screen after it restarts.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux13.gif/311163158/eclipseLinux13.gif[/IMG]


Go the Eclipse menu, Window->Open Perspective->Other


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux14.gif/311163368/eclipseLinux14.gif[/IMG]


Notice C/C++ is highlighted by default, so just click OK.
This will open up a window that is your basic cockpit and has what you need to code and run your first program.

From the top menu, choose File->New->C++ Project
This will bring up a form, which you will:
1. fill in project name, for example, 'Hello'
2. click on the "Hello World C++ Project"
3. click Finish.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux16.gif/311163920/eclipseLinux16.gif[/IMG]


Then Window above appears, and you want to click in the Project Explorer area. Click the arrows to have them expand, until you see - main()

Then double-click main() and it will open the Hello.cpp to the right of it, which is basically your project code.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux17.gif/311164140/eclipseLinux17.gif[/IMG]


Now if you go to the Menu, Project->Build All, and you will see the window shown below.


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux18.gif/311164332/eclipseLinux18.gif[/IMG]


Notice the circled portion on the bottom, you may have an error like I did. Eclipse didn't come with a C++ compiler built in, and even though you installed the plug-in, Eclipse will still use the Ubuntu Linux C++ compiler which you need to install. How do you install it? 

Go back to the Ubuntu Software Center, and this time search for 'g++' and click Install... and then close the Ubuntu Software Center.

Try again the menu, Project->Build All as show below, and notice this time it completes


[IMG]http://linuxford.wikispaces.com/file/view/eclipseLinux20.gif/311167030/eclipseLinux20.gif[/IMG]


Now click the Green arrow which will run your program.
Now notice the bottom of the window (as shown above). There is the output of your program -- !!!Hello World!!!

---

