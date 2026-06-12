---
title: "can't install .bin in Jaunty"
date: 2009-09-08
forum: General Help
---

### Post by tango_ninja on 2009-09-08
I'm having a problem installing .bin files in Jaunty.  The system does nothing when double clicking on the icon, and I get a **command not found** message when running from terminal. 

In this case, the file is GoogleEarthLinux.bin 

```
me:~$ cd /home/apohran/Desktop
me:~/Desktop$ sudo GoogleEarthLinux.bin
[sudo] password for me: 
sudo: GoogleEarthLinux.bin: command not found
mep:~/Desktop$ chmod +x GoogleEarthLinux.bin
me:~/Desktop$ GoogleEarthLinux.bin
bash: GoogleEarthLinux.bin: command not found
me:~/Desktop$ GoogleEarthLinux.bin --mode text
bash: GoogleEarthLinux.bin: command not found
me:~/Desktop$ GoogleEarthLinux.bin
bash: GoogleEarthLinux.bin: command not found
me:~/Desktop$  
```

Any suggestions?

---

### Post by karthick87 on 2009-09-08
Execute this command in the directory where the bin file is located:

chmod a+x name_of_file.bin
To run:
sudo ./name_of_file.bin

---

### Post by lykeion on 2009-09-08
Try this:
./GoogleEarthLinux.bin

Why the dot slash before running command in current directory??

Read this: [http://ubuntuforums.org/showthread.php?t=731230]("http://ubuntuforums.org/showthread.php?t=731230")

Edit:
getyourkarthick got before me (and yes you might need the sudo to install google earth)

---

### Post by tango_ninja on 2009-09-08
thanks very much.  you have set me straight and I have run my .bin file.  Thanks also for the link explaining **./**

---

