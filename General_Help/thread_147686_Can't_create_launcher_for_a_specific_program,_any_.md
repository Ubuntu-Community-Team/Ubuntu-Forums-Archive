---
title: "Can't create launcher for a specific program, any advice?"
date: 2006-03-20
forum: General Help
---

### Post by FaytlND on 2006-03-20
So, I am a bit of an Ubuntu newbie, but after a few day of searching the forums, and the web, I think I have it set up close to how I want it.  I still am having one problem, however.  I installed Predixis MusicMagicMixer successfully, and I have no problems running it as long as long as I run it from the terminal.  To do so, I have to cd to the install directory (/home/Software/Predixis/MusicMagicMixer) then use "sudo ./MusicMagicMixer" to actually get it to run.  I cannot just click on the file from File Manager, nor can I execute without sudo...both result in nothing happening.

This program is not distributed as a deb or as source, so to install I just had to untar and execute the file from the directory.  Is there a way to register the command so I can run it from any directory (like you can with gedit, nautilus, etc)?  

Ultimately, the question is, how do I create a launcher on the desktop for this program?  Using the terminal isn't so bad, but I would prefer to simplify things.  Any help would be appreciated.

---

### Post by audax321 on 2006-03-20
You may want to right click the executable, go to properties, the permissions and make sure all the check boxes under Execute are checked. This may fix the problem with having to run it as root (which of course has security implications).

**TO RUN WITHOUT TYPING THE ENTIRE PATH OR CDing TO DIRECTORY:**

You could link the binary to /usr/bin

You would do this using this command:

```

sudo ln -s /home/Software/Predixis/MusicMagicMixer/MusicMagicMixer /usr/bin

```

This will allow you to launch it from any directory by typing: sudo MusicMagicMixer (you need the sudo since that is the only way you said it will run).

**TO CREATE THE LAUNCHER**
To create a launcher in the desktop you have to use gksudo:

gksudo <command>

This will prompt you for the root password prior to running the command. You create hte launcher by right-clicking on the desktop and choosing Create Launcher.

---

### Post by FaytlND on 2006-03-20
Thanks very much for the tip.  I got the link working, but now whenever I type in the command, the program attempts to start, but then I get a java error message.  I imagine that has to do with the software, so i will see if the developer has a fix.

Thanks again for the help.

---

