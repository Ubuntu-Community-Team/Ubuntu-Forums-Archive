---
title: "Viewing a desktop remotely"
date: 2010-01-07
forum: General Help
---

### Post by ram2500 on 2010-01-07
Hello everyone, 

I posted about viewing desktops remotely (received no reply), as I have an "off task web-drifting" problem with some students in my classroom, due to the fact that I no longer have my old SynchronEyes program. I have Windows Vista Business/XP Pro machines (32 of them in all) and I cannot view desktops remotely, regardless of the fact that 1) the Remote Desktop Service is enabled, and 2) I know the IP numbers and the domain names. How can I view desktops remotely with the Remote Desktop Viewer tool in Ubuntu, with the fact that the IP addresses are correct and the Remote Desktop Service is enabled on all 32 machines?

This web drifting problem with my students is irritating me.:(

---

### Post by Lars Noodén on 2010-01-08
What have you tried with the remote desktop viewer that does not work?
Try other displays than :0, like :1 :2 :3 etc

Which program are you using, [krdc](http://docs.kde.org/stable/en/kdenetwork/krdc/)?

It's also possible to have them reach over and turn off the monitor.

---

### Post by gradinaruvasile on 2010-01-08
AFAIK Remote Desktop does not let you to only view what they are doing. You will log them out of their session if you connect to the computer with remote desktop.

I suggest installing VNC and run it in background. You can view it without the users knowledge.

---

### Post by ram2500 on 2010-01-11
I have done just that, but VNC doesn't run well as a service in Windows. 
I have simply decided to cut Internet off unless it is needed until I get my SynchronEyes program back, which should be soon. Unfortunately, our content filter, Content Watch, doesn't block little game, forum, social networking and other nuances. And, to make matters worse, we seem to have a proxy hacker as a student somewhere in the school, but no one is speaking up.

---

### Post by Lars Noodén on 2010-01-12
> **ram2500 said:**
> I have done just that, but VNC doesn't run well as a service in Windows. 

Nothing ever does.  

You might find the talented students and redirect their bored mischief into activities that can help you.  Prototyping a server for LTSP based on SkoleLinux or Edubuntu along with a migration plan, including plans for pilot deployments, would not only focus their excess energies but also take advantage of what they have found lacking in the current set up.  

LTSP can the be deployed easily.

---

