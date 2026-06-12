---
title: "Desktop Effects Could Not Be Enabled: Ubuntu 9.04 Jj"
date: 2009-09-19
forum: General Help
---

### Post by Habboblob on 2009-09-19
Fixed my problem.
Just installed EnvyNG

[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

and it made everything work easy.

I didn't even need to do anything beside install it, the rest was easy!

---

### Post by Tamlynmac on 2009-09-19
Just a quick thought:

Have you checked "system/administration/hardware drivers" to assure your 3d driver is activated and currently in use? If it's not activated and in use, select the Activate Button in the bottom right hand corner. I believe that may require a reboot.

Good Luck and hope this helps.

---

### Post by mc4man on 2009-09-19
One thing worth checking **if you do have the drivers installed **(direct rendering enabled
in a terminal
```
gconf-editor
```

Then expand apps, scroll down to 'metacity', expand and click on 'general' 

look over in the r. side box for "compositing_manager" and make sure it's **unchecked**.
If it is checked then uncheck and try enabling desktop effects again

---

### Post by realgt on 2009-09-21
> **mc4man said:**
> One thing worth checking **if you do have the drivers installed **(direct rendering enabled
in a terminal
```
gconf-editor
```

Then expand apps, scroll down to 'metacity', expand and click on 'general' 

look over in the r. side box for "compositing_manager" and make sure it's **unchecked**.
If it is checked then uncheck and try enabling desktop effects again

worked for me, thanks!!

---

### Post by Habboblob on 2009-09-24
> **Tamlynmac said:**
> Just a quick thought:

Have you checked "system/administration/hardware drivers" to assure your 3d driver is activated and currently in use? If it's not activated and in use, select the Activate Button in the bottom right hand corner. I believe that may require a reboot.

Good Luck and hope this helps.
When I opened up Hardware Drivers at the top it has said "No proprietary drivers are in use on this system.

> **mc4man said:**
> One thing worth checking **if you do have the drivers installed **(direct rendering enabled
in a terminal
```
gconf-editor
```

Then expand apps, scroll down to 'metacity', expand and click on 'general' 

look over in the r. side box for "compositing_manager" and make sure it's **unchecked**.
If it is checked then uncheck and try enabling desktop effects again

I had also followed that and compositing_manager was already unchecked.

Please help me out :S:(:icon_frown:

---

### Post by Habboblob on 2009-09-30
Anyone? I really need to help to fix this problem.

I have a Gigabyte NVIDIA 8400GS, and my computer is a Dell Dimensions 4700 with an upgraded 2.5GB of Ram.

Please help me out, I am still a Noob with Ubuntu and am needing some desperate help here. :confused::confused::(

---

### Post by Tamlynmac on 2009-09-30
Are there any drivers listed in the "system/administration/hardware drivers" window or is it blank?

If any are any listed in the window, select the one that's "recommended" and then select the "Activate" button.

Good Luck

---

### Post by Habboblob on 2009-09-30
> **Tamlynmac said:**
> Are there any drivers listed in the "system/administration/hardware drivers" window or is it blank?

If any are any listed in the window, select the one that's "recommended" and then select the "Activate" button.

Good Luck

It's blank when I try that.
Just comes up with a Blank Window.
Here is a picture of what it looks like:
[img]http://victorystreet.net/uploader/filestore/2a/VvJq3iFkBF.Screenshot-Hardware_Drivers.png._[/img]

---

### Post by oldos2er on 2009-09-30
> **Habboblob said:**
> It's blank when I try that.
Just comes up with a Blank Window.
Here is a picture of what it looks like:
[img]http://victorystreet.net/uploader/filestore/2a/VvJq3iFkBF.Screenshot-Hardware_Drivers.png._[/img]

 Check System, Administration, Software Sources, and make sure all repositories, including Source code, are enabled. The open a terminal, and run ```
sudo apt-get update && sudo apt-get install nvidia-glx-180
```

---

### Post by Habboblob on 2009-09-30
> **oldos2er said:**
> Check System, Administration, Software Sources, and make sure all repositories, including Source code, are enabled. The open a terminal, and run ```
sudo apt-get update && sudo apt-get install nvidia-glx-180
```

I found out that source code wasn't ticked. To I ticked it.
But when I tick it, it comes up with out-dated, so I click on reload, and a window comes up with this
```
[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/B]
[CODE]GPG error: http://mirror.noreply.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDDGPG error: http://www.bashterritory.com  Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch http://www.bashterritory.com/pytube/releases/Packages.bz2  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
```[/CODE]

After that, another windows comes up with this error
```
**An error occurred**

The following details are provided:
[CODE]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```[/CODE]


When I tried the following command in the Terminal:
```
sudo apt-get update && sudo apt-get install nvidia-glx-180
```

This is the log which I receive:
```
sudo apt-get update && sudo apt-get install nvidia-glx-180
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 http://www.bashterritory.com  Release.gpg                                
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Ign http://archive.ubuntu.com jaunty/main Translation-en_US                    
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Get:2 http://mirror.noreply.org jaunty Release.gpg [197B]                      
Ign http://mirror.noreply.org jaunty/main Translation-en_US                    
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US              
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US   
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US     
Hit http://archive.ubuntu.com jaunty-updates Release.gpg            
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US 
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://archive.ubuntu.com jaunty Release                                   
Get:3 http://mirror.noreply.org jaunty Release [1930B]                         
Ign http://mirror.noreply.org jaunty Release                                   
Hit http://archive.ubuntu.com jaunty-updates Release                           
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Ign http://mirror.noreply.org jaunty/main Packages                             
Hit http://archive.ubuntu.com jaunty/main Sources                              
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Hit http://archive.ubuntu.com jaunty/main Packages                             
Hit http://archive.ubuntu.com jaunty/restricted Packages                       
Hit http://archive.ubuntu.com jaunty/multiverse Packages                       
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Ign http://mirror.noreply.org jaunty/main Sources                              
Hit http://archive.ubuntu.com jaunty/universe Packages                         
Hit http://archive.ubuntu.com jaunty/multiverse Sources                        
Hit http://archive.ubuntu.com jaunty/universe Sources                          
Hit http://archive.ubuntu.com jaunty-updates/main Packages                     
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages               
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages               
Hit http://archive.ubuntu.com jaunty-updates/universe Packages                 
Hit http://archive.ubuntu.com jaunty-updates/main Sources                      
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://mirror.noreply.org jaunty/main Packages                             
Get:4 http://www.bashterritory.com  Translation-en_US [1795B]        
99% [4 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign http://www.bashterritory.com  Translation-en_US                            
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources                
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources                
Hit http://archive.ubuntu.com jaunty-updates/universe Sources                  
Hit http://mirror.noreply.org jaunty/main Sources                              
Get:5 http://www.bashterritory.com  Release                                    
Ign http://www.bashterritory.com  Release
Get:6 http://www.bashterritory.com  Packages [1819B]
97% [6 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err http://www.bashterritory.com  Packages
  Sub-process bzip2 returned an error code (2)
Fetched 69.9kB in 4s (15.8kB/s)
W: GPG error: http://mirror.noreply.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: GPG error: http://www.bashterritory.com  Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://www.bashterritory.com/pytube/releases/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Then when I try to enable Visual Effects, it still comes up with the error "Desktop Effects could not be Enabled"[img]http://victorystreet.net/uploader/filestore/1a/VyGs-LJVLE.Screenshot-DesktopEffectNotApplied.png._[/img]

---

### Post by oldos2er on 2009-09-30
I would temporarily disable bashterritory.com and noreply.org, then retry the command I gave you.

---

### Post by Habboblob on 2009-10-04
Doesn't matter anymore.
I gave up at it and just re-installed Ubuntu to a External HDD.

Once freshly installed, what would be the best way for me to install the drivers?

---

### Post by Tanker Bob on 2009-10-04
Try [envyng](http://albertomilone.com/nvidia_scripts1.html).

---

### Post by Habboblob on 2009-10-04
Updated first post.

> **Habboblob said:**
> [B][I][COLOR="Black"]Just re-installed Ubuntu.
After installing, I had received a message about restricted drivers, so I clicked on it and it has opened a Hardware window.

Here are 2 screenshots to show you:
[[img]http://victorystreet.net/uploader/thumbstore/73/ILoFVnj73Z.Screenshot-Hardware_Drivers1_thumb.png[/img]](http://victorystreet.net/uploader/index.php/image/show/ILoFVnj73Z/screenshot-hardware-drivers1.png)

[[IMG]http://victorystreet.net/uploader/thumbstore/4f/8IrQC6LY8X.Screenshot-Hardware_Drivers2_thumb.png[/IMG]](http://victorystreet.net/uploader/index.php/image/show/8IrQC6LY8X/screenshot-hardware-drivers2.png)
What should I do to enable these drivers so that I can use desktop effects?

Once again, I have a Dell Dimension 4700 with a Gigabyte NVIDIA 8400GS.[/COLOR][/I][/B]

---

### Post by Habboblob on 2009-10-04
Fixed my problem.
Just installed EnvyNG

[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

and it made everything work easy.

I didn't even need to do anything beside install it, the rest was easy.

---

