---
title: "PuTTy error"
date: 2011-06-09
forum: General Help
---

### Post by l3v3ll on 2011-06-09
This is a PuTTy issue not an Ubuntu one, but I wasn't sure where to post this. Anyway, when I log onto my school's linux server using Ubuntu terminal it connects. If I use PuTTy in Windows I get a "Server unexpectedly closed network connection" popup. I put in the host name, connection data username, and have the SSH radio button selected with port 22. Something I just remembered, I believe it worked through PuTTy on campus, but does not off campus.

---

### Post by ruffEdgz on 2011-06-09
When you go to this link: [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)
Type in the ip that you are trying to connect to with the port you use to see if its open.

If the tool can't see it, there is a good chance that its being blocked by a firewall.

Also, are you sure the port for getting into the server is 20 and not 22? By default, ssh connections go to port 22 but I know it can be changed on the server side but wanted to make sure.

Cheers!

---

### Post by MSPdwalt on 2011-06-09
Do you need to specify a certificate as part of your authentication?

---

### Post by l3v3ll on 2011-06-09
I am not sure if I need a certificate and yes, I meant 22 and I just tried that website and it says the port is open and accepting connections.

---

### Post by MSPdwalt on 2011-06-09
Is there a reason why you want to use putty instead of gnome-terminal?

---

### Post by l3v3ll on 2011-06-09
Yes I use Windows-only computers.

---

### Post by MSPdwalt on 2011-06-09
Sad...When you SSH from a linux box to that server you don't have to use the -i switch do you?  That's usually how you specify a cert.

Do you have a firewall of any kind on your windows machine?

---

### Post by l3v3ll on 2011-06-09
No just "ssh username@server". And yes it has a firewall. I have tried on 3 different Windows computers and they all act the same. And since the website [ruffEdgz]("http://ubuntuforums.org/member.php?u=147600") gave me says the port is open I think I might just be missing something in the putty configuration.

---

### Post by MSPdwalt on 2011-06-09
Do you even get prompted to accept the RSA key?  Try setting the SSH version to 1 and see what happens.  Even though the default is to prefer 2 but use either I've had issues connecting to stuff with weak RSA keys.

---

### Post by l3v3ll on 2011-06-09
No i do not get prompted and neither 1 or 2 worked. The name of the server is in putty's title bar so it seems to me that it must be finding it.

---

### Post by MSPdwalt on 2011-06-09
What are you using for a firewall? Try shutting it off.  Does it work from windows, off campus, for any of your class mates?

---

### Post by l3v3ll on 2011-06-09
Windows firewall. I will turn it off when I get home, but I can't right now. I will let you know later. Thanks for your time.

---

### Post by MSPdwalt on 2011-06-09
No problem. Just a heads up, if it's windows XP I've had issues with the firewall not actually disabling through the control panel.  Best way to ensure it's dead is to stop/disable the windows firewall/internet connection sharing service and reboot.  

DON'T disable the service in Windows7/Vista/2008 the control panel applet actually does the trick and the service not running messes up file/printer sharing.

And you may wanna check your antivirus program just to make sure it doesn't do any firewalling.

---

