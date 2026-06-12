---
title: "My Dual Monitor Issue &amp; resolution in 10.10"
date: 2011-04-07
forum: General Help
---

### Post by mkeyes001 on 2011-04-07
So I had to reinstall yesterday due to a bad decision on my part to upgrade to 11.04.  After I reinstalled 10.10 I was attempting to set up my dual monitors with poor results. 

I wasn't able to get my 2nd monitor to show up in high resolution. I was able to get it working in lower resolution so I figured I had a driver issue.  

After some investigation I found a mention of a bug in 10.10 with dual monitors.  Now I'm no expert but this is what I did to fix my issue.

In synaptic go to settings - repositories.  Click on updates tab and check Pre-release updates.

Click Reload in synaptic and Mark all Upgrades - Apply.  This will download many packages and will take some time.

After the reboot I was able to get both monitors working in high resolution.

You can check your monitor settings from system - preferences - monitors

May not apply to all but it worked in my case.

---

### Post by seawolf167 on 2011-04-08
Just to check - did/do you have drivers installed for your graphics card? Either from System -> Administration -> Hardware Drivers or from Nvidia/ATI's proprietary suites available on their website.

---

