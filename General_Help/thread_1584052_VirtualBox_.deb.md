---
title: "VirtualBox .deb???"
date: 2010-09-28
forum: General Help
---

### Post by dougalkerr on 2010-09-28
Does anyone know where I can find the complete VirtualBox .deb file for Lucid? That is the one that doesn't need an Internet connection to install VirtualBox.

I downloaded the .deb available from virtualbox.org but, when I copied it to a desktop I have without Internet connection I can't install it because it looks for a connection to the repositories.

Thanks.

---

### Post by walwal on 2010-09-28
try this : [http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb](http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb)

---

### Post by SeijiSensei on 2010-09-28
What do you get when you type "sudo dpkg -i /path/to/virtualbox.deb"?

It may require that other files called "dependencies" be installed as well.  Perhaps they're available on the CD you originally installed from.  Otherwise you need to connect this machine to the internet during the installation.

---

### Post by Elfy on 2010-09-28
I'm almost certain that it will need a couple of dependencies.

On a machine that is connected you can get hold of those packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) search for the file and the version of ubuntu you are running.

Once you have those files on the machine not on the net - install them first - then try again with virtualbox.

---

### Post by dougalkerr on 2010-10-16
Sorry guys I've been away.

Haven't had time to scutter about so, I hauled the desktop machine to my router and connected via wire.
All installed.
I won't say it is solved because I firmly believe that Sun should make all dependent files built into the package as Microsoft programs do and if they are not there then the package should hunt down and install the files as needed...

---

### Post by Elfy on 2010-10-16
> **dougalkerr said:**
> I won't say it is solved because I firmly believe that Sun should make all dependent files built into the package as Microsoft programs do and if they are not there then the package should hunt down and install the files as needed...


Which is exactly what would have happened if you had been connected when you tried to install it.

---

### Post by asdlfkjdw202011 on 2010-10-16
The idea behind dependencies is that they are files potentially reused by multiple applications, thus installing them only once as an individual package is more desirable than including them in every single application over and over. :)

As for the package tracking them down as needed, it will. That's what it does when it looks to the repository. It will require a source for this though, be it an install CD or the Ubuntu repositories.

---

### Post by dougalkerr on 2010-10-16
Touches forestpixie... I did notice. I would like to get one over on all Windows users (myself included) when ever I want to install a Linux prog. It is a pity that we are still some way behind in this area when we try to install a standalone package like Sun's VB.
I don't know of a file from them that doesn't necessitate having a Network connection to complete the install, that's all I'm saying.

I do appreciate the huge leaps and bounds that the Linux community has made in just the last couple of years, especially Ubuntu. I only wish I had the know how to contribute more technically. However, that may change if I have time for a Uni course that is geared for Linux learning...

---

### Post by Elfy on 2010-10-16
I know what you mean. But ... :)

I'd rather this > they are files potentially reused by multiple applications, thus installing them only once as an individual package is more desirable  than the other option. Though I appreciate that it is a lot easier to deal with when you have a net connection.

> However, that may change if I have time for a Uni course that is geared for Linux learning...Good luck with that then - hope you get what you want.

---

### Post by dougalkerr on 2010-10-16
Thanks forestpixie

---

