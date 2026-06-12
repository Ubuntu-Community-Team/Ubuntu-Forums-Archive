---
title: "Synaptic Package manager: Error on launch"
date: 2012-06-07
forum: General Help
---

### Post by hiranyaroma on 2012-06-07
Hi, 
I am not able to open the synaptic package manager. I am using Lubuntu 12.04. I get the following error when I try to launch synaptic manager.

E: Type '<html>' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How do I get rid of the error?

May be this extra information is helpful. I got this error after i tried to run the code below as my adobe flash plugin was not working.

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get --quiet update && sudo apt-get -y --force-yes --quiet --allow-unauthenticated install medibuntu-keyring app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update

This resulted in an error in the terminal 

ERROR: cannot verify ifwa.iitb.ac.in's certificate.
Self-signed certificate encountered.To connect to ifwa.iitb.ac.in insecurely, use `--no-check-certificate'.

SInce then, the synaptics manager started showing the error.

---

### Post by wilee-nilee on 2012-06-07
In the terminal run.
```
gksudo nautilus
```open file/etc/apt/soruces.list.d and delete the medibuntu stuff close everything and then run this.```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```All this removes the medibuntu from source.list.d and installs it again.

Medibuntu has nothing to do with flash as well, use the flash aid addon in firefox to fix that.

---

### Post by hiranyaroma on 2012-06-07
> open file/ect/apt/soruces.list.d and delete the medibuntu stuff close everything and then run this.

I am not able to delete medibuntu stuff. It says

medibuntu.list: Error removing file: Permission denied

And yes, I have added flash aid and youtube videos are now running fine.

---

### Post by wilee-nilee on 2012-06-07
> **hiranyaroma said:**
> I am not able to delete medibuntu stuff. It says

medibuntu.list: Error removing file: Permission denied

if you run this;
```
gksudo nautilus
```It opens a window you now have root access to the root file system. 

Open in the left panel of that window that just opened
file then open etc-apt-sources.list.d and remove.

You running ubuntu or kubuntu?

---

### Post by hiranyaroma on 2012-06-07
> **wilee-nilee said:**
> if you run this;
```
gksudo nautilus
```It opens a window you now have root access to the root file system. 

Open in the left panel of that window that just opened
file-etc-apt-sources.list.d and remove.

You running ubuntu or kubuntu?
I am using Lubuntu 12.04 and nothing happens when i run ```
gksudo nautilus
```

---

### Post by Elfy on 2012-06-07
Hi - please open a terminal and run

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then 

```
sudo apt-get update
```

Once that all works without error - try adding the medibuntu source again.

---

### Post by wilee-nilee on 2012-06-07
> **hiranyaroma said:**
> I am using Lubuntu 12.04 and nothing happens when i run ```
gksudo nautilus
```
Ah different file set up than nautilus, I have passed on the thread to some others maybe they will post

---

### Post by wilee-nilee on 2012-06-07
So if you want to reload medibuntu use this link load it first then do your installs.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you still have a problem post all the text run from the terminal

cat /etc/apt/sources.list

---

### Post by hiranyaroma on 2012-06-07
> **Elfy said:**
> Hi - please open a terminal and run

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then 

```
sudo apt-get update
```

Once that all works without error - try adding the medibuntu source again.
Everything is working fine now. I still cannot add the medibuntu source as it gives the folowing error.

 Self-signed certificate encountered.
To connect to ifwa.iitb.ac.in insecurely, use `--no-check-certificate'.

But anyway, my reason for adding medibuntu was for playing flash videos. That got sorted out by using flash aid. Now, I dont seem to need medibuntu anymore. 
Thanks!

---

### Post by wilee-nilee on 2012-06-07
> **hiranyaroma said:**
> Everything is working fine now. I still cannot add the medibuntu source as it gives the folowing error.

 Self-signed certificate encountered.
To connect to ifwa.iitb.ac.in insecurely, use `--no-check-certificate'.

But anyway, my reason for adding medibuntu was for playing flash videos. That got sorted out by using flash aid. Now, I dont seem to need medibuntu anymore. 
Thanks!

Cool have you installed?
```
sudo apt-get install lubuntu-restricted-extras
```

---

