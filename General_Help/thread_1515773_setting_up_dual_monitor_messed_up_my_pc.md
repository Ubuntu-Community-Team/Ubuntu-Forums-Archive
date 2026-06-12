---
title: "setting up dual monitor messed up my pc"
date: 2010-06-22
forum: General Help
---

### Post by chrismitt2002 on 2010-06-22
I thought it would be nice if i set up a dual monitor i hooked up my 19 inch lcd and rebooted for unbuntu 1004 to see my 2nd lcd and now my pc wont boot + the boot logo can not be read and when i hit f1 esc for detaled screen i cant read that eather i have no clue what the he** to do to fix this

---

### Post by chrismitt2002 on 2010-06-23
plez help i have no clue how to fix it and relly dont want to reinstall as i will lose all that i have in jdownloader
bump

---

### Post by chrismitt2002 on 2010-06-23
bump

---

### Post by chrismitt2002 on 2010-06-23
bump

---

### Post by dhysk on 2010-06-23
could i get a little more info about graphics card, size/type of both monitors including the type of connection (VGA ect..) you are using, and the video driver you are using?

Also Ubuntu version may be help full.

What happens if you disconnect the monitor?  Does it go back to normal or still messed up?  And finally what happens if you connect just then new monitor?

---

### Post by chrismitt2002 on 2010-06-23
i have 1 32 inch sharp and one 19 inch westing house hooked up to a nvidia 9500 1gb 32 inch is via dvi to hdmi and the westing house is via vga i am useing ubuntu 10.04 not shure of the driver version if u can give me the command i  will give u that info also when i disconnect the 19 inch it still does not load same when the 32 inch is only hooked up

---

### Post by cariboo on 2010-06-23
Can you start in recovery mode? If you can at the menu select drop to root prompt with networking. Once at the prompt type:

```
lshw -C display > display.txt
```

this command will create a text file called display.txt, that you can copy to your Windows partition or a flash drive. Post the results in post.

---

### Post by chrismitt2002 on 2010-06-23
if u look @ the pictures i posted thats as far as i can get i cant even make out what its saying if i hit f1 del etc 
is their a key i can hit like with windows i can hit f8

---

### Post by mr clark25 on 2010-06-23
yes, there is a key. if you have grub2, you should be able to hold the SHIFT key during boot to bring up the grub menu. "recovery mode" is usually the second option.

---

### Post by chrismitt2002 on 2010-06-23
it wont even get that far plez look @ the picture i posted thats the only text i can see whitch of corse i cant even read so if their is a was to do this from a live install that would be great

---

### Post by chrismitt2002 on 2010-06-23
bump
plez help me i am @ a total loss on how to fix this problem i would reinstall but dont relly want to do that if i dont have to

---

### Post by wilee-nilee on 2010-06-24
Plugin the original monitor you were using, nothing else, hit the power on then click on the shift repeatedly until you get to the grub screen hit e and use the arrow key to navigate to the end of the kernel and put nomodset in and remove the splash reference, then hold down the ctlrl key and hitx this will boot you in in low graphics mode. Then when in if this works run in the terminal.
```
lspci | grep VGA
```

This will tell you your graphics card I think you have a driver problem with just a regular monitor. Now this method of getting in a per session method so you will have to investigate the card by reposting and looking in synaptic to see what driver is being used. 

With the second monitor you want to after you have fixed this problem plug it in while the computers running and also look iy up on the web for a linux driver is needed.

I think cariboo907 command is a good one as well.

---

### Post by chrismitt2002 on 2010-06-24
is it possable to do a in place repair install as i cant read the txt its all messed up so plez take a look at the pictures i post would be very helpful if i could repair that 1st then fix the other problem but might be easyest + quickest to just do a complete reinstall

---

### Post by wilee-nilee on 2010-06-24
I'm not real familiar with these sort of problems, but I would boot a live cd and see if you get the same problems. To me it looks like a graphic driver problem. run the command in my last post from a live cd if it boots up and post the results for others to see.

Did you do any updates before you plugged in the second monitor, and what really helps is if you are given a set of solutions that you itemize them in a response and in what order, some of us are a little slow and may not be as experienced in this area.:p For example I suggested using the original monitor you need to let us know if you tried that, I suggested the nomodset, were you able to do that.

I have found that on a desktop of my own If I unplug the monitor and use it with my netbook and then plug it back in to the desktop I almost always get a black screen and have to do a couple of restarts with hard shutdowns to get it going again. I appreciate your angst with this, but you have to have some patience.:p

---

### Post by chrismitt2002 on 2010-06-24
1 when things went south i pluged the only the 32 inch back in 
2 i beleave i did do updates but cant be 100% shure of that
3 yes live usb boots perfect every time no problems useing 32 inch tv
4 not real shure why but i have to try sevril times to try to get to the grub menu
and even then it doesnt seem to want to work
5 i have uploaded the gfx card detals i shure hope i can fix this soon 
i hope i was able to idimize the list ok

---

### Post by realzippy on 2010-06-24
**If** you formerly had installed a NVIDIA driver,there is a file in your filesystem:  /etc/X11/xorg.conf
You could boot a live system (from USB eg) and mount your filesystem and simply delete that file,so the nvidiadriver will not be loaded and system should fallback to the VESA driver...

---

### Post by wilee-nilee on 2010-06-24
Thats great to list them it makes it easier to get help:p here is the card for those that can help.
```
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
```

If it was me since I keep everything backed up on a external HD I would just reinstall. But I don't know what you have backed up nor do I know if you have multiple OS on the computer. You can pull everything out that you need to with the thumb to a external HD so nothing is lost as far I can tell so far it just isn't accessible through a regular boot.

It is rather strange that grub doesn't come up with the shift key when you start the computer.

Just for kicks lets look at your system by running the bootscript in my signature this will tell us a a lot especially the time out at the boot. So run the script from the thumb and copy and paste the readout from it to a reply then highlight the txt and click on the # in the reply panel this will put it in code tags.

---

### Post by wilee-nilee on 2010-06-24
> **realzippy said:**
> **If** you formerly had installed a NVIDIA driver,there is a file in your filesystem:  /etc/X11/xorg.conf
You could boot a live system (from USB eg) and mount your filesystem and simply delete that file,so the nvidiadriver will not be loaded and system should fallback to the VESA driver...

That would be a great thing.

---

### Post by chrismitt2002 on 2010-06-24
1 no i have just ubuntu installed 
2 all importenet files are on other hds
3 the reasont i didnt want to reinstall was that i have jdownloader installed and hadnt finished downloading what i had in my q
4 is it possable to do a in place repair like you can with windows xp etc

---

### Post by mr clark25 on 2010-06-24
> **realzippy said:**
> **If** you formerly had installed a NVIDIA driver,there is a file in your filesystem:  /etc/X11/xorg.conf
You could boot a live system (from USB eg) and mount your filesystem and simply delete that file,so the nvidiadriver will not be loaded and system should fallback to the VESA driver...


did you try this? it is a great suggestion...

if you need help doing this, just let us know...

---

### Post by chrismitt2002 on 2010-06-24
i said screw it and just broke down and reinstalled

---

