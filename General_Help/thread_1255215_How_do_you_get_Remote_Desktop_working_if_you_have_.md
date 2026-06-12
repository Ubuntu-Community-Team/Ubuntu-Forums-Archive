---
title: "How do you get Remote Desktop working if you have not logged in yet?"
date: 2009-09-01
forum: General Help
---

### Post by infocom on 2009-09-01
Hi

Seems to be a lot of asking about this but no answer yet, not one I can find that is suitable...

If I have not logged in to my Ubuntu machine, then VNC does not work. So **how can I get Remote Desktop to start before the login** so I when I connect I can see the login screen and login as normal? 

I dont want to SSH to login like some others said you should do, and I dont want automatic login due to security as others also said. I want Remote Desktop as it is to start before a user logs in so they can use Remote Dekstop and then login. 

Thanks

---

### Post by DFlame on 2009-09-01
I think you need to take a look at [FreeNX](https://help.ubuntu.com/community/FreeNX). It beats the stuffing out of VNC in terms of speed, it's pretty secure and can be accessed before a user logs on.

[XDMCP](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu). Would also work, and it does offer a native solution.

---

### Post by infocom on 2009-09-01
I enabled automatic login for my user as a temporary measure but when it logs in it asks for the "password for default keyring to unlock" before starting Remote Desktop, so this solution does not work anyway unless that is disabled too which would be really bad with automated login.

---

### Post by infocom on 2009-09-01
thanks DFlame but the setup intructions just lose me, seems quite long winded... i just want something out of the box I got no time to keep messing with command line stuff to set things up. Will just have to stay logged in with screen locked and hope I dont have to restart the computer anytime via VNC unless someone **knows how to start Remote Desktop before login screen**?

---

### Post by XCan on 2009-09-01
Sure, the following should work fine. But a word of caution, you'll have to setup a vnc password for root as well.

What you want is for vino-server to start at the login screen, this can be achieved by editing ```
 /etc/gdm/Init/Default 
```

add ```
 /usr/lib/vino-server &  
``` just before 
```
 exit 0 
```

That's all, you should now be able to login through vnc at the login screen, however, you will get booted as soon as you log in. But a simple reconnect fixes that as your user starts up its own vino vncserver. You can also stop yourself from being booted by editing ```
 /etc/gdm/gdm.conf 
``` by commenting out ```
 #KillInitClients 
``` but I find that unnecessary.

Now, remember to setup a password for the vnc-server for root using, for example, ```
 gksudo vino-preferences 
```

---

### Post by infocom on 2009-09-01
will give that a go... thanks

---

### Post by Bucky Ball on 2009-09-01
> **infocom said:**
> Hi

I dont want to SSH to login like some others said you should do, and I dont want automatic login due to security as others also said. I want Remote Desktop as it is to start before a user logs in so they can use Remote Dekstop and then login. 

Thanks

You don't want ssh to login but you're worried about security with auto login?

If you are accessing your machines from outside the LAN network I strongly advise ssh. :)

---

### Post by infocom on 2009-09-01
Yes, auto login in case the PC is nicked is a bigger issue for me than some hacker listening in to my non SSH. I dont know how to do VNC over SSH anyway, I have Real VNC Viewer and I cant see anything about using it over SSH.

---

