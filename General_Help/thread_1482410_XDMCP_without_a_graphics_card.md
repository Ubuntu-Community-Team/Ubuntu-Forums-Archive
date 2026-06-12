---
title: "XDMCP without a graphics card?"
date: 2010-05-13
forum: General Help
---

### Post by BigWoop on 2010-05-13
Using Lucid here.

I want to run a system that acts as a basic file server, I want to remove the graphics card for the sake of power saving and less heat in the box. 

My machine can boot without the GPU, and I can ping it and use putty to do things, but I'm still new to Linux and don't really know what I'm doing so GUI is best for me atm.

From somewhere I picked up that this is possible (the XDMCP server machine can have no GPU).

This post here [http://www.mail-archive.com/xpert@xfree86.org/msg09293.html](http://www.mail-archive.com/xpert@xfree86.org/msg09293.html), seems to be what I am looking for, but I don't know how to "convert" these instructions to Ubuntu (the files mentioned do not exist on my install anyway).

>  > Hi list!
 > I want to install a terminal server on a PC without  grpahics 
 > card(plaesa don't ask why).I wonder if it is possible.

Yes. 

 > If so, can anyone explain how?

Just disable the local server in /etc/X11/xdm/Xservers  (add a '#' in
the front of the last line) and then use the preferren method for your
OS to start xdm on your server. (/etc/init.d/xdm or such). 

If anyone knows what I should be doing I'd appreciate the input, or if you can suggest an alternative way that I can get a remote gui from my server to a Windows and Linux client. FYI I am using Xming/Putty atm.

I made use of these instructions to get XDMCP working, [https://bugs.launchpad.net/gdm/+bug/408417/comments/15](https://bugs.launchpad.net/gdm/+bug/408417/comments/15), and, [http://www.peppertop.com/blog/?p=690](http://www.peppertop.com/blog/?p=690), so I just need to get it going without the GPU if possible.

Thanks for reading.

---

### Post by BigWoop on 2010-05-14
Hope it's okay if I bump this.

---

### Post by almufadado on 2010-05-14
Your motherboard must be able to start without a graphic card.

---

### Post by BigWoop on 2010-05-14
I did already mention that it can.

The machine boots fine, and as I mentioned I can use putty to get into the machine, but without the graphics card installed XDMCP won't function (the client won't connect).

The link I posted mentions something about disabling the local X server and then using "the preferred method for your OS to start xdm on your server", how do I do that?

---

### Post by dino99 on 2010-05-14
found this oldy howto, if that help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess](http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess)

[http://manpages.ubuntu.com/manpages/jaunty/man1/xdm.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/xdm.1.html)

[http://www.peppertop.com/blog/?p=690](http://www.peppertop.com/blog/?p=690)

[http://marionote.wordpress.com/2010/03/07/ubuntu-xdmcp-access-with-xephyr/](http://marionote.wordpress.com/2010/03/07/ubuntu-xdmcp-access-with-xephyr/)

---

### Post by HiImTye on 2010-05-14
why not skip the graphic end and make it a samba server?

---

### Post by BigWoop on 2010-05-14
> **dino99 said:**
> found this oldy howto, if that help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess](http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess)

[http://manpages.ubuntu.com/manpages/jaunty/man1/xdm.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/xdm.1.html)

[http://www.peppertop.com/blog/?p=690](http://www.peppertop.com/blog/?p=690)

[http://marionote.wordpress.com/2010/03/07/ubuntu-xdmcp-access-with-xephyr/](http://marionote.wordpress.com/2010/03/07/ubuntu-xdmcp-access-with-xephyr/)

Thanks, though I have seen much of that already, I may have missed something, I'll have to peruse it in detail.

@HiImTye, I do have samba set up so that I can share files with Windows (am I misunderstanding your suggestion?), as I said I want the GUI as It's better/easier for me atm, at least until I become more proficient.

---

### Post by HiImTye on 2010-05-14
if you set up the Samba daemon to share the root folder as read/write then you will have access to the entire folder structure and can make changes from your other box (without the need to view the other computer at all) it will be like it is simply another drive.
also, you won't have to worry about sensitive files as root will own all of them so you won't be able to fiddle with them.
just mount whatever folders you use as a network drive (I assume youre using windows)

---

### Post by BigWoop on 2010-05-14
Okay I see what you mean, that might be all right once I have it all up and running, but I'd rather be able to administrate the system properly really.

---

### Post by HiImTye on 2010-05-14
you can still administer the system, using the faster/more efficient command line
[http://ubuntuforums.org/showthread.php?t=191760](http://ubuntuforums.org/showthread.php?t=191760)

if you want remote access without a graphics card you can try this
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by BigWoop on 2010-05-14
Yes I know and I have ssh setup and working, I ideally want a GUI though. :D

---

### Post by HiImTye on 2010-05-14
freenx is a graphic solution, full instructions on how to install it are in the second link

---

### Post by atomizer on 2010-05-14
if you ssh with a linux client, you can do that with a GUI.

you will have to type the command in the commandline to start them.

eg:

```
ssh -X mediabak

tom@mediabak$ rhythmbox &
```

will start rhythmbox with GUI from mediabak on remote computer.
(with the '&' you can use the commandline while the program is running)

---

### Post by HiImTye on 2010-05-14
they want to be able to -see- the programs, simply starting them does not give them access to the display

---

### Post by atomizer on 2010-05-14
dont forget the -X option (manpages say -Y is better)

I see the programs when I use it.

That way I can start a gnome-panel too (from the server on the client) and access all my programs, files and devices without touching my server.

(must say when I opened transmission remote, it wanted to save the file on my client)

---

### Post by BigWoop on 2010-05-17
I really need to do it from Windows if possible.

I really thought the message I posted earlier held the key,

>  > Hi list!
 > I want to install a terminal server on a PC without  grpahics 
 > card(plaesa don't ask why).I wonder if it is possible.

Yes. 

 > If so, can anyone explain how?

Just disable the local server in /etc/X11/xdm/Xservers  (add a '#' in
the front of the last line) and then use the preferren method for your
OS to start xdm on your server. (/etc/init.d/xdm or such). 

Am I just misinterpreting this? (I think I might be.)

I got as far as disabling the X server on the server machine (I think), using this instruction, [http://ubuntuforums.org/showpost.php?p=8372546&postcount=2](http://ubuntuforums.org/showpost.php?p=8372546&postcount=2).

Am I just totally on the wrong track?

---

### Post by R3VAMP3D on 2010-05-17
> **atomizer said:**
> if you ssh with a linux client, you can do that with a GUI.

you will have to type the command in the commandline to start them.

eg:

```
ssh -X mediabak

tom@mediabak$ rhythmbox &
```

will start rhythmbox with GUI from mediabak on remote computer.
(with the '&' you can use the commandline while the program is running)
using ssh -X usually ends up in clunky programs that don't operate normally. 
However, it is possible to have an X11 server on a different machine, and use a machine with video output to connect to it remotely.

---

### Post by BigWoop on 2010-05-17
Ok great any idea how I can do that? (Connecting from Windows especially).

---

### Post by binkiev on 2010-12-06
Solved. Really problem is in new GDM 2.3 which does not launch anyway without X11 launched.
Downgrading GDM to 2.20 (as described in [http://ubuntuforums.org/showthread.php?p=8350408](http://ubuntuforums.org/showthread.php?p=8350408))
and install Xvnc and xinetd (configurations easy to be found anywhere) solving this problem.

---

