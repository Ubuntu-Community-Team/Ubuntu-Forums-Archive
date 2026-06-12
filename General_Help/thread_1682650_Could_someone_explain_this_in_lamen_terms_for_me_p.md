---
title: "Could someone explain this in lamen terms for me please?"
date: 2011-02-06
forum: General Help
---

### Post by godfromdfo on 2011-02-06
Could you please explain how I could do this a bit easier? the sound is driving me crazy! thank you!

> **chronozphere said:**
> Hi everyone,

I'll explain how to fix the driver. 

What you need:

> Some "updated" source files (attachement)
> The ALSA update script (It's [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")). It's a good idea to read the instructions of the script first.

**Warning**: By using the alsa update script, your version of alsa will be out-of-sync with the package-manager. For more info, see the thread of the update script.

**Warning: Use at your own risk!** The fixes will eventually be released officially. If you mess something up, you can try to restore alsa by doing  everything again (except step 2). This'll give you a clean ALSA 1.0.23  install.

Instructions:

Step 1: Download the script and run it with the -d option. This will download the files for the latest alsa release (this should be 1.0.23). "cd" to the download directory and do:

```

sudo ./<alsa update script name here> -d

```Step 2: Now copy the files to their place. The files are attached in an archive. 

Kconfig must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/ and
the other files must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/.

Note: On my PC /usr/src/alsa/ doesn't exist. Instead I have /usr/src/Alsa-1.0.23/

Note: It's a good idea to make backups of the files you are going to replace. Rename the files to <filename>.bak or something. Again, using this fix is at your own risk.


Step 3: Now you can compile alsa by running:
```

sudo ./<alsa update script name here> -c

```That'll take a while. ;)

Step 4: Finally install the new alsa version:
```

sudo ./<alsa update script name here> -i

```Step 5: Reboot. 

This patch should fix the dual boot bug and should also enable front panel support for your headset. ;)

Hope this works for you!

**Update:** The previous version didn't work correctly. The new version does solve the problem for me. As a bonus, you get HDA frontpanel support and better stereo upmixing (A two-channel source will now be played through sub/center aswell). :D

---

