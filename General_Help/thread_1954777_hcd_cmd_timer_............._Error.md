---
title: "hcd_cmd_timer: ............. Error"
date: 2012-04-08
forum: General Help
---

### Post by asifrazzaq on 2012-04-08
hi there

i am facing problem with booting Ubuntu on Dell N5110 3 GB RM with 1 GB NVIDIA Graphic card, it get stuck with black screen having following lines

19.2222 hci_cmd_timer: hci0 command tx timeout
.
.
.
goes on

this problem arise when i tried to install NVIDIA-Linux-x86_64-295.33.run

by following commands from website
[http://www.moonlitdog.com/nvidia_ubuntu](http://www.moonlitdog.com/nvidia_ubuntu)

commands as under

1) Stop X by
> sudo /etc/init.d/lightdm stop

2) Navigate to your download folder and type
> chmod +x NVIDIA-Linux-x86_64-290.10.run
then
> sudo sh NVIDIA-Linux-x86_64-290.10.run

3) That should do it, to start X and see if it worked
> sudo /etc/init.d/lightdm start


from then on i cant find the desktop because it seems it goes in halt state, if a press ctrl+alt+f2 i can reach the prompt

If anyone can help


Best Regards

---

### Post by Paddy Landau on 2012-04-09
If it worked before, why were you installing the driver? Does it offer features that you needed?

On the page that you indicated, it says:
> 7) You can uninstall this driver by
> sudo sh NVIDIA-Linux-x86_64-290.10.run --uninstallI suggest that you do that.

After rebooting, you can run *Additional Drivers*, which will automatically search for proprietary drivers. If found, they will be listed, and you can try enabling them if you think it necessary.

---

### Post by asifrazzaq on 2012-04-11
thanks for considering my problem, i hope everything would be fine around you,

in fact i was in search of other features, as offered by windows, to install separate drivers for Nvidia, my question is how to get out of such "time out"  state (Seems Hung),

---

### Post by Paddy Landau on 2012-04-12
[LIST=1]
[*]Start your computer.
[*]While it is starting up, press and hold the Shift key.
[*]You should be presented with the Grub menu --  a purple screen with a few lines.
[*]Use your arrow keys to choose the first one with "recovery mode". It will read something like:```
Ubuntu with Linux 3.2.0-23-generic (recovery mode)
```Press Enter.
[*]You will receive a new screen with a list of items. Use your arrow keys to choose:```
root     Drop to root shell prompt
```
[/LIST]
Now, you will be able to try to uninstall. Try entering the command that you were instructed to do:
```
sudo sh NVIDIA-Linux-x86_64-290.10.run --uninstall
```Let us know what happens.

For future note, while you are a beginner, please **never** download programs from the Internet. Always install **only** through the official channel, which is through the **Ubuntu Software Centre** (unless someone on this forum tells you otherwise). You can also use **Additional Drivers**, which will automatically find proprietary drivers for your system if they are available.

---

