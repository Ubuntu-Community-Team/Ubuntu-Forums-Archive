---
title: "Connect extrernal monitor to laptop"
date: 2012-08-24
forum: General Help
---

### Post by sagar_322 on 2012-08-24
Hi all, I have Lenovo ideapad laptop and I want to connect a external monitor to it. I have LG W2243T monitor with resolution of 1920x1080 now I want to connect the monitor to laptop and set the max resolution (i.e 1920x1080) how do I do that.. Now currently I am running ubuntu 10.04. 
Thanks in advance..

---

### Post by kimberlite on 2012-08-24
Install "grandr" either via synaptic or from terminal:
```
sudo apt-get install grandr
```.
GRandr provides a friendly interface to monitor configuration and includes controls for video mode, rotation and monitor position.

---

### Post by sagar_322 on 2012-08-24
> **kimberlite said:**
> Install "grandr" either via synaptic or from terminal:
```
sudo apt-get install grandr
```.
GRandr provides a friendly interface to monitor configuration and includes controls for video mode, rotation and monitor position.

I did that but I got max resolution for the external monitor as 1280x720 in grand UI. because of which display in monitor looked bigger. I want to set maximum resolution for monitor(which is 1920x1080)

---

### Post by kimberlite on 2012-08-24
Read this [wiki]("https://wiki.ubuntu.com/X/Config/Resolution") page and post the output of xrandr command from terminal.

---

### Post by sagar_322 on 2012-08-24
> **kimberlite said:**
> Read this [wiki]("https://wiki.ubuntu.com/X/Config/Resolution") page and post the output of xrandr command from terminal.

this is what I am getting after xrandr

Screen 0: minimum 320 x 200, current 2646 x 768, maximum 2732 x 768
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.0*+
   1360x768       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.0  
   800x480        60.0  
   640x480        60.0  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x768+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x768       75.0*    60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   1024x600       75.0     60.0  
   800x600        75.0     60.3  
   800x480        75.0     60.3  
   640x480        75.0     59.9

---

### Post by kimberlite on 2012-08-27
I see, the problem is that your maximum available resolution is 1280x768 instead of full HD. I guess this is because of your graphic card's driver. Posting the output of "lspci |grep VGA" may provide useful info... 
Also make sure that your monitor is connected and turned on when you log in.

---

### Post by sagar_322 on 2012-08-28
> **kimberlite said:**
> I see, the problem is that your maximum available resolution is 1280x768 instead of full HD. I guess this is because of your graphic card's driver. Posting the output of "lspci |grep VGA" may provide useful info... 
Also make sure that your monitor is connected and turned on when you log in.
Thanks for the reply.. This what I got from lspci |grep VGA
'01:00.0 VGA compatible controller: ATI Technologies Inc Device 68c0'

---

### Post by kimberlite on 2012-08-28
> **sagar_322 said:**
> 
'01:00.0 VGA compatible controller: ATI Technologies Inc Device 68c0'

Let's see any proprietary driver is installed or a generic one is used. To tell the truth I do not have any experience with ATI cards, but I red about "aticonfig" command, which is available, when proprietary driver is used.
What is the output of "jockey-text -l" and "aticonfig"?

---

### Post by kimberlite on 2012-08-28
The strange thing in your setup that your LCD was recognized by xrandr as "CRT1" rather than VGA1. By the way, do you use a standard VGA cable and can you connect to your monitor using DVI or HDMI cable?

---

### Post by sagar_322 on 2012-08-30
> **kimberlite said:**
> The strange thing in your setup that your LCD was recognized by xrandr as "CRT1" rather than VGA1. By the way, do you use a standard VGA cable and can you connect to your monitor using DVI or HDMI cable?

I am using standard VGA cable to connect

---

### Post by dodo3773 on 2012-08-30
Try disabling your laptop monitor and only using the external one instead of trying to stretch the two. Can you hit 1920x1080 then? I am also confused about the CRT portion as well. Do you have any type of configuration interface on the monitor itself that would affect the way it is read by your computer?

---

### Post by sagar_322 on 2012-09-01
> **dodo3773 said:**
> Try disabling your laptop monitor and only using the external one instead of trying to stretch the two. Can you hit 1920x1080 then? I am also confused about the CRT portion as well. Do you have any type of configuration interface on the monitor itself that would affect the way it is read by your computer?

Tried that also but no luck... And there is no configuration interface as such on the monitor

---

### Post by kimberlite on 2012-09-01
> **kimberlite said:**
> Let's see any proprietary driver is installed or a generic one is used. To tell the truth I do not have any experience with ATI cards, but I red about "aticonfig" command, which is available, when proprietary driver is used.
What is the output of "jockey-text -l" and "aticonfig"?

So, what about your video card driver? Is it proprietary or generic?

---

