---
title: "Ubuntu on USB, best solution to choose"
date: 2012-03-09
forum: General Help
---

### Post by Ubuntter on 2012-03-09
Hi,

I am new to Ubuntu OS and I would like to give it a try. 
I am using Windows 7 and I would like to use Ubuntu from USB drive. 
Which is the easiest way to install and use Ubuntu on USB?
Here is what I would like to do: 

- be able to launch Ubuntu from USB drive, if possible without need to reboot my PC!
- be able to install and test applications on Ubuntu installed on the USB drive without affecting my Windows files and folders. .

Would this be possible?
For example, I have WAMP installed in Windows 7, could I install WAMP or LAMP on Ubuntu at the USB drive without conflict between Windows and Ubuntu?

I googled and found some solutions proposed but I don't know which one to choose, and which one is the most relevant for my request:
- Virtualbox,
- Unetbootin,
- VMware.

So, which is the "best" solution to use on Windows and which is the more suitable for my request above?

Thank you very much 

Thank you

---

### Post by codemaniac on 2012-03-09
> - be able to launch Ubuntu from USB drive without need to reboot my PC.
Hello mate ,
I am not sure if you can do the above , seems not possible .
If you want to boot up to ubuntu without physically rebooting your system , then definitely you should try out virtualization tools like virtualbox or VMWare .

But you can surely able to install and test applications on Ubuntu installed on the USB drive without affecting my Windows files and folders.

---

### Post by Ubuntter on 2012-03-09
> **codemaniac said:**
> Hello mate ,
I am not sure if you can do the above , seems not possible .
If you want to boot up to ubuntu without physically rebooting your system , then definitely you should try out virtualization tools like virtualbox or VMWare .

But you can surely able to install and test applications on Ubuntu installed on the USB drive without affecting my Windows files and folders.

Thanks a lot.
I am sorry, I realized that my message was duplicated, so I deleted it.

So, which solution could I use for UBS installation?

---

### Post by Ubuntter on 2012-03-09
Could we use WUBI to install Ubuntu on USB drive?

---

### Post by codemaniac on 2012-03-09
The best bet would be to trying out ubuntu on virtualbox .
Virtualbox comes free and you could download and install it in your windows environment .You can install your ununtu instance in virtualbox .
virtualbox download link [https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by squilookle on 2012-03-09
You can find a tutorial on running Ubuntu in VirtualBox [here]("http://www.psychocats.net/ubuntu/virtualbox"). As others have said, it's a good bet and will give you the chance to try the system without affecting your Windows install: you just need to make sure you computer is powerful enough to run Windows and Ubuntu at the same time.  You won't need a USB drive if you take this route.

Alternatively, you can install Ubuntu to a USB drive using something like pendrive Linux (You can find the instructions on the [download page]("http://www.ubuntu.com/download/ubuntu/download"), select USB stick and then click "Show me how". This would require you to reboot the computer, but it might run faster than in a virtual machine.

---

### Post by Ubuntter on 2012-03-09
Thanks.
I would prefer to install it on USB drive to avoid any potential conflict with local Windows system or application. 
I want to test the same application on Ubunto, so I would like to make it properly, on a separate drive. 
USB drive may be better than Virtualbox.

---

### Post by scrooge_74 on 2012-03-09
Search and you will find

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

scroll down to the USB part

Cheers

---

### Post by Ubuntter on 2012-03-09
> **scrooge_74 said:**
> Search and you will find

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

scroll down to the USB part

Cheers

Thanks.
The problem is that there are many "confusing" apps! I searched and found: Wubi, unetbootin, virtualboox, etc, so it is not easy to make difference between all these possibilities when we are new to ubuntu!

I am looking for a simple and good solution for using Ubuntu on Windows from USB drive. This maybe Unetbootin or Wubi. 
Is there any difference/preference between the two?

---

### Post by squilookle on 2012-03-09
I would say the simplest way to try Ubuntu on a USB drive without affecting you Windows installation is to follow the instructions on the Ubuntu download page, which uses Pendrive linux. 

To do that, go to this page: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and then look at step 2: it gives you the option: "I would like to create a CD/USB stick. Select USB stick, click  the "Show me how" button, and then follow the instructions that appear. 

I believe UNetBootin does a similar thing, but I have never used it so can't advise you on it, and it is not the solution named on the Ubuntu download page. 

Wubi install Ubuntu on your computer without partitioning your hard drive. I believe it is a safe method of installing, and you can uninstall it as you would any other , but I don't believe it is what you are looking for, based on what you have said. 

Virtualbox is different and runs Ubuntu in a virtual machine. The advantage is you can run it while Windows is running. 

Basically, use the option on the downloads page to try Ubuntu from a USB, unless you must keep your Windows install running while you are trying Ubuntu, in which case you should use Virtualbox. I hope that clarifies things and doesn't make it more confusing. :)

---

