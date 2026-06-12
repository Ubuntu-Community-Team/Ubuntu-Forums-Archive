---
title: "legacy packaging tool? - locked out of installing packages"
date: 2009-12-22
forum: General Help
---

### Post by bmaguire on 2009-12-22
Yesterday I was trying to install java on a newly installed system.    When the license agreement came up I could not enter "OK" in the console -- it just wouldn't accept a mouse click, return.. anything.
Now if I try to run kpackagekit I get the following message:

Cannot get the exclusive lock on the packaging backend.
Please close any other legacy packaging tools that may be open.

If I try apt-get I get the following:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I get out of this?  
Brian

---

### Post by starcraft.man on 2009-12-22
In a terminal:

```
sudo apt-get -f isntall
```

I assume ya didn't finish the java install, that will continue installation. At screen, push TAB and then highlight ok, then push ENTER. Hope that fixes it, should. Also, ensure no other package program working like software center or synaptic....

---

### Post by bmaguire on 2009-12-22
Thanks, Starman.  It worked!
Brian

---

### Post by jabbermacy on 2011-01-26
Hello, just installed Kubuntu 10.10 and I have this error:

cannot get exclusive lock on the packaging backend

Using Kpackagekit, tried deleting lock file, sudo apt-get update works, just cannot get past this error!!!

Please help, very sad now...

---

### Post by Saintmeh on 2011-09-28
> **jabbermacy said:**
> Hello, just installed Kubuntu 10.10 and I have this error:

cannot get exclusive lock on the packaging backend


I don't know about Kubuntu 10.10... but on 11.04 I had this same problem.  So I tried running 
```
sudo apt-get install
``` from the command line instead of the "KPackageKit"

apt-get told me that "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


Typing ```
sudo dpkg --configure -a
``` Fixed it!  

Now apt-get and KPackageKit both work!  I guess the newb lesson from this is: try the command line when the GUI fails.  Also... when you write programs...  be kind enough to suggest a possible fix in each of your error messages.

---

