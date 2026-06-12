---
title: "How to Remotely Shutdown Ubuntu from Win7"
date: 2012-05-12
forum: General Help
---

### Post by Seth.Meyers on 2012-05-12
Hi.
I have a computer running Ubuntu off of the live disk (there's no hard drive) and a computer running Windows 7. They're connected to the same home wifi network. I want to be able to shutdown the Ubuntu computer remotely from the Windows 7 computer. Is it possible?

---

### Post by MG&amp;TL on 2012-05-12
Yes. One way would be to have an ssh client on the windows machine, and a server on the Ubuntu machine, so that you could issue a shutdown command from your Windows machine.

On the Ubuntu machine:

```
sudo apt-get install openssh-server
```

Then you need a client on the windows machine (I recommend Putty), and you can connect to your Ubuntu machine, and issue the following command:

```
sudo shutdown now
```

which should work nicely.

---

