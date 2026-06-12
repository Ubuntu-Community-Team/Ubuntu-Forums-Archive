---
title: "Virtual box not starting due to ownership?"
date: 2011-06-07
forum: General Help
---

### Post by jang0 on 2011-06-07
Hi,
I am trying to cope with a problem that I have trying to solve for days, but with no succes so far.
I am relatively new to Ubuntu, so forgive me if I ask a silly question.
I recently installed ubuntu 10.04 on a new system and installed Virtual box to run a virtal Windows environment.
I also added an additional 2 Tb hard disk to the system that will be used to store the virtual machine(s).
I managed to add the hard drive in ubuntu and it is recognized as DriveD_ in the Media folder (don't ask me how i did it ... trial and error). I am the owner of this folder. In the media folder there is also a folder named DriveD, and this is an empty folder. The owner of this folder is Root.
When I start Virtualbox, Windows starts up normally, and recognizes the second drive D (which I partitioned and formatted before).
After closing the Windows, Virtual box and Unbuntu, the mystery begins. When I start Ubuntu, the DriveD_ folder is not visible and I cannot start the Windows virtual machine (error message: VD: *error VERR_FILE_NOT_FOUND opening image file).   *When using Tux Commander, I do _not_ see DriveD_. When I use Nautilus to go to the same Media folder, both folders are visible (DriveD and DriveD_). When I open Drive_, the Virtual machine files are present. After doing this, I can start Virtual Box and start Windows normally.
I think it has someting to do with the ownership of the second hard drive that I added (maybe I made a mistake attaching it in ubuntu?) Has anyone experienced this before?

Many thanks for your feedback.
[I]Jan
[/I]

---

### Post by jerrrys on 2011-06-08
your VB install sounds all wrong to me.  use "synaptic package manager" to download the five packages for the host and after you get a guest up and running, load the three guest packages.

or

just go to the VB site for the latest and greatest (4.x).

not that this will happen to you, but i had problems with 4.x on 10o4 so i switch back to 3.x.

either way, good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+virtualbox&sa=Search&cof=FORID:9#1016](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+virtualbox&sa=Search&cof=FORID:9#1016)

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **jang0 said:**
> Hi,
I am trying to cope with a problem that I have trying to solve for days, but with no succes so far.
I am relatively new to Ubuntu, so forgive me if I ask a silly question.
I recently installed ubuntu 10.04 on a new system and installed Virtual box to run a virtal Windows environment.
I also added an additional 2 Tb hard disk to the system that will be used to store the virtual machine(s).
I managed to add the hard drive in ubuntu and it is recognized as DriveD_ in the Media folder (don't ask me how i did it ... trial and error). I am the owner of this folder. In the media folder there is also a folder named DriveD, and this is an empty folder. The owner of this folder is Root.
When I start Virtualbox, Windows starts up normally, and recognizes the second drive D (which I partitioned and formatted before).
After closing the Windows, Virtual box and Unbuntu, the mystery begins. When I start Ubuntu, the DriveD_ folder is not visible and I cannot start the Windows virtual machine (error message: VD: *error VERR_FILE_NOT_FOUND opening image file).   *When using Tux Commander, I do _not_ see DriveD_. When I use Nautilus to go to the same Media folder, both folders are visible (DriveD and DriveD_). When I open Drive_, the Virtual machine files are present. After doing this, I can start Virtual Box and start Windows normally.
I think it has someting to do with the ownership of the second hard drive that I added (maybe I made a mistake attaching it in ubuntu?) Has anyone experienced this before?

Many thanks for your feedback.
[I]Jan
[/I]

If you are new, and you not familar with debugging this kind of issue yourself.. I suggest that you download and burn a copy of Ubuntu 10.10, and install everything with this step-by-step guide.  It includes Virtualbox 4.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat]("http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/")

---

