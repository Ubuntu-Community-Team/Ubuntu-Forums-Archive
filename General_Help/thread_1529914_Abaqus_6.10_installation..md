---
title: "Abaqus 6.10 installation."
date: 2010-07-12
forum: General Help
---

### Post by wobert on 2010-07-12
Anyone has installed abaqus 6.10 on ubuntu latest release (10.04).
 
I just started using ubuntu and have no clue on this.
 
I will really appreciate your help 
 
thanks

---

### Post by wobert on 2010-09-30
I am adding the files from the installation DVD so that hopefully someone can help me with the installation of this software.

So the first level has the following:

sysinfo.tar
setup (no extension or type file)
product folder

I guess the product folder is the indicated for setup, so it has:

Folder "NoVM"
Resource1.zip (size 496,570,164)
MediaId.properties



Resource1.zip has:

Folder1
Folder2 
(Product folders, images, and examples from the program)

MakeExecutableAction_zg_ia_sf.jar
uninstallerCustomerCode.jar


Folder "NoVM" has:

install.bin
Folder "resource"

Folder "resource" has:

comVers.pl
copyright.htm
hp.txt
lmdiag (no type file)
lmhostid (no type file)
lmstat (no type file)
perl (no type file)
QueryServer.pl
readlicensekey.pl


I will really appreciate your help on this

---

### Post by P4man on 2010-09-30
What happens when you run setup? If a double click doesnt work, try it from a terminal so we have a much more verbose output (useful for copy/pasting any issues). Open a terminal and change directory to your cd drive.

```
cd /media/name_of_cd_volume
```

(you can find out the name of the cd volume by pressing "tab" while typing in the path, it will offer all options or autocomplete.

Then start the installer
```
./setup
```

and lets see what happens.

---

### Post by wobert on 2010-10-13
Thank you very much for your response.
I did try the setup from the main folder but did not work.


I went to the folder which has the install.bin  (this is the folder where I usually go to when installed at windows to start the installation).  

So at the terminal  I added 

./install.bin

and this was the message:

"

Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system´s environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to running this program 

"

How can I proceed with this?

Thanks

---

### Post by P4man on 2010-10-14
Its a java application, so you need to install java.
IN system > administration > software sources, make sure universe repository is marked. Then install sun-java6-jre from synaptic package manager. Or copy this in to a terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by wobert on 2010-10-14
In system--> administration--> I do not find software sources 

This is the list of options: additional drivers, computer janitor, disk utility, language support, log file viewer, login screen, network tools, printing, startup disk creator, synaptic package manager, system monitor, system testing, time and date, update manager, users and groups. windows wireless drivers.

The other point is that I do not have internet access on my computer with ubuntu, I have a very problematic network card 

   0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  0c:00.0 0280: 14e4:4315 (rev 01)

I have been trying for months without success, 10.10 version did not help me on this sense.  I am writing this so that if I need internet access, you can help me download it from the net to a usb and install it (or any other alternative).

thanks for your help I really appreciate it.

---

### Post by P4man on 2010-10-14
"Software sources" was moved to the edit menu in the ubuntu software center in 10.10, but you said you where on 10.04. Anyway, thats a moot point if you are offline.

Id suggest you open a new thread for the wifi problem (if you have created one already, throw me a link).

If you must download offline, assuming you are on ubuntu 10.10 now, grab the packages here:

[http://packages.ubuntu.com/maverick/openjdk-6-jre](http://packages.ubuntu.com/maverick/openjdk-6-jre)

Installation  will require you get other packages first, including this one:

[http://packages.ubuntu.com/maverick/openjdk-6-jre-headless](http://packages.ubuntu.com/maverick/openjdk-6-jre-headless)

And probably many other dependencies as well. So much easier if you are online. Cant just connect an ethernet cable for a minute?

---

### Post by wobert on 2010-10-14
Yes, I did open a thread before, here you have it

[http://ubuntuforums.org/showthread.php?t=1538035](http://ubuntuforums.org/showthread.php?t=1538035)

hopefully you can help me now, I have the latest version 10.10 from ubuntu at my computer.

thanks

---

### Post by wobert on 2010-10-30
Hello P4men, 

Should I follow the commands form this page

 [http://au.ubuntuforums.org/showthread.php?t=586032&page=2](http://au.ubuntuforums.org/showthread.php?t=586032&page=2)

just wanted to verify that nothing has changed for the recent ubuntu distribution

e.g.  

chmod a+x install.bin 
 ./install 
is it the same as just getting into the folder and typing in the terminal ./install.bin

thanks

---

### Post by P4man on 2010-10-30
The commands you typed there would work on any linux distro or version (even OS-X I think), but I have no idea about the rest. 

Oh, and you must do that chmod command first, that sets permissions on the file so its allowed to execute, a file you download by default doesnt have that.

I dont know if wobert managed to get it installed, maybe he can help. I dont know the first thing about abaqus Im afraid. If it throws some error messages I can look at them and apply common sense, but no abacus experience Im afraid :S

---

### Post by wobert on 2010-12-04
Hello , me again

I found this link  [http://caejournal.com/showthread.php?tid=1&page=1&highlight=abaqus+installation](http://caejournal.com/showthread.php?tid=1&page=1&highlight=abaqus+installation)

which provides details regarding the installation.

The first steps it states that it is needed the following packages:
a. Java JDK. Sun java preferred.
b. libXp
c. libstdc++5 (compat-libstdc++-33 for centOS)
d. csh

I already have the Sun java,  can you help me with the steps for downloading the rest? I have Ubuntu 10.10, 64 bit

thanks

---

### Post by wobert on 2011-03-25
Please check this website

[http://sites.google.com/site/abaqus2010/help_0](http://sites.google.com/site/abaqus2010/help_0)

I followed the instructions and finally have it running.

Now the issue is that the graphical display is not showing properly the program.  Please review the attachment, the front window is the starting window of the program, the back window is the main window of the program.

Obviously there is a graphics issue, can you recommend me what drivers or plug ins should I download ?

On my computer settings, I have on my visual effects properties the "extra" option checked.


thanks

---

### Post by wobert on 2011-03-26
Here is the attachment showing my screen

thanks

(Is there a way to edit the title of this thread?, now the really issue is how to make the graphics work, the installation from the product is done)

---

