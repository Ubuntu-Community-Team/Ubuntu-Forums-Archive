---
title: "Problems connecting computer to TV via HDMI"
date: 2009-10-20
forum: General Help
---

### Post by maghus on 2009-10-20
[FONT=Arial][SIZE=2]My computer, Asrock 330 ION, works great with my Apple monitor via DVI (adapter) but when I connect it to my Samsung UE-40B7070 I get a flickering red background with vertical stripes during startup and in Gnome.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]When I install the NVIDIA drivers the signal to the TV disappears when entering Gnome. In recovery mode I am able to get to Gnome but then without the NVIDIA driver and still flickering and red background with stripes.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I have done a complete format and re-install of Ubuntu but with no luck, the problem persists. [/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I am a total noob on Linux, any help is much appreciated![/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Thanks[/SIZE][/FONT]

---

### Post by P4man on 2009-10-20
if you boot with the tv connected, can you get to a terminal by pressing control+alt+F1 ?

if so, then try running

```
sudo nvidia-xconfig 
```

then reboot (sudo reboot).

---

### Post by kpholmes on 2009-10-20
you could try and pluging in the tv as a second monitor when using your apple monitor, then open up the nvidia driver, have it detect the display, then try and save the xorg config file,

it wont let you fully write everything in the xorg file, so just select the option where you can see a copy of the new one, save that as on your desktop, then in the command line replace the old file with the new one,

then reboot.

that has always worked for me when trying to update my xorg.config file for a tv

---

### Post by maghus on 2009-10-20
Thanks to both of you.
 
I will test this when I get home, however I do only have one HDMI output, so connecting the TV and Apple monitor at the same time is not possible. I'll see if I can work something out with an old monitor on VGA or something.

---

### Post by maghus on 2009-10-20
Hi Guys,
 
I have tried some of your sugguestions.
 
First I connected my computer to the Samsung TV using both HDMI and VGA. The VGA connection worked just fine but I experienced the same issues via HDMI.
 
> **P4man said:**
> if you boot with the tv connected, can you get to a terminal by pressing control+alt+F1 ?
 
if so, then try running
 
```
sudo nvidia-xconfig 
```
 
then reboot (sudo reboot).
 
I tried this but with no success. I have attached the backup file to this post hoping it might give some clues. It is saved as txt.
 
I then tried:
> **kpholmes said:**
> you could try and pluging in the tv as a second monitor when using your apple monitor, then open up the nvidia driver, have it detect the display, then try and save the xorg config file,
 
it wont let you fully write everything in the xorg file, so just select the option where you can see a copy of the new one, save that as on your desktop, then in the command line replace the old file with the new one,
 
then reboot.
 
that has always worked for me when trying to update my xorg.config file for a tv
 
As you can see from the attached screenshot both (the same but with two connections) monitors where detected but the DFP one, witch I suspect is the digital connection, seems to be missing EDID information. I did "Acquire EDID..." and got a .bin file that I do not know what to do with.
 
Do you think the problem is that my TV is not sending EDID? I have tried several ports on the TV with the same result.
 
I could use the VGA cable permanently but as all my other cables are built into the wall I want to avoid this.
 
Any help is mutch apreciated!

---

### Post by maghus on 2009-10-20
I have now tried: [http://www.mythtv.org/wiki/Nvidia-cards_and_no_picture_when_box_is_on_before_the_TV](http://www.mythtv.org/wiki/Nvidia-cards_and_no_picture_when_box_is_on_before_the_TV)
 
But with no luck..

---

### Post by P4man on 2009-10-20
Looks indeed like there is problem with the EDID. Can you manually configure resolution in X server display configuration, after enabling the screen and setting it to twin view ?

---

### Post by maghus on 2009-10-21
No, I can not even enable the HDMI connected screen from the settings...

---

### Post by maghus on 2009-10-21
I have managed to open the EDID.dat in a software called Monitor Asset Manager (Windows). It seems to me that my TV is sending out EDID info, but I do not know what to correct to get this working. 
 
I have attached the EDID pasted to txt, would love some hints on what to amend in it to get this working.
 
Thanks

---

### Post by P4man on 2009-10-21
No idea... but perhaps this helps:
[http://forums.nvidia.com/lofiversion/index.php?t73027.html](http://forums.nvidia.com/lofiversion/index.php?t73027.html)

If not, search these forums, I remember a long thread a few weeks (months?) ago on the subject with someone extremely knowledgeable on the subject (which is more than can be said about me heh). It certainly had nvidia and edid in it.

---

### Post by maghus on 2009-10-22
Thanks for not giving up on me!
 
I have tried the fix you link to, but with no success. This makes me think that the TV is sending corrupt EDID and that I need to correct this and then link to it in my xorg.conf
 
The problem is that I have no idea what to change. Will do some more investigating.

---

