---
title: "Automatic crash report generation - FAIL"
date: 2011-05-01
forum: General Help
---

### Post by ergo-proxy on 2011-05-01
Hi, I'm a satified user of ubuntu 11.04 64bit (installed on a laptop). Everything works fine (unity, sound etc) no problems at all except that when I shutdown my computer on of the services is marked as FAIL. In a boot log I found:

* Stopping automatic crash report generation[74G[[31mfail[39;49m]

Is it anything serious? How can it be fixed?

---
Ok updating, nothing serious, can be ignored or uninstalled.

---

### Post by Zevaka on 2011-05-03
having same thing and wondering if it is important or not

---

### Post by peligro18 on 2011-05-03
yeah...i am having the same problem
the desktop keep crashing i have to select everything to appear something

i still like it better than windows
i f h w

---

### Post by lloux on 2011-05-03
I am having the same problem when restating my PC. Attached is an image of the screen when I click restart.

---

### Post by nomiz on 2011-05-04
Same here..

---

### Post by 3rdalbum on 2011-05-04
Automatic crash report generation is part of what Apport does. In previous years, the Ubuntu developers have turned off Apport shortly before the release of that version of Ubuntu, and turned it on in the new development version.

Seems like everyone has this, and if it was a real issue I'm sure a developer would have noticed it during the development cycle. So don't worry too much about it, it's only a crash report collector anyway.

---

### Post by lloux on 2011-05-04
But my system doesn&#8217;t restart by itself, it just hangs at this screen and I have to manually restart it.

---

### Post by aniac on 2011-05-09
Hi guys, are there any news regarding the above issue "automatic crash report generation [failed]" ? 

I have 5 questions and would appreciate if you could answer these for me please: 

1. How serious is this issue? 
2. What is the reason for this happening? 
3. Can this be fixed or do I need to reinstall Ubuntu Server 11.04? 
4. Will this issue re-occur on a fresh Ubuntu 11.04 Installation? 
5. How can this issue be resolved?

I hope to hear from you soon again! 

Regards,

---

### Post by lloux on 2011-05-09
For me this issue has been fixed with the latest updates, now my PC restart with no issues.
  Just use the update manager and see if it’ll solve for you.

---

### Post by aniac on 2011-05-10
Thanks for the reply, but unfortunately the update dosnt fix this issue on my machine... :confused:

I previouly used GNOME but I realized I dont need it anymore for this server. 
Now I removed GNOME  and all files which were related to it -so dont think that this could be NVIDIA related? Indeed there are some threads pointing to NVIDIA driver problems...

I dont understand where this issue comes from... 

Any ideas?

---

### Post by Aenima99x on 2011-05-10
> **aniac said:**
> Thanks for the reply, but unfortunately the update dosnt fix this issue on my machine... :confused:

I previouly used GNOME but I realized I dont need it anymore for this server. 
Now I removed GNOME  and all files which were related to it -so dont think that this could be NVIDIA related? Indeed there are some threads pointing to NVIDIA driver problems...

I dont understand where this issue comes from... 

Any ideas?

You can remove apport from the system. I got tired of the error messages and just removed it.

---

### Post by aniac on 2011-05-10
> **Aenima99x said:**
> You can remove apport from the system. I got tired of the error messages and just removed it.
Cheers for that...

---

### Post by nate1010smith on 2011-05-12
I was having the same issue and ended up using the same "solution" as @Aenima99x and @aniac.

I hadn't paid attention while rebooting since upgrading to 11.04 until today when I edited /etc/rc.local to autostart a vm for me. For a while I was convinced that the error was my fault because somehow ouptut from was being highlighted in red along with the apport failure. I've had no issues during boot since removing apport.

---

### Post by jasmines on 2011-05-18
I removed apport, but still receive the message...
how can this be possible?

I'm on a 11.04, obviously.

---

### Post by aniac on 2011-05-18
well, evryone seems to have this problem. For example, I installed Ubuntu 11.04 Desktop version 32bit on my laptop (a fresh installation) and still got this error. I think this issue cannot be fixed unless the developers come up with a bugfix i.e. an update which will fix this... 

However, this seems not to be a big issue at the moment, as the system seems to be fine appart of this little problem. I wouldnt worry too much about it, but it would be nice if this is fixed soon. In general and for your information, the automatic crash report generation is a part of apport, which does not rally interefe with any integral parts of your system. It is a useful tool for developers and in general good for statistics and error reporting though. So it is in the interest of Ubuntu programmers to get this thing running again anytime soon. 

Lets hope they find a solution for this problem.

---

### Post by Nuc72 on 2011-06-26
Hi Guys,

Try this:
- Edit the file "apport" as superuser in /etc/default/
- Set 1 to Enabled (it was 0 by default in my case)
- Save file and restart

It solved the problem on boot and shutdown. Post your experiences!
I hope it helps.

---

### Post by ak030 on 2011-07-25
thx @Nuc72

I could fix the problem that way

edit:
Hmm, a restart still causes a crash...

---

### Post by bamdad.khan on 2011-07-30
you have to apt-get **purge **apport, that removes the leftover files from /etc/init.d so you don't get the error message again. cheers.

---

### Post by upaoron on 2011-08-02
> **Nuc72 said:**
> Hi Guys,

Try this:
- Edit the file "apport" as superuser in /etc/default/
- Set 1 to Enabled (it was 0 by default in my case)
- Save file and restart

It solved the problem on boot and shutdown. Post your experiences!
I hope it helps.

It seems to work fine: once applied the message no longer appeared and no crash at boot. I'll see and let you know next times.
Many thanks.

---

### Post by hiyamandal on 2011-08-27
i am having the same problem, my ubuntu is updated regularly, and its not fixed yet! :(:confused::confused:

---

### Post by buzzing_bee on 2011-08-30
hmm..same problems with me..after upgrading my 10.10 to 11.04...
there's that error message..so i can't login to my 11.04 with 2.6.38-11-generic...but i can login with 2.6.35-22

but after sometimes..i update several times...so now i can use the 2.6.38-11, but still with the same problem (Automatic crash report generation - FAIL)

---

### Post by whitfield.fowler on 2011-10-01
> **Nuc72 said:**
> Hi Guys,

Try this:
- Edit the file "apport" as superuser in /etc/default/
- Set 1 to Enabled (it was 0 by default in my case)
- Save file and restart

It solved the problem on boot and shutdown. Post your experiences!
I hope it helps.

I would like to try this, however, upon startup I keep getting a page similar to the picture posted by lloux on May 3rd, and the machine seems to be hung.  Is there some obvious way to get past this screen so that I can try to implement the suggested solution?

Thanks,
-Whit

---

### Post by chopperprop on 2011-10-06
[COLOR=black][FONT=Verdana]I am a new user to Ubuntu and was excited to try it , now I see my laptop is hung on this error/ it will not go past the boot where it check everything and says ok except for the auto crash report fail in red. I have a cursor at the bottom what if anything should I type ? :guitar:[/FONT][/COLOR]

---

### Post by chopperprop on 2011-10-06
> **lloux said:**
> I am having the same problem when restating my PC. Attached is an image of the screen when I click restart.
  
[COLOR=black][FONT=Verdana]This has happened to from the very beginning after the install on the first restart and it will not move past this screen so I am getting ready to reinstall since there are no answers for me yet.:guitar:[/FONT][/COLOR]

---

### Post by chopperprop on 2011-10-07
[COLOR=black][FONT=Verdana]So I reinstalled with a fresh download and used the onsite ISO utility to burn the disk and also created a USB install from the USB utility. Still have the same issue. I have tried to run from CD only and it just hung there all night. I have run DBAN 2x and no errors. One more time. I see there are no replies to my questions and I am wondering if I am asking wrong ?. [/FONT][/COLOR]

---

### Post by chopperprop on 2011-10-07
[COLOR=black][FONT=Verdana]Forgot to post specifics. I am trying this for the first time ever. Using  Dell C810 laptop. 512 mb  old as dirt P3 1.3ghz system.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Tried several wipes and re installs with the new version and kept getting the same error on the first reboot( the (ACRG-F) as of 10 min ago I had finished the reinstall of the next older version 10 of Ubuntu and so far so good , it came up and is updating., I just restarted it.  It had done 60 somewhat updates and mind you this laptop was so slow with windows***oops can i say that here*** any way mouse seems ok now and it is restarted for the 2nd time and looks good. Something is not working correctly for the newest version and maybe it only applies to older systems. More to follow Thanks.[/FONT][/COLOR]

---

### Post by wane.dacha on 2011-10-15
I've been playing around with this, as I am trying to tweak gnome-shell to work better with me.  If you hang during the start, you can use ctrl+alt+f1 to spawn a terminal instead, for those who were stuck.

Usng the /etc/default/apport change fixed the fail for me (but my boot still hangs - alienware hates ubuntu)

---

### Post by p37307 on 2011-10-18
The fail warning is for a service  that automatically will notify you of a crash on the system. From my understanding it is disabled by default during roll outs of software other than the long term release. It just means it failed to start. Fixing it by editing apport in /etc/default will turn the service on.

Regarding some of the other problems that has be introduced in this post. I can assure you that the issue with apport is not causing your hang up. I am 100% sure. 

For those who removed apport, I would say you should have it so you can report problems and get solutions. Here is a good wiki page at Ubuntu about it. [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

The automatic crash system, which you were notified failed to load, even when you log off that is there from logging on, just means the service didn't start and is not a crash.

From experience, let me say that hang ups often are caused by hardware.

If it is taking long to boot, appearing to hang, walk away for thirty minutes and see if it boots anyway. I had a system that did that every time I upgraded ubuntu.

I then realized that the intial bootup can be very long cause the new system wants to check the disks good.

If it is just appears to be hanging up, try adding nomodeset in your grub on the after /boot/vmlinuz-(versionnumbers)-generic  nomodeset

IF you have a video problem that should get you to boot.

I hope this helps. chopperprop, sounds to me that nomodeset should work for you.

---

### Post by W29 on 2011-10-19
I had the same problem, so I removed Apport. That worked fine.
Now I reinstalled Apport and got this error message:
> Selecting previously deselected package apport.
(Reading database ... 137495 files and directories currently installed.)
Unpacking apport (from .../apport_1.23-0ubuntu3_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Setting up apport (1.23-0ubuntu3) ...
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.I'll restart my system to check whether I can boot.

Edit: I can boot my system without any problems now. I'll keep this post updated.
Edit: The problem occured again this morning. Removed apport and I'll be waiting when there is a fix for this.
Edit: The problem appeared again once, altough I have removed apport. Maybe something else is the problem?

---

### Post by W29 on 2011-11-03
The problem still exists. Any sugestions?

---

### Post by tico86 on 2011-11-07
Hey, I had the same problem, and apparently most of us who tried 64bits have it, so what I found on the web is that it has to do with the video card drivers, in my case it's a radeon hd 6470, so the restricted driver for the card, fglrx, is the one that gives problems, so I just removed it, following this:

[http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/](http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/)

;)

---

### Post by Qutaibah on 2011-11-11
hi 
I have the same problem :(

I am using ubuntu server 11.10 64 bit 

and I am using nvidia graphic card

---

### Post by W29 on 2011-11-12
I also work with the 64bit version and have a Nvidia card (Geforce GTS 360M).
I suspect it has something to do with that. (I had to install Ubuntu under nomodeset.)

---

### Post by bingaling on 2011-11-19
I have Ubuntu 32x and Intel graphics, so it's unlikely to be that...

---

### Post by bigo72 on 2011-12-12
I'm still not able to understand why this forum is so rushy to write [Solved] on top of unsolved threads .... mistery of life :-)

---

### Post by W29 on 2012-01-05
*bump*
Still not fixed.

---

### Post by bitf on 2012-01-12
I have a similar problem. My Dell Latitude sometimes hangs on shut down, but it has an Intel Graphics card, so the driver can't be an issue. It often creates corrupted files which is really frustrating.

---

