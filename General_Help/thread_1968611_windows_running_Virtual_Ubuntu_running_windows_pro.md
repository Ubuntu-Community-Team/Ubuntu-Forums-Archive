---
title: "windows running Virtual Ubuntu running windows programs via Wine"
date: 2012-04-29
forum: General Help
---

### Post by IamNotGoodWithComputer on 2012-04-29
I have a windows machine that I want to take care of but I also have a game that I want to play that occasionally has hackers. So what I was thinking of was emulating ubuntu in a closed environment and running the windows game using ubuntu.  I am wondering about these following things:  What is a good virtual environment that wont affect my host system (lets say I ran a virtual windows and it gets a virus, it wont affect my system)  If wine gets a virus how can I get rid of it?  Does wine require a windows firewall to protect the windows program files used by wine?  If I delete wine will a virus delete itself? If not can I run mse to get rid of it?  If I ran a virtual windows xp lets say and it gets some malawre, can I simply delete the virtual system to get rid of it?

---

### Post by twipley on 2012-04-29
Nothing is 100% safe. There might be unknown vulnerabilities just waiting for themselves to be exploited.

That said, virtual-machine guest systems should not, by design, be interacting in unwanted ways with the host system. In other words, that means malware should stay where it is, locked in the guest-machine container.

One software I would recommend you is VirtualBox. It is able to run lots of games if you know how to use it properly. It is also quite user-friendly. You might ask though in the forums over there if there would be any way to make it safer for your own purposes. I believe avoiding installing guest additions should make it safer, but that might not be such an appropriate way for you. Again, head over their forums.

---

