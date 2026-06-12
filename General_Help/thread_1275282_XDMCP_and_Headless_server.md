---
title: "XDMCP and Headless server"
date: 2009-09-25
forum: General Help
---

### Post by prem1er on 2009-09-25
I have a headless Ubuntu server running and I want to set up XDMCP so I can use a couple of GUI apps when I am at home.  I'm following the procedure listed [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess") and I wanted to know if anything else was needed on the server for this to work.  I may be a little confused as I didn't install any gnome packages after I installed the server.  Will I need to install something else besides XDMCP on the server in order to get it working?

---

### Post by toupeiro on 2009-09-26
Basically, you don't need X running on your server at all to do this

login to your server, then export DISPLAY=yourclientmachinename:0 and run your gui application.  Your application will look for X running on whatever $DISPLAY is set to.

---

### Post by FunkyRes on 2009-09-26
I've used XDMCP on local networks before but to be honest, there are other technologies that are much better for remote login.

And as mentioned above, you don't need X running on the remote machine.
Best way to do it is to set up X11 forwarding in your ssh configuration, so you can ssh in and launch the application and it will just work.

I do not know how Ubuntu does it, I've only used ssh client on Ubuntu, but most distributions I have used turn off X11 forwarding in sshd by default, so you may need to edit your sshd configuration and restart the server.

Doing it over ssh is a lot more secure than just setting display variable as it tunnels it through ssh.

---

