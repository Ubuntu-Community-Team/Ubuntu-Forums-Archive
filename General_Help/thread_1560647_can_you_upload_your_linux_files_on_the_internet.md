---
title: "can you upload your linux files on the internet?"
date: 2010-08-25
forum: General Help
---

### Post by LxxRyuzaki on 2010-08-25
Like I want the bin folder and all the folders and files in the file system of different linux os's on the internet, except xubuntu.

---

### Post by micheledm on 2010-08-25
> **LxxRyuzaki said:**
> Like I want the bin folder and all the folders and files in the file system of different linux os's on the internet, except xubuntu.

What for? 

And please stop with your text on steroids.

---

### Post by LxxRyuzaki on 2010-08-25
I want the bin folder and the other file system files uploaded on the internet, so, that I can install different linux os's in an easier way than iso or on a flash drive.

---

### Post by quizno50 on 2010-08-25
There are ways of doing internet installs of Linux. However they are quite complex, and VERY slow unless you have a VERY fast connection. A good alternative; is if you have all your computers on the same network you can make one a server and have it host all the ubuntu files then the others can install them from that server (if you're really feeling gutsy you can try and setup PXE and have them boot from the server).

This site may give you some ideas:
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

---

### Post by LxxRyuzaki on 2010-08-25
My computer doesn't have a CD drive, I have no flash drives,and my computer only supports usb, and that following web tutorial did not help me to install Linux. This is why I want the bin folder and the files of the file system of any Linux OS except xubuntu uploaded onto the Internet.

---

### Post by Toz on 2010-08-26
If you're looking at testing out different linux distros from within Xubuntu, how about installing virtualbox and running them as vms from within Xubuntu? 

Instructions at: [http://theubuntunews.blogspot.com/2010/08/virtualbox-328-released-install-on.html](http://theubuntunews.blogspot.com/2010/08/virtualbox-328-released-install-on.html)

You can also download pre-cooked vms and run them (so you don't have to install the O/S yourself). Have a look at: [http://virtualboximages.com/](http://virtualboximages.com/)

/ToZ

---

### Post by varunendra on 2010-08-26
First, please use normal fonts if you are not doing so due to accessibility or some other problem. It will make your posts more readable. Customized fonts are usually meant for only highlighting imp. **parts** of whole text.

Now to your question.

If you want to test different OSes, VMs are the way for you as Toz already said.

If you want to **natively install** any of them on your hard-disk, I'm afraid you don't have many choices.

[LIST]
[*]If yours is a desktop, getting a new internal optical drive is your best bet since it'd go a long way with your experiments as well as regular needs.
[/LIST]


[LIST]
[*]If it is a Laptop/Netbook then your options are:
[/LIST]

[LIST=1]
[*]getting a USB optical drive (all-purpose solution), or
[*]getting a USB flash/hard drive (linux-specific solution), or
[*][network-install]("http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/").
[/LIST]
You can of-course upload any and all of the files to internet, but they will sit there as simple data-files. To perform an installation, you need at least once to boot into an OS which can proceed with the installation process. This requires a BIOS-recognizable boot-strap which I'm afraid is not possible to get from internet while booting! It can be a local drive, or a removable drive, or network - any of whom should be recognizable by BIOS as a possible boot source.

From your last post I assume you have a desktop PC without an optical drive. It supports booting from USB but has no option to boot from network (that's bad!). If this is true, you can install either from a removable drive (which you currently don't have), or from within a currently working OS (not sure about the procedure right now).

If something is wrong in the above assumption, then maybe it will help if you could deliberate a bit more about what you actually want to accomplish, what are the specs of the target system & what resources you have (or can have).

One more thing- why are you constantly saying "**except xubuntu**", what do you mean by it?

---

### Post by LxxRyuzaki on 2010-08-26
You know when you are in a Linux OS and there is something that says install Linux OS, can you upload that on the internet?

---

