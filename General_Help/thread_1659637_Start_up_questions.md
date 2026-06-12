---
title: "Start up questions"
date: 2011-01-04
forum: General Help
---

### Post by Ekoscorn on 2011-01-04
Hi all.  

I'm looking for some general help here, nothing too hard.  Or at least I hope it isn't!  

Basically I have installed Ubuntu on one of my machines to act as a server.  The server is to run minecraft (insert lol here!) and really I want it to be plug and play.  

By plug and play I mean, I want to turn the computer on and the server program for minecraft will automatically start without any user intervention.  The computer running the server has no mouse, keyboard or monitor, or at least won't do (for now it has) if I can get around these questions.

What I'm looking to do is get a script into the start up applications to run the following two lines of code in Terminal:

```
cd /home/server/Desktop/minecraft 
```then

```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar
```That's the first part, and for the second part I am trying to set up the 'Remote Desktop' application to allow the computers on my network access it via VNC for any trouble shooting.  Though with the settings below I cannot seem to access the computer remotely (on my network) via the VNC Viewer on a Windows machine.  Or at least I can, but directly after boot I can't.

[IMG]http://img694.imageshack.us/img694/1820/screenshotremotedesktop.png[/IMG]

So that's three questions I have:

[LIST=1]
[*]How can I get the minecraft server running with the code shown above after boot without any human interaction?
[*]How can I remote desktop to the server?
[*]How can I restrict number 2, to just my LAN computers and therefore separate question number 2 from the Internet?
[/LIST]
Thank you all.

---

### Post by Ekoscorn on 2011-01-04
Giving this a bump.

---

### Post by hawkmage on 2011-01-04
It may take a little tweaking but you can create a Upstart script to start the application.  First of all are there any environment variables that it relies on, those would have to be defined in the upstart script?  The sctipt should be put in the /etc/init/ directory and call it something like minecraft.conf (It has to have the ".conf" extension)

It would look something like this:
```
# minecraft Service

description     "minecraft Server"
author          "Whatever you want"

start on (net-device-up
       and local-filesystems
       and runlevel [2345])
stop on runlevel [016]

script
        export Varable='Value'
        cd /home/server/Desktop/minecraft
        exec /usr/bin/java -Xmx1024M -Xms1024M -jar minecraft_server.jar
end script

```
I included the "export Varable='Value'" to show you how to set an environment varable for the application if needed.  If your version of java is not /usr/bin/java then replace it with the full path to your version of java.  

OK this should take care of your first item.  I am not going to tackle the other two.

---

### Post by Ekoscorn on 2011-01-05
> **hawkmage said:**
> It may take a little tweaking but you can create a Upstart script to start the application.  First of all are there any environment variables that it relies on, those would have to be defined in the upstart script?  The sctipt should be put in the /etc/init/ directory and call it something like minecraft.conf (It has to have the ".conf" extension)

It would look something like this:
```
# minecraft Service

description     "minecraft Server"
author          "Whatever you want"

start on (net-device-up
       and local-filesystems
       and runlevel [2345])
stop on runlevel [016]

script
        export Varable='Value'
        cd /home/server/Desktop/minecraft
        exec /usr/bin/java -Xmx1024M -Xms1024M -jar minecraft_server.jar
end script

```I included the "export Varable='Value'" to show you how to set an environment varable for the application if needed.  If your version of java is not /usr/bin/java then replace it with the full path to your version of java.  

OK this should take care of your first item.  I am not going to tackle the other two.

Forgive me for being such a noob!  However I'll try that out.  Thanks very much.

Though I think my 2 other questions have been asked in error due to me not having much sleep!  They both make much more sense now.  Haha.

---

### Post by Ekoscorn on 2011-01-05
Alright just a little update.  I understand that question three is quite the stupid question.  So ignore that. 

However, upon boot of the machine, I open VNC viewer on my Windows machine, type in the IP address of the Ubuntu box, and then asks for a password.  However after typing in the correct password nothing happens.  

So what am I doing wrong?

---

### Post by hawkmage on 2011-01-05
The VNC service doesn't start until someone logs in.  I have installed xrdb by running "sudo apt-get install xrdp" then I use an RDP client to log in.  From Linux I use "rdesktop", Windows I use "mstsc" OS X I use "CoRD" which you can find here [http://cord.sourceforge.net/](http://cord.sourceforge.net/).

---

