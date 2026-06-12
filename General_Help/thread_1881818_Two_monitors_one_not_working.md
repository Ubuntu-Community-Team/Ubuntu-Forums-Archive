---
title: "Two monitors one not working"
date: 2011-11-16
forum: General Help
---

### Post by davidtheo on 2011-11-16
Can someone please tell me how I can get my two monitors working, they where mirroring each other but when I updated the driver one stopped working, I would like them both working but not mirroring each other

 They both work when I boot to windows

---

### Post by spacesamurai on 2011-11-16
There are a couple of ways to do this. Lets do the easiest. Can I assume you are using Unity? If so, open up the gnome-control-panel. This can be found from the settings in the upper right-hand corner on, looking like the power button. 

Once you open up the settings, look for display. You should be able to do this here.

If you have a separate driver installed, you can also start the driver config tool to set the displays.

Hope this helps.

---

### Post by davidtheo on 2011-11-16
> **spacesamurai said:**
> There are a couple of ways to do this. Lets do the easiest. Can I assume you are using Unity? If so, open up the gnome-control-panel. This can be found from the settings in the upper right-hand corner on, looking like the power button. 

Once you open up the settings, look for display. You should be able to do this here.

If you have a separate driver installed, you can also start the driver config tool to set the displays.

Hope this helps.

I have tried this and it is only showing one monitor and the mirror check box can not be used.

---

### Post by Mark Phelps on 2011-11-16
HOW are the monitors connected?

Are you running two video cards, and each monitor is connected to its own card?

Are you running one card, with both monitors connected?

Are you mixing onboard (i.e., motherboard) monitor connection and separate video card monitor connection?

Are you connecting both monitors to your motherboard? If so, to which connecters (i.e., VGA, DVI, HDMI, Display Port)?

IF you want help, you need to provide details.

---

### Post by davidtheo on 2011-11-16
> **Mark Phelps said:**
> HOW are the monitors connected?

Are you running two video cards, and each monitor is connected to its own card?

Are you running one card, with both monitors connected?

Are you mixing onboard (i.e., motherboard) monitor connection and separate video card monitor connection?

Are you connecting both monitors to your motherboard? If so, to which connecters (i.e., VGA, DVI, HDMI, Display Port)?

IF you want help, you need to provide details.

They are both connected to the video card, The card has two video HDMI plugs I have one monitor connected to each plug

I am using the NVIDIA accelerated graphics driver in Ubuntu the recommended one.

Anything else you need?

---

### Post by davidtheo on 2011-11-16
Windows is showing my Display adapter as an Nvidia Geforce 9600 GT (Microsoft Corporation - WDDM v1.1)

---

### Post by davidtheo on 2011-11-16
I have gotten this driver from the nvidia web site can you please tell me how to install it?

NVIDIA-Linux-x86-285.05.09.run

---

### Post by DeMeNt3d on 2011-11-16
I believe to run it you type:

```
sudo sh file.run
```and if you need to give it permission then:

```
sudo chmod -x file.run
```

---

### Post by davidtheo on 2011-11-16
> **DeMeNt3d said:**
> I believe to run it you type:

```
sudo sh file.run
```and if you need to give it permission then:

```
sudo chmod -x file.run
```

I am getting this error

You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

do I need to reboot in terminal mode or something ? :confused:

---

### Post by DeMeNt3d on 2011-11-16
To stop the X Server in ubuntu try from a terminal:

```

sudo /etc/init.d/gdm stop
``` 

Then switch to a virtual console, e.g. press Alt-Ctrl-F1, login and launch the Nvidia [[COLOR=blue]Installer[/COLOR]]("http://www.linuxquestions.org/questions/#") from there. When you've finished, do

     ```
sudo /etc/init.d/gdm start
```

logout from the console, switch to the X screen (Alt-Ctrl-F7) and the trick is done! Hope this helps. :)

---

### Post by davidtheo on 2011-11-16
> **DeMeNt3d said:**
> To stop the X Server in ubuntu try from a terminal:

```

sudo /etc/init.d/gdm stop
```Then switch to a virtual console, e.g. press Alt-Ctrl-F1, login and launch the Nvidia [[COLOR=blue]Installer[/COLOR]]("http://www.linuxquestions.org/questions/#") from there. When you've finished, do

     ```
sudo /etc/init.d/gdm start
```logout from the console, switch to the X screen (Alt-Ctrl-F7) and the trick is done! Hope this helps. :)

I do not have gdm in the init.d folder :confused:
Also kdm does not work.

---

