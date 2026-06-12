---
title: "Unrar"
date: 2006-03-21
forum: General Help
---

### Post by GreveFelix on 2006-03-21
Hello,
I tried to unpack some RAR files. So I installed "unrar". But is it a programm or a extention of "Ark" (or for another programm)?
 Because I dont find it in my programm list and in the "open with list" neither. And when I open the RAR files with ARK, the programm tells me : " The utility unrar is not in your path. Please install it or contact your system administrator".

I am sorry for bothering you but I dont have a clou what to do ......:???:

---

### Post by jamesford on 2006-03-21
not sure but try: unrar e /path/to/file.rar

---

### Post by damu on 2006-03-21
You should probably [install automatix]("http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29"). It allows you to install loads of softwares/packages in  just one click.

One of this packages is an add on so that you can extract formats not originally supported by Ark (including rar).

;)

---

### Post by Sutekh on 2006-03-21
Which unrar package did you install?  The free or nonfree one?

[Ubuntu Packages - unrar-free]("http://packages.ubuntu.com/breezy/utils/unrar-free")

[Ubuntu Packages - unrar-nonfree]("http://packages.ubuntu.com/breezy/utils/unrar-nonfree")

It seems that unrar-free can't handle archives in RAR 3.0 format but unrar-nonfree can.

---

### Post by GreveFelix on 2006-03-23
yes, I installed the free one. I tried now to install the non free one. But actally I dont know exactly how ... :( 

I downloaded the non free unrar files. But now how do I intall the files.

---

### Post by Sutekh on 2006-03-23
Sorry I didn't mean for you to go to the links and download anything.  I just linked them to show you the package descriptions.

That website contains lists the packages that are available in the Ubuntu repositories.  All those packages are ready to be installed through apt-get or in Synaptic.

So the question is, how did you install the **unrar-free** package? Apt-get (at the command line) or Synaptic?


You need the multiverse repository enabled to get the unrar-nonfree package.

Copy and backup your apt-get sources.list then edit it to enable the multiverse repository
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
When the editor opens find *all* the lines which contain **multiverse** like this one
```
# deb http://archive.ubuntu.com/ubuntu breezy multiverse
```
and remove the '#'.

When they are removed, save the file (Ctrl+O) and exit (Ctrl+X)


**To use apt-get to get unrar-nonfree** just type this in a terminal window
```
sudo apt-get update
sudo apt-get install unrar-nonfree
```
and you are away.

**To use Synaptic to get unrar-nonfree**, just open it up, Reload the packages list, then Search for **unrar-nonfree** and Mark it for installation then click Apply.

---

### Post by GreveFelix on 2006-03-24
Hey thank you very much for your support!!
It worked out just as you said....

I felt a little like a dump man, because I was not able to tell the computer what to do. I really appreciate the possibility to get help from the community!!! I am just hoping one day I am able to give something back. ;)

---

### Post by a_hippie on 2006-10-14
I just responded to another forum post.  There is a tiny little program that makes it very easy to extract (unrar) archives.  It's called "unp" and it's in the ubuntu repositories.

I just used it and I was amazed to see how quickly it rebuilt the program that had been rar'd.

wishing you well.

---

