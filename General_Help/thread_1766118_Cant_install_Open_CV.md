---
title: "Cant install Open CV"
date: 2011-05-24
forum: General Help
---

### Post by lakshmen on 2011-05-24
I am not able to install Open CV. I followed the following steps:
1)
1sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg62-dev libtiff4-dev cmake libswscale-dev libjasper-dev

2)
cd ~

wget [http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.0/OpenCV-2.0.0.](http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.0/OpenCV-2.0.0.)tar.bz2/download

3)tar -xvf OpenCV-2.0.0.tar.bz2 


i got stuck at step 3...it says no such command.  what shld i do next? any idea?

---

### Post by yetiman64 on 2011-05-24
You will need to decompress the bz2 file using the command,

```
bzip2 -dkv download
```Then run the command

```
tar -xvf download.out
```After this you will have the directory "OpenCV-2.0.0" in your home folder, with the source you want in it.

BTW the latest version available is 2.2.0 for OpenCV, if you need it change the download path .../2.0/OpenCV-2.0.0.tar.bz2 to .../2.2/OpenCV-2.2.0.tar.bz2.

From then on follow your instructions for configuring, making and installing etc.

---

### Post by lakshmen on 2011-05-24
tar: OpenCV-2.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

this is the error that i get.... after doing what u said

---

### Post by yetiman64 on 2011-05-24
> **lakshmen said:**
> tar: **OpenCV-2.0.0.tar.bz2**: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

this is the error that i get.... after doing what u saidThat file is not what you downloaded, the downloaded file is called "download".
> 
wget [http://sourceforge.net/projects/open.../OpenCV-2.0.0.]("http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.0/OpenCV-2.0.0.")tar.bz2/**download**Look in your home folder for a bzip file called download.

My first command unzips it to a file called download.out, a tar file.

My second command untars the file download.out to the directory "OpenCV-2.0.0". This is the directory you will need to build from.

After downloading just copy and paste my commands into a terminal.

---

### Post by lakshmen on 2011-05-24
> **yetiman64 said:**
> 

After downloading just copy and paste my commands into a terminal.

Didnt understand this line. btw the folder formed is OpenCV-2.1.0. 

but after that i put tar -xvf OpenCV-2.1.0.tar.bz2 it shows error. what shld be the next step?

---

### Post by yetiman64 on 2011-05-24
> **lakshmen said:**
> Didnt understand this line. btw the folder formed is OpenCV-2.1.0. 

but after that **i put tar -xvf OpenCV-2.1.0.tar.bz2** it shows error. what shld be the next step?
Your first post link is what I downloaded here and is for version 2.0.0.

I assume you have already done the download and have checked it is in your home folder.

As has already been explained copy and paste the 2 commands I gave in post 2 into a terminal**.** **Do not put the command tar -xvf OpenCV-2.1.0** in as there is no such file in your home folder, the file is called "download" (without the quotes).

It does not matter what version is downloaded follow the commands in post #2 to to get the OpenCV source folder extracted from what you downloaded.

---

### Post by lakshmen on 2011-05-24
i got it extracted... then what shld i do?

---

### Post by yetiman64 on 2011-05-24
> **lakshmen said:**
> i got it extracted... then what shld i do?

Do you have experience with compiling from source ?

It is usually not the recommended means of installing software in Ubuntu for a beginner (if you are indeed a beginner as such).

I will post you a couple of links to read regarding compiling software, but cannot give further support specifically for this software sorry.

The links to read are,

[[COLOR=Blue]https://help.ubuntu.com/community/CompilingEasyHowTo[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo")   and
[[COLOR=Blue]https://help.ubuntu.com/community/CompilingSoftware[/COLOR]]("https://help.ubuntu.com/community/CompilingSoftware")

If you go ahead with the instructions in the links, pay particular notice to the use of checkinstall rather than install (as it gives an easier/cleaner method of software removal should anything go wrong).

There is a [[COLOR=Blue]--ppa for OpenCV--[/COLOR]]("https://launchpad.net/%7Egijzelaar/+archive/opencv2") for Lucid if you prefer not to install from source and are on Lucid.
What Ubuntu version are you running ?

---

### Post by lakshmen on 2011-05-24
i am running 10.10..

---

### Post by yetiman64 on 2011-05-24
> **lakshmen said:**
> i am running 10.10..

Ok, it appears there is no Maverick ppa as such for OpenCV. I'd advise you wait for more advice from others regarding this package and building it from source (I'm not particularly familiar with it).

Regards and best of luck,
yetiman64

---

### Post by lakshmen on 2011-05-24
i tried the first website u gave.... got  stuck step 2 at the tar thing again

---

### Post by CharlesA on 2011-05-24
Compiling from source can be a bit of a pain if you haven't done it before.

Can you post the output of what happens if you try to use tar.

I found some info about installing OpenCV on Ubuntu, but it all looks a bit over my head.

---

### Post by lakshmen on 2011-05-24
as stated earlier in the post, for example for Open CV, i am able to until this step...

tar -xvf OpenCV-2.0.0.tar.bz2

and the result i get is 

tar: OpenCV-2.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

what shall i do??

---

### Post by lakshmen on 2011-05-24
i have downloaded both meshlab and opencv but dunno how to install them... can any one help?

---

### Post by CharlesA on 2011-05-24
> **lakshmen said:**
> as stated earlier in the post, for example for Open CV, i am able to until this step...

tar -xvf OpenCV-2.0.0.tar.bz2

and the result i get is 

tar: OpenCV-2.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

what shall i do??
Post the output of this from the same directory you downloaded OpenCV to:

```
ls -l
```

---

### Post by lakshmen on 2011-05-25
> **CharlesA said:**
> Post the output of this from the same directory you downloaded OpenCV to:

```
ls -l
```
hey sorry man, i didnt understand what u meant by this....

---

### Post by webofunni on 2011-05-25
> **lakshmen said:**
> I am not able to install Open CV. I followed the following steps:
1)
1sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg62-dev libtiff4-dev cmake libswscale-dev libjasper-dev

2)
cd ~

wget [http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.0/OpenCV-2.0.0.](http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.0/OpenCV-2.0.0.)tar.bz2/download

3)tar -xvf OpenCV-2.0.0.tar.bz2 


i got stuck at step 3...it says no such command.  what shld i do next? any idea?

Is there any reason that you are installing from source ? I can see that it is in the repository 

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

### Post by lakshmen on 2011-05-25
Hi... I was actually following the instructions in this page...

[http://www.samontab.com/web/2010/03/installing-opencv-2-0-in-ubuntu/](http://www.samontab.com/web/2010/03/installing-opencv-2-0-in-ubuntu/)

Btw, following instructions in the page [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV) can install Open CV?

---

### Post by webofunni on 2011-05-25
As far as I can see in Ubuntu 11.04 opencv version is 2

```

# apt-cache show python-opencv | grep -i version
Version: 2.1.0-3ubuntu1

```

so you will be able to install it through apt-get.

---

### Post by lakshmen on 2011-05-25
> **webofunni said:**
> As far as I can see in Ubuntu 11.04 opencv version is 2

```

# apt-cache show python-opencv | grep -i version
Version: 2.1.0-3ubuntu1

```

so you will be able to install it through apt-get.
hi friend, i didnt understand what u meant....

---

### Post by webofunni on 2011-05-25
The blog that you are following says, opencv version 2 is not available in Ubuntu repository. But I guess that blog post is old. Ubuntu version 11.04 ( That I am using ) contains opencv version 2 in repo, so the link [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV) will work. Try the steps mentioned in that link, that should work. 

I guess you are following that blog post to install version 2, correct ? 

Which version of ubuntu you are using ? 

```

lsb_release -a

```

will give ubuntu version. 

Try following command to see which version of opencv available.

```
 
sudo apt-cache show python-opencv | grep -i version

```

---

### Post by lakshmen on 2011-05-25
ubuntu 10.10 and version 2.1.0-2 for the opencv

---

### Post by lakshmen on 2011-05-25
basically i need to install opencv and meshlab... i tried to install but it failed... i downloaded the file... but i dunno how to extract them....

---

### Post by lakshmen on 2011-05-25
would appreciate any help provided...

---

### Post by webofunni on 2011-05-25
> **lakshmen said:**
> ubuntu 10.10 and version 2.1.0-2 for the opencv

Then try [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV) . are you able to install using that link ? 

```

sudo apt-get install meshlab

```

is that working for meshlab ?

---

### Post by lakshmen on 2011-05-25
for the meshlab, i typed what u said... it says the latest version..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
meshlab is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 281 not upgraded.

but when i go into meshlab, it is version 1.2.2, i want version 1.3.0.. how do i get that??

---

### Post by webofunni on 2011-05-25
1.3 is not there in repository. You need to install from source itself. 

[http://downloads.sourceforge.net/project/meshlab/meshlab/MeshLab%20v1.2.3/MeshLabSrc_AllInc_v123a.tgz](http://downloads.sourceforge.net/project/meshlab/meshlab/MeshLab%20v1.2.3/MeshLabSrc_AllInc_v123a.tgz)

are you able to install opencv ? is that the version that you were looking for ?

---

### Post by lakshmen on 2011-05-25
yes, thats the version i am looking for... but how do i download from source... i downloaded the meshlab into my hard drive but dunno how to install it....

---

### Post by webofunni on 2011-05-25
Press ALT+F2 and execute gnome-terminal and copy paste following command line by line. some of the compiling commands will take time to finish. 

```

cd ~
mkdir meshcomp
cd meshcomp
sudo apt-get install libqt4-core libqtcore4 libqtgui4 libqt4-dev python-qt4 qt4-qmake build-essential checkinstall
wget http://downloads.sourceforge.net/project/meshlab/meshlab/MeshLab%20v1.2.3/MeshLabSrc_AllInc_v123a.tgz
tar zxvf MeshLabSrc_AllInc_v123a.tgz 
cd MeshLabSrc_AllInc_v123a/meshlab/src/external/
qmake -recursive external.pro 
make
cd ..
qmake -recursive meshlabv12.pro 
make
cd distrib/
./meshlab

```

---

