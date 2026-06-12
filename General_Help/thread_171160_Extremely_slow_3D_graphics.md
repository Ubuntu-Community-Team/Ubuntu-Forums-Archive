---
title: "Extremely slow 3D graphics"
date: 2006-05-06
forum: General Help
---

### Post by justin2021 on 2006-05-06
When Im trying to play a 3d game such as Armagetron, I only get about 2-4 fps. Also, the graphics look choppy and jumbled up. I have an nVidia card and I dont think it should be that slow and ugly. Any way to download anything to fix this? :confused:

---

### Post by tseliot on 2006-05-06
Follow this guide of mine to install the nvidia proprietary driver:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by ffferko on 2006-05-06
**Select System** >> **Administration** >> **Synaptic Package Manager**.

Click the Search button and enter *nvidia-glx* as a search term. In the list of results, click the check box next to *nvidia-glx* and also* nvidia-settings*, so that both are marked for installation. Then click Apply.

After the Instalation has completed, open a GNOME Terminal window and type *sudo nvidia-glx-config enable*.

Reboot your system (**CTRL + ALT + Backspace**).

To further configure the Nvidia card once your PC is back up and running, open a GNOME Terminal window and type *nvidia-setting*.

---

### Post by justin2021 on 2006-05-06
Ok, i did that and it worked perfectly but now there is another problem. When i shut off my computer for the night, and got back on in the morning, it went into text mode and gave me this error:

Error: API mismatch: the nvidia kernal module is version 1.0.7174, but this x module is version 1.0.7667. Please be sure that your kernal module and all nvidia driver files have the same driver version.

What do I have to do to get my desktop back?

---

### Post by ffferko on 2006-05-07
type
[I]
sudo dpkg-reconfigure xserver-xorg[/I]

at the command prompt to reconfigure your graphics settings.

---

### Post by ffferko on 2006-05-07
try

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29")

---

