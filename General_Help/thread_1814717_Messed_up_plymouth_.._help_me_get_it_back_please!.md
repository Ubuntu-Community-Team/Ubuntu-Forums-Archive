---
title: "Messed up plymouth .. help me get it back please!"
date: 2011-07-30
forum: General Help
---

### Post by QwUo173Hy on 2011-07-30
Plymouth has been running fine on this machine for the last few years (I'm now upgraded to 11.04).

I installed kubuntu-desktop and since then had a new blue boot screen instead of the purple. I removed the plymouth-kubuntu packages (keeping the plymouth-ubuntu ones) but I get a messy boot up now with verbose output.

I tried reinstalling plymouth but there's no difference. does anyone know how to reconfigure it properly?

---

### Post by garvinrick4 on 2011-07-30
[LEFT]                                  
#In Synaptics make sure you have your selection of Plymouth themes installed: Then below.

```
sudo update-alternatives --config default.plymouth 
```Select which theme I believe they are numbered for selection according to what themes installed:


#Then update your initramfs as per below and should now boot with theme you selected:

```
sudo update-initramfs -u
```                                   [/LEFT]

---

### Post by QwUo173Hy on 2011-07-30
Thanks garvinrick4. I ran the first command but it said 
> There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.

probably because I removed the kde-plymouth packages.

After running the second command I did get a glimpse of the Ubuntu logo on shutdown but now the behaviour is the same again as the original problem.

---

### Post by garvinrick4 on 2011-07-30
Only one plymouth theme installed so no choices.

---

### Post by garvinrick4 on 2011-07-30
Use Synaptices quite a few themes to install, I use solar. Not kubuntu or xbuntu but the other theme packages.

---

### Post by QwUo173Hy on 2011-08-02
Thanks Garvinrick4. Now I have plymouth for shutdown, which is very nice. For startup though, I only have a purple screen with ugly text. But I will install 11.10 in October so maybe that will fix it.

Thank you for your time, help and screenshots!

Jarlath

---

### Post by garvinrick4 on 2011-08-02
You can give this a shot it makes graphic drivers start first:

```
sudo -i 
```
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

```

---

### Post by QwUo173Hy on 2011-08-03
I still only get the shutdown view (solar looks great!). Thanks garvinrick4.

---

### Post by tweakmy on 2011-08-09
say i got the same issue as well. Anyone could help to give some guide?

Even if I set it back to the default ubuntu logo. It still does not work on startup and only appears on the shutdown. even if i use the plymouth manager

---

### Post by tweakmy on 2011-08-09
just to recall what I have check

/lib/plymouth/themes/default.plymouth



i have done this 

sudo update-alternatives --config default.plymout 

have check that 

FRAMEBUFFER=y
have add into
/etc/initramfs-tools/conf.d/splash
and then

sudo update-initramfs -u

---

### Post by tweakmy on 2011-08-09
Do you have to add the GRUB_GFXPAYLOAD_LINUX to your grub? as shown

[http://ubuntuforums.org/showthread.php?t=1701789]("http://http://ubuntuforums.org/showthread.php?t=1701789")

---

### Post by QwUo173Hy on 2011-08-11
I'm not sure, but the link isn't working for me. Would you mind reposting it?

---

### Post by LukeMorrison on 2011-08-11
Click on the link and then delete the http// in the middle of the address bar.  It will then load properly.

---

### Post by QwUo173Hy on 2011-08-12
Thanks LukeMorrison / Tweakmy. I tried it and I still only have 'nice plymouth' during shutdown. I'll do a clean install when Oneiric comes out (depending on how the new developments in Unity work for me).

Thanks for your help!
Jarlath

---

