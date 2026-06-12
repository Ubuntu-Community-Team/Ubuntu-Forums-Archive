---
title: "sudo for graphical Nautilus operations possible?"
date: 2010-12-28
forum: General Help
---

### Post by pstein on 2010-12-28
I am currently logged in as "Normal" (=non-root) user.
 
Now I want to peek into certain folders in Nautilus file browser resp. create some
new folders in protected directories. An error popup appears informing me that I have no permission.
 
In a terminal I would simply do a
 
sudo mkdir newfolder
 
but how can I perform such a "visual" sudo in Nautilus file browser?
 
Is there something like an "open File browser (or other GUI based prgm) as root" ?
 
Peter

---

### Post by Cavsfan on 2010-12-28
> **pstein said:**
> I am currently logged in as "Normal" (=non-root) user.
 
Now I want to peek into certain folders in Nautilus file browser resp. create some
new folders in protected directories. An error popup appears informing me that I have no permission.
 
In a terminal I would simply do a
 
sudo mkdir newfolder
 
but how can I perform such a "visual" sudo in Nautilus file browser?
 
Is there something like an "open File browser (or other GUI based prgm) as root" ?
 
Peter


Use **gksu** instead of **sudo** for gui.

---

### Post by Cavsfan on 2010-12-28
I think this is more what you wanted - get **Ubuntu Tweak** from **Applications** > **Ubuntu Software Center**.
Then it will be in **Applications** > **System tools** and on the left side under **System** there is **Nautilus Settings**.
Just click the check box "**Open folder with root privileges**".

Then you can right click on folders and open them as root.

---

### Post by Irony on 2010-12-28
Install nautilus-gksu which will allow you to right click on a file or folder to open it as root.

---

### Post by Cavsfan on 2010-12-28
> **Irony said:**
> Install nautilus-gksu which will allow you to right click on a file or folder to open it as root.

I guess what I mentioned above installs nautilus-gksu, except Ubuntu Tweak does many other things too.

---

### Post by pstein on 2011-02-06
> **Cavsfan said:**
> I think this is more what you wanted - get **Ubuntu Tweak** from **Applications** > **Ubuntu Software Center**.
Then it will be in **Applications** > **System tools** 
 
Hmm, I tried to find this. But when I enter "Ubuntu Tweak" (without quotes) in the search field of the Ubuntu Software Center nothing is found.
 
How can I tell Ubuntu to find "Ubuntu Tweak" software?
 
Is this a software form Ubuntuo, from Canonical Partners or Other?
 
Peter

---

### Post by mcduck on 2011-02-06
> **pstein said:**
> Hmm, I tried to find this. But when I enter "Ubuntu Tweak" (without quotes) in the search field of the Ubuntu Software Center nothing is found.
 
How can I tell Ubuntu to find "Ubuntu Tweak" software?
 
Is this a software form Ubuntuo, from Canonical Partners or Other?
 
Peter

Just install the *nautilus-gksu* package. There's no reason to install Ubuntu-tweak just to install some other package, when you can directly install what you want. ;)

---

### Post by firebird_1979 on 2011-02-06
Install the package called gksu. It does exactly what you want, not only for Nautilus, but for any program you would like to run as root or any other user.

Ubuntu Tweak does a whole lot more and is not in the standard repositories.

---

### Post by pstein on 2011-02-06
> **mcduck said:**
> Just install the *nautilus-gksu* package. There's no reason to install Ubuntu-tweak just to install some other package, when you can directly install what you want. ;)
 
Maybe nautilus-gksu is enough for the original problem.
 
But I want to have a look at Ubuntu Tweak anyway.
Possibly there are other some good tweaks inside.
So the question is still open:
 
How do I download Ubuntu Tweak?
 
Peter

---

### Post by randiroo76073 on 2011-02-06
How to add the source of Ubuntu Tweak (The easy way, works since Ubuntu 9.10):
Go to System / Administration / Software Sources, click on Other Software tab, click Add button, and enter “ppa:tualatrix/ppa”.

This will add the PPA repo and the GPG key automatically.

You can also do it from command line by running:

sudo add-apt-repository ppa:tualatrix/ppa

---

### Post by cogier on 2011-02-06
To run Nautilus in root Press [Alt] + F2 type ```
gksu nautilus
``` and enter your password when requested.

Ubuntu Tweak is available here [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

