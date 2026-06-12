---
title: "photorec rovered file directories permissions"
date: 2010-05-04
forum: General Help
---

### Post by n1ght5t4lk3r on 2010-05-04
I recently accidentally deleted a wrong directory of images from a USB memory stick, which I managed to successfully recover using Photorec . Photorec created a couple of directories (which I asked it to put in Documents), which i was then able to re copy back onto the USB disc. My problem now however is that I do not need that almost 4GB of files on my PC but I cannot delete them since the files are all root owner, and being somewhat new to ubuntu I am not sure of how to go about changing the permissions and deleting these files.
Any pointers would be much appreciated, thanks

---

### Post by jobix on 2010-05-04
To delete them, use the sudo operative, e.g.:

> sudo rm your_file_name


If it asks you for the password, it's the same as your normal login password.

You need to do this from a command line inside a terminal. You can open a terminal by clicking Applications->Accessories->Terminal.

---

### Post by n1ght5t4lk3r on 2010-05-04
do I have to do this for each individual file? becasue there are around 500 of them :S

---

### Post by jobix on 2010-05-04
You can do a force remove on all the files or delete the whole directory.

1) e.g., to remove the entire directory named /home/user/nightstalker/Documents/USBfiles

from the Documents directory, i.e., /home/user/nightstalker/Documents, execute:

> sudo rm -rf USBfiles

Be careful and type the command exactly as shown. It won't ask you for confirmation and will delete the USBfiles directory permanently.

2) The alternative is to go down one level down into the USBfiles directory itself and execute:

> sudo rm -rf *.jpg

Again, be very, very careful with this - there is no space between the '*' and the '.'. So if you say "sudo rm -rf * .jpg" it will remove everything without asking. Also make sure you are in the USB-files directory. One way to make this safer is to pattern match, e.g., if your image files begin with P (e.g., P435322.jpg, etc) you can type:

> sudo rm -rf P*.jpg


---

### Post by n1ght5t4lk3r on 2010-05-04
Ah, thank you very much. All gone now :)

---

