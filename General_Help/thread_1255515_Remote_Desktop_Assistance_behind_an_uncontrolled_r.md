---
title: "Remote Desktop Assistance behind an uncontrolled router"
date: 2009-09-01
forum: General Help
---

### Post by exutable on 2009-09-01
Hey guys,

I want to give somebody access to my computer with remote access or SSH, the problem is that I live in a dorm and don't have control over the router.

This means:

I can't forward ports

I can't mess with any iptables on the router

I have to find a means outside of forwarding ports


My question is:

Is there something like crossloop for linux(crossloop doesn't really work and especially not for sharing)?

Is there a way to maybe provide ssh access anyways without forwarding port 22 to my IP?



Thanks,

Dane

---

### Post by P4man on 2009-09-01
reverse ssh tunnel:

[http://articles.techrepublic.com.com/5100-10878_11-5779944.html?tag=nl.e011](http://articles.techrepublic.com.com/5100-10878_11-5779944.html?tag=nl.e011)

thats exactly what crossloop does ;)
It does require you initiate the connection though.

---

### Post by P4man on 2009-09-01
Oh, and I just found this:
[http://en.wikipedia.org/wiki/Hamachi](http://en.wikipedia.org/wiki/Hamachi)

Never used it, looks promising though.. have to try :)

---

### Post by exutable on 2009-09-01
The reverse SSH looks sexy, but if I want to have commands go through what options do I leave out?

I don't really understand the part that says, "this option is because you don't want any commands"

---

### Post by P4man on 2009-09-01
I guess the link I gave wasnt the best. Perhaps this explains better:

[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)

---

### Post by kevinatkins on 2009-09-01
OK, this is just the sort of problem I faced in trying to offer remote assistance to Linux users over the net. This should work for you, and makes use of VNC. You'll probably also need to be in contact over the telephone to set things up

On your computer, install the x11vnc package (sudo apt-get install x11vnc);

Your friend will need to install a VNC viewer on his/her computer. Assuming Ubuntu, he/she just needs to run 

```
sudo apt-get install xvnc4viewer
```

Your friend will then need to forward port 5500 from their router to their PC.

Your friend will need to obtain their current public IP address and tell you ([http://www.whatsmyip.org/](http://www.whatsmyip.org/) will give the necessary information).

Your friend will need to open a terminal and run their VNC viewer in listening mode -

```
xvncviewer --listen
```

(Your friend MUST have their viewer running in listening mode before the next step!)

Now, what you need to do is establish a reverse connection to their VNC viewer, which is where x11vnc comes in - open a terminal and run -

```
x11vnc -connect <friend's IP address>:5500
```

where <friend's IP address> is entered in the form xxx.xxx.xxx.xxx without the <>...

Job done - they should be able to see and interact with your desktop...

---

### Post by spegru on 2010-01-04
I'm still struggling with this.
If I dont have control of the remote router, I cant set up port forwarding?
What if both ends of the link are behind NAT?
Also if there are several PCs behind the remote NAT, and I want access to any of them at different times does port forwarding work anyway?

Help please?

---

### Post by zaphod777 on 2010-01-04
Unfortunately I think not unless you have some sort of 3rd party service or network you can both VPN into. 

That is the nature of firewalls. 

That would be an interesting service though have someone setup a VPN server to have both parties connect to so you can both VNC to each other for support. Maybe somthing through "Ubuntu One" would be nice.

---

### Post by junapp on 2010-01-04
I could be misunderstanding, but isn't that exactly what teamviewer does. Other sites like logmein as well?

[http://www.teamviewer.com](http://www.teamviewer.com)
[https://secure.logmein.com](https://secure.logmein.com)

edit: for some reason I had thought that teamviewer was available as a .deb. Guess not but have read that it can be installed under Wine in a Win98 setup.

other links point to :
[https://na.ntrconnect.com/web/default.asp?redir=0](https://na.ntrconnect.com/web/default.asp?redir=0)

---

### Post by krunge on 2010-01-04
> I'm still struggling with this.
If I dont have control of the remote router, I cant set up port forwarding?
What if both ends of the link are behind NAT?
The original post (if I understood correctly) only had no control over the VNC server-side router.  So the VNC viewer-side was used for the incoming connection (reverse VNC connection.)


For the case of both sides having incoming connections blocked and no port forwarding: If there is a common machine on the internet (perhaps at a university or a free shell account) that one or both parties can SSH into you can set up your own port redirection on that common machine (either VNC or SSH traffic):

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out](http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out)[/INDENT]

Otherwise you would need to use a remote desktop company that provides such a service as the other recent posts have pointed out.

---

### Post by mgmiller on 2010-01-04
Another nice reverse vnc application is gitso.  It was developed by google and has a .deb installer.  Super simple gui on both ends.  As in the xvnc, the person who is going to control the desktop (give support) needs to forward port 5500 in their router.  The person with the desktop being controlled (get help) only needs to input the ip address of the other party and click start.

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by Spantiznik on 2010-01-06
I was looking for information like this as I am trying to remote into my Ubuntu 9.10 system from work.

On my Win7 machines I have Logmein installed and I would prefer using this as the software to take over my Ub9.10 system. As I found working on the Ub9.10 system with web developing easier.

Before installing it on the Ub9.10 system would like to get your thoughts on this.

Thanks

---

### Post by exutable on 2010-01-14
I ended up using gitso.  It's pretty awesome.

---

### Post by spegru on 2010-02-04
Thanks exutable and mgmiller. I tried gitso and it does exactly what I wanted! 
No more messing about with firewalls for friends before I can help them remotely, and the _only_ method I have found to connect to a particular PC when the friend has several PCs.

Gitso. Brilliant

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)
(Works with Windows and Mac too)

PS. an interesting thing I discovered is that one you have opened the Gitso session (which brings up tightVNC), you can close Gitso and it still works until you close the VNC session. So presumably Gitso could work with any remote desktop application if suitably configured. All gitso does is open the door.............

---

### Post by zaphod777 on 2010-02-04
Actually in the new release of skype for linux you can now control someone else's desktop.

---

