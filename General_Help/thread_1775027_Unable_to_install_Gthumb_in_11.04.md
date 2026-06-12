---
title: "Unable to install Gthumb in 11.04"
date: 2011-06-04
forum: General Help
---

### Post by SirPecanGum on 2011-06-04
I'm unable to install Gthumb in 11.04 with the following error:

magnus@gube:~$ sudo apt-get install gthumb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gthumb : Depends: libbrasero-media1 (>= 2.31.91) but it is not going to be installed
E: Broken packages
magnus@gube:~$ sudo apt-get install libbrasero-media1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libbrasero-media1 : Depends: brasero-common (< 2.33) but 3.0.0-1ubuntu2~natty1 is to be installed
E: Broken packages

Is there a work around? It is not the first time I've had problems installing Gthumb in Ubuntu. I wonder if Ubuntu doesn't like it? Seems to me to be significantly better than any other photo library tool despite the lack of xmp/iptc search facility (which Geeqie can manage). 

A link to a solution or work around would be appreciated. Thanks !

---

### Post by M@x on 2011-07-31
Got the same error when trying via terminal... :(

---

### Post by wavded on 2011-08-05
Same problem, any solutions?

---

### Post by SirPecanGum on 2011-08-17
For me the problem turned out to be with the repository sources - when I enabled the correct repositories gThumb installed correctly. Hope that is of help and sorry for the delay in responding. 

...The repositories or software sources are available through the Edit Menu in the Ubuntu Software Centre...

---

