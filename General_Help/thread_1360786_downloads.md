---
title: "downloads"
date: 2009-12-21
forum: General Help
---

### Post by Dieter3 on 2009-12-21
Am having problems installing downloads. The following message pops up:

Archive:  /home/dieter/Downloads/MediaCopeSetup.exe
[/home/dieter/Downloads/MediaCopeSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dieter/Downloads/MediaCopeSetup.exe or
          /home/dieter/Downloads/MediaCopeSetup.exe.zip, and cannot find /home/dieter/Downloads/MediaCopeSetup.exe.ZIP, period.

I've tried mediacope, xvid and avimediaconvertor.exe which all downloaded well but then the message appeared each time i tried to install. Advice most gratefully received.

Also, any ideas on which application i should use to install adobe reader?

Thanks for your time.

---

### Post by prem1er on 2009-12-21
You could be a little more descriptive, as I'm not sure exactly what you are trying to accomplish, but all those applications you are trying to download are written for Windows, not Linux. What are you trying to do? There may be a similar Linux application that will do what you want.

---

### Post by Dieter3 on 2009-12-21
Thanks for replying. I'm looking for a media player mp4, avi, flv etc.. Can you suggest where i can find one?

---

### Post by Isengrin on 2009-12-21
> **Dieter3 said:**
> Thanks for replying. I'm looking for a media player mp4, avi, flv etc.. Can you suggest where i can find one?

VLC in the repos. It's pretty good.
For reading PDFs, try Evince. I think it's installed by default.

Edit:
It looks like you are new, so here are some advices:
1) .exe files are Windows binary files, so they won't work here. There is Wine to make them work, but avoid it if there is a native equivalent.
2) Everything you'll need will be probably in the repos. I don't use Ubuntu, but I think you will find them in your main menu as "Install applications" or something like that. There, just search for what you need and mark it for install. Pretty straightforward.

Have a nice day. : )

---

### Post by ankspo71 on 2009-12-21
Hello,
Welcome to Ubuntu. 

You can search for these packages and install them by using Synaptic Package Manager or Software Center

**ubuntu-restricted-extras ** 
contains most of your audio/video codecs, flash player plugin, and more

**vlc **
a good all around audio/video player. 

**wine **
can be used to run *some* windows applications on Linux. See [http://appdb.winehq.org/](http://appdb.winehq.org/) for windows applications that have been tested in Wine.

---

### Post by Dieter3 on 2009-12-21
Great. Will the synaptic package manager also install adobe reader?

---

### Post by scouser73 on 2009-12-21
**1** - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.2** & Click **Download Now**
**7** - Open With **GDebi Package Installer**

If the **GDebi Package Installer** isn't showing then save the file to your desktop and install it that way.

That will start installing Adobe PDF Reader for you, once installed you can find it in the Office menu.

---

### Post by prem1er on 2009-12-21
I like foxit better than adobe. You may want to give it a try. Here are the installation instructions, because it is not in the repository.

[https://help.ubuntu.com/community/Foxit](https://help.ubuntu.com/community/Foxit)

---

### Post by Dieter3 on 2009-12-23
Yes. Thanks a bundle. Very helpful!

---

