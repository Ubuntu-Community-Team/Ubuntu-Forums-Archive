---
title: "Joomla on 10.04"
date: 2010-07-05
forum: General Help
---

### Post by cruising on 2010-07-05
Hello fellow Geeks :)! 
I've been trying to get Joomla! up and running on my hp 64-bit laptop which runs ubuntu 10.04. I want to use it to develop websites and upload them later. I also want to use it as a testing environment for other sites I make using HTML/CSS. I know I need LAMP and then Joomla!. But it all seemed to be a little too unclear right now. I've looked around for a smooth and straight-forward instruction to install it on my machine. Alas, it has not come to my screen, ... at least not for now. The Joomla wiki does not have Ubuntu instructions and I am absolutely sure somebody has done this in Ubuntu and can give me a step-by-step instruction on how to do that. 

Any help is really appreciated. Thanks a lot!

---

### Post by Ocxic on 2010-07-05
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Google is your friend :)

once all that is setup, just copy the joomla files to your Apache web root, and run the installer

TIP: when setting up MySQL in joomla use localhost as the address or it won't work.

---

### Post by cruising on 2010-07-05
> **Ocxic said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Google is your friend :)

once all that is setup, just copy the joomla files to your Apache web root, and run the installer

TIP: when setting up MySQL in joomla use localhost as the address or it won't work.

Thanks for the quick reply OCxic... was waiting eagerly for someone to say something! But ... is that all it takes? And where do I go from here? I'll need to try this out first and let you know, but, until I do that I just want to know if this is all I need to do.

Thanks again!

---

### Post by bikeboy on 2010-07-05
Another option if you have a computer capable of virtualisation is [http://www.turnkeylinux.org/joomla](http://www.turnkeylinux.org/joomla)

It's a pre-configured Joomla install (apache, php, mysql talking to it already)  based on Ubuntu 8.04, with a 10.04 version arriving this month or so. Keeps it isolated from your main Ubuntu install, but still allows you to tinker with the underlying parts when you're comfortable.

---

### Post by cruising on 2010-07-05
> **bikeboy said:**
> Another option if you have a computer capable of virtualisation is [http://www.turnkeylinux.org/joomla](http://www.turnkeylinux.org/joomla)

It's a pre-configured Joomla install (apache, php, mysql talking to it already)  based on Ubuntu 8.04, with a 10.04 version arriving this month or so. Keeps it isolated from your main Ubuntu install, but still allows you to tinker with the underlying parts when you're comfortable.

Thanks bikeboy! That sure is an option to explore! But ... then again, this intelligent solution has alienated me and my AMD64 pavilion dv7 laptop, by making the package for only x86 machines! Grrr .... I'm sure 64-bit versions will soon be available. Thanks for the info, though. Or is there a way to make it work on my machine?

---

### Post by bikeboy on 2010-07-06
I think on a 64-bit platform with 64-bit Virtualbox, you can run 32-bit VMs. Not vice-versa though. At least, that's what I'm doing with VBox from the Ubuntu repositories on 10.04.

---

### Post by cruising on 2010-07-06
> **bikeboy said:**
> I think on a 64-bit platform with 64-bit Virtualbox, you can run 32-bit VMs. Not vice-versa though. At least, that's what I'm doing with VBox from the Ubuntu repositories on 10.04.

That's great info, bikeboy! It will come in handy soon. Why soon? Because right now, I have a very slow connection and I even have to refresh a couple of times to see pages load fully!?! You can imagine how long it would take to download 170MB! 

I was thinking more on "repository-based" solutions. I did manage to install LAMP and did the configuration to the best of my ability. Started to download the XAMPP package following a very detailed instruction on wikipedia. But download will take a few more days to finish!!!! Absurd, right? I know.

Fast Internet here is like Gold itself! Hope the situation changes soon!

Thanks to you all for trying. But I would still love to hear from other people on Joomla setup, and how to get started once you're there. eBooks, torrent links, and related stuff is highly appreciated. I wish there was this Ubuntu-specific "How to install Joomla on Ubuntu 10.04" page that is straight-forward and very easy to do. If somebody out there won't get that page first, either I will, or CREATE IT MYSELF! :D 

Good Luck to us all!

---

