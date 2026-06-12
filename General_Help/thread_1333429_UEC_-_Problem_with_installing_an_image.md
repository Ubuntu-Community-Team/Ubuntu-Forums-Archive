---
title: "UEC - Problem with installing an image"
date: 2009-11-21
forum: General Help
---

### Post by db91977 on 2009-11-21
I'm trying out the UEC cloud on two computers on my LAN at home.  I have the Ubuntu 9.10 Server CD, and I used the page at [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) for a guide.  The installation of the cloud controller and node went okay, up until Step 6, "Install an image from the store".  I might be missing something very basic, but on my node machine, there is no GUI.  Step 6 says to access the Web interface on the cloud controller at https://<cloud-controller-ip-address>:8443/, but without a GUI installed, there is no browser to use!  

When I installed the node according to the previous steps, there was no mention of the need for a GUI interface on the node server, and in fact, no option during the install process.  So I'm wondering if there's a command line way of installing an image from the store. Besides, isn't it recommended that we don't run a GUI on servers anyway, because of the processing overhead, package maintenance overhead, and possible additional security holes? 

Also, the UECCD installation page mentioned above seems to be confusing at a few points as to whether the author is referring to the cloud controller machine or the node, when performing installation steps.  But it might just be my incomplete understanding of the entire system at this time.  

Thanks for any insights!

--Doug

---

### Post by varunpandeyengg on 2010-03-21
Hey db9197, I had Similar same problem(I didn't get GUI option for both nc and cc). After trying a lot, I installed GUI separately. While doing that, do not forget to install gnome-terminal or else it will be troublesome to configure your cloud since SU mode is locked by default. But there is one more problem - After all this, when I am trying to download and install image, it is giving me error. ](*,) I am still trying. Now I am trying to install it manually. Lets see. My way of approach was to remove the GUI when I am done with installation...

---

### Post by krishna_iyer on 2010-07-23
Me thinks you need to access the web interface from another machine other than the controller and the node. That is because the server OS comes without the GUI by default.

---

