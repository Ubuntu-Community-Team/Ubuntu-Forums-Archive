---
title: "Compiz (opengl) - Fatal: Root visual is not a GL visual"
date: 2012-04-15
forum: General Help
---

### Post by asuastrophysics on 2012-04-15
Hey guys,

As usual, I trusted update-manager to actually update things. This is wrong though. I restarted my computer, and now unity won't launch in 3D. I get this error:
```
Compiz (opengl) - Fatal: Root visual is not a GL visual

```

Why am I getting this? 
I am running proprietary NVIDIA drivers.
     Why is canonical seemingly against proprietary graphics drivers? Every time I update anything, it disables my 3D desktop. Any idea as to why this is happening, or how to fix this error?

---

### Post by Yellow Pasque on 2012-04-16
If you just installed nvidia driver 295.40, there are similar complaints. Just hold tight for a fix..

---

### Post by asuastrophysics on 2012-04-17
For anyone else using proprietary drivers, I fixed the problem. 

The nVIDIA drivers I had already installed were a little old (~2 months old), version **295.20**
After going to the nVIDIA website and downloading the latest drivers, I had a file with the version **295.40**

In my unique circumstances, it appears that the 295.20 driver does not play well with the latest updates to libgl-mesa-*
In my case, changing the driver to 295.40 fixed the problem and allowed me to run unity in 3D again. Below is my written-up procedure, in case you want to try this:

1. First, allow your new .run file to be executed as a program. To do this, in the terminal:
```
sudo chmod +x /PATH_TO_YOUR_DOWNLOAD/nVIDIA_DOWNLOAD.run
```

Now, to run the installer, you must exit your X session. To do this, hit CTRL+ALT+F6, and login to the shell with your username and password. Then type the following:
         ***If you are using Unity:***
```
sudo service lightdm stop
```    
         ***If you are using Gnome:***
```
sudo service gdm stop
```

Now, change directories over into the folder containing your nVIDIA download (in my case, the Downloads folder)
```
cd /
cd /home/user/Downloads
```

Now, execute the driver installation by running the following:
```
sudo ./nVIDIA_DOWNLOAD.run
```

Follow the on-screen setup instructions. It will ask you if you want to overwrite the previous driver with the new one. Select "Yes"

Once this is finished, reboot the computer, and all should be well and good now. For good measure, if you still have trouble getting a desktop session started, type 
```
unity
```
Your 3D unity desktop should be working now.

 I'm not exactly sure what libgl is, but I believe it is an open-source generic video driver.
**always check the log files in /var/log/apt  if you're having problems after an update. It will help clue you in on how to fix your issue.**!!! 
^I cannot stress this enough. It will really help you out!


...Long live linux. Long live Ubuntu :guitar:

---

