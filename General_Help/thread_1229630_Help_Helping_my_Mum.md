---
title: "Help Helping my Mum"
date: 2009-08-02
forum: General Help
---

### Post by kentcb on 2009-08-02
Hi,

My Mum has issues with her Ubuntu installation (not network problems, thankfully). Problem is, she's in Australia and I'm in the UK. I run Ubuntu as well, but I also have a Windows machine if that makes things any easier.

I've been looking into the options for remote support and the most promising seems to be using tightvnc over a reversed SSH tunnel. I want the tunnel reversed to minimize the amount of effort required by her.

I am attempting to write a script that she can run whenever I need to connect to her machine. It will do the following:
[LIST=1]
[*]Start SSH in reverse mode, forwarding her port 5901 to the same port on my router (I have a DNS entry I can use)
[*]Start tightvncserver
[/LIST]
Can anyone validate whether I'm tackling this problem in a sane manner? Am I doing anything obviously stupid based on my description so far?

Also, I'm having problems with the first step (set up reverse SSH). When running this command:
```
ssh -R 5901:localhost:5901 kent@MY_DNS_ENTRY
```
from my machine, I promptly get:
```
ssh: connect to host MY_DNS_ENTRY port 22: Connection refused
```
I have set up my router to forward traffic on ports 22, 5500, 5800, 5900, and 5901 to my Ubuntu box. Any ideas why the connection would be refused?

EDIT: I installed opensshserver and the same commands appear to be doing *something*, but I won't know if it's really worked until I try from work tomorrow. I don't really understand why though. Does opensshserver replace the ssh SSH command?

Thanks,
Kent

---

### Post by jms1989 on 2009-08-02
I believe you will need to install the ssh server.

sudo apt-get install openssh-server

---

### Post by kentcb on 2009-08-03
*bump* Can anyone confirm that I am actually going about solving this problem correctly?

---

### Post by slakkie on 2009-08-03
If you are behind a router you will probably not connect to your external IP which is on the same device as your outgoing interface.. 

You need another box to test if it works, or nmap your own machine: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Be aware that she need to run putty to create that tunnel. So you probably want to make a screenshot of the settings which she has to save. Unless you have ssh clients for windows which run on the cli.. or with batch files.. or something like that :)

---

### Post by kentcb on 2009-08-03
@Slakkie. She is running Ubuntu, so I can just run ssh. And why wouldn't I be able to connect to my machine through my router? I've forwarded all relevant ports onto my Ubuntu machine. :confused:

---

### Post by jms1989 on 2009-08-03
Here something you could try, run this on the computer you want to create a tunnel on. You can change the local port if needed. You can use this to create a SOCKS v5 proxy for a local app to be tunneled over.

ssh -fND localhost:8080 XXX.XXX.XXX.XXX (or domain.tld)

---

### Post by Primefalcon on 2009-08-03
if your going to want to help her, she's going to have to have the ssh server install and the ports forwarded on her router

then you just ```
ssh -X user@ip
```

doing it like that you'll even be able to open apps graphically such as 

```
sudo gedit filetoedit
```

or ```
nautilus /path/to/location
```

---

### Post by slakkie on 2009-08-03
> **kentcb said:**
> @Slakkie. She is running Ubuntu, so I can just run ssh. And why wouldn't I be able to connect to my machine through my router? I've forwarded all relevant ports onto my Ubuntu machine. :confused:

Then setup dyndns for her, setup an ssh server on her machine, create yourself an account with admin group access. And you can do anything you want. Setup IP tables so you can only connect via ssh.. 

Enable X-forwarding and you can do anything you want on her machine..

---

### Post by The Cog on 2009-08-03
As I understand it, you want her to connect SSH to you, not hte other way round. This is the way my mum wanted it, so she could be sure that she could control my access. Also it means that she has no open ports to the internet. 

You are on the right track by the sound of it. You only need to forward port 22 through your router though - I advise that you stop forwarding all the others again.

In addition to forwarding port 22 to your PC, you also have to install openssh-server on your PC. The connection refused message tells me that openssh-server is not yet running and listening. Beware that there are lots of bots out there that spend all day guessing SSH passwords, so make sure all yours are really tough. And look at using public keys instead of passwords - google for password-less SSH.

Use the command **netstat -lnt** to see all the listening ports, and see if someone is listening on port 22.

---

### Post by asmoore82 on 2009-08-03
I wouldn't worry with tightvnc, I just use the built in vino-server for this:
"System -> Preferences -> Remote Desktop"
```
vino-preferences
```

---

### Post by Hobgoblin on 2009-08-03
> **kentcb said:**
> 
Can anyone validate whether I'm tackling this problem in a sane manner? Am I doing anything obviously stupid based on my description so far?


Seems to me you are doing it backwards.

You really need to set up ssh server on her machine and forward ports on her router so you can connect.  Once you've done that there is no input required by your mum, you can forward X via ssh when you connect.

I realise getting your mum to forward ports on her router could be awkward but it's going to save a lot of hassle in the long run.

Might be easier to get her to enable remote administration of the router, then when you've set up the port forwarding, disable it.

---

### Post by kentcb on 2009-08-24
Thanks to all respondents.

I managed to get this working exactly as I wanted - with no configuration at all on my Mum's side of the connection. I blogged about it [here]("http://kentb.blogspot.com/2009/08/ubuntu-ssh-and-remote-support.html").

---

