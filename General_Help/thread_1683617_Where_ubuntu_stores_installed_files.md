---
title: "Where ubuntu stores installed files?"
date: 2011-02-07
forum: General Help
---

### Post by vat with tux on 2011-02-07
where ubuntu 10.04 stores files related to s/w installed from ubuntu software center?

---

### Post by snowpine on 2011-02-07
It depends on the specific software, but most of the time in /usr/bin. For example if you open a Terminal window and type:

```
whereis firefox
```

You will see it is installed as /usr/bin/firefox. :)

---

### Post by vat with tux on 2011-02-07
Then suppose i want to "completely" remove a s/w from my pc then should i remove the folder of that s/w manually from usr/bin?

---

### Post by snowpine on 2011-02-07
> **vat with tux said:**
> Then suppose i want to "completely" remove a s/w from my pc then should i remove the folder of that s/w manually from usr/bin?

No; you should use a package manager such as the Ubuntu Software Center or the "apt-get remove" terminal command:

```
sudo apt-get remove firefox
```

---

### Post by Quadunit404 on 2011-02-07
> **vat with tux said:**
> Then suppose i want to "completely" remove a s/w from my pc then should i remove the folder of that s/w manually from usr/bin?

I am sorry, but I don't know what this "s/w" is :P

No, no, jk. Linux =/= Windows. Just removing a folder will not count as uninstalling something. It'll probably end up breaking your system instead. Just use the above recommendation for removing software.

---

### Post by snowpine on 2011-02-07
Here is a collection of how-to documents on adding/removing/managing s/w in Ubuntu:

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by WorMzy on 2011-02-07
Ubuntu doesn't install programs in the same way that Windows does. For example, on Windows, Firefox would be installed to "C:\Program Files\Mozilla Firefox\". On Ubuntu the files get separated into their respective directories. Libraries go into /usr/lib, executables go into /usr/bin, and documentation goes into /usr/share/doc. ([complete list]("http://packages.ubuntu.com/maverick/i386/firefox/filelist")).

To remove software installed by official means (e.g. software centre, synaptic, apt-get), you can use the same tool you used to install it, to remove it. You can even use one of the other tools I just mentioned, even if you used one of the others to install it.

To remove custom software, such as software you compiled yourself, use the tool you used to install it. e.g. navigate to the build directory and run "sudo make uninstall", or "sudo setup.py remove". Commands may vary, so read the README, check the developer's website, or examine the build files.

---

### Post by sisco311 on 2011-02-07
> **WorMzy said:**
> 
To remove custom software, such as software you compiled yourself, use the tool you used to install it. e.g. navigate to the build directory and run "sudo make uninstall", or "sudo setup.py remove". Commands may vary, so read the README, check the developer's website, or examine the build files.

Make *checkinstall*, not war & don't *make install*. :)

[uhelp]community/CheckInstall[/uhelp]


@OP:

There are many sites which explain the Linux filesystem hierarchy, but if you're offline for some reason, you can read the man page:
```
man hier
```

---

### Post by vat with tux on 2011-02-08
Thanks to all for replies. Let me elaborate my problem. :)  

I had installed eclipse which took around 20 or more minutes. 
After some time i removed it from ubuntu s/w center, it was removed successfully. 
Now before three days i reinstalled it & surprisingly it took less then 5 mins. 
Means files of eclipse was not completely removed from the system. Rather it's entry was only removed from s/w center.
I think that files were unnecessarily occupying my disk space. My question is that how can i free up that space?  

I hope u r getting my question.

---

### Post by mcduck on 2011-02-08
> **vat with tux said:**
> Thanks to all for replies. Let me elaborate my problem. :)  

I had installed eclipse which took around 20 or more minutes. 
After some time i removed it from ubuntu s/w center, it was removed successfully. 
Now before three days i reinstalled it & surprisingly it took less then 5 mins. 
Means files of eclipse was not completely removed from the system. Rather it's entry was only removed from s/w center.
I think that files were unnecessarily occupying my disk space. My question is that how can i free up that space?  

I hope u r getting my question.

More likely it took you 20 minutes to *download & install* Eclipse. When you installed it second time the downloaded .deb package was still available in apt's cache directory, so it could be installed directly without having to download it again.

I've never seen the actual *installation* of a package take 20 minutes, not even on my old 450MHz/128MB RAM machine.... :D

(if you want to remove the package manager's cached packages you can run "sudo apt-get clean".)

---

### Post by snowpine on 2011-02-08
> **mcduck said:**
> More likely it took you 20 minutes to *download & install* Eclipse. When you installed it second time the downloaded .deb package was still available in apt's cache directory, so it could be installed directly without having to download it again.

I've never seen the actual *installation* of a package take 20 minutes, not even on my old 450MHz/128MB RAM machine.... :D

(if you want to remove the package manager's cached packages you can run "sudo apt-get clean".)

+1, I agree with all of the above.

Unless you are extremely short on hard drive space, cache is actually a good thing. :)

---

### Post by vat with tux on 2011-02-08
> **mcduck said:**
> More likely it took you 20 minutes to *download & install* Eclipse. When you installed it second time the downloaded .deb package was still available in apt's cache directory, so it could be installed directly without having to download it again.

I've never seen the actual *installation* of a package take 20 minutes, not even on my old 450MHz/128MB RAM machine.... :D

(if you want to remove the package manager's cached packages you can run "sudo apt-get clean".)

"sudo apt-get clean". This is what i was looking for. :) thanks a lot. I'm having just 22 GB allocated for my ubuntu system.:) 

I thing time taken for downloading depends more on speed of INTERNET connection not on ram size. :) 
And i'm having just 256kbps speed .:)

---

### Post by vat with tux on 2011-02-08
Thanks to all.:)

---

### Post by mcduck on 2011-02-08
> **vat with tux said:**
> 
I thing time taken for downloading depends more on speed of INTERNET connection not on ram size. :) 
And i'm having just 256kbps speed .:)
Yes, that's why I said that I don't believe the *installing* of the package could have taken you 20 minutes, but more likely *downloding and installing* it did... ;)

---

