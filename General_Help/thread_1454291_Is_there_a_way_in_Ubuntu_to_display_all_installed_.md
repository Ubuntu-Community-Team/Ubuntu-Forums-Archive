---
title: "Is there a way in Ubuntu to display all installed software by date?"
date: 2010-04-14
forum: General Help
---

### Post by Rytron on 2010-04-14
Hi.
In Ubuntu is there a way to display all installed software by date?
For example it would be handy to show the most recent installed software like in Revo Uninstaller in Windows [picture attached].

---

### Post by bobcollard on 2010-04-14
> **Rytron said:**
> Hi.
In Ubuntu is there a way to display all installed software by date?
For example it would be handy to show the most recent installed software like in Revo Uninstaller in Windows [picture attached].
You can sort by date in your File Manager see screenshot for example

---

### Post by oldfred on 2010-04-14
Install history is in the log files.

system, administration, log file viewer

Look for dpkg.log

I do not know how far back it goes.

---

### Post by Rytron on 2010-04-15
> **oldfred said:**
> Install history is in the log files.

system, administration, log file viewer

Look for dpkg.log

I do not know how far back it goes.

There should be a GUI method!

---

### Post by plucky on 2010-04-15
Open **Synaptic Package Manager** Go to **File > History**.

Is that what you mean?

---

### Post by Rytron on 2010-04-15
> **plucky said:**
> Open **Synaptic Package Manager** Go to **File > History**.

Is that what you mean?

Sweet. Thank you plucky. :)

---

### Post by bobcollard on 2010-04-15
That will give you what you installed through Synaptic, not all.  As I was trying to point out in my first post you can find them all with your File Manager.  Open it and look under 
/File System/var/cache/apt/archives  You will see something like the following screenshot.  Then sort it like I told you.

---

### Post by Rytron on 2010-04-15
> **bobcollard said:**
> That will give you what you installed through Synaptic, not all.  As I was trying to point out in my first post you can find them all with your File Manager.  Open it and look under 
/File System/var/cache/apt/archives  You will see something like the following screenshot.  Then sort it like I told you.

Thanks bobcollard. I did that. There are only 19 files there!

---

### Post by Miljet on 2010-04-15
If you have ever run apt-get clean, apt-get autoclean, or apt-get autoremove, it will have removed packages from /var/cache/apt/archives. See man apt-get for more details.

---

### Post by Rytron on 2010-04-16
> **Miljet said:**
> If you have ever run apt-get clean, apt-get autoclean, or apt-get autoremove, it will have removed packages from /var/cache/apt/archives. See man apt-get for more details.

Cheers Miljet.

---

### Post by nothingspecial on 2010-04-16
Hi Rytron, I know it`s not gui but


```
cat /var/log/dpkg.log | grep "\ install\ " | less 
```

Will give you a nice list of all the packages you have installed in date order that you can scroll up and down easily.

---

### Post by Rytron on 2010-04-16
> **nothingspecial said:**
> Hi Rytron, I know it`s not gui but


```
cat /var/log/dpkg.log | grep "\ install\ " | less 
```

Will give you a nice list of all the packages you have installed in date order that you can scroll up and down easily.

Cool. I appreciate this nothingspecial. :P

---

