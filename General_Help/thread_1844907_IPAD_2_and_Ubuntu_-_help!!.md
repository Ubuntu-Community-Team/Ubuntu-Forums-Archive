---
title: "IPAD 2 and Ubuntu - help!!"
date: 2011-09-15
forum: General Help
---

### Post by auscanstom on 2011-09-15
Hi guys,
 
I just got my IPAD delivered and I am wondering how I'd set this up with Ubuntu 11.04.
Firstly, I know that itunes cannot be installed on Ubuntu and so does anyone know how I would get the IPAD 2 up and running?
Secondly, is there a way for sync docs, photos, videos etc between my Ubuntu laptop and IPad?
 
I am still a beginner when it comes to Ubuntu commands. Can anyone help with my above questions?
 
Regards,
 
auscanstom

---

### Post by xutnubu on 2011-09-16
> **auscanstom said:**
> Hi guys,
 
I just got my IPAD delivered and I am wondering how I'd set this up with Ubuntu 11.04.
Firstly, I know that itunes cannot be installed on Ubuntu and so does anyone know how I would get the IPAD 2 up and running?
Secondly, is there a way for sync docs, photos, videos etc between my Ubuntu laptop and IPad?
 
I am still a beginner when it comes to Ubuntu commands. Can anyone help with my above questions?
 
Regards,
 
auscanstom

Have you tried installing Wine and then iTunes?

---

### Post by infinitybot on 2011-09-16
> **xutnubu said:**
> Have you tried installing Wine and then iTunes?
Method 1 -
First, you’ll need to install Wine itself on Ubuntu
Next, you’ll need to install PlayOnLinux
Finally, you’ll need to download the iTunes installer ([http://www.apple.com/itunes/download/](http://www.apple.com/itunes/download/))

After you have Wine and PlayOnLinux downloaded and installed, launch PlayOnLinux. After it opens, click on the Run button, select the Multimedia category, and scroll until you see the icon for iTunes 10. Select iTunes 10, and then click the Apply button in the lower-right hand corner. When the iTunes 10 installer script appears, click the Forward button to continue. The script will then ask you where to find the iTunes installer. If you downloaded it to the default location, it’s probably in the Downloads folder. Click on the Browse button, navigate to the installer’s location, select “iTunesSetup.exe”, and then click the Forward button.

From there, follow the default prompts to install iTunes 10 on your system. After the installation is complete, you can launch iTunes by going to the Dash, searching for “iTunes”, and clicking on the iTunes icon (it will probably have the default Wine icon).

Method 2- 
1.) Check libimobiledevice version in System -> Administration -> Synaptic Package Manager, it’s recommended to uninstall libimobiledevice0 if installed.


2.) Add ppa : pmcenery/ppa and install the latest libimobiledevice1 package. Use the commands:

sudo add-apt-repository ppa : pmcenery/ppa
sudo apt-get update
sudo apt-get install libimobiledevice1

3.) Install gtkpod from ubuntu software center.

4.)Now, plug-in your iTouch or iPad device and it should appear in gtkpod.


Sources - [http://www.jonathanmoeller.com/screed/?p=3022](http://www.jonathanmoeller.com/screed/?p=3022)

---

### Post by Kaizoku001 on 2011-09-16
> **infinitybot said:**
> Method 1 -
First, you’ll need to install Wine itself on Ubuntu
Next, you’ll need to install PlayOnLinux
Finally, you’ll need to download the iTunes installer ([http://www.apple.com/itunes/download/](http://www.apple.com/itunes/download/))

After the installation is complete, you can launch iTunes by going to the Dash, searching for “iTunes”, and clicking on the iTunes icon (it will probably have the default Wine icon).

Method 2- 

4.)Now, plug-in your iTouch or iPad device and it should appear in gtkpod.


Sources - [http://www.jonathanmoeller.com/screed/?p=3022](http://www.jonathanmoeller.com/screed/?p=3022)

I'm new to Ubuntu and had the same question.
Thanks for the 2 methods. before I try them, I was wondering what the major diff was between using Itune in Wine and GTKpod.
can you do the same things in gtkPod? (If so no real need to go through Wine)

---

### Post by Kaizoku001 on 2011-09-16
And one more thing, 
What about APPS?
What can I use to synk and back up APPS and contacts and such?

---

