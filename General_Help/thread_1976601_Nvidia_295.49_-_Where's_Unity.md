---
title: "Nvidia 295.49 - Where's Unity"
date: 2012-05-09
forum: General Help
---

### Post by aoniumo on 2012-05-09
I updated nvidia drivers to 295.49 and now unity is gone.  Just nothing. No unity 2d or whatever.  When I login it's just a blank screen and all I see is my wallpaper.  No way to access stuff.  Restarted and still the same.  Went back to 295.40 and still the same.

What happened and can anyone help?

---

### Post by Sef on 2012-05-09
how did you upgrade the driver and downgrade the driver?

---

### Post by aoniumo on 2012-05-09
> **Sef said:**
> how did you upgrade the driver and downgrade the driver?

Upgraded via Update Manager and downgraded via Additional Drivers.

---

### Post by ladasky on 2012-05-09
Hi, aoniumo,

I feel your pain.  There are so many things that can go wrong with video drivers, it's not even funny.

I just went through an NVidia driver crash (because of NVidia's security fix from last month), followed by a driver AND video card upgrade, which STILL required me to manually build the 295.49 driver from a rescue shell to make it all work.

It appears that the central hub for this type of discussion is _[this thread]("http://ubuntuforums.org/showthread.php?t=1743535")_.  Join us over there?

---

### Post by Baldrick_NZ on 2012-05-09
Hi aoniumo,

Try ctrl-alt-F1 to get to terminal, then```
unity --reset
```
which should reset unity to default state.

Best then to reboot then re-configure Unity the way you like it.

---

### Post by aoniumo on 2012-05-09
> **Baldrick_NZ said:**
> Hi aoniumo,

Try ctrl-alt-F1 to get to terminal, then```
unity --reset
```which should reset unity to default state.

Best then to reboot then re-configure Unity the way you like it.


Commands do not work.
As I said, it's just a blank screen with a wallpaper - no shortcuts, menus, etc.  Pressing Super key does nothing.  Ctrl Alt F1 takes me to a full screen terminal and unity --reset does nothing.   This is not terminal, I don't think since I can't ESC or X out of it.  I can only press power button to restart computer.

---

### Post by Baldrick_NZ on 2012-05-09
> **aoniumo said:**
> Commands do not work.
As I said, it's just a blank screen with a wallpaper - no shortcuts, menus, etc.  Pressing Super key does nothing.  Ctrl Alt F1 takes me to a full screen terminal and unity --reset does nothing.   This is not terminal, I don't think since I can't ESC or X out of it.  I can only press power button to restart computer.

Oops, sorry, crtl-alt-f7 to back out into unity again.

---

### Post by needeffexor on 2012-05-09
> **aoniumo said:**
> Upgraded via Update Manager and downgraded via Additional Drivers.

The drivers in the repos are still at 295.40 (Unless someone can show me otherwise.)  There is a known OpenGL regression with GeForce 6 and 7 integrated GPU's that cause this problem.  295.49 fixes this but you have to download it from nVidia and install it manually.  This is a real pain and continues to be a pain with every kernel upgrade.  I have 295.49 working on my laptop and it does indeed solve the problem, but I would probably recommend waiting until it is at lease in the ppa:ubuntu-x-swat/x-updates ppa.  Until then suffer with Nouveau.  

LMK if would like to install 295.49 manually and I will dig up the instructions.

---

### Post by aoniumo on 2012-05-09
> **Baldrick_NZ said:**
> Oops, sorry, crtl-alt-f7 to back out into unity again.


Sorry, nothing happens when I press CTRL ALT F7 on my blank screen with a wallpaper (nothing loads, appear, flicker or whatever).

---

### Post by aoniumo on 2012-05-09
> **needeffexor said:**
> The drivers in the repos are still at 295.40 (Unless someone can show me otherwise.)  There is a known OpenGL regression with GeForce 6 and 7 integrated GPU's that cause this problem.  295.49 fixes this but you have to download it from nVidia and install it manually.  This is a real pain and continues to be a pain with every kernel upgrade.  I have 295.49 working on my laptop and it does indeed solve the problem, but I would probably recommend waiting until it is at lease in the ppa:ubuntu-x-swat/x-updates ppa.  Until then suffer with Nouveau.  

LMK if would like to install 295.49 manually and I will dig up the instructions.


295.49 is already installed.  Attached is a screencap of my Nvidia Xserver Settings showing version.

---

### Post by bogan on 2012-05-10
Hi!, **aoniumo**,

After pressing Ctrl+Alt+F1, logging-in and entering password, have you run ```
gksudo nvidia-settings
``` [ or from root] and saved the settings to /etc/X11/xorg.conf and rebooted?? [COLOR=Yellow]*[Edited: first phrase added.]*
[/COLOR] 
This cured similar problems I had after a change of Monitor with 295.49 and a GT7650 card.

Chao! **bogan**.

---

### Post by philinux on 2012-05-10
> **aoniumo said:**
> I updated nvidia drivers to 295.49 and now unity is gone.  Just nothing. No unity 2d or whatever.  When I login it's just a blank screen and all I see is my wallpaper.  No way to access stuff.  Restarted and still the same.  Went back to 295.40 and still the same.

What happened and can anyone help?

Are you running Precise or Quantal?

---

### Post by aoniumo on 2012-05-11
Oh, well. I'll just live with it and use Cairo dock.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by Frogs Hair on 2012-05-17
When you enter TTY make sure to login by typing with your user name and  password then enter the code as described before.  ```
unity --reset
```

Wait for the process to complete and use Ctrl + Alt F7 to enter the desktop. If an error report is being sent wait until complete and Unity should appear shortly after.

---

