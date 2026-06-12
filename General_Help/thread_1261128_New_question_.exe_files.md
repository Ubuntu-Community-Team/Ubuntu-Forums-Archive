---
title: "New question .exe files"
date: 2009-09-08
forum: General Help
---

### Post by Rage Wraps on 2009-09-08
Ok everyone how about this. I started to put some applications on this new machine like Microsoft office, Acrobate Reader, some car related software, etc... Nothing will install and I don't know why. All of these files are .exe extensions. I even tried to install Winzip and Winrar and nothing. It keeps giving me osome strange error code message about it might not be a zip file. Any suggestions? I thought Linux works like a PC, but it has a MAC interface.

---

### Post by philinux on 2009-09-08
Linux is not windows and will not run .exe files without installing someting called wine from add/remove, Even then it's hit and miss.. You should seriously be looking for open source alternatives to windows programs. 


[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by Rage Wraps on 2009-09-08
I am very new to Linux and I like what I see so far. i just had a copy of office and figured I could still use it. I tried to install Open Office, but it did not work also.

---

### Post by philinux on 2009-09-08
Open office is installed by default. Applications > office.

Also seen as you are new to this look in System>help and support. You got some reading to do. But it's worth it. :P

Especially look into installing programs. Forget looking on the net.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Rage Wraps on 2009-09-08
I am still a newbie so if you can explain it a little better that would be great. THANKS!

---

### Post by Rage Wraps on 2009-09-08
> **philinux said:**
> Open office is installed by default. Applications > office.
 
Also seen as you are new to this look in System>help and support. You got some reading to do. But it's worth it. :P
 
Especially look into installing programs. Forget looking on the net.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
 
Sounds good. I will start reading up right now. I just need some basic programs that a windows based inorder to run my car. I will get it soon. So far I am liking everything Linux has to offer. 
 
Also do you know if Photoshop will work on it?

---

### Post by philinux on 2009-09-08
> **Rage Wraps said:**
> Sounds good. I will start reading up right now. I just need some basic programs that a windows based inorder to run my car. I will get it soon. So far I am liking everything Linux has to offer. 
 
Also do you know if Photoshop will work on it?

Under wine I think yes. But an equivalent is already installed. Applications>graphics>gimp


[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)

---

### Post by sideaway on 2009-09-08
download the latest wine.deb from their website, the one in the repos is inferior.

Also the command

sudo apt-get install openoffice.org

will give you a office suite, if that isn't good enough, office 2007 works with wine 1.1.28

---

### Post by Joshua Lückers on 2009-09-08
If you really wanna run Windows programs you can try out [wine]("http://winehq.org/"). To check how well a Windows program runs under wine you can check out the [Wine Application Database]("http://appdb.winehq.org/").

---

### Post by philinux on 2009-09-08
> **sideaway said:**
> download the latest wine.deb from their website, the one in the repos is inferior.

Also the command

sudo apt-get install openoffice.org

will give you a office suite, if that isn't good enough, office 2007 works with wine 1.1.28

Open office is installed by default.

---

### Post by Rage Wraps on 2009-09-08
Looking good so far. There are 4 different files for me to download.
 
 
[[COLOR=#0092e8]wine-1.1.28.tar.bz2[/COLOR]]("http://ubuntuforums.org/projects/wine/files/Source/wine-1.1.28.tar.bz2/download")
[[COLOR=#0092e8]wine-1.1.28.tar.bz2.sign[/COLOR]]("http://ubuntuforums.org/projects/wine/files/Source/wine-1.1.28.tar.bz2.sign/download")
[[COLOR=#0092e8]wine-1.1.29.tar.bz2[/COLOR]]("http://ubuntuforums.org/projects/wine/files/Source/wine-1.1.29.tar.bz2/download")
[[COLOR=#0092e8]wine-1.1.29.tar.bz2.sign[/COLOR]]("http://ubuntuforums.org/projects/wine/files/Source/wine-1.1.29.tar.bz2.sign/download")
 
Which do I need or do I need all? I know I am a pain in the ***, but I am just trying to learn. If I can get all of the stuff I need to work for my business, you will have another convert on your hand. I iam tired of all this microsoft crap. Viruses, fees, it is just out of control and not worth it any more.

---

### Post by philinux on 2009-09-08
The latest stable version of wine 1.0.1 is available from Applications>add/remove which is the easy way to install.

The versions from wine hq are beta and can be prone to break. See the warning.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Rage Wraps on 2009-09-08
Do you have to be online inorder to install Wine?

---

### Post by sashoalm on 2009-09-08
> **Rage Wraps said:**
> Do you have to be online inorder to install Wine?

Yes, you have to, because Wine must be downloaded from the repository servers.

---

### Post by Rage Wraps on 2009-09-09
> **sashoalm said:**
> Yes, you have to, because Wine must be downloaded from the repository servers.
 
 
What if I just put them on a flash drive and installed them from there? For some reason it is being a pain in the *** to get it online.

---

### Post by sideaway on 2009-09-09
> **Rage Wraps said:**
> What if I just put them on a flash drive and installed them from there? For some reason it is being a pain in the *** to get it online.
That would be fine, you can safely download the .deb and install it from a flash drive. As long as you have the necessary libs etc. But you'll quickly find out if you do and come and post here if an error is thrown up!

Also, what is it doing that's being a pain to get online?

And true OOo does come preinstalled, sorry philinux. Been a while since I installed a vanilla Ubuntu :p

---

### Post by Whiffle on 2009-09-09
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)


MS Office works pretty well under wine.

---

