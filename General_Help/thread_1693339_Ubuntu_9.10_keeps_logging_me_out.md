---
title: "Ubuntu 9.10 keeps logging me out"
date: 2011-02-22
forum: General Help
---

### Post by modmidget on 2011-02-22
Why does Ubuntu 9.10 keep logging me out?  This only started about a week ago and it seems to be getting worse.  I have not installed any new hardware or software.  The only thing that's been installed recently are the routine Ubuntu updates.  I just got logged out 4 times in less than 10 minutes while I was trying to type a reply to a message in another forum.  I had to reboot into WinXP to post this message and finish my reply in the other forum.  This is getting REAL annoying and I can't find any solutions.  Someone suggested that uninstalling Compiz would fix it so I did that, but it seems to have gotten worse.

I've really liked Ubuntu until now, but I'm on the verge of trashing it if this problem can't be fixed.

---

### Post by modmidget on 2011-02-25
I guess I should have mentioned that when I'm in Firefox I get completely logged out of Ubuntu kind of like a system restart.  If I'm in Seamonkey I don't get completely logged out of Ubuntu, Seamonkey just disappears from the screen and I get a message that says "Seamonkey had a problem and crashed.", then I get the option to "Restart" or "Restart and Restore".  I've also tried running Ubuntu's Epiphany browser but had errors similar to Seamonkey.

When I reboot into XP I do not get any crashes in Firefox, Chrome, or IE 8.

---

### Post by WorMzy on 2011-02-25
Sounds like Xorg is crashing. What does the last few entries in ~/.xsession-errors say?

What graphics card are you using? Have you installed propriety drivers?

---

### Post by modmidget on 2011-02-28
Where do I find xsession-errors?  I did a file search and only found xsession, xsession.d, and xsession.options.  I'm not real familiar with the Ubuntu file structure and it's difficult for me to find anything.

My display adapter is an S3 Graphics ProSavageDDR that's built onto the motherboard.  It's not a PCI card.  I've been running Ubuntu on this machine for a few years and never had this problem until recently.  The display adapter has always worked very well in the past and I have not recently installed any new drivers.

---

### Post by modmidget on 2011-02-28
I figured out how to run "gedit ~/.xsession-errors".  At first the log looked ok but then I tried to play a short video in Movie Player.  Movie Player always fails and aborts about 10 to 15 seconds into all videos.  Here are the final few lines of ~/.xsession-errors right after Movie Player failed:

(soffice:2158): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample 

** (process:2194): WARNING **: Couldn't change nice value of process. 

(totem-video-thumbnailer:2195): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample 
NOTE: child process received `Goodbye', closing down 

(firefox-bin:2217): GLib-WARNING **: g_set_prgname() called multiple times 

(totem:2298): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample 

(totem:2308): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample

---

### Post by modmidget on 2011-02-28
OK, I just got logged off for no reason.  When I logged back in I went into terminal mode and typed "gedit ~/.xsession-errors" and it opened an empty file......  Then I tried to go into my web browser "Seamonkey" and the browser instantly shut down.

---

### Post by WorMzy on 2011-03-01
Well, the file that keeps cropping up in the log is part of the gstreamer0.10-plugins-bad package. I don't know whether installing/reinstalling this package will help or not, but it's the only thing I can suggest. Run this from a terminal, or install the package through Synaptic/Software Centre.

```
sudo apt-get install gstreamer0.10-plugins-bad
```

---

### Post by modmidget on 2011-03-01
Thank you for the help WorMzy.  I ran the sudo apt-get install command but it didn't help.  I tried running two video files after I did the install but they would only run for about 10 seconds and then they crashed.

---

