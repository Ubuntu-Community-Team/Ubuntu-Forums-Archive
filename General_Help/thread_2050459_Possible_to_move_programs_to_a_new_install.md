---
title: "Possible to move programs to a new install?"
date: 2012-08-30
forum: General Help
---

### Post by 777funk on 2012-08-30
I'd like to try a new install but hate downloading and installing everything again. Is it possible in Linux to backup and move all the programs to a fresh install?

---

### Post by PhantomTurtle on 2012-08-30
Well you can create an iso of all the debs of programs you got through the software center and the ppa's you added to your system using APTonCD. There is a great article at Howtogeek about how to backup and restore them with ease. This is a link to the article - [http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/]("http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/"). You do not need to burn the iso to a CD because that would be a waste of a CD. Instead just create a copy of the iso on a USB or back it up on to something like dropbox and then mount it in Ubuntu. Instructions on mounting an iso are here - [http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html") and it is very easy. Gmount-iso still works in 12.04. 

If you want to save config files of programs you will want to backup the files and folders that start with a "." in your home folder. For example your wine configuration and "C" drive are stored in the ".wine" folder located in your home folder. They are hidden by default and to show them, just press
```
Ctrl + H
```

Just back them up and copy them back to the new home folder after the install.

An easier way to do this is to use Ubuntu One. Simply right click configuration file or folder, move over Ubuntu One and click on synchronize. Another article about it on Howtogeek here - [http://www.howtogeek.com/108000/how-to-synchronize-your-configuration-files-with-ubuntu-one/]("http://www.howtogeek.com/108000/how-to-synchronize-your-configuration-files-with-ubuntu-one/"). I recommend you look at that because it is very short and explains everything clearly.

Once you have backed up the config files just reinstall and sign in at the Ubuntu One client and let it restore the files for you. And that's all there is to it.

To backup PPA's use the YPPA Manager. Install instructions are here - [http://www.webupd8.org/2012/08/y-ppa-manager-0090-released-with-new.html](http://www.webupd8.org/2012/08/y-ppa-manager-0090-released-with-new.html). It is a very straight forward program and will get the job done easily. You will need to install it again on the new install to restore the PPA's and make sure that you don't loose the backup file.

Hope that helps you and answers your question):P

---

### Post by 777funk on 2012-08-30
Sounds like a great option and thanks!

---

