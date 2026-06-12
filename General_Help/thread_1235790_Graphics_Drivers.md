---
title: "Graphics Drivers?"
date: 2009-08-09
forum: General Help
---

### Post by headshotaof on 2009-08-09
Well i have an ATI radeon card and click the hardware driver button on ubuntu and it said no prop drivers are in use on this system. On my other machine i have a nvidia. I went to look for simple-compiz on the packet manager and it is not listed. I found compiz backend but when i click it it wont let me donwload it. Does compiz/ubuntu only support nvidia?

---

### Post by Rocket2DMn on 2009-08-09
What model is your ATI card?  Please post the output of
```
lspci | grep VGA
```
Radeon cards older than 9500 don't need to restricted drivers, they use the open source radeon drivers.

---

### Post by headshotaof on 2009-08-09
its an x1600 pro series i cant put the  code in b/c when i went to the download manager to look at what games and stuff there was to download. I saw the Catalyst control center which is what i use on windows for my card. So i downloaded that and a couple other games and stuff. 

Then i downloaded the updates for ubunta that automatically appear on the right side of your screem. There was like 180 files and it finished and said it needed a restart.

 I restarted and now when i load ubuntu i get a black screen with RED BLUE GREEN strokes of color around the top.  I tried doing the fix graphics problems in the recovery mode and no luck. Also did a dskcheck and a repair neither worked.

---

### Post by headshotaof on 2009-08-09
am i looking at deleting the partition? and reinstalling ubuntu?

---

### Post by Rocket2DMn on 2009-08-09
Ok, let's try to remove what you installed.  You shouldn't need to reinstall Ubuntu.

Get to a TTY by doing CTRL+ALT+F1, and login at the terminal prompt.  Then run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Now restart the computer:
```
sudo reboot
```
You should be back at your graphical login screen.  Let me know if you're not.  Once we are back here, we will sort out looking into the restricted drivers.

---

### Post by jocko on 2009-08-09
> **Rocket2DMn said:**
> ... Once we are back here, we will sort out looking into the restricted drivers.
There are no restricted drivers that supports that card. Ati dropped support for anthing older than the radeon hd 2xxx series before jaunty was released. Just help him get the open source drivers back. They are the only ones that will work.

---

### Post by Rocket2DMn on 2009-08-09
Thanks jocko, I was unaware of that.  I haven't done much support for graphics drivers recently :)  I guess the [uhelp]community/BinaryDriverHowto/ATI[/uhelp] and [uhelp]community/RadeonDriver[/uhelp] pages need to be updated.

---

### Post by headshotaof on 2009-08-09
I dont think i can get far enough to get on the terminal. All i can do is. 

System Reboot----->BIOS screen---------->Choose which OS i want to load--------->

After i click ubuntu i can see it is the loading screen ( where the ubuntu name and loading bar is ) but i can see multi colored slahes below it. Then it loads and before i can even get to the screen where i type my password it goes black with multi colored lines. I also tried typing my login and password ( asuming the box is there i just cant see it ) and it did not login.

---

### Post by matthewbpt on 2009-08-09
You have to choose recovery mode in the GRUB menu, then in the menu that comes up after it boots choose to go to commad line with networking or something like that. Then type in

```
sudo apt-get remove --purge xorg-driver-fglrx
```

Now reboot and tell us what happens. I think we may need to edit your xorg.cong file. This is the driver your computer needs to use [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) look at that page it has a lot of info on how to set it up.

---

### Post by headshotaof on 2009-08-09
Thanx that worked the system is now up, so the catalyst control center is what caused that?

I am going to go read up on that driver info you gave me.

---

### Post by headshotaof on 2009-08-09
that stuff is so confusing i got lost at "configuring your xorg.conf" it doesnt really specify where things are and how to find them. "usually after your mouse entry" it doesnt say where your mouse entry is at or if its not there where is it unusually at. I see it says "mouse" under syste/pref but under that is networking.

---

### Post by Rocket2DMn on 2009-08-09
If you are up and running with the graphical display, then you are already using the open source Radeon drivers.  No further configuration should be necessary.

---

### Post by headshotaof on 2009-08-09
ok thanks for the help.

---

