---
title: "Enable Remote Desktop from CLI"
date: 2009-09-02
forum: General Help
---

### Post by snorkytheweasel on 2009-09-02
I am at a remote computer and forgot to enable RD on a jaunty desktop when I was at the computer. Using the command line how do I enable remote desktop (so that I can connect into GUI)?

---

### Post by XCan on 2009-09-02
The messy way is to edit ```
 ~/.gconf/desktop/gnome/remote_access 
``` and restart vino. But I think it would be way easier for you to simply enable x-forwarding and type ```
 vino-preferences 
``` to do it graphically.

---

### Post by DFlame on 2009-09-02
To make a slight expansion to XCan's post, you'd need to add a flag to your SSH connect command. For example:

```
ssh user@ipaddress
```

would become..

```
ssh -X user@ipaddress
```

After that, when you open vino-preferences - It will appear on your local computer as if it were on the server itself. Just a matter of enabling the feature in the window that appears after that :)

---

### Post by fluffman86 on 2009-09-02
Here's how I do it:
First, set up an ssh server on the machine you want to connect to:
```
sudo apt-get install openssh-server
```
Your standard username and password are what you use to connect.

Go ahead and test this connection from another computer with:
```
ssh username@192.168.1.103
```
Where the IP is the IP or URL of the machine you want to connect to.

If that works, then while you are already connected to the machine via ssh, install a VNC server:
```
sudo apt-get install tightvncserver
```
And then set up your VNC server on an unused X display:
```
vncserver :86
```
the "86" can be any unused X display; typically Ubuntu only uses 0 or 1.  

Now exit your SSH session (type "exit") and you will return to your local shell.  Install xtightvncviewer:
```
sudo apt-get install xtightvncviewer
```

Open a VNC window with:
```
vncviewer -via username@192.168.1.103 localhost:86
```
First, that will establish a secure SSH connection just like before (with the "-via" part) and then it opens the local display that you created before.

Once you're done using VNC, you can just close the window that you opened.  To stop running display 86, just ssh back into the server, and run:
```
vncserver -kill :86
```

More information:
[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)
It's kinda old and based on red hat, but it still mostly works.

---

### Post by snorkytheweasel on 2009-09-02
It all went well until

[FONT="Courier New"]Open a VNC window with:
```
vncviewer -via username@192.168.1.103 localhost:86
```
First, that will establish a secure SSH connection just like before (with the "-via" part) and then it opens the local display that you created before.
[/FONT]

The command returned:
```
leon@voip-backup:~$ vncviewer -via leon@10.21.1.16 localhost:86
leon@10.21.1.16's password:
Error: Can't open display:
```

However,
[LIST] 
[*]if I use web browser to access [http://10.21.1.16](http://10.21.1.16)
On the screen I get :
"It works!"

I guess that's a good thing.

[*]if I use VNC Viewer from a remote machine, I get

[IMG]http://truthfordummies.com/images/computer/tight-vnc_error.jpg[/IMG]
[/LIST]
The user in question, leon, is the user id I'm using to do all of the CLI and VNC work.

Close, but I'm not whipping out the cigar lighter just yet.:P

---

