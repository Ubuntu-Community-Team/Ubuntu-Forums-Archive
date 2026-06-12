---
title: "sharing folders and usb in virtualbox xp-guest."
date: 2011-06-07
forum: General Help
---

### Post by nos09 on 2011-06-07
hey, 
i need to share folders and usb form my ubuntu,as host, to xp as guest.. and plus i need some advice if i can play games on it. 
i've searched the web but didnt find a proper solution but i found two : [http://usablesoftware.wordpress.com/2010/05/21/virtualbox-share-folder-between-ubuntu-host-and-windows-xp-guest/]("http://usablesoftware.wordpress.com/2010/05/21/virtualbox-share-folder-between-ubuntu-host-and-windows-xp-guest/") but it didnt helped at all.. and i was wondering how come there's an option of USB in that device menu ?!?!? 

thanks in advance.

---

### Post by howefield on 2011-06-07
Have you installed the extension pack ?

This has the closed source code needed for sharing folders and USB capability.

---

### Post by nos09 on 2011-06-07
i installed virtualbox from ububtu software center... so i dont know if thats the right one !? how can i check it ? and if its not how can i install extentions ?

---

### Post by howefield on 2011-06-07
There used to be two versions of VirtualBox.

Firstly, the OSE (Open Source Edition) which could be installed via the Ubuntu Software Centre or Synaptic Package Manager. This version did not have the capabilities/features you want.

Secondly, there was the PUEL (Personal Use and Evaluation Licence) which was downloaded via the VirtualBox website and which did have the capability you need.

Now however, there is only one version, the open source version to which you can install an "extension pack" giving you the closed source code allowing you to share folders and use USB devices amongst other features.

Sorry if this seems confusing, but if it were me, I guess I'd uninstall the version you have and download the appropriate .deb file for Maverick (if that is what you are using) and also download the extension pack. You shouldn't lose your VMs if you have already created any, but you may have to recreate your settings for them.

Once you have installed VirtualBox, go to the VirtualBox File menu and select preferences, and click on Extensions and install your downloaded extension pack.

Hope that makes sense.

---

### Post by nos09 on 2011-06-07
> **howefield said:**
> There used to be two versions of VirtualBox.

Firstly, the OSE (Open Source Edition) which could be installed via the Ubuntu Software Centre or Synaptic Package Manager. This version did not have the capabilities/features you want.

Secondly, there was the PUEL (Personal Use and Evaluation Licence) which was downloaded via the VirtualBox website and which did have the capability you need.

Now however, there is only one version, the open source version to which you can install an "extension pack" giving you the closed source code allowing you to share folders and use USB devices amongst other features.

Sorry if this seems confusing, but if it were me, I guess I'd uninstall the version you have and download the appropriate .deb file for Maverick (if that is what you are using) and also download the extension pack. You shouldn't lose your VMs if you have already created any, but you may have to recreate your settings for them.

Once you have installed VirtualBox, go to the VirtualBox File menu and select preferences, and click on Extensions and install your downloaded extension pack.

Hope that makes sense.

oh that makes perfact sense ! and i ll download that as soon as i get home as i m at friends anf will get back to this thread to report. thanks by the way.

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **nos09 said:**
> hey, 
i need to share folders and usb form my ubuntu,as host, to xp as guest.. and plus i need some advice if i can play games on it. 
i've searched the web but didnt find a proper solution but i found two : [http://usablesoftware.wordpress.com/2010/05/21/virtualbox-share-folder-between-ubuntu-host-and-windows-xp-guest/](http://usablesoftware.wordpress.com/2010/05/21/virtualbox-share-folder-between-ubuntu-host-and-windows-xp-guest/) but it didnt helped at all.. and i was wondering how come there's an option of USB in that device menu ?!?!? 

thanks in advance.

First make sure you install the latest version of Virtualbox 4.  Remove any old versions you have runnning now from your Synaptic Package manager. Make sure when you uninstall it to right click on it's name in Synaptic and select "completely remove" so it gets everything..

After you have rebooted your system, you need to install the Virtualbox 4 PPA from your terminal like this:
```

sudo echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.0

```Restart your system after it has been installed. 

Then you run the program and make sure it installed correctly.   You can add the virtualbox additional packages after you have installed whatever OS you want to emulate in the virtualbox. There is USB support for Virtualbox 4 after you have installed the additional packages.

---

### Post by nos09 on 2011-06-07
i guess you were right ! i did installed virtualbox ose. but now i m confused the vbox site dosent define which virson they are giving, i mean its simply virtualbox for 10.10 ), 57 mb sized. but as far as i remember the ose was only 14mb. so is it right version !?

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **nos09 said:**
> i guess you were right ! i did installed virtualbox ose. but now i m confused the vbox site dosent define which virson they are giving, i mean its simply virtualbox for 10.10 ), 57 mb sized. but as far as i remember the ose was only 14mb. so is it right version !?
 
No you are using the older version.  Uninstall it from synaptic package manager.. 

Then reboot your system.

Then use the PPA for Virtualbox 4 I gave you above in your terminal..   :guitar:

---

### Post by howefield on 2011-06-07
> **nos09 said:**
> but now i m confused the vbox site dosent define which virson they are giving, i mean its simply virtualbox for 10.10 ), 57 mb sized. but as far as i remember the ose was only 14mb. so is it right version !?

The file will be about that size, yes.

The file I have for Natty is 58.2 megabytes big.

---

### Post by nos09 on 2011-06-07
> **howefield said:**
> The file will be about that size, yes.

The file I have for Natty is 58.2 megabytes big.

i was wondering.. can i save the .deb file while it gets downloaded from this command : apt-get install virtualbox-4.0 (from the code someone mentioned above) for later use. like i have another pc running mint on it and if i can save this file i'll be able to install the package on that one too without downloading it again as i have a little problem about my bandwidth.. 

i think it might be saved somewhere on the system with all the dependencies before apt installs it right !?!? would it be /tmp ?!?!

---

### Post by howefield on 2011-06-07
Download the file that matches your Ubuntu version from here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and choose the Save File option to save the .deb file to your download location. Once downloaded, double click the file to start the install process. The downloaded file can then be copied and used in another computer, 

If your Mint install is based the same version of your Ubuntu install, it will most likely work, but no guarantees.

---

### Post by nos09 on 2011-06-07
> **howefield said:**
> Download the file that matches your Ubuntu version from here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and choose the Save File option to save the .deb file to your download location. Once downloaded, double click the file to start the install process. The downloaded file can then be copied and used in another computer, 

If your Mint install is based the same version of your Ubuntu install, it will most likely work, but no guarantees.

excellent !! and one last question.. do i have to delete .virtualbox folder in my home directory that created by the old virtualbox OSE ? there's a xp virtual hdd there and some other logs and stuff ?! i mean if the version are different would it cause the trouble ?!!?

---

### Post by howefield on 2011-06-07
I don't think you need to delete that folder, although I'd be inclined to after saving the .vdi file which is your XP virtual machine "disk".

You can recreate your settings for the Virtual Machine and point it to your .vdi file where ever you store it.

---

### Post by nos09 on 2011-06-07
Thank you all for the guidance, especially *howefield* and *linuxinstalledfromhdd*, you really saved my day !! 

So I last night I really wanted to share folders with my virtual os but as i googled it didn't really fond any helping tutorial at once (I'm sure there would be.) so by the help of ubuntu community i did the trick so thought may be I should post steps to do that to help others .. ( and of course as I don't know much about this stuff, people should correct this if I'm wrong in somewhere. 

> step 1) There are two versions available 1. virtualbox OSE(Open Source Edition) and 2. Virtualbox. Basically the difference what I've learned is in the OSE the folder sharing facilities are not provided. So we need to download the second one. the download link is [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

now choose your appropriate Distribution and download it. 

or alternatively you can directly download and install the package on the ubuntu 10.10 by this code : ```
sudo echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.0
```

step 2) Install the downloaded package.

step 3) Now to enable sharing we need a extra package to download called 'Oracle VM VirtualBox Extension Pack'. You can download the extension from the oracle site using this link :[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html")
To install the extension pack File > Preferences > Extension, click on the add button and navigate to your downloaded extension pack file.

step 4) install "Guest Additions" in the guest machine. To install it, there should be an option in your Device > Install guest additions (or Host+D) click on it. the setup will then run on the guest OS, just follow the installation wizard.

step 5) we're done here. now to share a folder just add the path of the folder you want to share in your shared folder tab (setting > shared folders). The folders should displayed in your guest OS as a network drive.

step 6) to enable usb access in the guest OS there's an awesome tutorial I've found on the net : [http://www.dedoimedo.com/computers/virtualbox-usb.html]("http://www.dedoimedo.com/computers/virtualbox-usb.html") which i believe would help you more than i can, and there are some other pretty interesting stuffs too ..
. 

this should work on Windows and some other linux distribution too, as i've tried the same on Fedora and windows.

 for more information you should see this virtualbox manual page : [http://www.virtualbox.org/manual/ch04.html#idp11234128]("http://www.virtualbox.org/manual/ch04.html#idp11234128")  
:popcorn:

---

### Post by linuxinstalledfromhdd on 2011-06-07
Hey thanks for posting the followup to share with others about your success.:popcorn:

---

### Post by nos09 on 2011-06-08
> **linuxinstalledfromhdd said:**
> Hey thanks for posting the followup to share with others about your success.:popcorn:

who said i did that to help 'others' !! ;) ;)

---

### Post by nos09 on 2011-06-08
i was wondering is there anyway to change the name of the thread.. i mean it does says "sharing folders and usb in virtualbox xp-guest", but its not the full truth i have succeded to do the same on other linux distoes too like fedora and slackware as guest too.. so ummm i was thinking may be its good to change the name though its not a big deal anyway..

---

