---
title: "Zune help"
date: 2010-05-05
forum: General Help
---

### Post by Dustdj20 on 2010-05-05
I'm new to Ubuntu and previously asked how to download the zune software.  I was told that you cannot use a zune on anything other than windows, and I was wondering if there was any other way to sync my zune. Any help will be appreciated.

Thanks

---

### Post by jbrown96 on 2010-05-05
I don't have a Zune, but I've heard that it's not possible on Linux. Your best bet is to download [virtualbox]("http://virtualbox.net") and setup a Windows installation in it. Then you can add a USB filter and it will work flawlessly in Windows.

---

### Post by Dustdj20 on 2010-05-05
And how will you go about setting up a windows installation in virtualbox?

---

### Post by jbrown96 on 2010-05-06
You will need a copy of Windows. Here's a decent tutorial [http://www.youtube.com/watch?v=Vpuz4mzL3yM](http://www.youtube.com/watch?v=Vpuz4mzL3yM). Go to virtualbox.net and install the correct version of virtualbox. After the installation finishes, then make sure to go the following ```
sudo usermod -aG vboxusers $USER
``` then reboot and follow the tutorial. 
You will need to create a USB filter. In the settings for your virtual machine, go to the USB section. Plug in your zune, then create a new filter. Start up windows and you should be able to put music on it. You may also want to create a shared folder setup, so you can access your music from Ubuntu to Windows.

---

