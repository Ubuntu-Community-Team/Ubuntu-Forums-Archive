---
title: "Using a program as a shell in linux"
date: 2012-02-13
forum: General Help
---

### Post by jonnis2206 on 2012-02-13
I have a computer which currently runs on Linux Ubuntu. I don't want actually want to see Linux running and simply want to use it as a background operating system.
 
Instead I have this software package: [Eldy]("http://www.eldy.eu")
This package is designed for use by the elderly, and so I am trying to simplify the computer. At the moment the only way to activate this program is to double click the .sh file via the folder, and click run, which starts the .jar file and the program. 
 
I want the program to open automatically on start up, as a shell interactive window. When I open the program through Linux (or if I were to open it using start-up applications) it does not cover the whole screen. It's normally a full screen program but it gets shifted by the toolbars. 
 
I'd also like it if exiting the program shut down the computer. I am not sure if the best way to go about this is through the BIOS or through Linux itself, but was wondering if you had any ideas.
 
I'm not certain if what I'm talking about is even possible. I suppose its the equivalent of doing the same with a package like word in microsoft, which seems unfeasible, as its just a piece of software. Any help working towards this goal or with other suggestions would be greatly appreciated.

---

### Post by drmrgd on 2012-02-13
Just skimmed the documentation, but from a first glance, I'm betting the program doesn't have the necessary components to be a proper shell.  You could get close to what you want by running a desktop environment that doesn't use Unity and / or hiding the taskbars.  You might consider something like Lubuntu for this, since if I recall correctly, there are no launchers or taskbars by default (could be Xubuntu that I'm thinking), or at the very least, I sort of remember easily hiding them.  

From there, you should be able at add the program launcher to the startup programs (for example in Kubuntu, add the .sh script to be run at login in System Settings -> Start Up and Shut Down -> Add Script...).

Setting up something to shut down the computer when the program is exited, though, is a bit more complex. I can't think of a clever solution for that one.  About the only think I can think is to make a shutdown launcher, which you put on the desktop.  When the person closes the program, they can just click the shutdown button on the desktop.  

Not really a total solution, but a couple ideas to explore anyway :)

---

### Post by jonnis2206 on 2012-02-13
I have looked into the shutdown methods. I've actually got one. As the program is launched using an executable sh file, I can put in a shutdown command after the launch of the .jar file in that file. It will run when the application terminates I think, just need to go try it out. 

"
You could use the linux 'shutdown'command.

details on its usage can be found here:
[http://www.computerhope.com/unix/ushutdo&#8230;]("http://www.computerhope.com/unix/ushutdow.htm")

preferred usage is:
sudo shutdown -h 0


put this in your shell script, after your java execution. It will run when the java program has exited.
**"**
 
Used good old Yahoo answers for that one. Thats very useful though, thanks! Im realising now that all I really need to do is get rid of the toolbars on Ubuntu. Will do some research into the different software options and see if I can get it working.

---

### Post by drmrgd on 2012-02-13
> **jonnis2206 said:**
> I have looked into the shutdown methods. I've actually got one. As the program is launched using an executable sh file, I can put in a shutdown command after the launch of the .jar file in that file. It will run when the application terminates I think, just need to go try it out. 

"
You could use the linux 'shutdown'command.

details on its usage can be found here:
[http://www.computerhope.com/unix/ushutdo…]("http://www.computerhope.com/unix/ushutdow.htm")

preferred usage is:
sudo shutdown -h 0


put this in your shell script, after your java execution. It will run when the java program has exited.
**"**
 
Used good old Yahoo answers for that one. Thats very useful though, thanks! Im realising now that all I really need to do is get rid of the toolbars on Ubuntu. Will do some research into the different software options and see if I can get it working.

That's kind of a interesting idea.  Make a shell script to run the program at login, and then add a shutdown command to run when the program is finished running (user exits) by, I guess, adding a '&&' in between.  Probably need a little tweaking and honing, but seems like an interesting strategy.  Hope it works out for you!

---

### Post by jonnis2206 on 2012-02-13
Now to admit I have no experience whatsoever with linux. A shell script is a fairly foreign concept to me. My only example is the Eldy script:

#!/bin/sh
 
java -Xmx256M -Xms64M -XX:MaxHeapFreeRatio=35 -XX:MinHeapFreeRatio=20 -jar eldy.jar
 
 
How could I modify this script to do all these things you're suggesting?

I'm assuming I'd need to run the sh file as a startup application, and I think there's a special way to do that too?

Any guidance at this point would be great. I know there needs to be a shutdown -h 0 in there somewhere, no idea where though.
 
Thanks again!

---

### Post by jonnis2206 on 2012-02-13
> **jnisa said:**
> You could use the linux 'shutdown' command. It will be better and helpfull.
 
Where would I insert it into my file though?

---

### Post by jonnis2206 on 2012-02-13
Cancelled post

---

### Post by drmrgd on 2012-02-13
> **jonnis2206 said:**
> Now to admit I have no experience whatsoever with linux. A shell script is a fairly foreign concept to me. My only example is the Eldy script:

#!/bin/sh
 
java -Xmx256M -Xms64M -XX:MaxHeapFreeRatio=35 -XX:MinHeapFreeRatio=20 -jar eldy.jar
 
 
How could I modify this script to do all these things you're suggesting?

I'm assuming I'd need to run the sh file as a startup application, and I think there's a special way to do that too?

Any guidance at this point would be great. I know there needs to be a shutdown -h 0 in there somewhere, no idea where though.
 
Thanks again!

Might be best for BASH guru advice at this point.  Intuitively, seems like just putting a wait command between the two would work .  But, I'm betting there are more problems associated with this than it seems.  

One obvious problem that stands out to me is what to do if the program crashes?  If the script just waits for the program to exit before running shutdown, it'll shutdown the whole computer if the Eldy program crashes, which is probably not what you want.  So, probably some sort of query into how Eldy was shutdown is needed.

Also, usually shutdown is run as root (i.e. sudo shutdown now). So, this would have to be taken into account as well.  It might be otherwise hard to explain to a user why they have to type a password to shut their computer down!

Anyway, once one of the BASH elite on here come by, I'm sure they'll be able to point you in the right direction.

---

### Post by ajgreeny on 2012-02-13
This is a longer but duplicated thread of [http://ubuntuforums.org/showthread.php?t=1924715](http://ubuntuforums.org/showthread.php?t=1924715).

Please do not duplicate threads as it makes it very difficult to see what has been happening on a problem.

---

### Post by jonnis2206 on 2012-02-13
No idea what that means being completely honest. I look forward to that though. For all the details look here:


 
I'd like to start out by saying Ive got absolutely 0 experience with Linux. I lack a good understanding of what I'm doing. I'm using the operating system because it is free, and its part of a computer project I'm doing to produce a computer from scratch. 

I have installed Linux Ubuntu successfully and am trying to use another application as the user interface, its called Eldy ([www.eldy.eu]("http://www.eldy.eu/")). I don't want the end user of the computer to have any interaction with Linux at all.

In that vein, what I'm trying to do is have the .sh file run automatically on startup, which should automatically open up Eldy. The only way to open eldy that I can work out currently is to open the file from the folder and click run. Nothing else seems to work, even in the terminal. 

I also want to insert some code into the sh file to cause the computer to shutdown when I close the program. I know its something along the lines of shutdown 0 but have no idea where to put it.

Currently the file information for the program is located in my documents. When I try to run this line of code in the terminal:
sh eldy.sh
I get the following error:
sh: Can't open eldy.sh
I have no idea why this is, does it need to be in system files?

The sh file has this code in:
#!/bin/sh

java -Xmx256M -Xms64M -XX:MaxHeapFreeRatio=35 -XX:MinHeapFreeRatio=20 -jar eldy.jar

I've also tried to put the program into my startup success but have never had anything appear on startup with the various methods I have tried, not even an error message.

The sh file executes a .jar folder full of information.

I know exactly what I want to do, but I completely lack the know how to do it. Is what I'm talking about possible? Do I need to edit system files in which case how do I make myself the root user. I tried root passwd user and went through that process, changing the root user password, but it hasnt changed my priveledges. I can't understand why I'm the administrator and yet can't edit system files but there we go. 

If someone could talk me through everything I want to do, which I don't think is actually as complicated as I'm making it, that would be great!

On a side note, when I load the program, it normally loads as a full screen program. For some reason though on ubuntu it is pushed to the bottom right by the toolbars, and parts of it are obscured off the screen. Any solutions for this would be great too.

Thanks

---

### Post by jonnis2206 on 2012-02-13
I was asking for more information in this thread on a few slightly different topics. My apologies though, content moved to other post. This thread can be deleted

---

### Post by drs305 on 2012-02-13
The other thread was merged here as you were posting. We'll keep it here rather than moving it again.

---

### Post by jonnis2206 on 2012-02-13
you were way ahead of me! thank you

---

### Post by 1clue on 2012-02-13
Been awhile since I messed with this sort of thing, but back in the day we used to write our own $HOME/.xsession files.  You pretty much had to back then.

First thing I would do is create a separate account to go messing with, leaving your current default account in case you mess up and need to fix it.

.xsession runs when you log in from an X login, or when you start X from a command line.  It sets up your customized environment and then runs a program.  That program is normally a shell or a desktop manager, but it doesn't have to be.  I messed with all sorts of things, including using firefox as the "shell."  As soon as your shell app closes, you are logged out.

I don't know how much different it is today.  It may be that the X initialization is different, but I suspect there is still a way you can do your own thing, or it wouldn't be Linux anymore.

I think your .xsession would set up your java environment and then run that command you posted.

With regards to shutting down, that can be a can of worms but really to do it all you need to do is add yourself to /etc/sudoers so you can shutdown without a password, and then put **sudo shutdown -h now** at the end of your .xsession file.

That said, doing something like shutting down at the end of your session with this account means you will NEED to have a login screen that lets you choose your user, or you will never be able to change your computer once it's set up.

---

### Post by Khayyam on 2012-02-13
> **jonnis2206 said:**
> [...]Currently the file information for the program is located in my documents. When I try to run this line of code in the terminal:
sh eldy.sh
I get the following error:
sh: Can't open eldy.sh

I've some experience with running 'kiosk' like applications from init (the boot process) without login .. just boots directly into the kiosk. I think some experience with how the OS works is required before I could give you some idea of how to go about achieving this. Otherwise, I'd have to explain every term and every step and not having any specific experience with Eldy, things will probably end up frustrated for both parties.  
 
The following may be all that is required to have it run from the command line (terminal):

```
#!/bin/bash

export DISPLAY=:0

java -Xmx256M -Xms64M -XX:MaxHeapFreeRatio=35 -XX:MinHeapFreeRatio=20 -jar eldy.jar
```My guess is that it doesn't know what display to use.

Note that I've also changed the shell to /bin/bash (probably not important but why use sh when you have bash).

You would then make the script executable, and (attempt to) run it

```
chmod u+x eldy.sh
./eldy.sh
```> **jonnis2206 said:**
> I've also tried to put the program into my startup success but have never had anything appear on startup with the various methods I have tried, not even an error message.

OK, here is where it starts to get difficult ... why do you plan to run it under your user, with the Unity Desktop running? If you want to have this as "the interface" then you should run it as a seperate entity, with its own account, and with nothing else running but Eldy (and X11) .. an "Eldy Kiosk" (you might find some of the information on the [Kiosk Project Page]("http://stlouis-shopper.com/cgi-bin/mozdev-wiki/kiosk-wiki.pl")).

> **jonnis2206 said:**
> I know exactly what I want to do, but I completely lack the know how to do it. Is what I'm talking about possible? Do I need to edit system files in which case how do I make myself the root user. I tried root passwd user and went through that process, changing the root user password, but it hasnt changed my priveledges. I can't understand why I'm the administrator and yet can't edit system files but there we go.

Yes, its "possible", though I've never done it with Eldy. You might also want to take a look at [JoliOS]("http://www.jolicloud.com/jolios") which though a "OS" and not a Java applet, has some similarities with Eldy. JoliOS can be installed or run from a CD/USB Disk, has minimal hardware requirements, a 'guest' user, and is based on Ubuntu, so perhaps this might work in place of Eldy.
 
> **jonnis2206 said:**
> If someone could talk me through everything I want to do, which I don't think is actually as complicated as I'm making it, that would be great!

Thats a big ask. Its not just a matter of how complicated it is or might be, but to go from experience=0 to completion would require that some one do it and then provide a command-by-command tutorial.
 
> **jonnis2206 said:**
> On a side note, when I load the program, it normally loads as a full screen program. For some reason though on ubuntu it is pushed to the bottom right by the toolbars, and parts of it are obscured off the screen. Any solutions for this would be great too.

I don't know, could be a number of reasons, probably Eldy expects to manage the screen but as Unity is doing that already .. who knows .. could be Eldy expects a certain geometry for the X11 display .. who knows. Without someone actually downloading it and figuring it out its a difficult guess, you'll have to troubleshoot this the best you can.

HTH ...

---

### Post by lykwydchykyn on 2012-02-13
I did a write-up recently about how to create a web browser kiosk with linux:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

What I did could easily be adapted to run any kind of graphical program as a shell (side note -- "shell" in Unix-speak refers to the program you use as a text terminal, so this wording can be confusing to long time *nix users).

Basically, you would just replace the call to chromium with the command to run eldy.

---

### Post by Khayyam on 2012-02-13
> **1clue said:**
> [...] With regards to shutting down, that can be a can of worms but really to do it all you need to do is add yourself to /etc/sudoers so you can shutdown without a password, and then put **sudo shutdown -h now** at the end of your .xsession file.

That is one way of doing it, perhaps a better would be to use gdm with a guest/guest account. This way when the user exits the Elfy session getty respawns gdm where the next 'guest' session can be started. The guest account would also be cleaned of any changes, etc, and should shutdown be needed its available from gdm.

With this setup the elfy script is run much the same way that 'gnome-session' is run. It just has to be made the only option in the gdm session dialog.

gdm-guest-session has features that the OP might find useful, but AFIAK it can't be run from gdm. Some of its features: it hides most of the filesystem (or gives read-only access), users can save files to USB, some restrictions on network access, uses tmpfs for guests $HOME, and others. I've not used it so can't comment but it looks like some of its inner working could be applied (using tmpfs for instance).

gdm is a better solution than having the UI crash and the machine shutdown (not really what grandma would expect .. she'd probably have a heart attack!).

Couldn't find much info on the subject, but here are a few links that might be of some interest:

1. [How to set default desktop session on ubuntu](http://www.worldofnubcraft.com/947/how-to-set-default-desktop-session-on-ubuntu/)
2. [How to allow password-less logins from gdm](http://lists.debian.org/debian-user/2005/11/msg00139.html) and the [reply](http://lists.debian.org/debian-user/2005/11/msg00228.html)
3. [This](https://fedorahosted.org/guest-account/) might be useful (though its directed af Fedora).

HTH ... khay

---

### Post by jonnis2206 on 2012-02-13
While a newbie at Linux I consider myself fairly computer literate. I'm still getting used to the workings of the software, but am getting there in general with the coding. Obviously what I'm trying to do is at a relatively high level, but I need to achieve it for my project. I can't thank you guys enough for all the help you've provided! I can only access the computer in working hours but I'm going to write down a list of things to try for myself and see where they take me. As far as making this a guest account goes, I actually want it to be the only accessible thing on the computer. I imagine that minimising it instead would not shutdown the system if I needed to make changes, and if not then I believe I could use the BIOS? 

Its aimed at users that wont change their system though, so I'm very happy for it to all just be in one session.

Again thanks everyone for your help!

---

### Post by drmrgd on 2012-02-13
> **lykwydchykyn said:**
> I did a write-up recently about how to create a web browser kiosk with linux:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

What I did could easily be adapted to run any kind of graphical program as a shell (side note -- "shell" in Unix-speak refers to the program you use as a text terminal, so this wording can be confusing to long time *nix users).

Basically, you would just replace the call to chromium with the command to run eldy.

Wow!  Really cool write up on that.  Tons of great info that's really nicely laid out.  Definitely going to bookmark that for future reference.

---

