---
title: "configure login file remotly"
date: 2010-12-28
forum: General Help
---

### Post by Ceiber Boy on 2010-12-28
My remote machine did an update which required a restart, after the restart i cant see the screen with VNC, is their a way to log in remotely?

I've heard that the login file can be configured to auto login to circumvent this problem, i've got the file /etc/logins.??? but what do i need to change to make logins automatic?

---

### Post by cariboo on 2010-12-28
you need to create a file called custom.conf in /etc/gdm, it should look something like this:

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=cariboo
TimedLoginEnable=true
TimedLogin=cariboo
TimedLoginDelay=10
DefaultSession=une
``` 

substitute your username for mine, and change the seesion type to whatever you are using.

Another way to acess the system is to use ssh and X-forwarding if you have sshopen-server install. Type:

```
ssh -X user@server
```

then once at the prompt type the name of the program you want to run.

---

### Post by pricetech on 2010-12-28
I'd recommend SSH as well, though if you need or want a GUI, NX from nomachine dot com works for me.  There's a Windows client too.

---

### Post by Ceiber Boy on 2010-12-29
> **cariboo907 said:**
> you need to create a file called custom.conf in /etc/gdm, it should look something like this:

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=cariboo
TimedLoginEnable=true
TimedLogin=cariboo
TimedLoginDelay=10
DefaultSession=une
```substitute your username for mine, and change the seesion type to whatever you are using.

Another way to acess the system is to use ssh and X-forwarding if you have sshopen-server install. Type:

```
ssh -X user@server
```then once at the prompt type the name of the program you want to run.

Thank you, this worked a treat. if i delete this file now will it go back to its previous behaviour?

---

### Post by Ceiber Boy on 2010-12-29
between my local and remote machines I have two firewall creating an VPN tunnel for me, therefore both machines act as if they are on the same local network. on my remote machine i have windows running in virtual box, so from my local machine command line i can run as suggested

ssh -X usermane@192.168.x.x VirtualBox

which brings up the virtual box screen, then i can chick on my windows machine, but this just takes so so long to work its unusable, so, i use the terminal server on my local machine to access my remote windows machine. I know it sounds a bit convoluted but it seams to be the most workable solution

I am however open to other suggestions!

---

