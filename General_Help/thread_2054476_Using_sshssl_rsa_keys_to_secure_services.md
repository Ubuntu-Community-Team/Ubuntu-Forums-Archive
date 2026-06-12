---
title: "Using ssh/ssl rsa keys to secure services"
date: 2012-09-07
forum: General Help
---

### Post by kmas on 2012-09-07
Hey guys I know its been 3 years but I am having an issue on this topic and not too many documentation out there. 

I have a major confusion on where the certs should go. 
For instance, at the server I run 

```
xvnc -ssl SAVE
``` 

it goes saves the certs with passwords. 

then I open SSVNC on the server and my certs are as follow
```
MyCert: ..../server.pem
ServerCert: ...../server.crt
```

now at the SSVNC
```
Host: localhost:5900
```

and this connects perfectly. But this connection was however on the fly. 

so I create a file called 

```
/etc/init/x11vnc.conf
start on login-session-start
script
x11vnc -xkb \ 
       -noxrecord \ 
       -noxfixes \ 
       -noxdamage \
       -display :0 \ 
       -rfbauth /etc/x11vnc.pass \ **# can this be used with SSL?**
       -auth /var/run/lightdm/root/:0  \
       -forever \
       -bg \ 
       -o /var/log/x11vnc.log \ 
       -rfbport 5901 \
       -ssl .../server.crt \** # are the cert correct?? **
       -sslverify .../server.pem 
end script
```

With this setup now, 

Keeping my certs are as follow
```
MyCert: ..../server.pem
ServerCert: ...../server.crt
```

now at the SSVNC
```
Host: localhost:5901
VNC Password: ********

```

but in my logs,
```
[CODE]07/09/2012 08:36:54 rfbProcessClientSecurityType: executing handler for type 2
07/09/2012 08:36:54 Couldn't read password file: /etc/x11vnc.pass
07/09/2012 08:36:54 rfbAuthProcessClientMessage: password check failed
07/09/2012 08:36:54 rfbClientSendString("password check failed!")

```[/CODE]

---

### Post by oldos2er on 2012-09-07
Post moved to its own thread.

---

### Post by krunge on 2012-09-08
How did you create /etc/x11vnc.passwd?  Or does it even exist?

You can use the x11vnc -storepasswd command to create it initially, and then use it as you have in your cmdline above.

Yes, the VNC password you use via -rfbauth can be used with SSL. It is a separate auth check (done after the SSL channel is set up.)

---

