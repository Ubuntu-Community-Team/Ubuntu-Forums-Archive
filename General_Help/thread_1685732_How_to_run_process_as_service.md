---
title: "How to run process as service"
date: 2011-02-11
forum: General Help
---

### Post by tmsandeep on 2011-02-11
Hi
   am having a native c process which should be run as service in background
So that it should be started while bootup as a service again. Can anyone please help me

---

### Post by Wtower on 2011-02-11
Hi, take a look at:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by tmsandeep on 2011-02-11
Am bit new to linux can you be clear the link you provided is bit complex

---

### Post by Cheesehead on 2011-02-11
I found the link to be one of the *best* explanations of how to do it.

Upstart is the project name of Ubuntu's init daemon, process #1. Services should be supervised - started, stopped, respawned, etc. by Upstart (init). Upstart provides a lot of services (automatic respawn, multiple conditions for start/stop, unified event signal framework, hooks for pre-start/post-start/pre-stop/post-stop actions, and more) to make your service more robust.

To use Upstart, simply create a .conf file as shown in the link, and put it in the right place as shown in the link. The syntax is pretty easy for a simple 'start upon startup' service.

---

