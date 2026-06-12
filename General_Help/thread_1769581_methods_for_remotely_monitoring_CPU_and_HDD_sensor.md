---
title: "methods for remotely monitoring CPU and HDD sensors with lm_sensors?"
date: 2011-05-28
forum: General Help
---

### Post by per0xide on 2011-05-28
I'm not sure where to post this, so please move it if it's posted in an inappropriate section.

I'm  looking for a method of monitoring my server's CPU and HDD temps  remotely. I'm running Debian (squeeze), not technically Ubuntu, but  anytime I need help with it, these forums have been an invaluable asset.  I'm not running X on it, just CLI. 

I'm running Ubuntu 11 on my  desktop, with Gnome. I also installed Ubuntu 11 on my laptop, and my  girlfriend's laptop. So now we're Windows free. :) Plus, our experience  with Ubuntu has proven to be very refreshing. The installs on our  laptops went without a hitch, and I only had one issue with my desktop,  which was relatively easy to fix once I remembered that it has an on  board sound card that I don't use. I have an HT Claro+ Plus on it, and  I'm using the optical out, to a Logitech z-5500. This card was mediocre  in Windows, and though the system has a 10" sub, I could only feel the  bass from it if I got up and stood in the door way to the room, and it  was very finicky about distortion. FLACs, and mp3s that were encoded for  5.1 always sounded muddy. It was like the sound card didn't know which  speaker to send the signals to. Under Linux, it's amazing. Everything is  so much more crisp. I can play music _much_ louder, without any hint of  distortion, my 5.1 encoded files play through the correct speakers, and  I can feel the bass just fine at the keyboard. When I was running  Windows, I hardly ever listened to music, because it always resulted in  me trying to tweak the sound to fix it, and just ended in frustration.  Now, I listen to music anytime I'm at my computer, and it's almost  always at a deafening level. 

Anyway, enough happiness, back to the problems.

Initially,  when I setup Debian on the server, I only intended on using it as a  samba box, so I could toss all of my files on it for a backup. This  worked great when I was running Windows on the rest of the computers,  it's kind of iffy under Linux, though. When I mount the samba share, I  can get to it, but my user accounts don't have access to anything other  than the root of the share. Under the root account though, I have access  to everything. That's a whole other problem that's currently on the  back burner. 

After my girlfriend and I uploaded around 2TB of  stuff to the server, I did something to break apache. I don't remember  what it was, but when it broke, I couldn't even access it without  getting an internal server error. To fix it, i did an apt-get purge  apache2, hoping to just reinstall apache and start fresh. However, when I  attempted to reinstall it using apt-get, the package it downloads is  only 36k, and after it "installs" there's no executables anywhere on the  system. To get around this, I just compiled apache and php5 from  source.

Now apache works, and php sort of works. I can load  simple php pages on it, but anything that's useful to me (like  phpsysinfo) doesn't work. It just loads a blank page. When I right click  the page and hit view source, there's no code. Torrentflux also no  longer works. The page loads, and everything looks good, until I attempt  to start a torrent, then it just hangs at "starting" and never  downloads anything. 

This problem's also currently on the back  burner. I believe I'm missing something simple, but can't seem to figure  it out. At first, I didn't think it was much of a problem. I figured as  long as I don't do anything to break Webmin, I'd be fine.

Normally  at this point, since everything worked on it when I initially  installed, I would just move everything I wanted to keep over to the  desktop, and do a format/reinstall. However, we've got so much stuff on  it now, that that's no longer an option. 

I started looking up  ways to monitor the CPU and HDD temps on it. It's running sensorsd,  which supposedly will send me an email when one of the sensors trigger  an alarm, but I'd also like to have something that I can constantly  monitor, in case I do something to break postfix.

It would be  real nice if I could get a gnome applet that will monitor a remote  system. But I've been unsuccessful in finding one. I installed Nagios on  the server, and I actually got it to launch. But I need to fix apache  in order to view it. I've tried looking for CLI based programs to  monitor it with, but haven't had much luck with that either. 

Webmin has a monitoring feature, but it only monitors running processes, not temps. 

I wrote a shell script with my extremely limited shell scripting abilities, that goes like this:

```

#!/bin/sh
while true; do
clear
sensors -f | grep emp
hddtemp -u F /dev/sda
sleep 10
done

```Which gives me this:

```

temp1:      +107.6°F  (crit = +194.0°F)                  
k8temp-pci-00c3
Core0 Temp:  +93.2°F                                    
Core0 Temp:  +82.4°F                                    
Core1 Temp: +104.0°F                                    
Core1 Temp:  +82.4°F                                    
/dev/sda: WDC WD20EARS-00MVWB0: 93°F

```It  works, but I don't like how it redraws the entire screen. I'd rather it  only redraw the values when they change, but I don't know how to do  that. It'd be real nice if I could get it to go into it's own little  window, instead of having to launch a terminal, ssh to the server, and  then just resize that terminal window to where it doesn't take up as  much space. 

If anyone knows of a better method, or of a way to improve my shell script, any help would be greatly appreciated.

---

### Post by bertiebaggio on 2011-07-19
This is 6 weeks old, are you still having problems? If so:

[FONT="Courier New"][watch]("http://manpages.ubuntu.com/manpages/natty/man1/watch.1.html")[/FONT] is useful for monitoring the output of a program. If you remove the loop and clear from your script and then do [FONT="Courier New"]watch /home/per0xide/script/temperature.sh[/FONT], that should save the whole terminal window being redrawn. As for GUI monitoring of the output, I can't really help you there, other than to say 'look into the remote monitoring programs available'. I stumbled on this thread because I'm using the CLI and graphing the output!

Blank PHP pages with Apache sounds like a misconfiguration or some other error. I think the the error messages are suppressed because that is more secure. Have a look in [FONT="Courier New"]/var/log/httpd/error.log[/FONT] and see what that says, or can use the [error_reporting]("http://php.net/manual/en/function.error-reporting.php") function:

```

<?php
error_reporting(E_ALL);
phpinfo();
?>

```

---

### Post by bertiebaggio on 2011-07-19
> **per0xide said:**
> This  worked great when I was running Windows on the rest of the computers,  it's kind of iffy under Linux, though. When I mount the samba share, I  can get to it, but my user accounts don't have access to anything other  than the root of the share. Under the root account though, I have access  to everything. That's a whole other problem that's currently on the  back burner. 

I could be off the mark with this too, but I had problems with user accounts and samba, and it could be a user id number problem. Even if you have the same username on both computers, you might have a different user id. Check with [FONT="Courier New"]id -u[/FONT] on both boxes, or ssh to the debian machine and try [FONT="Courier New"]ls -l[/FONT] to see if it has numbers instead of your username in the second and third columns. If you discover this is the case, you can do a number of things to remedy it, eg changing your uid ([FONT="Courier New"]usermod -u *newid*[/FONT]). 

However, I put a caveat on the above advice: I'm no expert, and I remember having to edit the smb.conf file. YMMV.

---

### Post by per0xide on 2011-07-19
> **bertiebaggio said:**
> This is 6 weeks old, are you still having problems? If so:

[FONT=Courier New][watch]("http://manpages.ubuntu.com/manpages/natty/man1/watch.1.html")[/FONT] is useful for monitoring the output of a program. If you remove the loop and clear from your script and then do [FONT=Courier New]watch /home/per0xide/script/temperature.sh[/FONT], that should save the whole terminal window being redrawn. As for GUI monitoring of the output, I can't really help you there, other than to say 'look into the remote monitoring programs available'. I stumbled on this thread because I'm using the CLI and graphing the output!

Blank PHP pages with Apache sounds like a misconfiguration or some other error. I think the the error messages are suppressed because that is more secure. Have a look in [FONT=Courier New]/var/log/httpd/error.log[/FONT] and see what that says, or can use the [error_reporting]("http://php.net/manual/en/function.error-reporting.php") function:

```

<?php
error_reporting(E_ALL);
phpinfo();
?>

```

Thanks! I didn't even know about the watch command. This will be very useful. Thanks for the Apache help as well :) I'll try that out ASAP.

---

### Post by per0xide on 2011-07-19
> **bertiebaggio said:**
> I could be off the mark with this too, but I had problems with user accounts and samba, and it could be a user id number problem. Even if you have the same username on both computers, you might have a different user id. Check with [FONT=Courier New]id -u[/FONT] on both boxes, or ssh to the debian machine and try [FONT=Courier New]ls -l[/FONT] to see if it has numbers instead of your username in the second and third columns. If you discover this is the case, you can do a number of things to remedy it, eg changing your uid ([FONT=Courier New]usermod -u *newid*[/FONT]). 

However, I put a caveat on the above advice: I'm no expert, and I remember having to edit the smb.conf file. YMMV.

I'll give that a shot too. Thanks for the advice. :)

---

