---
title: "install vidoe driver"
date: 2009-11-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-11-02
Edit:
was resolved but just got a problem see post 4
Edit:
Resolved again see post 8
---------------------------------------------------------------
i downloaded a run file
[NVIDIA-Linux-x86-190.42-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run") ([ License For Customer Use of NVIDIA Software]("http://www.nvidia.com/content/DriverDownload-March2009/licence.php?lang=us") apply to that driver)
made it executable and ran by opening nautilus as root
but i got 
```
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.
```i dont know where this README file is[/code]
Edit:
to install run file
[COLOR="Red"]**Important:**
keep the run file in a place you can remember where it is
some updates will require it to be reinstalled and you will be unlikely to have a gui to do it
i choose /opt/drivers/NIVIDIA/195.22-beta.run to keep it
i don't know how to undo this with out reinstalling[/COLOR]
press [ctrl]+[alt]+[F1]
login
then type
sudo gdm stop
sudo killall gdm
sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run
replace ./ with the address to the file (NVIDIA-Linux-x86-190.42-pkg1.run)
follow instruction
then type
sudo gmd start
and you are done

---

### Post by DeMus on 2009-11-02
> **pqwoerituytrueiwoq said:**
> i downloaded a run file
[NVIDIA-Linux-x86-190.42-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run) ([ License For Customer Use of NVIDIA Software]("http://www.nvidia.com/content/DriverDownload-March2009/licence.php?lang=us") apply to that driver)
made it executable and ran by opening nautilus as root
but i got 
```
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.
```i dont know where this README file is

Don't install using the run file, instead look [_here_]("http://ubuntuforums.org/showthread.php?t=1303215") to install it on a different (and better) way.

---

### Post by pqwoerituytrueiwoq on 2009-11-02
thanks
did find out this
16bit+desktop effect=no titlebar
no i can actually enable extra effects

---

### Post by pqwoerituytrueiwoq on 2009-11-05
dam have an issue the updater manager said i had to do a partial grade
i did
now the 190 driver does not work
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-190: Depends: nvidia-190-libvdpau (>= 190.42) but it is not going to be installed
E: Broken packages
```i managed to get the 185 driver working at least

---

### Post by pqwoerituytrueiwoq on 2009-11-06
anyone?

---

### Post by mo.reina on 2009-11-06
have you tried the ENVY script?
[http://albertomilone.com/]("http://albertomilone.com/")

---

### Post by pqwoerituytrueiwoq on 2009-11-06
still gives me the broken package error
i believe i need nvidia-190-libvdpau (>= 190.42)

---

### Post by pqwoerituytrueiwoq on 2009-11-07
any suggestions?
edit never mind found this command 
sudo apt-get install nvidia-glx-190 nvidia-190-modaliases nvidia-190-libvdpau
on this forum
[http://ubuntuforums.org/showthread.php?t=1266607](http://ubuntuforums.org/showthread.php?t=1266607)

---

