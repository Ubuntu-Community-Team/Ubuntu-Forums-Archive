---
title: "How to get higher screen resolution in ubuntu 11.04"
date: 2011-09-20
forum: General Help
---

### Post by solorize on 2011-09-20
Hi,

I have recently put Ubuntu 11.04 (dual boot with Windows XP) onto an old HP xw6200 workstation that has a Nvidia Quadro FX540 graphics card in.

The problem I now have is that Ubuntu only gives me a maximum resolution of 1024 x 768, while if I boot into Windows XP I can get 1280 x 1024.

Does anyone know how I can get Ubuntu to display in 1280 x 1024?

As I want to use Ubuntu as my main OS and just have XP as a backup.

Any help would be appreciated.

Mark

---

### Post by patryk77 on 2011-09-20
Did you install the NVidia drivers?

They should be available under System / Administration / Hardware Drivers (I think)

---

### Post by solorize on 2011-09-20
Hi Patryk77,

I have the following NVidia drivers installed:

[IMG]http://i11.photobucket.com/albums/a199/solorize/drivers1.png[/IMG]


Also under Monitors I can only select a maximum resolution of **1024 x 768**

[IMG]http://i11.photobucket.com/albums/a199/solorize/monitor1.png[/IMG]

Also as shown in the above Monitor settings it states my monitor is "Unknown" but I can't find a way to change this either. My monitor is a Samsung SyncMaster 913N.

I have an older version of Ubuntu running on another another older machine (FYI. I have the two machines hooked up via a KVM Switch, so both machines use the same monitor), and it found my monitor OK and runs the resolution at 1280 x 1024. So I'm unsure why I can't get it to do it on this newer machine. Especially as if on this dual boot machine I select and run Windows it runs at 1280 x 1024 fine, but went I boot into Ubuntu the max it will let me run is 1024 x 786.

FYI. I have the two machines hooked up via a KVM Switch, so both machines use the same monitor.

---

### Post by realzippy on 2011-09-20
You should use nvidia-settings for your resolution settings when running the nvidia driver,not the Gnome GUI.
If 1280x1024 also is not offered there, 
open terminal,run:

```
gksudo gedit /etc/X11/xorg.conf

```
and edit the "section monitor" ,so it contains:
```
....................
HorizSync 30.0 - 83.0
VertRefresh 55.0 - 75.0
....................
```
reboot...
1280x1024 available ?

---

### Post by solorize on 2011-09-20
Realzippy,

Thanks for that, I managed to get it to work.

Cheers.

Mark

---

### Post by realzippy on 2011-09-21
How did you made it? (helps others)
Please set thread as solved (Threadtools) ...(helps others too)
Have fun,
zippy

---

### Post by solorize on 2011-09-21
Ok at first I did not have anything in my **"xorg.conf"**

So I went to **Nvidia X-server Settings**

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_01.png[/IMG]



Then I clicked on the **Save X configuration file** button.
*(please note that the screen resolution that is showing in this screen shot is what I currently have, and was **1024 x 768** before I managed to change it)*

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_02.png[/IMG]


This then populated my "xorg.conf" file and I then edited the settings to:

> HorizSync 30.0 - 83.0
VertRefresh 55.0 - 75.0



As shown in the below image:

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_03.png[/IMG]


I then when back into **Nvidia X-server Settings** and then I had a whole list of higher resolutions that I could now select from.
So I selected the **1280 x 1024**.Then clicked the  **Save X configuration file** button.

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_04.png[/IMG]


I then rebooted my machine and the resolution went back to **1024 x 768**. So I then went back into **Nvidia X-server Settings** and reselected **1280 x 1024**.

Then went into **System -> Preferences -> Monitors**

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_05.png[/IMG]


And then selected **1280 x 1024** and clicked on the **[Apply]** button and then the **[Make Default]** button

[IMG]http://i11.photobucket.com/albums/a199/solorize/step_06.png[/IMG]

Then rebooted the machine and when it came up it had the correct resolution of **1280 x 1024** ;)

Doing it this way worked for me so it may work for other people too.

---

### Post by marelj on 2011-09-21
I did everything in terminal.

sudo apt-get install nvidia-settings nvidia-common nvidia-current

and then:

sudo nvidia-xconfig

Then i restarted my computer working fine with graphic.

I have a nvidia geforce 6600.

---

