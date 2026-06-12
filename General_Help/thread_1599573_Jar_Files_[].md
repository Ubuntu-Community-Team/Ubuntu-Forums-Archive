---
title: "Jar Files [?]"
date: 2010-10-17
forum: General Help
---

### Post by nmcgrew on 2010-10-17
It's all so confusing *lol*

I am trying to download this: [http://manuelbarzi.com/pola/](http://manuelbarzi.com/pola/) and when I do, it opens a read only thing for all these pola.jar files.  I have NO idea what to do with them or how to make this program run.  In Windows you dl a program and click it to install and run.  In Linux it's this whole big deal.  Can anyone please tell me in idiot terms how to make this program run please?  I'm so lost in this and can't enjoy the things I want to anymore.

Thank you very much.

---

### Post by matsuzine on 2010-10-18
Ok, what you're looking at is a Java Archive file, or .jar for short.  It's a java thing, not a linux thing.  But since java is cross-platform, this program can also apparently be run on a linux box.  

A jar file is the standard way for java programs and libraries to be distributed.  You will need to install java on your system before you can run it:

sudo apt-get install openjdk-6-jre

Most likely, you can then run it using the command:

java -jar Pola.jar

***Please be aware that this application will then have access to anything that your user account has access to, and could also pass information over the internet.  In other words, be sure you trust the publisher before running this program.

In general, installing software through the ubuntu repositories is much easier than installing on windows.

---

### Post by nmcgrew on 2010-10-18
Question 1 - where do i save those files i downloaded?  the jar ones i initially downloaded.  they're on my desktop right now.
Question 2 - user account?  you mentioned they would have access to my user account, which user account?
Question 3 - when i attempted to do as you suggested this is what my terminal said to me:

-desktop:~$ sudo apt-get install openjdk-6-jre
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
-desktop:~$ java -jar Pola.jar
Unable to access jarfile Pola.jar
-desktop:~$ 

*note: i removed all of my personal information in the above copy/pasted text from my terminal window

and so i still have no idea what i'm doing or how to install or run or work this program :(

---

### Post by leon_chame on 2010-10-18
This typically is the same in linux to but in this case the 'Pola' folks have an .exe (something you can just click and run) for their windows version and for linux they use a jar..which btw is basically a zip file that has java in it...so they essentially give you a java file to run not a stand alone running application in this case.

Anyway, jar files can act like an exe too where you just double click it and run...but in this case, ubuntu's default way to treat this .jar file is to unzip (uncompress) it.

To fix this, you can do several things:

1. Run the jar as described on [http://www.wikihow.com/Run-a-.Jar-Java-File](http://www.wikihow.com/Run-a-.Jar-Java-File) gnu linux section which I essentially paste here:

**In the left click menu, there should be the "open with" enabled by default**. Select "Sun Java X.X runtime", and run it.2
**If you want to always open **.jar files with Java insted of the archiver, select the right click menu, click on properties. 
[LIST]
[*]Select the open with tab.
[*]There should be the Java software there to select. Make your choice, and confirm
[/LIST]



NOTE:  You will need to have Java installed on your machine in order to do this...so install Java first if you don't...goto software center and search on JRE (java runtime).



2. Save the jar and follow the instructions for running from a terminal via your pola site which again I paste here:

[CENTER][FONT=courier new][1] download Pola multiplatform (Linux download link)[/FONT]
[FONT=courier new][2] then run the following command on your Terminal to create your Pola:[/FONT]
[COLOR=Navy][FONT=courier new]java -Xmx1024M -jar Pola.jar -cartridgeSize=big -fontSize=medium -comment="MyLittle TRUCK :)" ./truck20.jpg[/FONT]
[/COLOR] [FONT=courier new][COLOR=Navy]the output you will see is:[/COLOR][/FONT][COLOR=Navy]
[/COLOR] [COLOR=Navy][FONT=courier new]Processing...[/FONT]
[/COLOR] [COLOR=#ffff00][FONT=courier new][COLOR=Navy]Pola created [/COLOR];)

[/FONT][/COLOR][/CENTER]
Same rules apply, make sure you hava java installed.

BTW, Many java archives (jar files) are not runnable so that is why it is a better choice to have extraction as the default in my option..if you are not a java developer..which I assume you arent...set the default behavior for jar files as described in the howto.wiki.

Hope this helps!

---

### Post by matsuzine on 2010-10-18
#3. The info you got when running the install for java just means that it is already installed.

#1. So when I clicked on the linux download link on the site you provided, it downloaded one file called Pola.jar. You referred to many .jar files?  

If you run the 

ls 

command, what is the output?

#2.  What I mean about the program being able to access your user account:  you are currently running as a user on your linux machine.  As an ordinary user, you have access only to files that you have permission to handle.  This program will have access to anything that you do.  As a normal user, that means it won't have access to your system, but anything in your home directories is fair game.  It's just good practice to only run programs from trusted sources.  :)

---

### Post by Yarui on 2010-10-18
> **nmcgrew said:**
> Question 1 - where do i save those files i downloaded?  the jar ones i initially downloaded.  they're on my desktop right now.
Question 2 - user account?  you mentioned they would have access to my user account, which user account?
Question 3 - when i attempted to do as you suggested this is what my terminal said to me:

-desktop:~$ sudo apt-get install openjdk-6-jre
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
-desktop:~$ java -jar Pola.jar
Unable to access jarfile Pola.jar
-desktop:~$ 

*note: i removed all of my personal information in the above copy/pasted text from my terminal window

and so i still have no idea what i'm doing or how to install or run or work this program :(

You can save the file anywhere you want.  It serves basically the same function as an exe file in Windows.  You just have to run it from the location where you saved it.  Anywhere in your home directory is good, and that includes your desktop.

What he means when he says it will have access to anything your user account has access to, he basically means that because you are running it as yourself, it can do anything you would be allowed to do.  The user account that it has access to is whatever user account you run it with.  So if you were to sudo when you run it, the program would have root access and could basically do anything it wanted to do to your system.  If you are on a more limited account, though, that only has write access to its own home folder, the program wouldn't be able to write anywhere except for the home folder of that user.  Basically what matsuzine was saying is to be sure the program is coming from a trustworthy source, because you are trusting the program not to do anything bad to your system.

When you ran that terminal command, the output basically told you that you already have java installed, so there is no need to worry about that.  If you still have the jar file on your desktop you should be able to run it with the following:
```

cd ~/Desktop
java -jar Pola.jar

```
The first command changes your working directory to your desktop and the second runs the program.  It is important to change your directory, because the command that runs the program looks in the folder that you are currently working in, and if it doesn't find Pola.jar in that folder, the command fails to execute.

---

### Post by nmcgrew on 2010-10-18
I'm sorry I"m such an idiot about this...

Ok, well that worked well re: the terminal window opening from my desktop.  The program opens and I think I can manage from here out but I have one more question please, so from now on to run this program, I need to open a terminal window and use this text in the terminal to make it work?  

cd ~/Desktop java -jar Pola.jar

---

### Post by matsuzine on 2010-10-18
Linux takes a little getting used to...  But once you're used to it, it's a pretty cool ride.

You can put that jar file in a directory somewhere and create a launcher to start it from the desktop or the menu.  I would create a .pola directory in my home directory and drop the jar file in there.  

These instructions assume you are using the Gnome desktop... If not, let me know.  

Right click on the Applications menu.  Choose Edit Menus.  Select the 'Graphics' category.  Push the 'New Item' button ( has a + next to it ).  

Name : Pola 
command:  java -jar ~/.pola/Pola.jar 
[or whereever you saved your file]
Comment:  Create Polaroid-like photos

Click 'Ok'.  Now, it should launch when you select it from the menu.

---

### Post by matsuzine on 2010-10-18
P.S.  Glad you got it to work. :)

---

### Post by nmcgrew on 2010-10-18
> **matsuzine said:**
> Linux takes a little getting used to...  But once you're used to it, it's a pretty cool ride.

You can put that jar file in a directory somewhere and create a launcher to start it from the desktop or the menu.  I would create a .pola directory in my home directory and drop the jar file in there.  

These instructions assume you are using the Gnome desktop... If not, let me know.  

Right click on the Applications menu.  Choose Edit Menus.  Select the 'Graphics' category.  Push the 'New Item' button ( has a + next to it ).  

Name : Pola 
command:  java -jar ~/.pola/Pola.jar 
[or whereever you saved your file]
Comment:  Create Polaroid-like photos

Click 'Ok'.  Now, it should launch when you select it from the menu.

i did all of this and it won't open.

how do i know if i'm using a gnome desktop?

---

### Post by nmcgrew on 2010-10-18
it says:
Failed to execute child process

---

### Post by matsuzine on 2010-10-18
Open the System menu.  Does it say "About GNOME"?

---

### Post by matsuzine on 2010-10-18
Try changing the command to:

java -jar /home/<your user name here>/.pola/Pola.jar

---

### Post by nmcgrew on 2010-10-18
*laughing* it actually works!  i'm stunned and amazed.  thank you so much for your help and really kind patience.

---

### Post by matsuzine on 2010-10-18
Totally awesome that it works!  Thanks for sticking with it.

---

### Post by Yarui on 2010-10-18
Sorry if the whole changing your directory and then running the command thing confused you.  That just seemed like an easier way to explain it to a new user.  The single line command you were given works just as well.  It is good that you got things working, though.  You should make sure to mark the topic as [solved] now that you have gotten everything sorted out.

---

### Post by brainformat on 2010-10-29
Hi.
I have another problem with running java application. I don't want to open a new thread, so I'll post it here.

this is the problem:
```
brainformat@c3po /Dokumenti/Programi $ java -jar GoogleHackPureJava.jar
Not enough input parameters! Exit.
brainformat@c3po /Dokumenti/Programi $
```
java is instaled on my machine.

any help would be much appreciated!

---

### Post by matsuzine on 2010-10-30
Hi, it really is usually best to start a new thread!  But anyway...  What this means is that whoever wrote the program expects you to provide command line parameters.  

When you run a jar file, 

```
java -jar jarfile.jar 
```

is how you get the jarfile to run.  Anything you add after this are the parameters and give the program more information, like what files to work with or what options to use.  You'll need to check on any documentation for this program.  Many times, using the parameter 

```
-h 
```
[or] 
```
--help
```

will bring up some documentation.

---

