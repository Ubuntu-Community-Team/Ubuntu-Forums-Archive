---
title: "Get updates/packages without internet?"
date: 2010-03-04
forum: General Help
---

### Post by Flexico on 2010-03-04
I have just installed Ubuntu on a computer that doesn't have internet where it is, and I was wondering, what is the best way to get the updates and packages that I want by downloading them somewhere else, putting them on a thumb drive, and then installing them?

---

### Post by cgroza on 2010-03-04
maybe there is a way to set your thumb drive as a repository , you know , like a cd-rom repository.

---

### Post by Flexico on 2010-03-04
How do I do that?

---

### Post by stinkeye on 2010-03-04
There are a couple of solutions here:[_**[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1326771[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1326771")

I used the solution in post #4 and works well.
I use a thumb drive and just changed the paths.

---

### Post by Flexico on 2010-03-05
OK, cool!  I got *APT on CD*, and I made an ISO of the packages. However, when I try to install them, it just says, "This does not install any software, it only makes it available to synaptic and aptitude." However, I tried both and neither seems to recognize them. I did manage to extract all of the packages into a folder, in case that would help.

How do I have Ubuntu just install all of them?

---

### Post by stinkeye on 2010-03-05
Never used aptoncd but maybe you have to update after running it
```
sudo apt-get update
```



[**_[COLOR="DarkRed"]http://aptoncd.sourceforge.net/doc-manual.html[/COLOR]_**]("http://aptoncd.sourceforge.net/doc-manual.html")

This is from another how to:
Restoring
What APTon CD does is create portable repositories. So you can use the APTonCD restore option to basically add your CD repository for installation. I have found, however, the best way to install all of the packages is with the command line. This allows you to quickly get all of your packages installed with a couple of easy commands. What you will want to do is this:
1. Insert your CD/DVD created by APTonCD.
2. Open a terminal.
3. Change to the directory where your CD is located.
4. Change into the packages directory with the command cd packages.
5. Issue the command sudo dpkg -i *deb to install all packages on the CD.
6. After the installation is complete you may need to use Synaptic in the event their are broken packages.

---

### Post by 2hot6ft2 on 2010-03-05
There is also the [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by manish23march on 2011-06-07
> **stinkeye said:**
> Never used aptoncd but maybe you have to update after running it
```
sudo apt-get update
```

[**_[COLOR=DarkRed]http://aptoncd.sourceforge.net/doc-manual.html[/COLOR]_**]("http://aptoncd.sourceforge.net/doc-manual.html")

This is from another how to:
Restoring
What APTon CD does is create portable repositories. So you can use the APTonCD restore option to basically add your CD repository for installation. I have found, however, the best way to install all of the packages is with the command line. This allows you to quickly get all of your packages installed with a couple of easy commands. What you will want to do is this:
1. Insert your CD/DVD created by APTonCD.
2. Open a terminal.
3. Change to the directory where your CD is located.
4. Change into the packages directory with the command cd packages.
5. Issue the command sudo dpkg -i *deb to install all packages on the CD.
6. After the installation is complete you may need to use Synaptic in the event their are broken packages.


Can u more info on how to "Change to the directory where CD is located"???

---

### Post by viperdvman on 2011-09-17
As far as I know, any mounted volumes are either in** /media** or **/mnt**, including HDD's, USB flash drives, SD cards, CD's/DVD's, mounted ISOs, etc.

---

