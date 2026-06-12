---
title: "Applications installations"
date: 2012-07-21
forum: General Help
---

### Post by barjaktar on 2012-07-21
Hello.

I am interested in where does the application actually gets installed. In other words, after I do "apt-get install some_app", where does apt-get put the "some_app"? In the folder structure, where does it go?

This question comes to me from the following problem. I wanted to install Blender. But, even though I did "apt-get update", my "apt-get install blender" brings me the old version 2.49. I went to Blender's webpage, downloaded the newest version (2.63), unpacked it in my Downloads folder and now I am able to run it from my terminal by just typing "blender". Ok, but I want it in my Ubuntu's application menu.

What do I need to do, where to put the downloaded folder or whatever, to get the version 2.63 installed and get it in the Application menu?

Thank you.

---

### Post by Lars Noodén on 2012-07-21
Most likely the executables will go in /usr/bin or /usr/local/bin and the configuration file(s) will go in /etc.  That is in accordance with the [guidelines for layout](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  

If you still have the .deb file cached in /var/cache/apt/archives/ then you can use [dpkg -c](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) to list the files in the package.  Or you can look online in the [packages database](http://packages.ubuntu.com/).  That, too, will list files in a package.

---

### Post by kc1di on 2012-07-21
Hi barjaktar and welcome to Ubuntu.

There are several places depending upon the exact desires of the software developer where it may be installed.  Most often the executable (That is the part that actually launches the program ) is found in /usr/bin our usr/local/bin.
It sounds from what you describe that blender was installed in /usr/bin. that being said some programs may be in /opt Directory also. (you can find a good explanation of the file system [here]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview").) 
to Put the Icon in the Dash Menu here are a couple of page that explain how to do that. 
[http://askubuntu.com/questions/144488/add-icons-to-dash-menu-from-programs]("http://askubuntu.com/questions/144488/add-icons-to-dash-menu-from-programs")  

[http://www.youtube.com/watch?v=PcX-Hok5Dbk]("http://www.youtube.com/watch?v=PcX-Hok5Dbk")

Good Luck

---

### Post by barjaktar on 2012-07-23
No, it is not in /usr/bin. It is where I downloaded it - in my Downloads folder. When I untar and open the blender folder I run it from terminal as follows: ./blender and it works.

So, there was no actual process of installation. All I am asking is where to put the untared folder in order for the application to appear in my menu (since I am still using ubuntu 10.04).

Also, another question. Before I installed Ubuntu, I read that it is recommended to have different partitions, so I made: boot (200MB), root (10GB) and home  (60GB) partitions. I made home partition the largest since I figured that I will be spending the most time working as a user, thus no need for root privileges. I thought that the application installation will stay within the home partition. Is this possible? Do I have to put my applications in root partition?

Thank you.

---

### Post by kc1di on 2012-07-23
any Program that does not require an install such as you have you can put anywhere you like.  I would most likely put blender in /opt but that is just personal preference.  


Look in the folder you un- tarred and see if there is a .desktop file in there if there is simply copy that file to the /usr/share/applications folder and it will show up in the menu.

since you mentioned your still using 10.04 I believe you can also right click on the menu button and select edit menu and add it there also.  (it's been awhile since I ran 10.04.)
good Luck
P.S. your partitioning looks ok. but there wasn't really a need for the boot partition. other than that looks fine.

---

### Post by mastablasta on 2012-07-23
create a launcher (shortcut in windows) in the menu or on desktop and point it to downloads and tell it to run ./blender

---

### Post by Scott Harrison on 2012-07-23
For future reference, you could have automatically updated Blender to the newest version from within the terminal:

```
sudo apt-get update
```This would have updated the original installation, allowing you to find it the way you want to.

If you like, you can remove Blender:

```
sudo apt-get remove Blender
```and start again, now that you know how to update.

I also suggest reading the apt-get manual when you have the time:

```
man apt-get
```

---

