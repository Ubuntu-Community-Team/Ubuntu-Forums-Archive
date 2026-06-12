---
title: "Live CD boots but stops at the gui"
date: 2006-03-10
forum: General Help
---

### Post by m_pav on 2006-03-10
I have a Toshiba M30 RE002 laptop with nVidia GeForce Go 6200 graphics. My problem is when booting from the Ubuntu 5.10 live CD, the system boots and all goes really well until the GUI starts up. X starts up and I get a mouse pointer at what looks like the right screen resolution that I can move anywhere on the otherwise blank screen, but that's about as far as it gets. I have had the same issues with other live CD's, but I want to really give ubuntu a try as it worked really well with my old laptop but I only had it for a few days before I sold the old acer to get this toshiba.

I'd like to install Ubuntu onto this machine, but if the lie CD is anything to go by, the install CD may not be any better and I do not wish to be in a position to hae to go through the process only to be left with an unusable system.

To get my system up and running with a fully functional gui, is there a command I can type at boot that will give me a working GUI using the live CD? I need to find out what hardware is supported because I have a wireless network and I want to check to see if the inbuilt wireless will work

---

### Post by leviathan660 on 2006-03-10
I had the same problem a couple of weeks back, as it turns out, your graphics card is too new, and is not supported by the drivers on that CD. (I have a 7800GT, dont worry, it can be updated). 
1) After it boots, Mash on the keyboard pressing Ctrl+Alt+F1 (or F2, doesnt matter), this will take you to the console. If you dont see it, and just see the GUI, you are doing it too late. You have to do this right when you see the GUI.
2) I assume right now that you can connect to the net. If not, I'll tell you what to do

If you can connect to the net, type in the following into the console

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nano /etc/X11/xorg.conf  
***From here, scroll down, find the part that talks about Nvidia drivers, change it from "nv" to "nvidia", press F3 to save, and F2 to quit***
sudo /etc/init.d/gdm restart

If that doesnt work (you may not be able to connect to the net like me), type in the nano bit, and change "nv" to "vesa", and then do the restart.  You can change you drivers later.

---

### Post by m_pav on 2006-03-10
Cool, thanks, I thought the graphics were the issue. So far, I have just been trying to run the live CD, and haven't tried the install disk yet. I will try your suggestions as I travel this weekend and report back because I don't have the time to do it right now .

The wireless internet connection would be a shame not to have, but if I can get the gui running, I will work on the wireless next. It works with Mepis, but I have to use their meauto to set the ssid name of the station I am connecting to. Maybe you could try whatever ubuntu has as an equivalent, or possible from the command line something like iwconfig (device) ssid (name). I saw this somewhere in a mepis forum and I'm going by memory only so it may not be the correct command, but it may help to get the grey matter thinking on the right path?

---

### Post by m_pav on 2006-03-10
Beautiful, lovely, magnificant, the process worked and I am in gui from the live cd and on the net via my inbuilt wireless and using the nidia drivers.

What can I say but awesome! Now it's time to shrink windows down to a litte iddy biddy partition, which is all it deserves and go live with a real system.

---

### Post by leviathan660 on 2006-03-11
Hey no problem, as for shrinking the windows partition, try Gparted, if it cannot be done, you're going to have to delete the partition (make sure you back up all your personal files) and do it from there.

---

### Post by SpankR on 2006-03-26
Has anyone merged the new drivers with the live cd?

---

