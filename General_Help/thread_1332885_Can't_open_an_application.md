---
title: "Can't open an application"
date: 2009-11-20
forum: General Help
---

### Post by JimHebert on 2009-11-20
I'm new to Ubuntu and Linux. I am running Ubuntu 8.10 in Sun virtual Box. I've just downloaded songbird application. I extracted it and I now see it in /home/jimhebert  How do I get it to appear as a shortcut in some more convenient place like a quicklaunch panel as in Windows. I can't even get it to function where it is currently located? I did a google on it but  all I found was talk about Wine and that confused me even more.

---

### Post by mechro on 2009-11-20
I'm guessing it's not available as a Ubuntu "package".

Is it a Windows application?

Is there a .exe file in a Songbird folder?... Is there a Songbird folder?

If it's a Windows app then that is where Wine comes in.

If you have Wine installed then I think you'd just click the application starter or .exe file. If Wine isn't installed then Songbird won't work.

---

### Post by JimHebert on 2009-11-20
I was browsing and searching for open source applications and found songbird at this page [http://getsongbird.com/](http://getsongbird.com/)

Knowing as little as I do, I don't know if I should trust this download or if I should just delete it. In windows I'm used to right clicking on the icon on the desktop after a download and running a scan on the download to see if it's clean of viruses. In Ubuntu I can't do that, So how does one know what he's downloading? Another example is I just added a 3rd party source to Synaptic so I could download Miro (free Internet TV). The page is [http://www.getmiro.com/download/for-ubuntu/](http://www.getmiro.com/download/for-ubuntu/)   Again the question is, is there a way to scan any downloads from 3rd party sources and if so what is the name of the tool  in Synaptic? Or should I just delete this 3rd party source  from Synaptic and forget  about the whole thing.

---

### Post by lisati on 2009-11-20
Have a look here, it might help answer your question: [http://getsatisfaction.com/songbird/topics/songbird_help_on_linux?utm_medium=widget&utm_source=widget_songbird](http://getsatisfaction.com/songbird/topics/songbird_help_on_linux?utm_medium=widget&utm_source=widget_songbird)

---

### Post by neerajadsul on 2009-11-20
This is the way to make it work - 

1. First install package called *getdeb*. From here
[http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb)

It will allow you to install applications from getdeb.net which make automatic installtion package .deb for debian based distributions like ubuntu.

2. Then you can install Songbird from following link - 
[http://www.getdeb.net/updates/songbird](http://www.getdeb.net/updates/songbird)

When you click on Install Now, Firefox might ask you which application to use and it will give you a choice of application called *apturl*. Choose it. Then it will start installation. It will also ask you root password. 

After all this you can find Songbird in Application-> Sound & Video.

ENjoy and HTH.

---

### Post by 3rdalbum on 2009-11-20
Miro is available in the software repositories. Install it from your package manager (Ubuntu Software Center, Synaptic Package Manager etc) rather than by downloading software from the web.

---

### Post by JimHebert on 2009-11-21
Geeeee you're smart, neerajadsul. I downloaded Frostwire which, for me, is good enough. But tell me, where did getdeb repository get installed at? I thought it might be under System>Administration but it's not there. 

that's OK, I've just found it in the synaptic repository list. 

But while I got you on line, what is a Ubuntu opensource  software that will give me live Internet TV. I tried ZiggyTV but it doesn't work on Ubuntu. I found this one  [http://www.howtoforge.com/zattoo_live_tv_ubuntu](http://www.howtoforge.com/zattoo_live_tv_ubuntu)   How do I know if that's clean? Is there an Ubuntu repository for this site like the one for getdeb? I googled it and looked for a URL but no luck.

---

### Post by JimHebert on 2009-11-21
to Lisati:

Thanks but I found out that songbird won't work on my Ubuntu 8.10 version. I use that old version in Sun Virtualbox. It's supposed to be the most stable version for use in the box.


To 3rdalbum:

Miro doesn't have a live stream. Thanks anyway. 


I'de like to download this one " http://www.howtoforge.com/zattoo_live_tv_ubuntu"     but I'de like to download through Synaptic package manager. Is there a way to do that? Any repositories? I Googled but didn't see any HowtoForge repository. Only their webpage.


To neerajadsul:

Thanks for the getdeb repository. It's really good to have.

---

