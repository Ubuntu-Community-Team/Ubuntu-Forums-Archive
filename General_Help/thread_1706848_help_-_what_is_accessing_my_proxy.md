---
title: "help - what is accessing my proxy?"
date: 2011-03-14
forum: General Help
---

### Post by dananarama on 2011-03-14
Hello,

I am running Hardy Herron on a VirtualBox VM at work to do tasks in Linux from time to time.  I'm currently having a problem that something on my Linux machine is trying to log in to my work environment with my username and an old password.  This is a serious issue, because whenever I start the Linux VM my account at work gets locked out immediately and I have to get IT to unlock it.  

I think it's likely that something has my username and password stored for accessing the proxy here.  Before I got rid of it, I had the 'export http_proxy' line in my .bashrc script so that apt-get would work.  But the problem persists.  I have also removed the proxy settings under synaptic and the Gnome desktop at preferences->Network Proxy.

Any ideas for what could be attached to the username and password?

Thank you all for your help,


Dan

---

### Post by blueridgedog on 2011-03-14
No, but it is an easy matter to wipe the instance and recreate it.

---

### Post by dananarama on 2011-03-14
> **blueridgedog said:**
> No, but it is an easy matter to wipe the instance and recreate it.

I'm unclear - are you talking about recreating the VM or recreating the issue?

Thanks,


Dan

---

### Post by blueridgedog on 2011-03-14
I was suggesting that in the absence of a solution, you could delete the VM and recreate it.  Alternatively, you could delete your user account in the VM and add a new user.  Your invalid credentials are cached someplace, at it is likely it is a user level issue.  I would unplug the host OS's network cable, launch the VM then add a new user account.  Log out, then in as the new user and you can re-attach to the network.  Your issue should be resolved.

---

