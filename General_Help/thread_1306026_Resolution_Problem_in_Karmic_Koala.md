---
title: "Resolution Problem in Karmic Koala"
date: 2009-10-30
forum: General Help
---

### Post by rehab123 on 2009-10-30
[SIZE=5]I have just upgraded my ubuntu 9.04 to 9.10 from an alternate ISO image file ... after completed upgrade i have noticed dat i can only set my resolution to 800x600 ... nd this is da highest ... other three is useless ... ... bt in 9.04 i hav used 1024x768 resolution ... is there ny way to get 1024x768 resolution in 9.10?



My karmic koala is fully updated & my pc configuration is :


Intel Dual core 2 Ghz

Intel 945GCNL Motherboard with integrated Intel GMA 950 graphics card

Ram 1 gb

Thanks[/SIZE]

---

### Post by pepcio666 on 2009-10-31
I have had the same problem on the same CPU and integrated graphic card and my solution is:

sudo apt-get install xorg*

I know that it's really invasive, unprofessional and takes about 250MB of hard disk, but it was the last, desperate idea and it really has helped me! 

I hope it will also help you.

---

### Post by WilyWelshWeasel on 2009-10-31
I've just tried this, and now my CPU is maxing out at 100% to the point I can't do anything! How do I remove the damage I've done and how do I set my resolution properly?  I consider myself a reasonably experienced user and after two days of Ubuntu hell I'm on the verge of getting my WinXP CD back out!

---

### Post by simplr on 2009-10-31
I'm also having the same problem with an Intel MB. I am busy installing xorg* at the moment. Until I found this thread I was about to do a fresh install of everything except /home. Have you tried the top command, or the System Monitor, to see which process(es) are hogging your CPU?

Edit: xorg install completed without errors, rebooted and saw an error message on the screen for a moment just when switching to the graphics mode. The error was too quick to read in full but it said something to the effect of "Fatal error inserting i915 ... kernel 2.6.31-14 ...". A quick search found another similar message in bug report 460315. The screen resolution is now almost normal but it does not see my monitor ("Unknown"). and the resolution options are not correct. CPU load is normal at about 98% idle.

---

### Post by WilyWelshWeasel on 2009-10-31
Well it was installing Xorg* that seems to have caused this in the first place. Although strangely the problem doesn't seem quite so bad if I don't open the system monitor.  Still can't sort my resolution but I'll happily trade that for not having a ridiculously slow PC.

---

### Post by R33D3M33R on 2009-11-01
Well, my Karmic Koala installation forgets the resolution I set every time I reboot. I must then enter System Settings > Display and it magically sets back to 1024x768. At every reboot the resolution is something like 1280x960. Since modifying the xorg.conf is having no effect, I'm wondering where are resolution settings saved in 9.10.

---

### Post by suniyo on 2009-11-04
I have the same problem. The highest resolution disappeared after I upgraded to 9.10 karmic koala. I still have 1024 and don't need higher resolutions but just curious how this happened as I had one more resolution available around 1200 before I upgraded to karmic. Any ideas??

---

### Post by guiliker on 2009-11-04
have a look at my thread about this and the bug report: [http://ubuntuforums.org/showthread.php?p=8246026#post8246026](http://ubuntuforums.org/showthread.php?p=8246026#post8246026)
[https://bugs.launchpad.net/bugs/470224](https://bugs.launchpad.net/bugs/470224)

there is a "workaround" that uses xrandr or the boot command "nomodeset" if X is not reading your monitor edid - have a look for a better understanding

---

### Post by suniyo on 2009-11-05
I tried the alternate method but it didn't work for me. Any other possibilities for this apart from the bug you mentioned here.

---

### Post by R33D3M33R on 2009-11-08
I solved my problem. I just created a custom xorg.conf file and then added only resolutions lower or equal to 1024x768. Now it works fine.

---

### Post by suniyo on 2009-11-11
> **R33D3M33R said:**
> I solved my problem. I just created a custom xorg.conf file and then added only resolutions lower or equal to 1024x768. Now it works fine.

Let me try and check it if it works for me or not.

---

### Post by samsonlu on 2009-11-14
> **R33D3M33R said:**
> I solved my problem. I just created a custom xorg.conf file and then added only resolutions lower or equal to 1024x768. Now it works fine.


can you please help me im new to ubuntu can you show me a step by step please.
Thanks.

---

### Post by R33D3M33R on 2009-11-15
1. Press Ctrl+Alt+F1, login
2. Stop kdm/gdm: ```
sudo service gdm stop
``` or ```
sudo service kdm stop
```
3. Do: ```
sudo dpkg-reconfigure xserver-xorg
```
4. Edit the created file with nano: Do: ```
sudo nano /etc/X11/xorg.conf
``` and remove the unwanted resolutions, save with Ctrl+O
5. Start gdm/kdm ```
sudo service gdm start
``` or ```
sudo service kdm start
```

---

### Post by suniyo on 2009-11-15
Thanks but it did not work with Karmic

---

### Post by e.m.fields on 2009-11-16
> **R33D3M33R said:**
> I solved my problem. I just created a custom xorg.conf file and then added only resolutions lower or equal to 1024x768. Now it works fine.

Hi R33d3m33r - 
How did you change your xorg.conf? Or what guide / thread lead you to a solution? Thanks

---

### Post by dracofusco on 2010-03-13
> **R33D3M33R said:**
> I solved my problem. I just created a custom xorg.conf file and then added only resolutions lower or equal to 1024x768. Now it works fine.
How do you make a custom xorg.conf file? 

I am a somewhat n00b so please try to explain it in relativey simple terms

thanks in advance

---

### Post by R33D3M33R on 2010-03-16
Follow the exact steps in the post [#13]("http://ubuntuforums.org/showpost.php?p=8323025&postcount=13")

---

