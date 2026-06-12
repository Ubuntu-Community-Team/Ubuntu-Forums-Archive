---
title: "Installing software from Ubuntu EXT HDD to main desktop"
date: 2010-07-17
forum: General Help
---

### Post by maizuddin35 on 2010-07-17
Hello.
I want you people help. Now, i have install ubuntu 10.04 inside my external hard disk, and it work nicely.
I update and upgrade the ubuntu inside the EXT HDD. and installed some software inside.

Is there a way, that I can install the software that I have install inside this external hard disk into my desktop computer that have low or none internet connection. 

Can I update and upgrade my desktop computer via the ubuntu on the external hard disk? and install some software.

salam.
adib. :)

---

### Post by JustinR on 2010-07-17
If you want, you could just copy the Ubuntu installation partition off your external HDD to main desktop. But if that's not an option / or its too complicated then try the potential solution below.

This solution is pretty complicated, so I would use this as a last resort only - trust me, its not as bad as it seems but some one might have a better solution.

I'm not necessarily sure if this works, but its worth a try since nobody else has responded to far, copy the folder /var/cache/apt from your external HDD and replace the /var/cache/apt on the Main desktop with it. The directory in /var/cache/apt labeled Archives contains all of the updates/programs from the external HDD and the two files in /var/cache/apt are updated some of the package lists so your main desktop looks for the newer files instead of its current package list it has, which should be outdated by know if it doesn't have an internet connection. When you are done with that, also copy this directory onto your main desktop (replacing the old one on the desktop), /var/lib/apt/lists. And one last file, /etc/apt/sources.list. Then try to reinstall your applications with the apt-get command with the --no-download option. It will fetch all packages from the archives instead of downloading them.

Using a graphical solution might cause problems because I'm not sure if you can pass the -no-download option to it.

If this is complicated I can clarify, I wrote this quickly so I might have missed a few things so if you are confused I can help tomorrow because I have to leave, good luck! Also, I can't explain this in much detail but you could use dselect to automate using the apt-get command instead of typing it all out yourself. Search for "Backing up Packages", or you can try this link: [http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html](http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html)

I'll explain more tomorrow, some parts are a little complicated!

Good luck!

---

### Post by maizuddin35 on 2010-07-17
thanks for the reply , I will try , and post a reply back for an update .

---

