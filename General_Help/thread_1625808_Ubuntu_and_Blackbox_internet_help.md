---
title: "Ubuntu and Blackbox internet help"
date: 2010-11-19
forum: General Help
---

### Post by thesilentfool on 2010-11-19
Short and sweet: for some reason when I'm using Ubuntu with gnome, I had relatively few problems with the internet connection (I'll explain below). But whenever I log in using Blackbox, it seems as though Blackbox recognizes that the internet is there, but doesn't know how to access it. Like if I ask it to grab something from the repositories, it can see the file, tell me how big it is, and ask if I want to download it. If I say yes, it then informs me that it cannot access the repositories (whereas in Gnome, it will work just fine). Similarly, I can't get anywhere with my browser.

The problem I had with Ubuntu originally was that I have a Broadcom wireless card in my computer, so it required a firmware install in order to get it up and running. This was back when I knew absolutely nothing about the terminal and was just asking people for commands to copy and paste into the terminal to get it to work, and miraculously, after about an hour it did, so is it possible that Blackbox isn't seeing the firmware? I don't think it's likely considering that it can see what's in the repositories. Today, I still know very little of the command prompt (I know commands and how to use them, but I don't really know what they do, and I don't know very many of them) so I'm really at a loss as to what the issue is. Could someone please enlighten me?

---

### Post by Zookalicious on 2010-11-19
What happens when you try using a web browser? If you are running wirelessly, it is possible that you are simply not connected to a network. A gnome-panel utilty takes care of wireless connections for you when running gnome, it will not automatically connect in Blackbox. 

The reason why you can see the sizes and names of files in repositories if because your computer stores an offline copy of them everytime you run an update.

---

### Post by thesilentfool on 2010-11-20
> **Zookalicious said:**
> What happens when you try using a web browser? If you are running wirelessly, it is possible that you are simply not connected to a network. A gnome-panel utilty takes care of wireless connections for you when running gnome, it will not automatically connect in Blackbox. 

The reason why you can see the sizes and names of files in repositories if because your computer stores an offline copy of them everytime you run an update.

When I run a browser nothing happens. How do I get the gnome utility to work over in blackbox? Or can I? Are there alternative methods to fetching a connection?

---

### Post by Zookalicious on 2010-11-20
Try editing your ~/.fluxbox/startup file by adding a new line that says 
```

nm-applet &

```
but make sure that it is **before** the line that says something like "exec /usr/bin/blackbox".

If I'm right it should start and automatically connect you to your previously configured wireless connections when you log into the blackbox session.

In order to access your network settings, I believe that (if it is similar to fluxbox) it can be accessed by right clicking on the desktop System > Preferences > Network Connections.

Also you can look into an application called "docker" which will handle gnome-panel applets without the gnome panel. 
```

sudo apt-get install docker

```

---

