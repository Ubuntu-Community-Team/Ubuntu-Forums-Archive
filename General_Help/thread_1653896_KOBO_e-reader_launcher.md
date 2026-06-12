---
title: "KOBO e-reader launcher"
date: 2010-12-27
forum: General Help
---

### Post by cattlerepairman on 2010-12-27
Here it goes..you received the cool KOBO e-reader with wireless from Santa and it only comes with the KOBO launcher for Windows and MacOS to access and sync with the online account.

You Google and find that there IS an ubuntu launcher as a dev: [http://dl.dropbox.com/u/2183775/kobo-desktop.deb](http://dl.dropbox.com/u/2183775/kobo-desktop.deb)

Cool, if you are running the 32bit edition of Ubuntu. Install the launcher and use.

Trying that on the 64 bit edition will give you an error message and not install the launcher.

**Here is what worked for me on Ubuntu 10.04 LTS - the Lucid Lynx**

Download the above deb file kobo-desktop.deb onto your desktop.
1) Install libzip: sudo apt-get install libzip

2) Force the install of the 32bit package onto your 64bit system: 
cd Desktop
sudo dpkg -i --force-architecture kobo-desktop.deb

3) You should now have a menu entry under "Applications/Other". Try and see if it works. If it does - woohoo. If not, read on.

4) Open a terminal window and type "Kobo" as a command. You may see the launcher trying to start and see an error message talking about "libzip.so.1 not found"

IF SO, use "sudo nautilus" and navigate to /usr/lib32/libz.so.1.2.3.3
Right click on the file and select "Make Link"
"Cut" the link you just created and "paste" it into /usr/local/Kobo
"Rename" this link file "libzip.so.1"

Close the terminal window, connect your Kobo via USB cable and run the Kobo launcher (Applications/Other)or type "Kobo" in the terminal window.

If your launcher launches and all is well, I get all the credit!

If it still doesn't work...sorry......

---

### Post by earlycj5 on 2011-01-03
Sweet!

Thank you.

Alternatively, if you're not afraid to copy/paste in the terminal.

```

sudo ln -s /usr/lib32/libz.so.1.2.3.4 /usr/local/Kobo/libzip.so.1

```

Will do the same without using Nautilus.

---

### Post by eapelzer on 2011-01-05
I installed the launcher and opened it, but to no avail. it doesn't do anything.
 help:confused:

---

### Post by t-bucket on 2011-02-08
> **eapelzer said:**
> I installed the launcher and opened it, but to no avail. it doesn't do anything.
 help:confused:

All I had to do to get it working was install libpng3, then create the link in /usr/local/Kobo

---

### Post by doogiekd on 2011-02-13
To get the kobo ereader launcher to work:

i installed "libzip1" from the synaptic package manager.

hope this helps, 

doogie

---

