---
title: "What nvidia driver do i need???"
date: 2009-07-10
forum: General Help
---

### Post by lapishc on 2009-07-10
I am running a Dell Precision work station with 64bit Hardy 8.04 and the following graphics card...

02:00.0 VGA compatible controller: nVidia Corporation Quadro FX 3700 (rev a2)

Hardy will only run in low graphics mode...

What Nvidia driver should be loaded on my system?

Thanks!

---

### Post by nice_like_rice on 2009-07-10
Does ubuntu not give you the option to automatically download and install the graphics drivers (maybe I am wrong, was that feature not available in hardy ?)

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Just download the version for your architecture, the same package for all graphics cards.

---

### Post by lapishc on 2009-07-10
I am pretty lost right now, but apparently I can not get the appropriate one to show up in my package manager.  

I believe I need the nvidia-glx-180 to be compatible this most recent round of updates, but it won't come up in Synaptic and I have seen multiple warnings about downloading and installing drivers outside of the package manager.  Given that I am a relative noob, I want to work within the framework of Synaptic...But I can't locate what I think is the right driver.

---

### Post by merlinus on 2009-07-10
Do you have System/Administration/Hardware Drivers?  That's how I installed 180.44.

---

### Post by Idaho Dan on 2009-07-10
Have you gone to System / Administration / Hardware Drivers?

---

### Post by lapishc on 2009-07-10
Going back and looking at BinaryDriverHowToNvidia in the Ubuntu documentation I find 3 drivers listed for hardy the...
nvidia-glx
nvidia-glx-new
nvidia-glx-legacy

Do I need all 3 of these, or what combination of these should I be using? 

I see each of these in Synaptic...but when I try to select all 3 of them Synaptic wants to remove the other ones I have selected...

---

### Post by lapishc on 2009-07-10
Idaho Dan/Merlinus: There is nothing listed in System> Admin> Hardware Drivers

Should there be and how do I add something?

Thanks

---

### Post by merlinus on 2009-07-10
It's in 9.04, but maybe not in hardy.

As for the drivers, you only need one, and that is why synaptic will not let you install more than that.  You might choose one and see if it works.

---

### Post by lapishc on 2009-07-10
ok which one would you suggest I try? 
nvidia-glx
nvidia-glx-new
nvidia-glx-legacy

I still don't understand why the nvidia-glx-180 driver refuses to show up in Synaptic.  

Thanks

---

### Post by lapishc on 2009-07-10
Could the fact that I still have Nvidia drivers load prevent Synaptic from acquiring newer ones?  

i.e. if I uninstall my current nvdia drivers would synaptic look for nvidia-glx-180?

---

### Post by merlinus on 2009-07-10
Even though nvidia-glx-180 is installed in my system, all the rest show up as well.

You also might try installing jockey, which is the gui frontend for configuring the driver, monitor, etc.

Again, these may be features and drivers available for 9.04, and not hardy.

---

### Post by lapishc on 2009-07-10
Does anyone know what the proper nvidia driver configuration for Hardy 8.04 and Nvidia Quadro 3700?????

---

### Post by lapishc on 2009-07-10
bump....still looking for a solution here, if anyone has any ideas.

---

### Post by oldos2er on 2009-07-10
Maybe this will help: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

