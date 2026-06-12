---
title: "Uninstalling Ubuntu Server Edition (Stupid mistake)"
date: 2010-03-19
forum: General Help
---

### Post by amonaaron on 2010-03-19
Hi everyone. So this is my last resort, I've done searches and for the life of me I cannot figure out how to solve my problem.

I got a shiny new 64bit computer today and decided to install Ubuntu. I did not do my homework on the Ubuntu Server Edition, as I didn't realize it was command line. So my issue is this: how can I remove the server edition (and it's associated partition) and still load Windows7? I know that the Windows boot was replaced with Grub, and there was no Windows7 recovery DVD supplied with my computer, only a partition in the hard drive for it. 

I do want to install the Ubuntu OS, but the server edition is worthless to me. I've grown so fond of Ubuntu, but unfortunately for some things I still must rely on Windows otherwise I would do what I did with this machine and remove Windows completely.

Thanks for any help, and I apologize if someone else has posted this before and I didn't catch their post.:cry:

---

### Post by 3rdalbum on 2010-03-19
There's two things you can do.

Number one is just install Ubuntu Desktop in the same partition as Ubuntu Server. It will overwrite the Server installation. You will need to use the "manually specify partitions" option in the Ubuntu installer, and then set your Server partition as having the mountpoint "/".

The second method is to turn Server into Desktop, by installing the ubuntu-desktop package. Connect your computer straight to your router via an Ethernet connection, type:

```
sudo dhclient
```

to connect, then:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

When the Ubuntu Desktop package has finished downloading and installing (it will automatically install a lot of other packages too), you can type:

```
sudo reboot
```

and you should be alright from there.

---

### Post by DeMus on 2010-03-19
> **amonaaron said:**
> Hi everyone. So this is my last resort, I've done searches and for the life of me I cannot figure out how to solve my problem.

I got a shiny new 64bit computer today and decided to install Ubuntu. I did not do my homework on the Ubuntu Server Edition, as I didn't realize it was command line. So my issue is this: how can I remove the server edition (and it's associated partition) and still load Windows7? I know that the Windows boot was replaced with Grub, and there was no Windows7 recovery DVD supplied with my computer, only a partition in the hard drive for it. 

I do want to install the Ubuntu OS, but the server edition is worthless to me. I've grown so fond of Ubuntu, but unfortunately for some things I still must rely on Windows otherwise I would do what I did with this machine and remove Windows completely.

Thanks for any help, and I apologize if someone else has posted this before and I didn't catch their post.:cry:

If you want to use Ubuntu just install it over the server edition. Make sure to format the partitions to make sure all data from the server edition is gone. You will install a new grub which will also find Windows to make a dual boot.
Take care not to install Ubuntu on the whole disk or Windows will be gone.

---

### Post by amonaaron on 2010-03-19
Thank you so much for the help. I used the commands you said and that took care of the issue. I'm actually somewhat new to Ubuntu (about a month since Windows died on this computer with limited experience beforehand) and thus far I've been able to figure out everything else, so I kind of got worried when I couldn't figure this out.

Thanks again!:D

---

