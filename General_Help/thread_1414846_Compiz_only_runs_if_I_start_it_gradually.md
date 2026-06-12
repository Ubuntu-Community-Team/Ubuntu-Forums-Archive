---
title: "Compiz only runs if I start it gradually"
date: 2010-02-24
forum: General Help
---

### Post by hawthornso23 on 2010-02-24
A botched ATI proprietary driver upgrade caused a cascade of problems. I've installed this driver many times before, but this time something just went wrong. I may have made a mistake. There don't seem to be many complaints about the ATI 10.2 driver so this seems likely. Anyway things were quite unstable for a while. I had problems with nautilus (lost the desktop) and segfaults from compiz. I had to reinstall a lot of stuff etc etc. 

Anyway, this episode  has left me with a strange lingering malaise. I can get the machine into a state where everything works perfectly - the cube is fine and quite snappy, the desktop is all there; it looks great; New driver seems to be working OK. But when I log out and log back in there are problems.

Step 1:
[LIST]
[*]If compiz is the window manager during login it dies killing the nautilus desktop and leaving me without a window manager running (no window decorations). This is a nasty state to be in  because you can't easily get at a terminal (yeah ctl alt F1 - but how to fix the window manager from there). I've got a keyboard shortcut for metacity which lets me recover from this state. But afterwards I can't get the desktop back.
[*]If metacity is the window manager during login - no problem. I've got a desktop. It starts up fine. Everything looks good. But I'm running metacity and I want to run compiz.  So now we try to get compiz running.
[/LIST]
Step 2:

[LIST]
[*]If I enter "compiz -- replace" in a terminal compiz segfaults and doesn't put metacity back leaving me without a window manager again. Just before it segfaults it complains about not finding some expected graphics files. This seems to have something to do with cube caps [Edit=Not - see later]- but I've restored defaults there so ... Fortunately ctrl C gets me out of that and back to metacity. Or I use my shortcut. But gee whiz no compiz.
[*]OK - here is where it gets interesting. If I go to the compiz settings manager and disable the cube, then compiz --replace works just fine. So it looks like something specific to the cube. This lets me get compiz running but without the cube.
[*]Now things get really interesting. Once compiz is running, if I open the compiz settings manager, then I can enable the cube and in fact ... it works!
[/LIST]
To sum up, I now have to go through the following procedure every time I log in.

1. Login in with metacity as default window manager
2. Disable the cube in compiz settings manager
3. Start compiz with compiz --replace
4. Enable the cube in compiz settings manager.

After doing that everything works fine ... at least until I log out. 

The fact that I can get everything to work indicates that I've got the driver installed OK and it is working. But why should I have to go through this bizarre procedure each time I log in? 

Anyone have any ideas or suggestions?

Notes:
1. The problem afflicts all users - so it probably isn't a user config file issue.
2. I've reinstalled compiz and a whole lot of xwindows stuff. Didn't help.
3. I will try downgrading the video driver to the previous version as a last resort. But if the problem is something I broke while things were messed up, downgrading the driver may not fix it.
4. I'll post the crash message compiz generates in a followup (I'll have to log out and back in to generate the crash so I can copy the message)

---

### Post by hawthornso23 on 2010-02-24
OK - I rebooted. Here is what I get when I try to start compiz in a terminal.

```
ian@einstein:~$ compiz --replace
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1Comparing resolution (1280x960) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Segmentation fault
^C
ian@einstein:~$

```

Actually I've just done what I should have done earlier which is look in /usr/share/gdm/themes/Human . Guess what - no ubuntu.png.  So now I'm going to go see if I can track down which package it is normally in and put it back. Very odd that a missing graphic could cause a segfault like that. Surely somebody wrote a fallback in case it was missing? And why is it all OK if I start up the cube later. Bizarre.

---

### Post by raktarok on 2010-02-24
What happens if you delete the file /usr/share/gdm/themes/Human/ubuntu.png? Is it the default image for the cube caps?

Edit: Oh, I see that you don't have that file. yeah, put it up there, and see if it works. 

And you said:
If compiz is the window manager during login it dies killing the nautilus desktop and leaving me without a window manager running (no window decorations). This is a nasty state to be in because you can't easily get at a terminal (yeah ctl alt F1 - but how to fix the window manager from there).

Now this is not going to help for this particular issue, but you can start metacity (and a lot of graphical apps) in this way:
```
metacity --display=:0.0
```

I am going to look and see if I can solve your problem.

---

### Post by hawthornso23 on 2010-02-24
The ubuntu.png file is suppose to be part of the ubuntu-gdm-themes package . But it isn't. It seems to be the same as the one in the HumanLive theme, and indeed you can even find the image on wikipedia. So I've got myself an ubuntu.png file now.

Compiz still fails, but the last thing it complains about is now

```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

So the missing ubuntu.png file wasn't the cause of my problem - just a side issue that got dragged into it. By the way - I have NO idea why compiz wants this graphic. It isn't anything I've ever seen on the cube.

---

### Post by raktarok on 2010-02-24
It seems that I was wrong earlier. The two errors that you saw are just warnings, and should not conflict with starting of compiz. See this:
[https://answers.launchpad.net/ubuntu/+question/29985](https://answers.launchpad.net/ubuntu/+question/29985)

You are having an entirely different problem, I think, and a very strange one..

I don't know what is wrong though, sorry. I will post here if I find something.

EDIT: Also, post a similar terminal output for the instance where compiz launches properly. (For 3, after steps 1 & 2, then we can compare the two...)

---

### Post by hawthornso23 on 2010-02-24
Thanks for your attention to my problem. 

Thanks also for the --display=:0.0 trick. Very useful to know.

---

### Post by hawthornso23 on 2010-02-24
Here is a successful startup of compiz with the cube disabled. 

Main difference = no segfault.

Datum: It did think a long time before I got my prompt back.

```
ian@einstein:~$ metacity --replace &
[1] 10656
ian@einstein:~$ compiz --replace &
[2] 10657
ian@einstein:~$ Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1Comparing resolution (1280x960) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
ian@einstein:~$
```

Running under gnome "seesion"?  
Should I submit a bug report to launchpad to fix the spelling mistake. :-)

---

### Post by hawthornso23 on 2010-02-24
I agree that this

```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

is not the problem, so don't go there. It is just a harmless warning.

Well that is enough for tonight. 

If noone has any suggestions, then tomorrow I'll have a go at 
rolling the ATI driver back to 10.1 and see if that fixes it.

---

### Post by hawthornso23 on 2010-02-25
Datum - piece of dmsg output follows. You can see the segfaults. libc-2.10.1.so seems also implicated

```
                 
[18080.383707] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X                                                                                                      
[18080.384307] [fglrx] Firegl kernel thread PID: 8549                                                                                                            
[18081.023521] [fglrx] Gart USWC size:1237 M.                                                                                                                    
[18081.023525] [fglrx] Gart cacheable size:491 M.                                                                                                                
[18081.023530] [fglrx] Reserved FB block: Shared offset:0, size:1000000                                                                                          
[18081.023533] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000                                                                                   
[18081.023535] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000                                                                                    
[18096.282254] compiz.real[8754]: segfault at 3143000 ip 00007fedc47ec927 sp 00007fff1b216698 error 4 in libc-2.10.1.so[7fedc476a000+166000]                     
[18145.519960] compiz.real[8974]: segfault at 4207000 ip 00007f292ac018f8 sp 00007fffa34a9dd8 error 4 in libc-2.10.1.so[7f292ab7f000+166000]                     
[19485.271301] compiz.real[9520]: segfault at 4645000 ip 00007f45e1a0d92f sp 00007fff85548428 error 4 in libc-2.10.1.so[7f45e198b000+166000]                     
[19807.534360] compiz.real[9732]: segfault at 2a7a000 ip 00007f3c25500927 sp 00007fff0f419c18 error 4 in libc-2.10.1.so[7f3c2547e000+166000]                     
[20285.758274] compiz.real[9864]: segfault at 311a000 ip 00007f9ceb9b593f sp 00007fff27108058 error 4 in libc-2.10.1.so[7f9ceb933000+166000]                     
[21516.490101] compiz.real[9983]: segfault at 27c5000 ip 00007fd9042b592f sp 00007fff3fbc26a8 error 4 in [7fd904233000+166000]
[21553.147470] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[21553.148047] [fglrx] Firegl kernel thread PID: 10016
[21553.787553] [fglrx] Gart USWC size:1237 M.
[21553.787557] [fglrx] Gart cacheable size:491 M.
[21553.787562] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[21553.787564] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000
[21553.787566] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000
[23276.399447] compiz.real[10950]: segfault at 3a7c000 ip 00007fc4db1fb8f8 sp 00007fff9be6a258 error 4 in libc-2.10.1.so[7fc4db179000+166000]
[24838.763385] compiz.real[11022]: segfault at 408f000 ip 00007f45a5a018e1 sp 00007fff9a08d0c8 error 4 in libc-2.10.1.so[7f45a597f000+166000]
[24870.451047] compiz.real[11152]: segfault at 4285000 ip 00007f200e50d93f sp 00007fff4d4783c8 error 4 in libc-2.10.1.so[7f200e48b000+166000]
[37677.212305] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[37677.212910] [fglrx] Firegl kernel thread PID: 11733
[37677.852331] [fglrx] Gart USWC size:1237 M.
[37677.852335] [fglrx] Gart cacheable size:491 M.
[37677.852339] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[37677.852342] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000
[37677.852344] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000
[60625.157030] compiz.real[12264]: segfault at 3e1b000 ip 00007f4444fa48f8 sp 00007fff8f65a598 error 4 in libc-2.10.1.so[7f4444f22000+166000]
[93238.402432] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X

```

---

### Post by raktarok on 2010-02-25
I looked around a bit, and I could see that a couple of people at other places were also having a similar compiz crash as you. But I really don't have any solutons, I don't know enough about things like these. maybe you can try reinstalling the ATI driver? People with ATI/nvidia graphics seem to have similar problems....

One easy option now would be to stop using compiz cube (and it should not be hard to do that, right ;)), but if you don't want to do that, and also don't want to go through the tedious 4 steps everytime you login, you can try automating the process. Have a look at this post about GUI automation, maybe you can use this to automatically disable the cube and re-enable it?
[http://www.webupd8.org/2010/02/sikuli-gui-automation-using-screenshots.html](http://www.webupd8.org/2010/02/sikuli-gui-automation-using-screenshots.html)

Or you can write a script to automate the entire 4 steps you mentioned earlier, using gconftool-2 to disable and enable the cube + compiz and metacity commands to start/shutdown the window managers. The script can be a bit tricky to write though, so if you are interested in it, and need some help, post back. I will try to help.

Good luck!

---

### Post by hawthornso23 on 2010-03-26
Installing the 10.3 release of the ATI driver fixed the problem. Thread marked as solved.

---

