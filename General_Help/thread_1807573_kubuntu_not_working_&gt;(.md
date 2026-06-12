---
title: "kubuntu not working &gt;:("
date: 2011-07-19
forum: General Help
---

### Post by francisbojczuk on 2011-07-19
:confused::confused: right so im running windows and i get vmware player 5 then i download and install kubuntu 10.10. THEN THIS HAPPENS: i create the vm and it just goes black, nothing happens the only thing i can do is move the kde mouse around the screen, iv left it for hours on end and nothing ! please hep, what should i do :'(
 
and by the way, i have been using linux for a while now, i just recently whiped my harddrive and started again, all my previous linuxs have runed smoothly

---

### Post by ankspo71 on 2011-07-19
Hi,
There is probably a problem with Kubuntu 10.10 not being able to set up the display correctly, or Kubuntu can't set up a configuration to work well enough with vmware player's virtualized hardware. 

Here are some troubleshooting links that might help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

Do you have the same problem if you tried to install Kubtunu 10.10 in another visualization software such as virtualbox?

hope this helps.

---

### Post by 2F4U on 2011-07-19
Did you try the most recent version of Kubuntu, which is 11.04?

Here is a ready to run image of Kubuntu 10.10 for VMWare

[http://ubuntuforums.org/showthread.php?t=1609327](http://ubuntuforums.org/showthread.php?t=1609327)

---

### Post by francisbojczuk on 2011-07-19
thanks, i know there is 11.04 out but i really have liked version 9 and 10, i think they are much more stylish :P but it does the same with 11 as well :'(

---

### Post by SeijiSensei on 2011-07-20
Do you have the option to boot into recovery mode when the VM starts up?  If so, do that and try running "startx".  What happens?

If you end up with a root prompt ("#") when you log into the recovery console, you might want to first change to being your own user before running startx.  Type "su username" at the root prompt.

---

