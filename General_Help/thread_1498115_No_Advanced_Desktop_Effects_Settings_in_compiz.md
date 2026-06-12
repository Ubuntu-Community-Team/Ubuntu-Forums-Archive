---
title: "No Advanced Desktop Effects Settings in compiz"
date: 2010-05-31
forum: General Help
---

### Post by elidoperezmd on 2010-05-31
Hi all.

there is no System > Preferences > **Advanced Desktop Effects Settings** .

im runnig compiz with lynx and im trying to access the advanced desktop effects but i can find it.


where is it? is it not installed?

thanks for the help

---

### Post by cogier on 2010-05-31
You need to start with **System>Preferences>Appearance** click on the **Visual Effects** tab and select **Normal** or **Extra**. If Ubuntu refuses to accept the change your video card is probably not up to the job.

Then you can load the **Advance Desktop Effects Settings** from the **Software Centre** to make your changes.

---

### Post by WinRiddance on 2010-05-31
As mentioned above if you can't choose advanced or extra settings (RIGHT CLICK on desktop then select CHANGE DESKTOP BACKGROUND followed by clicking on the tab with VISUAL EFFECTS) to work by default due to the chip in your graphic card ...

... you might also want to try and locate START then SYSTEM then ADMINISTRATION and finally select the symbol for HARDWARE DRIVERS. This will start a search for compatible hardware drivers and sometimes you'll get lucky with a supplied driver from there. That's what I had to do on an older version of Ubuntu with my horrible ATI 3200 Graphic Chip. It wasn't until 8 months later that I could use an official driver from ATI but due to the driver search function I was still able to use 3D settings anyway during that time.

---

### Post by Ginsu543 on 2010-05-31
The most comprehensive way I know of to control Compiz is to install compizconfig-settings-manager (it's found in the Lucid repos using Synaptic). It allows you to change the settings individually.

---

