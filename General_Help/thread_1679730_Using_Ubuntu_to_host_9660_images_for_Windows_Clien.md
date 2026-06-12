---
title: "Using Ubuntu to host 9660 images for Windows Clients - Help!"
date: 2011-02-01
forum: General Help
---

### Post by mtwelve on 2011-02-01
Hi,

I wondered if anyone can help me... My overall aim is to be able to share mounted CD images over the network to Windows clients.

I've been generally following instructions from two tutorials but have also searched google and the forums:

[http://www.linuxjournal.com/article/5639?page=0,0](http://www.linuxjournal.com/article/5639?page=0,0)
and
[http://tldp.org/HOWTO/CDServer-HOWTO/procedure.html](http://tldp.org/HOWTO/CDServer-HOWTO/procedure.html)


Now I'm behind a corporate firewall so can't use the Software Center to install packages but have installed the following:
**Samba		**- [http://packages.ubuntu.com/maverick/samba](http://packages.ubuntu.com/maverick/samba)
**WinBind		**- [http://packages.ubuntu.com/maverick/winbind](http://packages.ubuntu.com/maverick/winbind)
**ISO Master**	- As a GUI for creating images
**GMount	**	- As a Gui for mounting the images


Basically I can mount the images. I can share the folder containg all the mounted images using  the GUI (right click > Sharing Options) or write some lines in the smb.conf file.


From the Windows clients I can see the share with the mounted images and I can list the files at the top level of the mounted images but I can access any of the files or folders.


Another wierd thing is I can't attempt to run the Setup.exe locally on the Ubuntu machine, it just says Permission Denied.


I'm sure its got something to do with the images being mounted as root. 
**So my question is can you mount an image as 9660 without it being 'owned' by root? **

**is there another way to share mounted images?** 

or **am I missing something in what I'm trying to do?**



Massive Thanks
mwtwelve

---

### Post by Kirboosy on 2011-02-01
There is a [PXE server]("http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10") if you are trying to deploy images for install. If you install "system-config-samba" you should be able to know exactly how your samba is setup. 

For gaining ownership of the file on the local computer you might just have to ```
sudo chmod 777 "file location here"
```You might not want to use 777. IF you don't understand chmod please look at this [page]("http://www.corantodemo.net/doc/chmod-doc.shtml")


PS. For making your links easier to read and cleaner just use [URL ="website address here"]text to display[ /URL] I added spaces between URL= and /URL so you can see how to do it.

---

### Post by pricetech on 2011-02-01
I have a similar setup, though I only share a couple of ISOs.  I simply share the mounted ISOs via Samba as read only to everyone and I've never had a problem.

---

### Post by mtwelve on 2011-02-01
Thanks for the tips guys, here is a bit more information.

RE: Caboose885
Thanks for the samba-config-manager tip I'll check it out. 

Does it give you a GUI to configure/check Samba?

Can I take ownership of a mounted image...? 
Do I just type something to this effect in the terminal "sudo chmod 777 /home/oxfdev/images/bigabc"
or some threads mention I can use "gksudo nautalis" and do it through the GUI



RE: pricetech
This is exactly what I want to do... Did you take ownership of the mounted images or setup your SAMBA at all?

Also do your Windows clients treat them as a folder of CDs or as a folder of folders? if you know what I mean..



Thanks

---

### Post by mtwelve on 2011-02-02
Hi,

I've had a play with some of things suggested and have got no where:

I didn't find anything regarding **samba-config-manager** or any other GUI installed by default...?


I couldn't take ownership of the mounted image; the chmod and chown commands returned "Permission Denied: Read Only File System"


"gksu nautalis" and "gksudo nautalis" both returned no errors in the terminal but neither actually launched the browser....


Most worrying, and I think the main problem, is that I can't even access the mounted drives locally. They mount fine and I can see list the top level but I get "Permission Denied" if I tried to access any of the files or folders. I experience similar problems if I connect to the mounts from a Windows client


Gracias

---

### Post by coldraven on 2011-02-02
"gksudo nautalis" is wrong
"gksudo nautilus" is right! I just double checked and it works.

---

### Post by Kirboosy on 2011-02-02
Its available in Synaptic and its "system-config-samba"


You could use gksudo nautilus but for my chmod is faster. Either way works.

---

### Post by mtwelve on 2011-02-02
Thanks for more tips I'll try them out now.

Has anyone tried using mountmanager to manage mounts, etc?




Thanks
mtwelve

---

### Post by mtwelve on 2011-02-02
OK; just tried some bits...

Got the Samba GUI installed but it wont run. Probably because im having to get the dependencies manually through [Ubuntu Package Search]("http://packages.ubuntu.com/") because Software Center won't connect (darn firewall!)


**I still can't read the mounted images locally or over the network. It just says "Permission Denied"**


I've tried "chown", "chmod", and "gksudo nautilus" on the mounted images and they all say that the file system is Read-Only, which makes sense however noone it seems can read the files!




I still think the most important thing is that I can't even read the mounted images locally...

Any more thoughts?

---

### Post by Kirboosy on 2011-02-02
Where are you putting the images once you mount them?

---

### Post by mtwelve on 2011-02-02
The ISOs are in */home/oxfdev/ISO*
Once mounted they are in */home/oxfdev/IMAGES*

I have tried mounting them to /mnt/IMAGES/*imagename*


I'm putting them in a subfolder as I intend to share the subfolder with around 15 mounted in total

---

Just going to see if using fstab to automatically mount them changes anything: [this thread]("http://ubuntuforums.org/showthread.php?t=329215") implys there is a "user can mount" option

---

### Post by mtwelve on 2011-02-02
OK it doesn't like me automounting in fstab... it keeps hanging asking me to skip. 

I added the line:
/home/oxfdev/ISO/bigabc.iso /home/oxfdev/IMAGES/BIGABC udf,iso9660 user,loop 0 0


I separated with a single space and with a single tab; neither worked... is there something wrong with my syntax



Thanks

---

### Post by Kirboosy on 2011-02-02
```
sudo mount /home/oxfdev/ISO/bigabc.iso /home/oxfdev/IMAGES -t iso9660 -o loop
```I know you are using gMount to mount the images but it might be messing you up.

I'm not entirely sure what the line should be but your line doesn't look right...shouldn't you at least specify the mount command?

---

### Post by mtwelve on 2011-02-02
I'll continue to add information because it might be relevant....

Mounting the images to */media/BIGABC* still gave me "Permission Denied" locally


fstab continued to not like mounting the images automatically. I added some more options *dev,exec,suid*



Thanks again!

---

### Post by mtwelve on 2011-02-02
> **Caboose885 said:**
> ```
sudo mount /home/oxfdev/ISO/bigabc.iso /home/oxfdev/IMAGES -t iso9660 -o loop
```I know you are using gMount to mount the images but it might be messing you up.

I'm not entirely sure what the line should be but your line doesn't look right...shouldn't you at least specify the mount command?

Sorry I may not have been clear that was the line I added to fstab... it seemed to follow the idea in the documentation: [LINK ]("https://help.ubuntu.com/community/Fstab")and this thread about auto mounting images: [LINK]("http://ubuntuforums.org/showthread.php?t=329215")


Its unlikely to make a difference but I'm making the images on a Windows machine... ISO Master is a bit odd if your making an ISO out of a disk (adding folders rather than specifying the source)


Gracias

---

### Post by Kirboosy on 2011-02-02
Well if you think that Windows is messing you up try remaking the images in Ubuntu

```
sudo aptitude install isomaster
```

It has a GUI as the windows version :D

Or you can install a totally different CLI program

```
**sudo apt-get install **[B]ccd2iso
```

[FONT=Arial]Syntax would be

```
ccd2iso inputfile.iso outputfile.img
```
[/FONT][/B]

---

### Post by mtwelve on 2011-02-03
Ha! Solved!

The main culprit here is the images that ISOMaster was creating... 

All I have done is used an image made on my Windows machine and it mounts correctly (CLI or GMount) and it share fine (accessible locally and from a windows client)

It even mounted first time in fstab



Thanks to Caboose885 and pricetech


**BONUS QUESTION: **Does anyone know the maximum amount of iso9660 images you can mount at any one time?

---

### Post by Kirboosy on 2011-02-03
I'm guessing it would be as many as you want? I don't see anything online about a maximum. I think it would be based on how powerful your computer is.

Do you know the answer?

---

### Post by mtwelve on 2011-02-03
When looking into making a CD Server I'm sure I read somewhere that there is a limit to the number of file systems Linux can mount at one time... Somewhere around 20... 

It wasn't specifically 9660 file systems, just file systems in general...

---

### Post by Kirboosy on 2011-02-03
Well you could always copy the image contents and save them to the hard drive if you ever hit the max amount. It would probably end up being faster because the OS wouldn't have to keep all the images mounted all the time. It would end up being normal files on the system.

---

### Post by mtwelve on 2011-02-03
> **Caboose885 said:**
> It would end up being normal files on the system.

I tried this but most the software recognized that it was a collection of files and not a CD/iso9660 and so wouldn't launch

---

