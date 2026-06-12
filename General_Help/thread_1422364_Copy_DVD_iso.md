---
title: "Copy DVD iso"
date: 2010-03-05
forum: General Help
---

### Post by irontrav on 2010-03-05
Hello all,
I am trying to use k9copy to simply copy the iso of a DVD movie to my hard drive.  No matter what I select I can't get "copy" to enable - it stays grayed out.  When I try to run the wizard it crashes after I select in my input source.  

I don't care what app I use, I just want something lightweight and easy to use that will copy the iso.

Thanks,
Trav

---

### Post by coffeecat on 2010-03-05
When you say "copy a DVD ISO" do you mean to extract the AUDIO-TS and VIDEO-TS folders and all their contents to somewhere on the HD? If so, simply right-click on the ISO file and select either "Extract Here" to extract to the current location, or Open-With > Archive Manager, and choose the location for the extracted files. You can't get more lightweight than that! :p

An ISO image is just an archive file (basically a glorifed ZIP or TAR file) so you don't need anything as sophisticated as k9copy. K9copy is a DVD-ripping app (it will decrypt commercial DVDs if you have libdvdcss2 installed), which can rip part or all of a DVD to a folder structure and/or an ISO. Since you already have an ISO file you don't need to rip anything.

---

### Post by irontrav on 2010-03-05
Sorry, I wasn't clear.  What I meant was that I have a pre-recorded, store bought DVD movie and I would like to decrypt it and rip it to my hard drive in the form of an ISO.  Thanks.

---

### Post by dnairb on 2010-03-05
Have a look at this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

To enable copying (and playing) of DVDs, run the following commands in terminal:

```
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by jmichelsen on 2010-03-05
irontrav,

I'm more of a command line guy, and if you want lightweight, there is nothing better so here's how I would do it.

```
dd if=/dev/dvd of=/somelocation/dvd.iso
```

that will make a direct copy of the dvd and place it in somelocation with the name dvd.iso

to explain the commands,

```
dd
``` has many definitions, so I won't go into that.

```
if
``` is the Input File

```
of
``` is the Output File

If you're looking for something to rip a dvd to an avi file, check out [undvd]("http://sourceforge.net/projects/undvd/")

---

### Post by coffeecat on 2010-03-05
> **irontrav said:**
> Sorry, I wasn't clear.  What I meant was that I  have a pre-recorded, store bought DVD movie and I would like to decrypt  it and rip it to my hard drive in the form of an ISO.  Thanks.

Yes, that is clear. Quite different from what you first posted. The  information you need is all in this thread....

> **coffeecat said:**
> K9copy is a DVD-ripping app (it will decrypt commercial DVDs if you have libdvdcss2 installed

and..

> **dnairb said:**
> To enable copying (and playing) of DVDs, run the following commands in terminal:

```
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
```

To clarify, you need both libdvdread4 and libdvdcss2 to be able to play and/or rip commercial DVDs. The second command dnairb posted is the easiest way to get libdvdcss2. The other way is to enable the [Medibuntu]("http://www.medibuntu.org/") repository and install it with a package manager. Once you get both those packages, you should find k9copy will work for you.

While you're about it, you might want to install ubuntu-restricted-extras (which will pull in libdvdread4) - which includes a whole load of useful multimedia codecs, flash, java (and MS core fonts).

---

### Post by Jolicoeur on 2010-11-16
> **jmichelsen said:**
> irontrav,

I'm more of a command line guy, and if you want lightweight, there is nothing better so here's how I would do it.

```
dd if=/dev/dvd of=/somelocation/dvd.iso
```that will make a direct copy of the dvd and place it in somelocation with the name dvd.iso

to explain the commands,

```
dd
``` has many definitions, so I won't go into that.

```
if
``` is the Input File

```
of
``` is the Output File

If you're looking for something to rip a dvd to an avi file, check out [undvd]("http://sourceforge.net/projects/undvd/")


Does this command work if your DVD drive is read/play only?

---

### Post by mirearts KING SUNNY on 2010-11-16
By default you should be using Brasero. change the type from .bin to .iso from the brasero copying tab

---

