---
title: "Applications running SLOW after GSM revision"
date: 2011-09-01
forum: General Help
---

### Post by sunrise-7 on 2011-09-01
September 01, 2011 Gnome 2.30.2 Ubuntu 10.04 (lucid) Kernel: 2.6.32-33-generic GCC Version: 4.4.3 (i486-linux-gnu) Memory Total: 1949 MB, 70% Free Swap --- total: 4004 MB, 100 % free  Storage: 2 SCSI devices Advanced Micro Devices (AMD) K8 Athlon64/Opteron NVIDIA Model GeForce 6150 LE, 256 MB Video RAM Dell C521 Dimension Computer Memory: 1.9 GB   
[B]Applications running slower and slower with Ubuntu almost halting. 
File OPEN and SAVE functions, in particular seeming to take Minutes, instead of millisecs! 
[/B]

On checking the installed Gnome System Monitor (GSM), I found that it was taking as much as 44% of the CPU. 



NO other applications were continuously showing Active,  showing Sleeping, most of the time, even the one which was open, and  stalling. Using the Control-Alt-Delete was dead slow. 



Regardless of selecting either the work application, an  HTML editor I have used for 10 years, or, the GSM, and raising or  lowering, a lot, the Priority of one or the other at a time, there was  NO operational change. Most of the time, these changes were NOT retained  when I reopened the Display, even though they had been changed with a  Password, and, Ubuntu had NOT been restarted. 



I REMOVED the GSM, by way of the Synaptic Package Manager,  and, my working application ran again with NO hesitations or delays. I  installed slmon from SPM, and checked Sysinfo 0.7 from the Applications  Menu, Submenu: Utilities .. to confirm the above noted specs. 



I re-installed the GSM and checked the Default Preference Settings. 
At the Processes tab, the default for "Update in seconds, was 3.00. I raised it to the max of 100.0 
At the Resources tab, the default for "Graphs: Update interval in seconds, was 3.00. I raised it to 100.0 
At the FileSystems tab, the default for "Update Interval in seconds, was 5.00. I raised it to 100.0 
All 7 of the Information Fields checkboxes were selected by default. I left them unchanged. 

I retested using my HTML coding program with the NEW settings and detected no problem.  

  
This was NOT a problem until after 2011-08-10 and in the  latter days of August it quickly escalated to becoming almost unusable.  As the problem disappeared with the removal of the GSM, there is a good  indication that the GSM was revised recently, and contains a bug which  results in a high drain on CPU resources. Or,  a version of the Linux  image or Ubuntu version was revised recently, which is now in conflict  with the GSM, resulting in possible incomplete instruction operation and  looping CPU usage. Of course, could be something else with either or  more than one of the 3 packages. My WORK application is NOT the problem  as it works excellent, with this Ubuntu and Linux image, without the  GSM. 

  
I can only hope that this post saves others the  frustration and much time I lost, and, encourages developers to TEST  more thoroughly before releasing new versions, with bugs, that make  Linux/Ubuntu operate more like older Windows OS. If your applications  are suddenly almost halting to OPEN, or SAVE a file, try removing the  GSM, or, changing the Preference Settings much higher than the Default. 



It could be a Significant Benefit to Ubuntu supporters if  when updates are provided a description of which other Applications are  NOT supported by the changes, was offered for viewing BEFORE one agrees  to the update. If  DEFAULT settings are widely altered between versions,  it would also be most helpful to notify the supporter of these changes  and remind the user of the original defaults such that these could be  reinstated, if desired. I do not have the original default settings on  earlier version of GSM that I had so have no way of determing if changes  were made in this area. Doing a Major administrative check ever 3  seconds seems a little like overkill.

---

### Post by ajgreeny on 2011-09-01
So are you saying that simply having gnome-system-monitor installed on the system, as it is in a default installation, is causing this, even when GSM is not running?

---

### Post by sunrise-7 on 2011-09-02
Yes. On my system, if GSM is installed, it is running. Choosing Exit, does NOT reduce the Display showing that it is continuing to use CPU Resources.

---

### Post by ajgreeny on 2011-09-02
> **sunrise-7 said:**
> Yes. On my system, if GSM is installed, it is running. Choosing Exit, does NOT reduce the Display showing that it is continuing to use CPU Resources.
That's a new one for me!  I can think of no reason for that to happen.  I accept and agree that GSM is a bit of a resource hog, which is why I tend to use **top** or **htop** in terminal instead, but that does not really answer your problem.

---

### Post by sunrise-7 on 2011-09-03
You may note that if you re-read my original post, it was placed here to save others the frustration of a problem, by providing a solution, and, to encourage developers to place fewer problems into the field. I Solved the problem, by first removing GSM, and then, by re-installing and setting the time dependent variables to the max delay.

There is the option that someone, including the original modifier of GSM could remove whatever is resulting in the problem, or, add a note somewhere IN the installation to advise those installing it to check and set the Preferences as is best for them. One may also choose other monitoring apps, as you have, or, install only for immediate testing and then remove GSM.

The most obvious reason for the "intereference/slowing" problem is the Preference settings that result in an almost continuous looping of the app. As to why the Exit seems not to work, someone with the appropriate programming skills would have to check if the instructions have been connected to the menu entry to perform the task, if the instruction loop actually works, or, if the instruction loop, for exit, is conflicting with something else. 

Again, what I present here is a known real duplicated problem with a real duplicated correction .. which will hopefully be appreciated by others who wonder, "What the hell has happened to my system that was working OK previously and is now running like it is shutting down?"

---

### Post by ajgreeny on 2011-09-03
Have you reported this as a bug at launchpad?  If not I think you should certainly do so quickly, or at least search for anything similar that can be found.

---

