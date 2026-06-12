---
title: "Synaptic Package Manager and terminal wont update"
date: 2009-06-25
forum: General Help
---

### Post by Nyhus on 2009-06-25
Not sure if this is the right place to post this thread, but i'll give it a shot.

I'm pretty new to xubuntu so i'm pretty bad at everything. Installed the OS for the first time a few days a go on a old computer, and to day i installed it on my new laptop side by side with windows. But on this computer(the new one) i cant refresh or install new things in synaptic package manager or the terminal(i get the same error in both). 

The first thing i did was entering SPM to install xubuntu-restricted-extras, but the package manager didnt find it so i tried to reload the package informatian. It downloaded/read packages until it hit nr. 15, then i got a error. I noticed the package it wouldent fetch was language related, so i removed the current language and rebooted. this time there were less packeges to download, but i still got the error, at nr. 11 this time. 
This is the message i got:
[QUOTEW: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://no.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to no.archive.ubuntu.com:80 (129.241.93.37), connection timed out

W: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/...tes/Release.gpg]("http://no.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg")  Unable to connect to no.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]

Then i tryed to update with the terminal, same error at the same package(nr. 11). So at this time i have no idea what to do and how to fix this and i really wont it to work. It's probably woth mentioning that i'm abel to get online, its the computer with updating problems im using right now. Also, it wont let me log in to pidgin. I get a "Unable to authenticate: Authentication Failure" message. Not sure if this problem is related to the original one, but its worth a try.

Hope you guys can help, and that this is the right forum for this thread.

Sorry for my bad english, im for northern europe :P

---

### Post by loomsen on 2009-06-25
Choose another mirror, I can't connect neither.

You probably could do sth like

```

su -c 'sed -i 's/no/de/g' /etc/apt/sources.list'

```

for simplicity, or you can go to system -> admin -> software sources and add another mirror manually.

---

### Post by Nyhus on 2009-06-26
Thats it? Haha, what a relief. Everything works perfect now, thank you :)

---

