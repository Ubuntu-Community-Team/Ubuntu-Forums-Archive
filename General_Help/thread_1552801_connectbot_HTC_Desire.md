---
title: "connectbot HTC Desire"
date: 2010-08-14
forum: General Help
---

### Post by weeman7007 on 2010-08-14
Hi folks, I have recently purchased an HTC Desire, I have connectbot working via wifi, but if I use mobile internet I can't get it to work, how do I solve this problem? It is also my first experience with SSH so please be gentle :P

Also if you could tell me how to get mplayer to play videos on the remote screen that would be fantastic.

However more importantly I would like to know how to make commands stay running after I disconnect, for example running aria after I have logged out of my remote laptop. This would save battery on my phone due to being able to switch off network activity as well as application activity.

Many thanks in advance

---

### Post by Aearenda on 2010-08-14
> Hi folks, I have recently purchased an HTC Desire, I have connectbot working via wifi, but if I use mobile internet I can't get it to work, how do I solve this problem? It is also my first experience with SSH so please be gentle
I'm assuming you have mobile data turned on, so you can browse a web site for example. 

When you try to connect, are you using a public IP address that is accessible through your broadband modem, or a local one?
Local ones typically look like 192.168.n.n or 10.n.n.n. 
If you are trying to connect from the Internet at large using one of these it won't work - you're going to have to find out the IP address of your modem and then change the modem's settings to let SSH traffic through its firewall.

> Also if you could tell me how to get mplayer to play videos on the remote screen that would be fantastic.

I don't know how to do this, and I'm not sure I even understand the question!

> However more importantly I would like to know how to make commands stay running after I disconnect, for example running aria after I have logged out of my remote laptop. This would save battery on my phone due to being able to switch off network activity as well as application activity.

You can use the nohup command to allow commands to survive disconnection. No input is possible, and output goes to a file.

---

### Post by prshah on 2010-08-14
> **weeman7007 said:**
> It is also my first experience with SSH 

I would like to know how to make commands stay running after I disconnect,

Use "screen"; it's in the repos.

Example: 
a) type "screen" and press enter (twice); you will land up at the same command prompt.
b) Issue your command
c) Once you are satisfied your command is running and you want to quit, use Ctrl+A, Ctrl+D (in order) to "detach" the screen session.
d) "exit" your ssh session.

To get back to your screen session, login with SSH again, then use the command```
screen -r
```

If you plan to use only a single command, you can preface it with screen; eg```
screen sudo apt-get -y upgrade
```

Please see the man page of screen (after installation) for more details.

---

### Post by cj13579 on 2010-08-14
> **weeman7007 said:**
> Also if you could tell me how to get mplayer to play videos on the remote screen that would be fantastic.

If you have VLC installed on your system you could use GMote : [www.gmote.org](www.gmote.org)

---

### Post by weeman7007 on 2010-08-14
I wasn't sure what IP address to use because I thought if I used the public one then it wouldn't know which computer to control, but I guess that's where port forwarding comes in. 

Screen does the job perfectly thanks.

I'd prefer to use mplayer and have in fact found a solution after being at work for a few hours.

I have another question however, how do I make my public IP address static, I'm assuming that I don't really have too much control and therefore would need to talk to my ISP.. I'm hoping there is a way around it though!

Thanks again for all your help!

---

### Post by Aearenda on 2010-08-14
To make your address static you need to talk to your ISP. Or, you can use a dynamic DNS service (I use dyndns.com) so that you can use a proper DNS name and have it automatically updated when the IP address changes, using ddclient on your server for example.

---

### Post by weeman7007 on 2010-08-23
Sorry about the late reply, I've been busy at work :) the dynamic DNS thing worked a treat! Thanks very much!

---

