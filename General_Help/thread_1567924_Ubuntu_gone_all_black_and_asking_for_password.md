---
title: "Ubuntu gone all black and asking for password?"
date: 2010-09-04
forum: General Help
---

### Post by nu2buntu0 on 2010-09-04
I just recently booted up my Ubuntu PC, and it starts up normally but slower. Then the loading screen comes etc etc, and after the screen is all black and asks me for login: and pass: for my login I entered my username "JulianUbuntu" and my password. Yet it said incorrect password. Now I have three questions regarding this matter.

1) How do I fix this?

2) Why is this hap^pening?

3) Is this fixable?

Thanks for your time. 

Quick PC Details:
64 bit
1G of RAM
2.20 GHz
NVidia GeForce 6150 LE
(its a sucky piece of crap I know.)

---

### Post by nu2buntu0 on 2010-09-04
bump

---

### Post by DandyDon on 2010-09-04
> **nu2buntu0 said:**
> I just recently booted up my Ubuntu PC, and it starts up normally but slower. Then the loading screen comes etc etc, and after the screen is all black and asks me for login: and pass: for my login I entered my username "JulianUbuntu" and my password. Yet it said incorrect password. Now I have three questions regarding this matter.

1) How do I fix this?
Why is this hap^pening?
Who knows???
3) Is this fixable?
Try Repair.
Thanks for your time. 

Quick PC Details:
64 bit
1G of RAM
2.20 GHz
NVidia GeForce 6150 LE
(its a sucky piece of crap I know.)

1.At boot screen, select Repair.
2.Who knows?.
3.Try Repair, post back.

---

### Post by nu2buntu0 on 2010-09-04
I do not have a repair, I have recovery mode which I used.. which didnt really help. I guess I need the CD for this?

---

### Post by nu2buntu0 on 2010-09-04
I dont mean to be greedy or rude but, I need my computer for work.

---

### Post by nu2buntu0 on 2010-09-05
bump

---

### Post by coffeecat on 2010-09-05
Let's see if we can help you. There seem to be two problems:

1 You are booting into a text console. Something has gone wrong with your system and the GUI is not loading. This could be a trivial problem or a serious one. Can you remember what you did the last time you used your computer before this happened? Software update? Program installation? Were you editing system files?

2 Password problem. Make sure that caps lock isn't on. If you are confident you are typing in the correct password, have a look here for a howto on resetting the password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It involves booting into recovery mode, but is quite straightforward.

Try that and then see what happens when you reboot. Having said all that I'm concerned that the simultaneous appearance of two problems does not bode well.

You may not get a response from me until tomorrow. It's late here and I'll be logging off soon.

---

### Post by nu2buntu0 on 2010-09-05
Thank you for your help, I've tried multiple linux products, they all boot in to text.

I wasn't on it last, I'll ask my family regarding that issue.

I will try to reset the password and get back to you, thanks.

Ah it appears the last user was just searching the web. Nothing harmful.

---

### Post by coffeecat on 2010-09-05
> **nu2buntu0 said:**
> Thank you for your help, I've tried multiple linux products, they all boot in to text.

Just a couple of questions, then I will have to logoff.

Do you mean that Ubuntu was booting into a GUI but now it only boots into a black screen (a text console)? Or do you mean that you have never had a GUI and that every Linux distro you've tried boots into a text console?

If the former, then something has gone wrong in your system. If the latter, then it would suggest a hardware problem or some aspect of hardware that is not Linux-friendly.

Or do you mean that you were getting the GUI with Ubuntu and now you don't and neither do you get a GUI when you boot up with a live CD with another distro?  I don't understand what you mean in the quote above.

---

### Post by nu2buntu0 on 2010-09-05
Okay Im able to log in, however it's just welcoming me in text.. there is nothing else. Please help me as soon as you can.

Thanks!

---

### Post by nu2buntu0 on 2010-09-05
It used to have a GUI interface, now it's all text.
I've tried two linux distros they both are text based.

---

### Post by cake nom nom on 2010-09-05
> **nu2buntu0 said:**
> I do not have a repair, I have recovery mode which I used.. which didnt really help. I guess I need the CD for this?


 try typing in reboot 

if it says you have to be root type sudo reboot

if you get the option again pick recovery and repeat  see if that fixes the problem

---

### Post by nu2buntu0 on 2010-09-05
Thanks, I'll try that!

---

### Post by nu2buntu0 on 2010-09-05
Okay it didn't change anything. (commands work, but still same problem)

---

### Post by nu2buntu0 on 2010-09-05
bump

---

### Post by DemonBob on 2010-09-05
First lets see what version of ubuntu you are running. 

```
lsb_release -a
```

Next reboot, login then check /var/log/Xorg.0.log

```
more /var/log/Xorg.0.log
```

At the bottom of the file. 

Check for any errors near the bottom of the file. You'll should be able to notice the errors from normal output. If anything stands out post it here. 

Also lets try to start gdm

```
sudo restart gdm
```

if that doesn't work. 

```
sudo service gdm stop
sudo service gdm start
```

or
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

One of those commands, depending on your version of linux should either start your logon GUI, or output an error. Record the error and post it here.

Once done, recheck the bottom /var/log/Xorg.0.log to see if errors are thier also.

---

### Post by nu2buntu0 on 2010-09-05
Distributor ID: Ubuntu
Description: Ubuntu 10.04.1 LTS
Release: 10.04
codename: lucid
---------------
No layout section. Using the first screen section.
Using a default monitor configuration
Unable to estimate virtual size
Screen(s) found but none have a usable configuration
Fatal sevrer error:
no screens found

trying the other codes now..

thanks for the help, hopefully this can be solved soon.

---

### Post by nu2buntu0 on 2010-09-05
when i type in the sudo service gdm start, it sais fatal server error:
no screens found

---

### Post by DemonBob on 2010-09-05
You said your video card is nvidia correct? 


Lets try to reinstall the nvidia driver. 

I want you to run the following commands. 

```
sudo apt-get install envyng-core envyng-gtk envyng-qt
```

Now run: 

```
sudo envyng -t
```

You should see a list of options now. 

Select the option to Uninstall the nvidia driver. Should be option number 2. 

REBOOT when it is done. 

Once you system is backup re-run envyng 

```
sudo envyng -t
```

Select the option to install the nvidia driver. Should be option number 1. Install the recommended version of the driver. 

REBOOT when it is done. 

Let me know what happens. If you have a GUI, great, if not. We'll try some other options.

---

### Post by confused57 on 2010-09-06
Another thing you could try is pressing "e" with your first Ubuntu 10.04 grub entry highlighted in the grub boot menu, at the very end of the kernel line add "nomodeset"(without quotes), then ctrl+x to boot.

---

### Post by nu2buntu0 on 2010-09-06
E: Couldn't find envyng-core
sudo: envyng command not found

@ confused I manually edited the boot line to nomodeset a long time ago.

---

### Post by nu2buntu0 on 2010-09-06
bump

---

### Post by DemonBob on 2010-09-06
Ok just realized they phased out envy, so it's no longer available.

Try this. 

```
sudo dpkg-reconfigure xserver-xorg
```  

choose vesa as the driver. and the rest as defaults. 

Once your done, reboot or type. 

```
startx
```

---

### Post by DemonBob on 2010-09-06
Also, try not to bump the post so much. It is frowned upon in the fourms if you do it once more then every 24 hours. I get email's when you post to the thread.

---

### Post by nu2buntu0 on 2010-09-06
fatal server error:
no screens found

xinit No such file or directory (erno 2): unable to connect to X server.
xinit No such process (erno 3): Server error

also, I'm sorry for rushing things but I need this for work.. so right now I'm in a bad situation.

---

### Post by d3v1150m471c on 2010-09-06
if it can't find your screen it could be hardware confusion. try doing a hard reset. if it's a laptop, unplug EVERYTHING after your turn it off, take out the battery and hold the power button for about 10 seconds. let it sit for 5-10 minutes. for a desktop pc i think you just unplug everything from the tower and from the power source. press power like above for a few seconds and let it sit for 5 to 10 minutes. plug in only your necessary components and turn it back on.

---

### Post by DemonBob on 2010-09-06
This sounds like an update that went bad. 


Try this. 

```
sudo apt-get remove --purge nvidia-current
```

Then 

```
sudo apt-get install nvidia-current
```


Reboot.

---

### Post by nu2buntu0 on 2010-09-06
Sorry, I still get this same old black background, white text.

---

### Post by nu2buntu0 on 2010-09-07
i had to reinstall Windows on the PC. I cannot access the grub anymore, and I am still having this problem, please help.

---

### Post by nu2buntu0 on 2010-09-08
help please.

---

