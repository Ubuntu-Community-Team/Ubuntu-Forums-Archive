---
title: "GeForce 2 MX"
date: 2006-02-07
forum: General Help
---

### Post by Nitrous570 on 2006-02-07
Hello, I need to find graphics drivers for this video card, and how to go about installing it. is this the right driver to download? :

[http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html")

Also, do u downlaod it and then go into the terminal and go 
sudo apt-get install NVIDIA-Linux-x86-1.0-8178-pkg1.run 
?

and what is SuSE users?
thx for ur help. I just need to get the drivers for this video card installed under linux. Thx for ur help.

---

### Post by kakashi on 2006-02-07
try chmod 777 <path to file>
/<path to file>./file

---

### Post by kosmic on 2006-02-07
I think you are a little bit confused, SUSE uses the RPM file format and Debian distros (like Ubuntu) use .DEB file format.
 
To install your Graphic card just fire up synaptic and search for "nvidia"
 
sudo apt-get install is only to install programs that are in the repositories you can't do that to install program you get from other places
 
Alwayws read the README file that should be with that archive.

---

### Post by MartinG on 2006-02-07
To install drivers for NVidia cards, the best guide is tseliot's HOWTO, which covers both the repository drivers and the ones from the NVidia site:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Nitrous570 on 2006-02-07
[QUOTE=MartinG]To install drivers for NVidia cards, the best guide is tseliot's HOWTO, which covers both the repository drivers and the ones from the NVidia site:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)[/QUOTE]

which ones do I install. The repository drivers or the ones fromt the site?

---

### Post by Global Havok on 2006-02-07
Either should work.  You should take the easy route install via synaptic.

---

### Post by sjh on 2006-02-08
The GeForce 2 Mx (and Mx 400 like I have) fall in a crack.  I got mine working, on a clean install using this:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Hope it works for you
SJH

---

### Post by akiro.yamamoto on 2006-02-08
I think you have to use the Nvidia legacy drivers for your card.

---

