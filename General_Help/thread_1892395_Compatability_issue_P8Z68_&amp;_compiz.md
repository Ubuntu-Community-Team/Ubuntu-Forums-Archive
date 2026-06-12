---
title: "Compatability issue P8Z68 &amp; compiz"
date: 2011-12-07
forum: General Help
---

### Post by sandman3838 on 2011-12-07
Hello everyone!

I have a compatibility question about Compiz and Screen-lets with Ubuntu 10.10!

This last week I just put together a new system:

Asus P8Z68 Deluxe Pro MO

Intel I5 2500 K Sandy Bridge

GTX 550 ti video card

NVIDIA Driver v290

As this was working all with my old AMD 4x System, I’m getting the feeling that there is something that is doesn’t like with the new Chipset?

Has anyone come across a work around yet to get Compiz and Screen-lets running, or is there an update that I don’t know for the two programs?

Would possibly upgrading to Ubuntu 11.10 solve or help my issue.  Although I will have to admit that I did try it on my second system and I didn’t like it at all.  I would probably switch to classic mode anyway. 

Also, is there really any benefit in using Ubuntu 11.11 in classic mode VS Ubuntu 10.10?

---

### Post by sandman3838 on 2011-12-08
I think I got it going?

1st - 
I re-installed straight from the Compiz site


2nd
I found this from another posting on this site

If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

Code:

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

and to enable desktop effects you can get the slightly modified compiz from my ppa
Code:

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

Last edited by exobuzz;

Finally I installed 
DisPlex 0.7.2

looks like its working?
      
           ************************ 
However I do have the final question from my original post above?

"Is there really any benefit in using Ubuntu 11.11 in classic mode VS Ubuntu 10.10?"

---

