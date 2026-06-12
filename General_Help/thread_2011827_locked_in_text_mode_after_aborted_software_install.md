---
title: "locked in text mode after aborted software install"
date: 2012-06-27
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-06-27
Hi everyone,

I have a problem with xububtu on my P4 desktop, my primary computer. 

The problem started during the installation of a new browser, Google Chrome. The install stopped even though the progress bar in the Software Center was only around 50 percent complete. 

The Software Center said it was installed though. I closed the Software Center, and started Google Chrome. The system hung, I had to restart it by pushing the reset button.

When I tried to restart the system, it progressed normally....until it was almost to the point of getting the GUI log in screen. Instead of showing the GUI login prompt, it went to plain text and showed the following on the screen...........

```
could not write bytes: Broken pipe             {OK]  
  * Starting Winbind daemon winbind            [OK] 
  * Starting bluetooth
  * Pulseaudio configured for per-user sessions
       samed disabled: edit /etc/default/samed
          mountall: Plymouth command failed
            mountall: Disconnected from Plymouth
                                               [OK]
```

After that, it stops locked in text mode.

I can log in to the super user account and my account OK, but only in the terminal mode.

I have no idea what happened, and/or how to fix it.

I can boot with the live CD, and run programs from the CD....and it all works. Haven't tried anything else.

I need some guidance in order to restore the system to normal operation. I do have a backup system, so I can see replies via the forum.

TIA.

Art

---

### Post by jmfal on 2012-06-27
If you can get back to the terminal and run

```
 sudo apt-get install -f    
```

Answer question to continue>>>>  y >>>>enter 
At the command prompt try running

```
     sudo dpkg --configure  -a   
``` 

Again follow the prompts, after all that try

```
 startx      
```

And follow prompts,  it will probably tell you to restart at login.  Restart..

---

### Post by goodbye-windows(tm) on 2012-06-27
No joy.....

The first command didn't allow me to autoremove unnecessary files, asking me if I was 'root??

I logged in to the super user account, the one I created when I installed the os. I gave the proper password, and it was accepted. Not sure this is a problem.

The second command ran ok.

The third command gave about 3/4 page of errors. I don't know how to transfer the text of the screen output from a command line, so I can't copy the text and post it here.

Any suggestions?


Art

---

### Post by goodbye-windows(tm) on 2012-06-28
Hi Jmfal,

I found out how to export text from a tty session using pastebinit. It's all new to me, but I'll try it and get the results of the tty session errors posted.

More later, I hope::>

Regards,

Art

---

### Post by goodbye-windows(tm) on 2012-06-28
OK, I got pastebinit installed.

The sudo apt-get install -f command yields:


```



Reading package lists... 
Building dependency tree... 
Reading state information... The following packages were automatically installed and are no longer required:  
     libkexiv2-10 libtheora-bin liblensfun-data libboost-regex1.46.1 lives-data   
     libunicap2 libkvkontakte-data libweed0 libgpod4 libkgeomap-data ogmtools   
     libkvkontakte1 icedax libkexiv2-data liblensfun0 libkface-data  
     libgpod-common digikam-data kipi-plugins-common libkdcraw20 mkvtoolnix  
     libkgeomap1 libkdcraw-data 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded. 

```


The sudo dpkg --configure command yields no text output, other than a short pause while it runs, and the command prompt reappears.

The Startx command still produces about 3/4 of a screen worth of output, but pastebinit says:


```


You are trying to send an empty document, exiting. 


```


A few seconds later, the command prompt appears on the screen. So, I have no idea what's going on with pastebinit. 

During the execution of the startx command, the screen blanks immediately, then unblanks and the text resulting from the command appears. Maybe the screen blanking causes problems for oastebinit. 

I tried taking a picture with my digital camera, it's a good camera (12 megapixel), but the result is blurr and can't make out a single word on the screen when viewing the photo.

I tried it logged in to the superuser account and into my own account, the results are the same.

Any suggestions regarding the failure of pastebinit to produce any screen capture like data?


TIA

Art

---

### Post by goodbye-windows(tm) on 2012-06-29
Problem solved!!!! 

In the process of troubleshooting this issue, I came to realize (eventually) that my hard drive was full. I originally blamed the problem on an aborted software install, but only now did I realize I was copying some large files from my USB drive when the problem surfaced.

I'm not sure why there was no warning of a full drive though.

I used Gparted to eliminate one of the partitions on my hard drive (while running from the live cd), then reallocated that space to the xubuntu partition.

When I tried booting from the harddrive, the system started normally!!!!!

So, I'm a happy camper now, learned a bunch about the terminal use and realized I need to continue learning about the terminal commands and how to use them.

I also learned I need to copy desktop files to my usb drive more often than I am doing now!

Enjoy.

Art

---

