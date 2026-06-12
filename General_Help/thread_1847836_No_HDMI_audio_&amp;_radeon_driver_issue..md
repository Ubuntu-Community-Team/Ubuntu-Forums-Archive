---
title: "No HDMI audio &amp; radeon driver issue."
date: 2011-09-21
forum: General Help
---

### Post by alousyhero on 2011-09-21
I just built a custom PC with:
Gigabyte A75m-UD2h
8 GB Ram
AMD A6 APU
1TB HDD
DVD-RW

I installed Natty, updated and everything. No HDMI audio came out, and I tried to install ATI proprietary drivers. When I restarted, I got a balck screen with a nuch of text and [ok] on the right of each.

I've uninstalled three tmes, tried tons of ways. Could anyone help me please? I"m still relatively new to Ubuntu.

---

### Post by Mark Phelps on 2011-09-21
Need to know the make and model video card/chip you're using.

If you don't know that, open a terminal, enter "lspci" and look for the line containing "VGA".  Post that line back here.

---

### Post by seawolf167 on 2011-09-21
Each time you attempted to install the drivers you were unable to get back to a GUI? Did you uninstall the drivers between attempts? Did the driver under the "Additional Drivers" section work?

As MarkPhelps stated, so we can see what card you have, please run the following command

```
sudo lshw -class video
```

or

```
lspci | grep VGA
```

---

### Post by alousyhero on 2011-09-21
00:01.0 VGA compatible controller: ATI Technologies Inc Device 964a

I was unable to get back to a GUI. It hung on the screen. I tried the additional drivers one also. Same thing.

---

### Post by seawolf167 on 2011-09-21
Where did you get the driver from for this device?

---

### Post by alousyhero on 2011-09-21
I've tried the one on the AMD site and the one in the additional drivers window. THey both install, and once I go to reboot. it brings up a black with tons of text like 

starting ___________                                                                                            [ok]
starting ___________                                                                                            [ok]

The ________ is different items. I can hit Ctrl-Alt-Del to restart, and I went into TTY and logged in, but I had no clue how to get into the GUI from it.

---

### Post by seawolf167 on 2011-09-21
This driver [here ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")for the Raedon HD 3200?

From what I remember from installing these drivers you have to stop gdm before you can install them. Something like

```
sudo service gdm stop
cd /path/to/driver
sudo chmod +x name_of_driver.run
./name_of_driver.run
```

Did it give you any problems/issues/warnings during the *initial* graphics driver install?

When you are on the black tty screen, do either of these commands work, if not, what is the output

```
startx
sudo service gdm start
```

---

### Post by alousyhero on 2011-09-21
That's the driver. I'll try that then install again. Should I change it where it says name-of-driver?

EDIT:
Forgot. No errors or anything during intial install. Just tells me to restart.

---

### Post by Drake411 on 2011-09-29
You might find a clue in the article at the following link. I believe you are looking for a catalyst driver but I'm not sure.

[http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=3](http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=3)

Because the AMD A6 is a quad core with a GPU attached for graphics its a bit different than your traditional system.

I am glad to here your making some progress because I intend to buy the same motherboard and probably the AMD A8. I found your post because I would like to try postpone a Windows 7 purchase but still try set up my hardware. If that is even possible.
Drake

---

