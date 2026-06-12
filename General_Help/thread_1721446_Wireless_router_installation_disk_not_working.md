---
title: "Wireless router installation disk not working"
date: 2011-04-04
forum: General Help
---

### Post by morenon1118 on 2011-04-04
I have a belkin wireless "g" adapter and I use it on my dell optiplex 745 desktop. When I first got it, I installed the adapter easily witht the installation disk. However, when I completely erased the windows professional from my desktop and installed ubuntu 10.10 on my desktop, I had no internet connection. I tried to re-install the software but it would not work. I assumed that it wasn't working because the installation disk is not compatable with ubuntu. Is there any way to install the driver for the adapter to make it compatable with ubuntu?

---

### Post by bkratz on 2011-04-04
> **morenon1118 said:**
> I have a belkin wireless "g" adapter and I use it on my dell optiplex 745 desktop. When I first got it, I installed the adapter easily witht the installation disk. However, when I completely erased the windows professional from my desktop and installed ubuntu 10.10 on my desktop, I had no internet connection. I tried to re-install the software but it would not work. I assumed that it wasn't working because the installation disk is not compatable with ubuntu. Is there any way to install the driver for the adapter to make it compatable with ubuntu?

Do you any internet access via wired (wasn't sure from the posting). If so, check under system..admininistration..hardware drivers (this one may be called something else in 10.10) and see if there are any drivers waiting to be enabled.

---

### Post by Old_Grey_Wolf on 2011-04-04
From the Software Center find and install the "Windows Wireless Drivers" or enter "sudo apt-get install ndisgtk" in the terminl.

After it is installed open the application from the menu System &#8594; Administration &#8594; Windows Wireless Drivers.

Locate the .inf file for you adpter on the CD.

Select Install new driver.

Choose the location of your Windows .inf file and click Install.

Click OK.

---

### Post by morenon1118 on 2011-04-04
> **bkratz said:**
> Do you any internet access via wired (wasn't sure from the posting). If so, check under system..admininistration..hardware drivers (this one may be called something else in 10.10) and see if there are any drivers waiting to be enabled.
 
Well my desktop is in my room and my router is all the way in my basement, so I am unable to get any wired internet access from that computer. I don't know if that answered your question

---

### Post by Mark Phelps on 2011-04-05
Sorry ... but driver installation in Linux is basically designed to use Internet access by default -- and given that you have to fix the driver problem in order to get Internet access, you have a problem.

So, you're going to have to connect the Router to the PC in wired mode -- somehow.  Either move one of them, or get a very long cable to connect them.

---

