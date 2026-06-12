---
title: "Could not open the file /home/ssb/Desktop/ati-dr…installer-8.25.18-x86.run."
date: 2006-06-10
forum: General Help
---

### Post by SSB on 2006-06-10
Downloaded the Linux version of my video card drivers..

ati-driver-installer-8.25.18-x86.run


I open it and get this:

> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
How can I install these drivers?

---

### Post by npodges on 2006-06-10
you have to make it executable first either:

sudo chmod +x file.run

or right click the file, and under permissions, check the boxes for execute.

then when you open it, it will give you the option to run the file. i suggest running it in a terminal though..

---

### Post by SSB on 2006-06-10
I'm brand spankin' new to linux so I don't know my way around the terminal yet. Command help? I click run in terminal and it says i need to be super user.

---

### Post by scxtt on 2006-06-10
i think it'd be best for you to follow some installation instructions - which are peppered all throughout the forums (i have ATI fglrx install instructions posted as well) - works for me in both breezy and dapper ...

---

### Post by npodges on 2006-06-10
well, open up a terminal. applications > accesories > terminal.

navigate to the directory the in which you have the file:

cd Desktop

make the file executable:

sudo chmod +x ati-driver-installer-8.25.18-x86.run

then, run the file

sudo ./ati-driver-installer-8.25.18-x86.run

---

### Post by SSB on 2006-06-10
Ok, thanks for that. Now it said I need to save my X Window configuration file and run aticonfig to setup the configuration. Umm..

Heh, thank you for your patience.

---

### Post by jocko on 2006-06-10
There is no need to install the drivers from ati's binary, the easy way to install  is to get them from the repos. Open synaptic and search for 'xorg-driver-fglrx', or run the command 'sudo apt-get install fglrx' in a terminal.
When that is done you need to run the command 'sudo aticonfig --initial' to tell x to use the correct drivers. After a reboot everything should work...

---

