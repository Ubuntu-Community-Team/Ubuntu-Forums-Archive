---
title: "Screen resolution not working right."
date: 2006-06-29
forum: General Help
---

### Post by Compucore on 2006-06-29
I just received today my 10 cd's of Dapper drake and I am trying to install Dapper drake on an aptiva 2185-281 machine. The resolution when booting into initially is set to high when loading int the graphical mode. Is there a way of setting it manually to the kernal to say set it at 800X600 at what ever colours you want whether its 16 or 24 bit? Because what is happening my Daewoo monitor cannot handle anything higher than 800X600 24/rebit. And I had already tried the hitting function 4 on the keyboard there to set it at 800X600 16 or 24 and it just does not work. Any ideas guys and gals?? I need to see what I am doing here. 

Compucore

---

### Post by AndyCooll on 2006-06-29
You could edit xorg.conf and remove any screen sizes larger than 800x600. At the command line copy and paste the following:

```
sudo vi /etc/X11/xorg.conf
```

If you've got a gui you can change vi for gedit, a text editor maybe easier to use.

:cool:

---

### Post by Compucore on 2006-06-29
I am not even getting that. When you boot from teh CDROM itself. You are given the options to boot/start ubuntu installation, start with baic vga, Testing memory, Etc. When you look at the bottom of the screen you get some other options where you can choose screen resolution and some other things as well. It's going from there into the gui where it starts showing too high of resolution.Because it is loading from the CD so it gets all the other information as it goes. But does not remember from when I had highlighted in the beginning that I had chosen the option of 800X600. The menu option should have also been given the option to do a text mode option of installation as well. At leas you can work either way if the GUI is set too high in the initial starting. 

COmpucore

[QUOTE=AndyCooll]You could edit xorg.conf and remove any screen sizes larger than 800x600. At the command line copy and paste the following:

```
sudo vi /etc/X11/xorg.conf
```

If you've got a gui you can change vi for gedit, a text editor maybe easier to use.

:cool:[/QUOTE]

---

