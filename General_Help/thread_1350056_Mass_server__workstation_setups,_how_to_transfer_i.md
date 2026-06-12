---
title: "Mass server / workstation setups, how to transfer installed software packages?"
date: 2009-12-08
forum: General Help
---

### Post by xlinux1010 on 2009-12-08
I've been doing some searching on this but haven't found a lot of specific info... what I want to do is to transfer all the installed packages from an ubuntu based linux machine onto other machines, basically they are machines running on different hardware (and some on cloud / hosted environments as well) so I want to keep the base ubuntu system files different on each machine but want to be able to interchange the installed software packages (examples of this would be firefox, openoffice as well as a bunch of specific 3D and scripting / ide packages)
 
Does anyone have any information as to which directories to copy to the new machines? I assume /bin /usr/bin /home (etc) but am not sure of which others, basically which do I need to keep as original for the hardware, etc to work properly?
 
Thanks for any advice

---

### Post by dcstar on 2009-12-09
> **xlinux1010 said:**
> I've been doing some searching on this but haven't found a lot of specific info... what I want to do is to transfer all the installed packages from an ubuntu based linux machine onto other machines, basically they are machines running on different hardware (and some on cloud / hosted environments as well) so I want to keep the base ubuntu system files different on each machine but want to be able to interchange the installed software packages (examples of this would be firefox, openoffice as well as a bunch of specific 3D and scripting / ide packages)
 
Does anyone have any information as to which directories to copy to the new machines? I assume /bin /usr/bin /home (etc) but am not sure of which others, basically which do I need to keep as original for the hardware, etc to work properly?
 
Thanks for any advice

There are tools for creating a custom install disk from an existing installation, I suggest you do a search for these and see if they are what you need.

---

### Post by xlinux1010 on 2009-12-09
thanks, I'm actually creating my own install disks at the moment.... I guess this is the only way to do this? Since most of the software is compiled, it can't just be transferred to a machine with different hardware? (since this would save time over creating new install disks and installing)

---

### Post by iMisspell on 2009-12-09
I cant rember the details, but im pretty sure there is a way to create a list of programs using Synaptic, saving the list and then using that list to install the porgrams to other machines. Time wise it seams to be the same as creating your own install disc, but maybe something to look into.

Maybe...
Synaptic Package Manager -> File -> Generate package download script


_

---

### Post by xlinux1010 on 2009-12-09
For VPS and cloud servers it isn't possible to install from a disc since they just give you a machine that is already installed on their system, which is another reason why I'm wondering about other methods besides just making a full install disc, any additional info is appreciated

---

### Post by earthpigg on 2009-12-09
well... you could set up your own local internal repository. googling for "creating an ubuntu repository" has a few results, but ive never done it so i wont recommend any specific guide/how-to over any other.

whenever you install a package on a system, the .deb gets put in /var/cache/apt/archives

...so, if your machines are all on a LAN together, you only need actually download it from the internet a single time (maybe twice if some machines have 64 bit ubuntu) and then move it all over your LAN (im assuming that copying large files within the lan is faster than downloading them from the internet).

i suppose the local apt archive, on a 'master machine', would be the base of your custom repository.

---

### Post by xlinux1010 on 2009-12-09
Thanks, I'll look into the internal repository...

Any further information is appreciated, I'm not sure if, for most software packages, whether I can just copy over the files to  /var/cache/apt/archives and they will run fine, I plan on trying it myself but have been doing a lot of stuff involving setting up servers the last few days so if anyone has done this for themselves please post any info

---

