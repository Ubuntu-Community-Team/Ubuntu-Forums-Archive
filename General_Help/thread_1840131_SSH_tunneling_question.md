---
title: "SSH tunneling question"
date: 2011-09-07
forum: General Help
---

### Post by cyberjar09 on 2011-09-07
Hi,

I would like to set up an SSH tunnel with various clients that are running Ubuntu 10.04.3 LTS. I would like to use terminal to execute commands etc on various machines. 

can I SSH into the clients using their MAC addresses, or do I have to assign them static IP addresses and set up port forwarding?

Is it possible to SSH into the clients from another *nix like Red Hat 6 for instance?

Total SSH n00b here. 
Thanks.

---

### Post by e79 on 2011-09-07
> **cyberjar09 said:**
> Hi,

I would like to set up an SSH tunnel with various clients that are running Ubuntu 10.04.3 LTS. I would like to use terminal to execute commands etc on various machines. 

Simply type
```
ssh username@machinename
```or 
```
ssh username@ipaddress
```> **cyberjar09 said:**
> 
can I SSH into the clients using their MAC addresses, or do I have to assign them static IP addresses and set up port forwarding?
MAC Address can't be used for connecting with SSH, only IP address, so static IP is preferable I guess.

> **cyberjar09 said:**
> 
Is it possible to SSH into the clients from another *nix like Red Hat 6 for instance?

Yes.

Hope this helps

---

### Post by cyberjar09 on 2011-09-07
Thanks a ton e79, i Will test the solution you provided and report back in sometime. =D

---

### Post by e79 on 2011-09-07
Always a pleasure, good luck !

---

### Post by papibe on 2011-09-07
Besides e79's good tips, I just wanted to point out a few things (hope they are not too obvious):

In order to ssh into a machine you need to install the server side of OpenSSH in that machine. The package is called openssh-server, and you install it like this:
```
$ sudo apt-get install openssh-server
```

As e79 already pointed out, if you are in the same LAN than your clients, you can use the machine names to connect to them. In case something is not configured correctly there's a fail safe: the zero configuration. You would access a machine like this:
```
$ ssh user@machine.local
```

Whatever method you use, you also have to consider that in order to connect to the machines you would need a valid user and password. It's very unlikely that the users will share their passwords, so a solution would be to create a special user with admin privileges.

In the case that your clients are in different networks and maybe in home networks, things get a little more complicated, but it is possible (static LAN IPs, port forwarding, Dynamic DNS, etc).

Hope it helps,
Regards.

---

### Post by cyberjar09 on 2011-09-07
Hi papibe,

Thanks for the 'obvious' tips. As I said, im a total n00b so this information was very useful to me. 

Thank you.

---

### Post by cyberjar09 on 2011-09-07
I have installed openssh-server on both the client as well as the server. 

When I try to test if it is working using ```
ssh -v localhost
``` I am able to connect no problem, however, when I try to connect to another computer on the wifi network, I keep getting the error "Permission denied (publickey,gssapi-with-mic,password)." with an exit status of 255.

One of the computers is my laptop (me@mylaptop) and the other is a live cd running on my other computer. (ubuntu@ubuntu)

I tried changing the PasswordRequired to "no" in the sshd_config file but I still get the same problem.

---

### Post by cyberjar09 on 2011-09-07
Update: I guess the live session is not working as the client because I have not set any password for it.

When I used the live session as server I was able to log into my laptop using ```
ssh -X user@ipaddress
``` 

however, when I try to launch firefox for instance, I see the firefox being launched in my server window. This is not what I want, I want to be able to remotely launch the application on my client, not the server. 

How is this possible? only VNC?

---

### Post by e79 on 2011-09-07
> **cyberjar09 said:**
> however, when I try to launch firefox for instance, I see the firefox being launched in my server window. This is not what I want, I want to be able to remotely launch the application on my client, not the server. How is this possible? only VNC?

I hope this is what you want, but to tunnel Firefox over ssh, you might want to have a loot at [http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025). It is a bit old but should still work. If not, have a look here regarding the VNC:  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC).

---

### Post by SeijiSensei on 2011-09-07
> **cyberjar09 said:**
> however, when I try to launch firefox for instance, I see the firefox being launched in my server window. This is not what I want, I want to be able to remotely launch the application on my client, not the server.

If you're using "ssh -X" then running Firefox on the server will result in the application being displayed on the client.  Isn't that what you want?  What if you run a simple X application like xterm?  You should see the little xterm terminal window appear on the client.

I don't know what you mean by "remotely launch the application on my client, not the server."  To run Firefox on the client, you'd just run it normally.  The whole purpose of "ssh -X" is to be able to run X-enabled applications on the server and have them display on the client.

---

### Post by bodhi.zazen on 2011-09-07
firefox is a bit odd, it does not tunnel over ssh -X

You need to tunnel it like this

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

---

### Post by The Cog on 2011-09-07
> **cyberjar09 said:**
> ...however, when I try to launch firefox for instance, I see the firefox being launched in my server window. This is not what I want, I want to be able to remotely launch the application on my client, not the server.

I don't understand what you want to achieve here - I don't know what you mean by client and server. Please can you explain. 

If you are sitting at machine A and using ssh -X to connect to machine B, then:
1: Which machine do you want to run the firefox application?
2: Which machine do you want the firefox window to appear on?

When you use ssh -X, the normal behaviour is that the applications run on machine B, but the display appears on machine A. Firefox is unusual in that if firefox is already running on machine A, then the instance of firefox you start on machine B tells the one on A to create a new window, and then firefox-B exits, so you end up with the entire thing running on machine A. You can prevent this behaviour by launching firefox on machine B with the command **firefox --no-remote**.

---

### Post by cyberjar09 on 2011-09-07
> **The Cog said:**
> I don't understand what you want to achieve here - I don't know what you mean by client and server. Please can you explain. 

If you are sitting at machine A and using ssh -X to connect to machine B, then:
1: Which machine do you want to run the firefox application?
2: Which machine do you want the firefox window to appear on?

When you use ssh -X, the normal behaviour is that the applications run on machine B, but the display appears on machine A. Firefox is unusual in that if firefox is already running on machine A, then the instance of firefox you start on machine B tells the one on A to create a new window, and then firefox-B exits, so you end up with the entire thing running on machine A. You can prevent this behaviour by launching firefox on machine B with the command **firefox --no-remote**.

I think I had the naming all mixed up. I apologize for not being clear enough. 

I am at machine A and using ssh -X to connect to machine B.
Upon connecting to machine B, I wish to launch applications on machine B. 

What I do encounter though is that when launching an application, i.e., firefox, it opens locally on machine A. This is not what I require. 

is VNC my only option?

---

### Post by cyberjar09 on 2011-09-07
> **bodhi.zazen said:**
> firefox is a bit odd, it does not tunnel over ssh -X

You need to tunnel it like this

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

excellent read, thanks for the link.

---

### Post by cyberjar09 on 2011-09-07
> **SeijiSensei said:**
> If you're using "ssh -X" then running Firefox on the server will result in the application being displayed on the client.  Isn't that what you want?  What if you run a simple X application like xterm?  You should see the little xterm terminal window appear on the client.

I don't know what you mean by "remotely launch the application on my client, not the server."  To run Firefox on the client, you'd just run it normally.  The whole purpose of "ssh -X" is to be able to run X-enabled applications on the server and have them display on the client.

you are absolutely right. I had my naming conventions all mixed up. Sincere apologies. I wish to be able to launch an application on the server from the client over SSH.

---

### Post by SeijiSensei on 2011-09-08
Try running other applications besides Firefox.  As others have mentioned, it has a rather unique architecture when used over SSH tunnels.  Good simple tests are apps like xterm or xeyes, which should be available on any machine with X installed.

---

### Post by The Cog on 2011-09-08
I would like to repeat this bit of what I said earlier:> If you are sitting at machine A and using ssh -X to connect to machine B, then:
1: Which machine do you want to run the firefox application?
2: Which machine do you want the firefox window to appear on?

When you use ssh -X, the normal behaviour is that the applications run on machine B, but the display appears on machine A. 
In fact, the application is almost certainly running on B, which I gather is what you want to happen.

If the application appeared on B instead of A, then you would not be able to see or use the application after you launched it. But using ssh -X arranges for the application to tunnel its keyboard/mouse input from A, and send its display commands to a window on A. Thus the person at A is remotely operating the application that is running on B. 

Is your problem that you didn't realise that the application is running on B (because the window appears on A), or that you want the window to appear on B instead of A?

---

### Post by cyberjar09 on 2011-09-08
I am away from the computers right now, ill verify the findings and post back. 

Thanks.

---

### Post by galvatron408 on 2011-09-08
thats normal behaviour. 

from what i've read though, I think you're trying to find a solution to a problem that doesn't exist. you get what i'm saying? 

> **cyberjar09 said:**
> I think I had the naming all mixed up. I apologize for not being clear enough. 

I am at machine A and using ssh -X to connect to machine B.
Upon connecting to machine B, I wish to launch applications on machine B. 

What I do encounter though is that when launching an application, i.e., firefox, it opens locally on machine A. This is not what I require. 

is VNC my only option?

---

### Post by jwbrase on 2011-09-09
> **The Cog said:**
> I would like to repeat this bit of what I said earlier:
In fact, the application is almost certainly running on B, which I gather is what you want to happen.

If the application appeared on B instead of A, then you would not be able to see or use the application after you launched it. But using ssh -X arranges for the application to tunnel its keyboard/mouse input from A, and send its display commands to a window on A. Thus the person at A is remotely operating the application that is running on B. 

Is your problem that you didn't realise that the application is running on B (because the window appears on A), or that you want the window to appear on B instead of A?

From what I'm hearing, Firefox interacts abnormally (either because of a bug or because of a misfeature) with ssh, and instead of running on B and displaying on A, runs on B and displays on B (while presumably sending command line output to A). The OP wants it to display on A, like any other X application over ssh.

---

### Post by The Cog on 2011-09-10
> **jwbrase said:**
> From what I'm hearing, Firefox interacts abnormally (either because of a bug or because of a misfeature) with ssh, and instead of running on B and displaying on A, runs on B and displays on B (while presumably sending command line output to A). No. Actually, firefox starts up on B, and if it figures out that there's already another firefox window open on A, then it tells the Firefox instance on A to open a new tab/window instead. Then the firefox on B exits. So you end up with firefox on B, display on B even though you launched a firefox on A. This only happens if there is already a firefox running on A, and can be suppressed by launching the firefox on B with the --no-remote option.
> The OP wants it to display on A, like any other X application over ssh.That's what I'm not sure of. He's talking of using VNC, which suggests that maybe he wants to run the application on A and the display on A although it was launched from B. Or maybe he saw the display on A and assumed the application was also running on A even though it was actually running on B. But anyway, it seems like he's stopped answering questions.

---

