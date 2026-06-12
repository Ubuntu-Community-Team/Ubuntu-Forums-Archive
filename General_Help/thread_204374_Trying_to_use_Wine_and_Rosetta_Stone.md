---
title: "Trying to use Wine and Rosetta Stone"
date: 2006-06-26
forum: General Help
---

### Post by trbloomer on 2006-06-26
I've been reading most of this evening and tried several ideas that didn't work](*,) 

So now I'm asking for a little help. For those that don't know Rosetta Stone is language learning software. I can intstall the app just fine. Using the current version of Wine and version 2.07A of Rosetta Stone. I can even run it well as long as I use my cd drive. The program runs from the HD but uses Language files from a cd drive. 

But I want to run it all from my HD. So I can leave the drive at home making my laptop much lighter and smaller. 

In windows I used a virtual cd to do this but in mounting the image doesn't seem to work for Wine. Any ideas?

---

### Post by aysiu on 2006-06-26
Can't you mount the CD image without Wine, and then just use it in Wine after it's mounted?

---

### Post by toorima on 2006-06-27
I had that working before, didn't work with mounting an iso. What you need to do is make a dir and copy the cd into it, not the image but all the folders. Then in wincfg / Drives you just add a drive, the dir you made and in show advanced set type to cdrom. I made one dir for each language. Hope it's any help.

---

### Post by trbloomer on 2006-06-27
Toorima,

Thanks that worked a treat. It's so simple and works just like it should:D :D
Now if only Italian were just as easy.

---

### Post by cleverselfreferentialname on 2006-07-12
Ah....thanks people. I'll be getting Rosetta now then.

Wine can work wonders, huh?

---

### Post by Ketzusaka on 2008-02-01
Sorry to be bumping an old thread, but it best describes my issue. I attempted the solution written on here but I still cannot seem to get Rosetta Stone to recognize the language CD.

I'm thinking it might have to do with the Volume, but I'm not sure. :\

Any further advice on it would be greatly appreciated,

~Ketzu :)

---

### Post by hornetcoach on 2008-02-19
Same issue - won't recognize the CD or the dir mount point manually entered into Wine.  The application seems to start up fine...it just says "no language cd found"  Any ideas?...trying to learn Japanese.

---

### Post by foeuckh on 2008-03-13
Same issue here         

I changed my custom dir-drive to CDROM, too...

---

### Post by Oldsoldier2003 on 2008-03-13
> **hornetcoach said:**
> Same issue - won't recognize the CD or the dir mount point manually entered into Wine.  The application seems to start up fine...it just says "no language cd found"  Any ideas?...trying to learn Japanese.

Try running a Windows VM and installing it there.

---

### Post by CranKey on 2008-03-28
Unfortunately I've the same problem.  The program installs and runs, but it can't find the data.

I've tried mounting the iso image, mounting the CD, and copying the CD contents to a directory.  None of these seem to work.

Does anyone know of a way to monitor the Rosetta Stone application when it's running so that it would become apparent where it's breaking?  It must be looking somewhere, but where?  If we knew that then we would probably be a long way towards solving the problem.

---

### Post by davosba on 2008-05-26
I was using an iso and it couldn't be found.
I used a similar solution to above.
open winecfg go to drives and add
for the new drive change drive mapping to point to where iso is mounted.
language is installing now

---

### Post by Databit on 2008-06-09
Aight so I had the first issue discussed and the second. Awesome.
First with the install I was able to fix with the winetricks script. 
Second issue is the not recognizing cdrom. I went into wine config and set the cdrom to the directory I extracted the Language ISO too. Then I set it to cdrom. Still saying not found. So I went and removed all drives but c and d. Set D to the lang and still no go.
Any ideas?

---

### Post by snowteddy on 2008-06-27
> **toorima said:**
> I had that working before, didn't work with mounting an iso. What you need to do is make a dir and copy the cd into it, not the image but all the folders. Then in wincfg / Drives you just add a drive, the dir you made and in show advanced set type to cdrom. I made one dir for each language. Hope it's any help.

How do I do that?  I am running Hardy.

I also have another problem.  I mounted a cd image using:

sudo mount RS_ChineseMand.iso /media/cdrom -t iso9660 -o loop

now I cant seem to unmount the .iso file. (filename is RS_ChineseMand.iso)
:confused:

---

