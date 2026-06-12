---
title: "Problem with printer"
date: 2009-07-02
forum: General Help
---

### Post by venugopaljee on 2009-07-02
Hello all,
I am very new to Ubuntu.
I have successfully connected to the internet.
When I try to give a print command, it is able to recognise my HP laserjet P 1505 printer but is unable to print. It simply stops. I get the following error message: 
/usr/lib/cups/filter/foomatic rip failed 

I start the printer troubleshooter. But it leads to nowhere. When I think the problem could be with the printer driver, I go to HP website and download the printer driver. But when I try to install the driver, it gives error message saying  memory is inadequate. I am not using any programme other than firefox. But stillt he memory is consumed. 

Is there any other way to operationalise the printer?

---

### Post by Scunnered on 2009-07-02
Have you had a look at Linux Printing as they advise this printer only works partially.

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P1505](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P1505) will give you their assessment on your printer.

Hope this assists

---

### Post by Wim Sturkenboom on 2009-07-02
You can try the HP website. I can not remember how I got to it, but I recently installed a P1005 (indeed not the same as yours) and in some way I ended with a download/install from the HP website.

---

### Post by snek on 2009-07-02
HP links to this page for installing HP printers under Linux:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

After selecting your printer it says:
> 
[B]Ubuntu 9.04 supplies HPLIP 3.9.2 and it does support your printer.

As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.

You may now optionally download the latest version of HPLIP to get access to new features and bug fixes.[/B]




---

### Post by venugopaljee on 2009-07-02
Thanks, all of you. I tried all that you have suggested, but it didn't help. Perhaps the problem is with the memory. How do I free memory, so that it is available to install a new driver? How can I reduce the partition size for windows and increase the size of Ubuntu?

---

### Post by Wim Sturkenboom on 2009-07-02
You can use *df -h* in a terminal to see if there is still HD space available. What you see depends how you have partitioned.

```

fortyfourgalena@desktop1:~$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              25G  3.7G   20G  16% /
varrun                506M  116K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M   52K  506M   1% /dev/shm
lrm                   506M   40M  466M   8% /lib/modules/2.6.24-24-386/volatile
/dev/sda9              99G   14G   80G  15% /home
/dev/sda1              26G   12G   14G  48% /media/sda1
/dev/sda5              30G  9.5G   21G  32% /media/sda5
fortyfourgalena@desktop1:~$ 

```

I don't know the answer how to resize partitions. For some reason I never have to do that :)

PS memory is not the same as harddisk space !

---

### Post by venugopaljee on 2009-07-13
Thanks a lot, Wim, 
Here is what i get:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   51M  98% /
tmpfs                 118M     0  118M   0% /lib/init/rw
varrun                118M   96K  118M   1% /var/run
varlock               118M     0  118M   0% /var/lock
udev                  118M  144K  118M   1% /dev
tmpfs                 118M   84K  118M   1% /dev/shm
lrm                   118M  2.4M  115M   2% /lib/modules/2.6.28-11-generic/volatile

Anyway, it appears there is a reason for the driver  not getting installed: When I tried with synaptic manager, and went to hp and tried to apply,  it gives error message: "not able to configure archives.ubuntu."
Can something be done on this, so that the printer driver can be installed?

---

### Post by Wim Sturkenboom on 2009-07-13
With this much diskspace left, I would not even consider it. If I interprete your df output, you only have 51MB available. So first sort that.

---

### Post by venugopaljee on 2009-07-17
How does one sort that out?
Do I need to reformat the whole hard disk, as right now I am sharing part of the HDD with windows xp?
Secondly, the error message when I proceed for installation of the downloaded printer driver software is that repositories for Ubuntu are not available. It also says archives. ubuntu is not available. Can some thing be done on that?

---

### Post by Wim Sturkenboom on 2009-07-17
You can resize one of the other partitons. I think gparted can do the trick. Probably easiest to use the liveCD ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ).

It's advised to first defrag all windows drives.

[COLOR="Red"]**Make sure to backup all important data**[/COLOR] (both windows and linux) as a mistake from your site or a power failure might destroy your data. Probably not unrecoverable but it will give you a lot of pain to get it all back.

With regards to the archive question, which version of Ubuntu are you running?

---

### Post by cariboo on 2009-07-17
Before you start changing partiton sizes, get rid of any archived packages in /var/cache/apt/archives, in a terminal type:

```
sudo apt-get clean
```

and to remove unneeded dependencies:

```
sudo apt-get autoremove
```

and check your trash, to make sure there are no huge files in it.

---

