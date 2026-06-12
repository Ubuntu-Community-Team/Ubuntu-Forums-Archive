---
title: "Remote sessions"
date: 2011-08-26
forum: General Help
---

### Post by daverulz on 2011-08-26
I have ubuntu set up so that I can log in remotely using RDC for mac from my imac. 

I'm having a strange issue, and it;s probably something very simple, it's just not behaving the way I would expect it to, hopefully someone can help. 

If I log in to the machine locally, and start up Virtualbox and within Virtualbox start a VM, then I log in remotely from the imac using the same user, and Virtualbox (or any other application that is runnig for that matter) does not show up on the desktop, as if it's a new session. However if I now go and open virtualbox, it shows the virtual machine as running, but I can't show that machine on the remote session. Any ideas?

Ideally if I have it up and running locally I'd like to be able to log in remotely and see what is happening on the machine locally. 

Thanks in advance for any help!
Dave

---

### Post by aeiah on 2011-08-26
yea it creates a new session. your virtual machine will be locked because its already displaying elsewhere. 

if all your doing on your ubuntu machine is launching a virtual machine, why dont you remote desktop into the vm instead once the vm is running? virtualbox can be set to do that, and then you could launch the vm headless and connect from anywhere on your lan

you could even set up ssh keys between your mac and ubuntu, and then make a script on your mac that does this:
```

ssh username@ubuntu-machine '<command to start vm headless>'
sleep <for however long it'll take to start the vm>
<command to launch the remote desktop app and connect to the vm>

```

---

### Post by daverulz on 2011-08-26
Additionally, the look of the desktop locally and remotely is different. I'm thinking it might be something related to resolution, but I'm not 100% sure

The one with the Launcher along the left is when logged in locally. I can't get the menu's to show in the upper left.

The one with the menu in the upper left is when logged in remotely.

Again, this is with the same user.

Thanks!
Dave

---

### Post by daverulz on 2011-08-26
> **aeiah said:**
> yea it creates a new session. your virtual machine will be locked because its already displaying elsewhere. 

if all your doing on your ubuntu machine is launching a virtual machine, why dont you remote desktop into the vm instead once the vm is running? virtualbox can be set to do that, and then you could launch the vm headless and connect from anywhere on your lan


Is there any way to not create a new session?

Ultimately I am just going to be connecting to the virtual machines directly, I have that up and running beautifully. I'm just trying to figure out  how to manage remotely logging in. 

For example, if I remote into the ubuntu box and start up virtual box and the vm, then disconnect from the ubuntu box, when I try to log back in it starts a new session again and I have no control over the vms. 

I'm just trying to wrap my head around this before I put it into action and run into problems. 

Thanks!
Dave

---

### Post by daverulz on 2011-08-26
to add a little bit more information, the ubuntu box is going to be sitting in the server room without a monitor. I will not be able to log in locally to start and stop the virtual machines. Being able to log in remotely to the same session is required if I want this to work the way I had envisioned.

---

### Post by daverulz on 2011-08-26
Ok, so using X11vnc and chickenoftheVNC I'm able to log into my running session, I guess that works

---

