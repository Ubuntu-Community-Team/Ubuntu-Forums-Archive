---
title: "ubuntu software center out of date?"
date: 2010-07-20
forum: General Help
---

### Post by searayman on 2010-07-20
if something in the ubuntu software center is out of date who do we notify?

I just installed exaile from the ubuntu software center and it is out of date. I just created a few hundred playlist and am afraid to uninstall it and install the latest version via exaile software repo so when will the ubuntu software center version be updated?


Very Respectfully,

Mike

---

### Post by lovinglinux on 2010-07-20
> **searayman said:**
> if something in the ubuntu software center is out of date who do we notify?

Don't waste your time reporting this, because this is how it works.

> **searayman said:**
> ...when will the ubuntu software center version be updated?

It won't be updated. Ubuntu doesn't upgrade applications with new feature releases, only security patches, until a new version of Ubuntu is released. If you want the latest version of your application you have to download the deb file from the developer or add a third-party repository.

> **searayman said:**
> I just created a few hundred playlist and am afraid to uninstall it and install the latest version via exaile software repo

You should check the developer site to verify if there is any incompatibility with the database between the two versions. Unless the new version is a complete rewrite, is most likely that you won't have any problems upgrading it. Make a backup to be sure. I don't use exaile, but the user data should be saved somewhere like ~/.exaile or ~/.config/exaile.

---

### Post by deek0146 on 2011-03-05
Are there alternative repositories compatible with apt-get I could use that provide up to date software? Or is this a bad idea?

---

### Post by JKyleOKC on 2011-03-05
There are private repositories called PPAs that are compatible with apt-get, and may or may not provide more recent versions of things. Unfortunately, not all PPAs are vetted by anyone other than their owners to make sure that their content is valid; when you use one, you're trusting its owner to be a good guy. And although Linux is, by design, inherently more secure than some other systems, it's still possible for a vandal to destroy it.

You can find out more about PPAs at "launchpad" and there's a link at the absolute top of each forum page that will take you there.

Note that "up to date" does not imply "usable with your system" since many newer versions of software can use features that don't exist in older kernels. If reliability is important to you, stick with the official repositories. If you prefer to live dangerously, the decision -- and its possible consequence -- is up to you.

---

### Post by mynameissagarbhatt on 2011-03-05
just google the name of the software u need......m sure u'll find the latest .deb files.......download them n install.......

---

### Post by Mark Phelps on 2011-03-05
> **mynameissagarbhatt said:**
> just google the name of the software u need......m sure u'll find the latest .deb files.......download them n install.......

NOT that easy!!

If you start just grabbing new .deb files, you will invariably run into the dependency problem.  You will then have to start hunting down and grabbing new libraries as well, and not just the runtime version, but most probably the Development versions.

Worst case (which I've personally seen more than once) you spend HOURS doing this, and when you go to install you get "dependency not satisfiable" -- meaning that you can NOT solve the problem because there is a dependency conflict.

---

### Post by jmszr on 2011-03-05
deek0146,

Here is a link to getdeb.net, they may have the updated software you want: [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/) .

---

