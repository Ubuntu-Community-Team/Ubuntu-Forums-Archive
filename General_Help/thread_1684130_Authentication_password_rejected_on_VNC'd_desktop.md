---
title: "Authentication password rejected on VNC'd desktop"
date: 2011-02-08
forum: General Help
---

### Post by glenriggs on 2011-02-08
Hi

I've been using the Ubuntu desktop for a couple of years now, but I don't have much experience using the terminal.

I've just set up a home server using Ubuntu-server 64bit which will be headless and its main function will be a Mythtv backend.

I've worked out how to use VNC to send a desktop from the server to my laptop, but when I try to use any programs which require root privileges such as synaptic or the user/groups manager, the pop-up asking for authentication refuses to accept my password.

Is there a setting I need to change on the server which prevents remote users from getting root privileges on the desktop?

I can log into the server using ssh and use sudo without any problems

---

### Post by dcstar on 2011-02-08
> **glenriggs said:**
> Hi

I've been using the Ubuntu desktop for a couple of years now, but I don't have much experience using the terminal.

I've just set up a home server using Ubuntu-server 64bit which will be headless and its main function will be a Mythtv backend.

I've worked out how to use VNC to send a desktop from the server to my laptop, but when I try to use any programs which require root privileges such as synaptic or the user/groups manager, the pop-up asking for authentication refuses to accept my password.

Is there a setting I need to change on the server which prevents remote users from getting root privileges on the desktop?

I can log into the server using ssh and use sudo without any problems

If you search out VNC documentation it mentions that you need to manually create a VNC config file in the root user folder - that may be the issue.

Check the log files for any relevant messages.

---

### Post by glenriggs on 2011-02-09
Thanks for your reply.

I set up VNC using this guide:
[http://havetheknowhow.com/Configure-the-server/Install-VNC.html](http://havetheknowhow.com/Configure-the-server/Install-VNC.html)
I've spent over a week messing with it trying to get it to work, is there something missing from their guide?

My problem doesn't seem to be restricted to VNC. If I do ssh -X user@server mythtv-setup, mythtv setup appears properly on my laptop but as soon as I get a pop-up for root authentication, it wont accept my password. Everything works correctly if I log into the server locally, but thats not much use with a headless server!

Thanks

---

### Post by myth1914 on 2011-02-28
I've never seen it done quite this way.  I would suggest, if you're going to have the desktop components installed, and your hardware is capable, just run it as a desktop and use the built in VNC.  I know that's not the optimal solution, but realistically, you'll be using minimal RAM and very little CPU to have the GUI sitting there.  Just my 2 cents.

---

### Post by myth1914 on 2011-02-28
Also, you can use ```
telinit 3
``` To turn off the gui when there is no need to run it, and turn it back on with ```
telinit 5
```

That way, you can run headless and utilize the resources most efficiently while retaining the ability to VNC when needed

---

### Post by glenriggs on 2011-03-01
Thanks for everyone's input, but I got so frustrated with it that in the end I installed Debian Squeeze 64bit on the server, and everything is now working as expected. I'll stick to Ubuntu for all my other machines though!

---

