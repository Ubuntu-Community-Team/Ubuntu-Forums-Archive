---
title: "Can't get Adobe Reader on Kubuntu"
date: 2009-11-22
forum: General Help
---

### Post by TheNerdAL on 2009-11-22
I need Adobe Reader and I installed the .Deb file but when I try to open it, I need to use an application, but I don't know how. Can anyone help?

---

### Post by TheNerdAL on 2009-11-22
Anyone?

---

### Post by jrusso2 on 2009-11-22
either right click and open with gdebi or use the console the command is sudo dpkg -i nameoffile

---

### Post by TheNerdAL on 2009-11-22
> **jrusso2 said:**
> either right click and open with gdebi or use the console the command is sudo dpkg -i nameoffile

How Can I install Ddebi?

---

### Post by DeMus on 2009-11-22
> **TheNerdAL said:**
> How Can I install Ddebi?

Click on the menu System, then Administration and choose Synaptic Package Manager.
Type your password and let Synaptic start
In the small search field on top type acroread and wait (no enter necessary)
You will get a list of packages, including acroread.
When the line which says acroread has a green box at the beginning the program is installed. When not, click the box and choose Mark for installation.
When a new window appears requesting you to accept the fact more packages will be installed, do so. Then acroread is depending on other packages which need to be installed.
In the buttonbar on top click the apply button and in the new window click OK.

Now you have acroread. Close Synaptic.

---

### Post by TheNerdAL on 2009-11-22
> **DeMus said:**
> Click on the menu System, then Administration and choose Synaptic Package Manager.
Type your password and let Synaptic start
In the small search field on top type acroread and wait (no enter necessary)
You will get a list of packages, including acroread.
When the line which says acroread has a green box at the beginning the program is installed. When not, click the box and choose Mark for installation.
When a new window appears requesting you to accept the fact more packages will be installed, do so. Then acroread is depending on other packages which need to be installed.
In the buttonbar on top click the apply button and in the new window click OK.

Now you have acroread. Close Synaptic.

I have Kubuntu, not Ubuntu.

---

### Post by DeMus on 2009-11-22
> **TheNerdAL said:**
> I have Kubuntu, not Ubuntu.

I don't know kubuntu but there must be a similar program to install software, like Synaptic in ubuntu.

---

### Post by TheNerdAL on 2009-11-22
> **DeMus said:**
> I don't know kubuntu but there must be a similar program to install software, like Synaptic in ubuntu.

Does anyone else know? :(

---

### Post by TheNerdAL on 2009-11-22
Anyone?! :(

---

### Post by wilee-nilee on 2009-11-22
I tried Kubuntu a while back but I am not real knowlegable, but is just a desktop on top of the basic system that Ubuntu Xubuntu share. What ever the synaptic equal or apt get equal is look for acroread it is the adobe pdf reader. Make sure you have the Canonical repository in the software sources ticked on. You don't have to open that deb it is already available.

Here is a link just open it and hit crtl f to search page put in acroread and you will find the instructions.
[http://kubuntuguide.org/Karmic](http://kubuntuguide.org/Karmic)

---

### Post by TheNerdAL on 2009-11-22
> **wilee-nilee said:**
> I tried Kubuntu a while back but I am not real knowlegable, but is just a desktop on top of the basic system that Ubuntu Xubuntu share. What ever the synaptic equal or apt get equal is look for acroread it is the adobe pdf reader. Make sure you have the Canonical repository in the software sources ticked on. You don't have to open that deb it is already available.

Here is a link just open it and hit crtl f to search page put in acroread and you will find the instructions.
[http://kubuntuguide.org/Karmic](http://kubuntuguide.org/Karmic)

It says broken Packages.

---

### Post by TheNerdAL on 2009-11-22
Anyone?

---

### Post by Scott753 on 2009-11-22
Have you considered using an alternate pdf viewer? Since you're using kubuntu, I recommend KPDF

[http://kpdf.kde.org/](http://kpdf.kde.org/)

It says on their website that you should be able to get the package directly from your repository. So whatever tool you have in Kubuntu...

or you could always try the good ole

sudo apt-get install kdpf

---

### Post by wilee-nilee on 2009-11-22
> **TheNerdAL said:**
> It says broken Packages.

If you look at the dependencies and broken packages you will have to fix the broken ones and install any dependencies, it is not magic fix situation.

What are the broken packages?

---

### Post by TheNerdAL on 2009-11-23
> **Scott753 said:**
> Have you considered using an alternate pdf viewer? Since you're using kubuntu, I recommend KPDF

[http://kpdf.kde.org/](http://kpdf.kde.org/)

It says on their website that you should be able to get the package directly from your repository. So whatever tool you have in Kubuntu...

or you could always try the good ole

sudo apt-get install kdpf

Cause I need to it to fill forms online to copyright something and It says I need Adobe Reader, I think.

---

### Post by wilee-nilee on 2009-11-23
What I find strange that you get a broken package warning and not fix it post that you have fixed this, and ask for more help or try the multiple help replies you have gotten.

---

### Post by TheNerdAL on 2009-11-23
> **wilee-nilee said:**
> If you look at the dependencies and broken packages you will have to fix the broken ones and install any dependencies, it is not magic fix situation.

What are the broken packages?

The packages that install Adobe Reader.

---

### Post by scouser73 on 2009-11-23
**1** - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.1.2** & Click **Download Now**

That will start installing Adobe PDF Reader for you, once installed you can find it in Office.

---

