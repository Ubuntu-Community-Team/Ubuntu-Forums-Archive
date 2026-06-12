---
title: "Using UBUNTU (newest release) to run a minecraft server"
date: 2012-02-24
forum: General Help
---

### Post by AMBiEN22 on 2012-02-24
Hello everyone,

Recently i have been playing a game called [Minecraft]("http://www.minecraft.net"), a sandbox creation game. I have an old dell that i have installed the latest release of ubuntu on. Although after instillation and getting the server setup i noticed that there was a "Ubuntu server" software.

So my very simple question is, if i switch to this "Ubuntu server" software will i get better results than the OS version?

Also is it possible to just start Ubuntu with out the GUI and just run the "Terminal" if you will. (The UI was great for dragging and dropping server files, but now i want to free up some RAM that Ubuntu GUI and the extra software could be using)

Thanks ahead of time everyone and i appreciate the help.

---

### Post by Rafterman414 on 2012-02-24
I used to run a Minecraft server on my Ubuntu Desktop Installation and never had any problems, it depends on your system specs and how many people will be connecting. I never really noticed any difference the time that I did try out the server installation but I only had 10 people at the most on my 3 GHz Core 2 Quad with 8 GB of RAM. With a 150 Down 50 Up connection. If you are looking to go CLI only you can check out this post that I made back when I was trying to accomplish the same thing. 

[http://ubuntuforums.org/showthread.php?t=1924331](http://ubuntuforums.org/showthread.php?t=1924331)

Basically this is what I did:

Don't forget to backup /etc/init/lightdm.conf before you start!
 I edited the file /etc/init/lightdm.conf and changed this:
     ```

     start on ((filesystem                          
                                and runlevel [!06]                          
                                and started dbus                          
                                and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1                                 
                                or stopped udev-fallback-graphics))                                
                                or runlevel PREVLEVEL=S) 
     stop on runlevel [016] 

```I changed it to this:
     ```

     start on []
     stop on runlevel [0123456] 

```then I edited ~/.profile to contain an alias to start lightdm. This is what I added.

     ```

      alias startgui='sudo service lightdm start' 

```Then I added an alias to stop lightdm by also adding this:

     ```

      alias stopgui='sudo service lightdm stop' 

```if I want to start up the GUI i enter startgui and if I want to shut it down I do CTRL+ALT+F1 and then enter stopgui.

Pretty much what you are doing is telling lightdm to not start on any run levels. Then by creating that alias in your profile you can execute the command to have it start again.

---

### Post by AMBiEN22 on 2012-02-24
Thanks for the quick reply, I will try that out as soon as possible! Would love to hear other peoples solutions and opinions!

I'm also looking into trying to remote access the computer from my windows 7 main computer.

---

