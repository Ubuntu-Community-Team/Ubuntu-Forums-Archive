---
title: "Multiple queries from absolute beginner"
date: 2010-02-21
forum: General Help
---

### Post by cyberjar09 on 2010-02-21
Hi i am an absolute beginner with ubuntu but have decided to use open source software and have a few problems and questions i wish to clarify.

1) I have an nvidia gtx260 graphics card. I have installed the drivers from the synaptic package manager as well as downloaded and installed the drivers from the nvidia site but am still not getting he right colour representation. I think it maybe has to do with the codecs missing. The colours are grossly changed. Greens appear blue etc. Please help.

2) I wish to secure a pen drive and use it when accessing my data from a public computer. I know it is possible to boot up from a flash drive but my question is will I be able to access the local NTFS/FAT32 partitions on the computer into which I have plugged the drive in?

3) My ubuntu has updated itself several times since I first installed it and now the bootup screen shows 3 options (recovery mode, and 2 others) for every updated version along with my windows bootup option. How do i remove the older options from the boot record and how do i make it point to the os of my choice automatically?

Thanks alot for your help and im sorry if i have posted in the wrong category. 

regards, 
cyberjar09.

---

### Post by drpjkurian on 2010-02-21
> **cyberjar09 said:**
> 
3) My ubuntu has updated itself several times since I first installed it and now the bootup screen shows 3 options (recovery mode, and 2 others) for every updated version along with my windows bootup option. How do i remove the older options from the boot record and how do i make it point to the os of my choice automatically?

Thanks alot for your help and im sorry if i have posted in the wrong category. 

regards, 
cyberjar09.

Hi
When you have kernel updates, you will the entry of new kernel in bootup screen. It is recommended to keep atleast one so that you can boot into the old kernel in case if the new one nags.

You can delete the old kernels by deleting 'linux-image' from synaptic package manager

---

### Post by Swagman on 2010-02-21
I believe it's 

```
sudo nvidia-settings
```

You wont see your password when you type it in 

Your pen drive will access EVERYTHING on that computer

install startup manager for boot options

ubuntu tweak to get rid of old kernals and auto update grub to reflect changes

---

### Post by cyberjar09 on 2010-03-03
When I run sudo nvidia-settings in terminal, i get the NVIDIA X Server Settings in which i figured that in my X Server XVideo Settings, the Hue keeps going back to -1000 automatically causing the bad picture. Everytime i drag back the hue to 0 its fine again. Any fix??

Also, if ubuntu hangs, is there any remedy like alt+ctl+del in windows to pop up the task manager and close certain tasks.?

---

### Post by cyberjar09 on 2010-03-04
No help? kinda hanging here waiting for some help guys.
Thx.

---

### Post by byrneda on 2010-03-04
> **cyberjar09 said:**
> 
Also, if ubuntu hangs, is there any remedy like alt+ctl+del in windows to pop up the task manager and close certain tasks.?

I had this happen to me last night.
I foolishly setup the auto-login whilst having an encrypted /home profile.

If you're not getting anything on the GUI, try using the keyboard shortcut:
Ctrl + Alt + F1
This should give you a terminal login (similar to DOS, but don't call it that).
You can then enter in your username and password.

Now, for task manager, the application is called TOP
At the prompt, type TOP and press Return.

I believe the Page Up and Page Down keys will let you browse through the many pages.
What I think you're looking for is the process called Xorg.
Follow along this line until you get the corresponding PID (Process ID).  You can then call sudo to kill this and chuck you back to the login screen.

What I do, however, is this:
top | grep Xorg

I then press Q to exit from TOP, then type the following to kill the process:
sudo kill -9 <PID>
(where <PID> is the PID for Xorg)

It's very different to windows in that everything you can do in the Ubuntu Gui, you can do in the terminal window.

Hope this helps, I'll help when I can :)

---

### Post by cyberjar09 on 2010-03-04
Thanks alot Byrenda, im very new to ubuntu and im still trying to get my grip around working the OS.

---

### Post by cyberjar09 on 2010-03-10
> **Swagman said:**
> I believe it's 

```
sudo nvidia-settings
```You wont see your password when you type it in 

Your pen drive will access EVERYTHING on that computer

install startup manager for boot options

ubuntu tweak to get rid of old kernals and auto update grub to reflect changes


sudo nvidia-settings    does help me open the Nvidia X Server Settings but under the sub tab called "X Server XVideo Settings" the "hue" value keeps resetting itself to -1000 everytime a new video file is run. I have to keep going into the settings to reset it to 0. 

Please help.

also, I used gnome partition to create a partition on my flash drive 8gb as 2 gb ubuntu live and remaining for data storage but the problem i faced is that with windows based systems I was only able to access the ubuntu live partition. what file system is compatible with both windows and ubuntu? fat 32 would be my guess.

Ubuntu tweak is not even executing on my system... :confused:

---

