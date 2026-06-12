---
title: "Setting a folder as Repository?"
date: 2010-02-01
forum: General Help
---

### Post by rocket16 on 2010-02-01
Hello all. I have recently reinstalled Ubuntu 9.10 in my Compaq Notebook. I have a problem. In my Desktop, I have more than 4 GB of packages installed. As we all know, I do not need to download them again in my Laptop, and can simply add them with "sudo dpkg -i * *.deb" command. But, I do not want to install them all, and want to pick up only a few. So, is there a way, that I can set the Folder (after copying it to the Laptop) as my Repository, I mean, wheneven I seek to install a Package using Add/Remove or Synaptic or apt-get system, they are installed from the Folder instead of from the Internet? (I have all dependencies installed for each application). Thanks in advance.

---

### Post by rocket16 on 2010-02-01
Any way to do so? Please tell me, if there is. Thaks again.

---

### Post by moodog on 2010-02-01
You should just be able to put the *.deb files in the standard cache folder and they'll be picked up - I've done this before and it worked fine.

/var/cache/apt/archives/

---

### Post by rocket16 on 2010-02-01
Thanks a lot friend! It is really doing fine! Grand! Thanks again.

---

### Post by rocket16 on 2010-02-01
It gives me a new Idea! That is, I can create an Offline Software Library for Ubuntu, and thus, Ubuntu triumphs over Windows!

---

### Post by PCA on 2010-02-01
You could store it away in a DVD and free up your harddrive space. I was thinking of this too.. do a search here on the forums for "trusted local repository".

---

### Post by rocket16 on 2010-02-01
Oh no! It is not working in Ubuntu 9.04! Any Idea?

---

### Post by zery on 2010-02-01
hi...

i'm a newbie in linux, and i'm interest in this topic, can you explain it in more basic language, i got 7 DVD of karmic packages, it's give me a hard time everytime i want to install a packages,do i have to copy only .deb files into cache folder or i have to copy from the root folder (pool,universe,a,b...)

cheers.

---

### Post by PCA on 2010-02-01
@All. This is the [LINK]("http://ubuntuforums.org/showthread.php?t=1090731&highlight=make+trusted+local+repository") I was talking about. Once you have downloaded software from the net, all the packages would be stored away in the /var/cache/apt/archives/ directory. Then you follow the instruction in the link to CREATE a local repository that you could store away some place. 

@Zery, no need to do all that.Place the disk in your drive, open** software sources>other software** and click on add Cd-Rom. When you close it, it'll update the list. Now open **Synaptic package manager**, click on origin, select the local cd option and you'll have the list.

---

### Post by warfacegod on 2010-02-01
> **PCA said:**
> 
@Zery, no need to do all that.Place the disk in your drive, open** software sources>other software** and click on add Cd-Rom. When you close it, it'll update the list. Now open **Synaptic package manager**, click on origin, select the local cd option and you'll have the list.

Can this be done with a USB install drive as well?

---

### Post by sarin_cv on 2010-02-01
are u people talking about creating a local repository in hard disk?

---

### Post by PCA on 2010-02-01
@Warfacegod, I dunno if/how it can be done through the GUI, but you could edit the /etc/apt/sources.list file and add *deb file://<location> /*. Where the location would be your flash drive. In my installation CD i saw the release file in /dists/karmic, so try putting** deb file:///media/(flash drive name)/dists/karmic / **in sources.list

@Sarin_cv, that's what I think, all my replies were based on it.

---

### Post by warfacegod on 2010-02-01
> @Warfacegod, I dunno if/how it can be done through the GUI, but you could edit the /etc/apt/sources.list file and add deb file://<location> /. Where the location would be your flash drive. In my installation CD i saw the release file in /dists/karmic, so try putting deb file:///media/(flash drive name)/dists/karmic / in sources.list

Thanks.

---

### Post by sarin_cv on 2010-02-01
u need packages dpkg and dpkg-dev.

copy all the deb files to a folder, say /home/user/myrepo. 
from /home/usr/, execute
```

dpkg-scanpackages myrepo /dev/null | gzip -9c > myrepo/Packages.gz

```

Now the contents of this can be burned to a blank media. To set up a local repository,

Open System -> Administration -> Software Sources
Select third party software tab
Click on add 
enter "deb file:/home/username/myrepo ./"
Add source,close and reload. 

Now whenever you add new files to myrepo, run dpkg-scanpackages and reload the sources.

---

### Post by PCA on 2010-02-02
@Sarin_cv, that's not enough. That only creates the index not the release file. People had trouble with it.... check out the link that I had put in my earlier post. It may seem a little bit complicated... trust me it's not. That method works like a charm:P

---

### Post by zery on 2010-02-03
PCA : thanks, but i found another way that i think it's more easy and would save space on my harddrive, i made all the DVD as ISO and save them in my PORTABLE harddrive, then i make a launcher (each of them) on my desktop to mount and unmount each ISO as a CDROM, so everytime i want to install a packages i just click on the launcher.

Cheers,

---

### Post by PCA on 2010-02-03
Zery, won't that just take up space on your hard drive? You could just use the DVDs directly. I never supported the Idea of copying the .deb files to the hard drive.

What launcher are you talking about? I would like to know more please, also do tell me what software you are using for mounting the ISO images.

---

### Post by zery on 2010-02-04
using the DVD directly is hard working, for example, if i want to install GRASS packages, it will ask the dependencies too, and that dependencies is spread on all disc, so i have to insert disc #4, then disc#7, then #5, then #7 then #3 then #2 then #7...it is not in order when asking to insert the disc, sometimes it will only copy just one file then ask another disc for other file then go back to earlier disc for again another one file...you see, how much trouble that can be, and i'm afraid it will damaged the disc.

So i made the DVD as ISO and save them on my PORTABLE hard drive, so if i want to install a packages i just mount the harddrive then click on the launcher.

The launcher i'm talking about is a shortcut command line program to mount the ISO as CDROM, just right click on the desktop and selecting "Create Launcher". Then you can change the type to "Application in Terminal", and put the mount command in the "Command" box.

To mount the ISO i use this command

sudo mount -t iso9660 path/to/your/file.iso /media/cdrom -o loop

To unmount

sudo umount /media/cdrom

Now it's much easier for me to install new packages. Did i mention that the 7 DVD is full packages of Ubuntu Repository that it acts as the Repository, so i don't download each packages then burned it on the disc. It was set up as a Local Repository.

---

### Post by PCA on 2010-02-04
Interesting... the mounting feature is built into Ubuntu, no extra software needed huh? nice!

In your case, I can imagine the trouble that you would have to go through:(

Did you manually create these disks after downloading the packages? also, you could try copying the contents of all the 7 DVDs onto your portable disk and add the location in /etc/apt/sources.list file. This way you wouldn't even have to mount each of them. Just a suggestion :)

and, thanks for the info :)

---

