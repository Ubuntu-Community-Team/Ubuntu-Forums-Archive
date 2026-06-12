---
title: "Installed gui and now get black screen at boot"
date: 2010-04-17
forum: General Help
---

### Post by cbecker78 on 2010-04-17
I installed ubuntu server, then ran the following commands to set up my Xwindows environment:
```
sudo apt-get install xorg
sudo apt-get install gnome-desktop-environment
sudo apt-get install xfonts-base
startx
```
upon typing startx, i was greeted with a black screen.  And now, everytime I boot into the server, I am greeted with the same black screen.

If I boot into recovery mode, everything seems to go ok, and I get a prompt...  I'm afraid to type startx into the recovery prompt.

Can anyone help??

All I can boot into now is windows xp.  and who wants to use that?:confused:

---

### Post by itiswhatitis on 2010-04-17
Might be a configuraiton issue:

```
sudo dpkg-reconfigure xserver-xorg
```

That should allow you to setup your display and pick your desktop.

---

### Post by cbecker78 on 2010-04-17
OK, thanks... I jumped the gun here and tried to run "apt-get ubuntu desktop" from the recovery console to see if that corrected the problem... and halfway through it told me I was out of space...  df -h says I only have 2.16 GB of space on here!  I know I created a 13 GB partition when I installed the server... I have no idea what is going on.  

Does the recovery login go to a different partition or something?  apt-get doesn't work now because I need to reconfigure dpkg, and i can't do that because there is not space..  Well, I if no one posts a suggestion on how to correct this (or helps me understand my muddled mess) in a few hours, I will probably try to reinstall the server and try your suggestions...

I'm certainly not looking foward to fiddling around in vi agian to set up my source lists and internet...

thanks!

EDIT: scratch that idea... forgot I had left the CD.  Guess I'm just out of luck for the week.  I'll resume trying when I get back into town next week.  Or just drop that old laptop in the trash...  I'm starting to like that idea.

---

### Post by cbecker78 on 2010-04-24
After reinstalling the server to a space large enough for it to live, and trying the above plus some, I realized this is the same issue I was having with the live cd... and it is a problem universal with xorg on this model laptop apparently (as I tried debian and fedora also).  Not sure why puppy was good to go.  But I found the solution here:

[http://ubuntuforums.org/showthread.php?t=587668](http://ubuntuforums.org/showthread.php?t=587668)

---

