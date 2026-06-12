---
title: "hci_cmd_timer: ............. Error"
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

### Post by howefield on 2012-04-08
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1954777](http://ubuntuforums.org/showthread.php?t=1954777)

---

