---
title: "How to remote login and allow VNC"
date: 2010-06-16
forum: General Help
---

### Post by scott29 on 2010-06-16
Hi,

I just installed 10.04.  I currently have a monitor but I want to ditch this and use a VNC client to do what I need to on my server.  Here is the process I'm using:

1)  Remote login via SSH from another computer
2)  Once logged in, I run 'service gdm start' to start up GNOME
3)  I have the login set to automatically login in with my user account

At this point I thought I was home free and I could connect via VNC, but now I'm getting a prompt for a keyring unlock, as explained here:  [http://ubuntuforums.org/showthread.php?p=9109399]("http://ubuntuforums.org/showthread.php?p=9109399")

This has been a total pain.

1)  Are there any other simple solutions out there so that I can remotely log in and be able to connect to my server via VNC?

2)  If not, how do I get past this keyring issue?

Thank You!
scott29

---

### Post by cariboo on 2010-06-17
Why not just use X-forwarding? Use the following command:

```
ssh -X user@server
```

then once logged in just type the name of the program you want to run, if you want to run the file manager type:

```
nautilus
```

at the prompt.

---

### Post by scott29 on 2010-06-17
When I try the 'nautilus' command I get the following error:

[B]X11 connection rejected because of wrong authentication.
Could not parse arguments: Cannot open display: [/B]


I'm not sure this will get me what I want, either, although it could work in some situations.  I'm much more comfortable using the GUI when doing many administrative tasks.  I don't necessarily know the names of the programs to run.

There has to be a solution here...I can't imagine that everybody that has a server set up has a monitor attached, and many people don't know the command line to the point where they can effectively manage the server.

---

### Post by CharlesA on 2010-06-17
What OS are you trying to forward X to? If you are connecting from a windows box, you need something like XMing (which I use) to accept the display.

VNC is horridly insecure. If you want to use something like VNC over SSH, I would suggest using something like FreeNX, but I haven't been able to get it to work tho.

---

### Post by scott29 on 2010-06-17
In this example I was forwarding X to the latest version of Mac OSX.  

I also understand VNC is not secure.  I only allow it on my internal network and never access it over the internet.  I'm going to be setting up OpenVPN at some point, so if I do want to use VNC over the internet it will be through a secure VPN connection.

I think the best answer here is how to get past this Keyring issue.  I found a post where the Keyring can be deleted, but I'm not sure that's the right answer and it sounds like it may cause other issues.

---

