---
title: "Lost"
date: 2011-04-22
forum: General Help
---

### Post by talisman.26 on 2011-04-22
Hi!  I am in the process of switching from Windows.  I've pretty much done it all, and I really like Ubuntu.  It works, it's smooth, it looks nice and I'm productive on it.  So far, better than windows.  As I break, and learn, and break again, I'm stuck on a boot question.  When I boot, the first screen asks me which OS I want, XP or Ubuntu.  The next screen asks if I want 10.10 (generic) or safe mode.  Then it goes to "invalid card", which I think has to do with the video card drivers, but "additional drivers" says the one I have selected is the recommended one.  Anyway, it gives me the ~$ and asks for a log on.  But I don't need to...I told Ubuntu to log me in automatically (in hopes of skipping these screens in hopes of speeding the boot process), and it does, but it takes a little while.  Like, 60 seconds.  I don't know if it's loading the kernel (oh wow...there I go thinking I know Linux terminology) or what.  Any suggestions?  I've looked around on the forums, but there is either too much information here, or I'm not looking in the right place for my particular problem.  Could it be that I using a dual boot system?  It's not the LiveCD, and windows isn't running in the background.  Thanks guys!

---

### Post by hwttdz on 2011-04-22
You can change the grub options to not show the grub screen or show it for a shorter period of time.  There's a great grub howto here: 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If it's getting hung on boot look at dmesg for any errors, maybe install bootchart?  The OS doesn't start loading until after the grub screen, but from that point to a desktop I wouldn't expect it to take 60 seconds.  15-30 is more reasonable (I've seen less than 5, but that's a pretty barebones install on pretty powerful hardware).

---

### Post by Yellow Pasque on 2011-04-22
So is Xserver (i.e. the GUI) starting or not? Please post your /var/log/Xorg.0.log file

---

### Post by talisman.26 on 2011-04-22
Funnily enough, I re-read the Start Here thread and am reading the Ubuntu Pocket guide.  It's telling me why I'm getting all the screens.  I think I had this conversation with my daughter the other day about looking for your answer before asking it...BTW, it does start the GNOME GUI.  The desktop if my terminology is correct.

---

