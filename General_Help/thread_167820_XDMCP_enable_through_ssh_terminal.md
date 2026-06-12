---
title: "XDMCP enable through ssh terminal"
date: 2006-04-29
forum: General Help
---

### Post by the_tiger on 2006-04-29
I have logged in to my account on a remote machine using ssh. How do I enable XDMCP remotely. The only instructions I can find are through the System menu which I cant see as only have the terminal.

---

### Post by audax321 on 2006-04-29
I haven't ever used XDMCP, but according to this site, you shouldn't use it over the internet: [http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

If you're just using it over the LAN, there shouldn't be any need to go through SSH since only your own computers are using the protocol.

You can forward X11 through SSH, however. This won't display all of your windows, just the ones you choose to run from the remote machine. Here are steps to do this in Ubuntu:

1. ssh -X ip_to_remote_computer
2. run app on remote computer once you are connected: xclock
3. notice how the app from the remote computer runs on your local computer
4. close app and type 'exit' to disconnect from remote computer

This is nice because you only see one window at a time, but I'm not sure if you can show apps that are already running on the remote computer on the local computer. Also from my experiences it is incredibly slow over the internet and you need to know the command for the remote application you want to run.

---

### Post by Slim Odds on 2006-04-29
[quote=audax321]I haven't ever used XDMCP, but according to this site, you shouldn't use it over the internet: [http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html]("http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html")

1. ssh -X ip_to_remote_computer
2. run app on remote computer once you are connected: xclock
3. notice how the app from the remote computer runs on your local computer
4. close app and type 'exit' to disconnect from remote computer
[/quote] 
According to the article (and what I already know), you shouldn't run X over the Internet *without* some kind of encrytped tunneling. I'm not sure that it's possible to tunnel XDMCP. As you mention, you can run individual X applications through and ssh tunnel by using either the -X or -Y options.

Note that in step 3 above, the program does not actually run on the local computer. It runs on the remote with it's "view" on the local computer. That's an important distinction.

---

### Post by the_tiger on 2006-04-29
I used the VNC over SSH wiki to set up a secure tunnel and then followed the resumable sessions post to login to GDM.

VNC over ssh.
[https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29]("https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29")

Resumable sessions.
[http://ubuntuforums.org/showthread.php?t=122402&highlight=gdm+vnc]("http://ubuntuforums.org/showthread.php?t=122402&highlight=gdm+vnc")

When I now use vncviewer as described in the VNC over ssh post it first asks me for my password to set up ssh and then my password for remote access. Not as secure as totally disallowing remote access but more secure than straight VNC. I think!

---

