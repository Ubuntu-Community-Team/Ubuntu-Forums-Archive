---
title: "custom key for FreeNX server"
date: 2010-03-09
forum: General Help
---

### Post by missfroguk on 2010-03-09
Hi all, 

I've just successfully downloaded FreeNX and to my surprise I got it to work painlessly *but* I am trying to change the default keys to custom keys and *that* has not been successful. 

I saw on other posts that people had the same problem as me and got the error message 

```
sudo dpkg-reconfigure freenx-server
update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
Not starting freenx-server, it's already started.
```

It says on the Ubuntu help ([/https://help.ubuntu.com/community/FreeNX#How%20to%20start/stop%20FreeNX]("/https://help.ubuntu.com/community/FreeNX#How%20to%20start/stop%20FreeNX"))

[HTML]To change the default keys to your own custom keys - on the machine hosting the freenx-server, run the command: [/HTML]

and I know it sound like an obvious question/answer but...am I hosting the freenx-server?

I've obviously got freenx but I'm using it to connect to a nx server at Uni, so I'm guessing the Uni is where the freenx-server is in this case?

If I'm right, should I worry about changing the key as I won't be able to do it and should I just assume that the Uni has dealt with the security problem ... or am I wrong and my machine is actually the freenx-server and the problem is elsewhere is still unidentified?

Thank you for your help!

---

### Post by 2hot6ft2 on 2010-03-09
> **missfroguk said:**
> 
and I know it sound like an obvious question/answer but...am I hosting the freenx-server?

I've obviously got freenx but I'm using it to connect to a nx server at Uni, so I'm guessing the Uni is where the freenx-server is in this case?

If I'm right, should I worry about changing the key as I won't be able to do it and should I just assume that the Uni has dealt with the security problem ... or am I wrong and my machine is actually the freenx-server and the problem is elsewhere is still unidentified?

Thank you for your help!
Yes if you're running the server then you're hosting it. Or are you just running the client and the server is out of your control?
I don't know what Uni is.

How to start/stop/restart FreeNX

The FreeNX server is not a service but uses ssh. The following command will stop the FreeNX program from accepting connections. 
```
sudo /etc/init.d/freenx-server stop
```

(Replace stop by start for starting it again)

[Setting up FreeNX]("http://help.ubuntu.com/community/FreeNX")
use this to create a account on the NX server:
```
sudo nxserver --adduser (yourusername) (yourusername is the name you use when logging in on the server normally, without the ()'s)
```
NX server will reply with:

> NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

and add a password

> ```
sudo nxserver --passwd (yourusername)
```
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password: **(enter your NEW password here and hit Enter (I wont be displayed)see below)**
Password changed.
NX> 999 Bye

(you can paste in a good long premade password which is what you will put into the freenx client so make it a good one you'll only need to put it into the FreeNX client for each profile once if you tick the save password in the configuration for (Home and Away)
I'm not sure how long it can be but it can handle at least 30 characters see:
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

Don't forget to restart the sshd daemon after making that change using:
```
sudo /etc/init.d/ssh restart
```

I am not sure if it is really necessary but I guess it can do no harm to restart to freenx server.
```
sudo /etc/init.d/freenx-server restart
```

There is a guide in my sig. below

---

### Post by missfroguk on 2010-03-10
Thanks for your answer!

> Yes if you're running the server then you're hosting it. Or are you just running the client and the server is out of your control?
I don't know what Uni is.


I'm sorry, I wasn't very clear. "Uni" is university. I'm using FreeNX to log on to my files stored on the server at University. I've had to download FreeNX to be able to do this but what I meant is, I'm guessing that the University is the host and I'm the "guest"? 

Anyway, it's odd but despite the error messages I was having, it seems that I did manage to change the key...

---

