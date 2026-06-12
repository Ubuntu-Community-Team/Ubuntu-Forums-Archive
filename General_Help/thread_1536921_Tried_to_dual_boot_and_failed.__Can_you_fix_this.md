---
title: "Tried to dual boot and failed.  Can you fix this?"
date: 2010-07-22
forum: General Help
---

### Post by accurate270 on 2010-07-22
Hi- I'm fairly new to Ubuntu and am trying to set up a server.  I want**ed** to dual boot my PC with a ubuntu server so I got a harddrive and plugged it in.  Then I formatted it in Windows and mounted it, etc.  

Then I installed the Ubuntu Server live CD onto the 2nd harddrive.  It didn't work.  Then I took out the 2nd harddrive and put it in my other computer (and got it working on that.)

Now when I start my PC it states the following--


[INDENT]error: no such device: fb9ca7ca-a124-43fa-831d-eaa4117070cc.
grub rescue>[/INDENT]

I would love if anyone can help me get my windows running again (even though I'm not a big fan of windows I need it.)

Thank you,

Accurate 270

---

### Post by drs305 on 2010-07-22
For a (possibly quick fix to get it booted):

From the Grub2 menu, highlight the Linux OS, then press "e". 

When you see the menu commands, cursor to the "search" line. With the cursor at the start of the line, hold down the DEL key and remove the entire line.

Next, on the linux line, change the section "root=UUID=<some uuid>" to "root=/dev/sdXY" with X being the drive and Y being the partition.

After making the changes, press CTRL-x and see if it boots.  If it does, run "sudo update-grub" once it's booted.

If this doesn't work, run the boot info script from the LiveCD and post the results here.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by accurate270 on 2010-07-23
Great! this is definitely a start.

I'm trying to get to the grub2 and I cannot seem to find it.  Usually it would pop up right where it crashes.

This is the screen it gives me.  And I obviously can go into the basic editor.

[IMG]https://5059405226620249857-a-1802744773732722657-s-sites.googlegroups.com/site/rileyjadamson/Home/images/IMG_20100722_233145.jpg?attachauth=ANoY7coKCUNNSws_iG7doie7r-4DGVMwMi2JLfElLkO2QKUBlrVBP_dJeKrtn2rFfCGbL6H9E-CX_uRBJuDPAoiCAal6bmkpTFrdkK9Zo3nDFLNsV4Ao6U-K99XrqxRk-AgkrC5dIgEh6oNlSfPWRj2mZDacHR4wH5jsxIMvy0iviXj5VlCu7EtYRgODfc7YZJiPpXvlHSzxGoUIcwHs87xnR5jWMETZRAEhU-NH0Q5q8Dr7Ec03fGY%3D&attredirects=0[/IMG]

---

