---
title: "Suspend/hibernate problems - Kernel? ATI Radeon X300"
date: 2011-10-05
forum: General Help
---

### Post by DanielSenat on 2011-10-05
Hi,

I use Xubuntu, natty. My problem is that hibernate/suspend does not work. I can suspend, but can't get out of it. The screen is just black. I can't hibernate at all. I have followed the following guide to get more swap:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It didn't help but the computer feels a lot quicker now.

[http://pastebin.com/KVZYksSs](http://pastebin.com/KVZYksSs)

Once or twice the screen have turned black with white text on. I think it's when the screensaver turns on. The only solution from here is to turn of the computer pressing the on/off button.

My question is if there is a kernel that is particular stable for my hardware. I can't change back to my old kernel as I autoremoved it after a kernel update. For the moment I have 2.6.38-11-generic, it's ok, but suspend/hibernate.. 

Could it be the graphic card that is causing the problems? ATI Technologies Inc M22 [Mobility Radeon X300] Is there a better kernel for that?

/Daniel

---

### Post by Toz on 2011-10-05
Swap is only required for hibernate. Suspend stays in memory.

Is there anything in **/var/log/pm-suspend.log**?

Also, running the following command may yield some diagnostic info:
```
cat /var/log/dmesg* | grep PM:
```

EDIT:
My bad. Try instead:
```
cat /var/log/syslog | grep PM:
```

---

### Post by DanielSenat on 2011-10-07
> **Toz said:**
> Swap is only required for hibernate. Suspend stays in memory.

Is there anything in **/var/log/pm-suspend.log**?

Also, running the following command may yield some diagnostic info:
```
cat /var/log/dmesg* | grep PM:
```

EDIT:
My bad. Try instead:
```
cat /var/log/syslog | grep PM:
```

[http://pastebin.com/QatV5bUV](http://pastebin.com/QatV5bUV)

[http://pastebin.com/gr0CJnYh](http://pastebin.com/gr0CJnYh)

And there where also a "pm-suspend.log.1" :

[http://pastebin.com/59BWS0YK](http://pastebin.com/59BWS0YK)

Thank's!

---

### Post by Toz on 2011-10-07
Is your notebook a Toshiba M40X?

Can you also post results of:
```
cat /var/log/syslog* | grep PM:
```
...right after you attempt a suspend and recover.

---

### Post by DanielSenat on 2011-10-10
> **Toz said:**
> Is your notebook a Toshiba M40X?

Can you also post results of:
```
cat /var/log/syslog* | grep PM:
```
...right after you attempt a suspend and recover.

[http://pastebin.com/KLAifcfn](http://pastebin.com/KLAifcfn)

Yes my computer is Satellite MX40-185 :) Still working!

---

### Post by 2F4U on 2011-10-10
Did you already try to add nomodeset to the grub kernel parameters? I got suspend/hibernate working with this parameter on an old machine with ATI card.

---

### Post by DanielSenat on 2011-10-10
> **2F4U said:**
> Did you already try to add nomodeset to the grub kernel parameters? I got suspend/hibernate working with this parameter on an old machine with ATI card.

No I havn't, how do I do that?

---

### Post by DanielSenat on 2011-10-11
> **2F4U said:**
> Did you already try to add nomodeset to the grub kernel parameters? I got suspend/hibernate working with this parameter on an old machine with ATI card.

Is this what you mean? [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) And what option should i try?

---

### Post by Toz on 2011-10-11
Yes. Try it temporarily by following the section titled "How to temporarily set kernel boot options on an installed OS (not wubi)" The parameter is **nomodeset** (be careful of the spelling, the spelling in the screenshot is incorrect).

---

### Post by DanielSenat on 2011-10-11
> **Toz said:**
> Yes. Try it temporarily by following the section titled "How to temporarily set kernel boot options on an installed OS (not wubi)" The parameter is **nomodeset** (be careful of the spelling, the spelling in the screenshot is incorrect).

I will be careful! "To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:" How to enter the grup menu? When  boot my computer i can chose F12 or F2 to setup but thats not what I need. And pressing shift does nothing.


From another site: "When Ubuntu boots, you normally briefly see a screen that says &#8220;GRUB loading. please wait&#8230; Press Esc to enter the menu&#8230;&#8221;" I don't have the screen Grub Loading! I use Xubuntu

---

### Post by DanielSenat on 2011-10-11
> **Toz said:**
> Yes. Try it temporarily by following the section titled "How to temporarily set kernel boot options on an installed OS (not wubi)" The parameter is **nomodeset** (be careful of the spelling, the spelling in the screenshot is incorrect).

I managed to enter the grub menu... But after "quiet splash" it is written "vt.handoff=7" should i take that away and write nomodeset instead?

I did write nomodeset after vt.handoff=7 after the following example: [http://ubuntuforums.org/showthread.php?t=1742071](http://ubuntuforums.org/showthread.php?t=1742071)
"Adding nomodeset makes it look like: linux /boot/vmlinuz-2.6.38-8-generic root=UUID=65e6aaee-3822-2342-a1\
 3a-882342840824 ro quiet splace vt.handoff=7 nomodeset"

So i guess now i will try to hibernate and suspend to see what happened :)

---

### Post by DanielSenat on 2011-10-11
I tried the option nomodeset but it didn't change anything. When i tried to suspend, I managed like usual but could't get out from it like usual.. I pressed the powerbutton and tried again.. adding nomodeset and booting, then trying to hibernate. And as usual, I could not. The screen just turned black and computer working like crazy.. after some time I just did a forced powerbutton switch off.

Also tried adding acpi_osi= and acpi_osi="Linux" after vt.handoff=7 without any change...

---

### Post by Toz on 2011-10-11
Let's try getting a more complete log file to see whats going on when you try to suspend.

1. Become root:
```
sudo -i
```

2. Backup the existing log file:
```
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.bak
```

3. Create new log file:
```
touch /var/log/pm-suspend.log
```

4. Enable greater debugging:
```
export PM_DEBUG=true
```

5. Manually run suspend:
```
pm-suspend
```

6. After you have recovered your system, post back the contents of the **/var/log/pm-suspend.log** and the results of:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by DanielSenat on 2011-10-11
> **Toz said:**
> Let's try getting a more complete log file to see whats going on when you try to suspend.

1. Become root:
```
sudo -i
```

2. Backup the existing log file:
```
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.bak
```

3. Create new log file:
```
touch /var/log/pm-suspend.log
```

4. Enable greater debugging:
```
export PM_DEBUG=true
```

5. Manually run suspend:
```
pm-suspend
```

6. After you have recovered your system, post back the contents of the **/var/log/pm-suspend.log** and the results of:
```
cat /var/log/syslog* | grep PM:
```

The content of pm-suspend.log:
[http://pastebin.com/G7AmPvCM](http://pastebin.com/G7AmPvCM)

The content of cat /var/log/syslog* | grep PM:
[http://pastebin.com/tfGhUqRn](http://pastebin.com/tfGhUqRn)

There is also a "pm-suspend.log.1" and "pm-suspend.log.bak".. but I guess you know that.. they are minor in size!

---

### Post by Toz on 2011-10-12
Hmmm. Nothing sticks out, other than the fact that there is no resume logings. Why don't you try uswsusp and see if it works:
```
sudo apt-get uswsusp
```
Then run the following command to initiate a suspend action:
```
s2ram
```
...if you get an error about your system not being on the whitelist, try the following:
```
s2ram -f
```

See if this works.

---

### Post by DanielSenat on 2011-10-12
> **Toz said:**
> Hmmm. Nothing sticks out, other than the fact that there is no resume logings. Why don't you try uswsusp and see if it works:
```
sudo apt-get uswsusp
```
Then run the following command to initiate a suspend action:
```
s2ram
```
...if you get an error about your system not being on the whitelist, try the following:
```
s2ram -f
```

See if this works.

Trying that, should i also write "install" after apt-get?

Did it and tried s2ram: [http://pastebin.com/ynh7LcPw](http://pastebin.com/ynh7LcPw)

Tried s2ram -f: [http://pastebin.com/EjAgxKRh](http://pastebin.com/EjAgxKRh)

---

### Post by Toz on 2011-10-12
> **DanielSenat said:**
> Trying that, should i also write "install" after apt-get?
Sorry, yes, sudo apt-get install uswsusp

> Did it and tried s2ram: [http://pastebin.com/ynh7LcPw](http://pastebin.com/ynh7LcPw)

Tried s2ram -f: [http://pastebin.com/EjAgxKRh](http://pastebin.com/EjAgxKRh)
Sorry again.
```
sudo s2ram -f
```

---

### Post by DanielSenat on 2011-10-14
> **Toz said:**
> Sorry, yes, sudo apt-get install uswsusp


Sorry again.
```
sudo s2ram -f
```

No problem! :) I tried it and my computer did suspend, but same problem again. I couldn't come out from it, just black screen.

---

### Post by Toz on 2011-10-15
How about these:
```
sudo s2ram -f -v
sudo s2ram -f --vbesave
sudo s2ram -f --vbepost
sudo s2ram -f --vbemode
sudo s2ram -f -s -p -v
```

---

### Post by DanielSenat on 2011-10-15
> **Toz said:**
> How about these:
```
sudo s2ram -f -v
sudo s2ram -f --vbesave
sudo s2ram -f --vbepost
sudo s2ram -f --vbemode
sudo s2ram -f -s -p -v
```

First option didn't work(did suspend, but same...), second gave this: [http://pastebin.com/Ktxf480i](http://pastebin.com/Ktxf480i) Third gave this: [http://pastebin.com/z89Mr644](http://pastebin.com/z89Mr644) vbmode gave this: [http://pastebin.com/cCnZYLr1](http://pastebin.com/cCnZYLr1)

---

### Post by DanielSenat on 2011-10-15
> **DanielSenat said:**
> First option didn't work(did suspend, but same...), second gave this: [http://pastebin.com/Ktxf480i](http://pastebin.com/Ktxf480i) Third gave this: [http://pastebin.com/z89Mr644](http://pastebin.com/z89Mr644) vbmode gave this: [http://pastebin.com/cCnZYLr1](http://pastebin.com/cCnZYLr1)
sudo s2ram -f -s -p -v did not work the first time, but when i resumed i got a "daniel-satellite-login:" high up in the left corner. I couldn't do anything from there! The second time it did work! But the third time the "login" came up again, and the computer was blocked. Last time it did work again! I will try again :)

It worked again :) here is the text in the terminal after resume :[http://pastebin.com/sudGqXeJ](http://pastebin.com/sudGqXeJ)

edit 1: It works 2 times out of 3. First of all, It seems that I have to close the terminal before i try again. Second, it dooesn't help all the times, sometimes I can't even get down to suspend, the "login" thing in the left corner shows up directly and the system is blocked. But hey! :) It works :)

edit 2: I am satisfied! Is there any way to link this command with suspend option in meny?

---

### Post by Toz on 2011-10-15
I've had some difficulty getting uswsusp to be default on my other laptop. So here are the 3 approaches (best option first):

A1. Set correct pm-utils options
```
gksudo mousepad /etc/default/acpi-support
```
...and uncomment the line:
> # SAVE_VIDEO_PCI_STATE=true
...so that it reads
```
SAVE_VIDEO_PCI_STATE=true
```
...save the file.

A2. Recreate initramfs
```
sudo update-initramfs -u
```

A3. _Reboot_ and try using the menu options.

------------------------------------------------

If you have no luck with the above approach, here is the second approach:

B1. Set uswsusp as default in place of pm-utils:
```
gksudo mousepad /etc/pm/config.d/defaults
```
...and add the following content:
```
SLEEP_MODULE=uswsusp
S2RAM_OPTS="-f -s -p -v"
```
...save the file.

B2. Recreate initramfs
```
sudo update-initramfs -u
```

B3. _Reboot_ and try using the menu options.

------------------------------------------------

And finally, if neither of the above 2 options work, try this approach:

C1. Create new pm-suspend file:
```
gksudo mousepad /usr/sbin/s2ram_override
```
...with the following contents
```
#!/bin/bash
/usr/sbin/s2ram -f -s -p -v
```
...save the file then make it executable
```
chmod +x /usr/sbin/s2ram_override
```

C2. Backup the current pm-utils suspend file:
```
sudo mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.BAK
```

C3. Link in the s2ram suspend file:
```
sudo ln -s /usr/sbin/s2ram_override /usr/sbin/pm-suspend
```

C4. Try using the menu suspend option.

---

### Post by DanielSenat on 2011-10-15
> **Toz said:**
> I've had some difficulty getting uswsusp to be default on my other laptop. So here are the 3 approaches (best option first):

A1. Set correct pm-utils options
```
gksudo mousepad /etc/default/acpi-support
```
...and uncomment the line:

...so that it reads
```
SAVE_VIDEO_PCI_STATE=true
```
...save the file.

A2. Recreate initramfs
```
sudo update-initramfs -u
```

A3. _Reboot_ and try using the menu options.

------------------------------------------------

If you have no luck with the above approach, here is the second approach:

B1. Set uswsusp as default in place of pm-utils:
```
gksudo mousepad /etc/pm/config.d/defaults
```
...and add the following content:
```
SLEEP_MODULE=uswsusp
S2RAM_OPTS="-f -s -p -v"
```
...save the file.

B2. Recreate initramfs
```
sudo update-initramfs -u
```

B3. _Reboot_ and try using the menu options.

------------------------------------------------

And finally, if neither of the above 2 options work, try this approach:

C1. Create new pm-suspend file:
```
gksudo mousepad /usr/sbin/s2ram_override
```
...with the following contents
```
#!/bin/bash
/usr/sbin/s2ram -f -s -p -v
```
...save the file then make it executable
```
chmod +x /usr/sbin/s2ram_override
```

C2. Backup the current pm-utils suspend file:
```
sudo mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.BAK
```

C3. Link in the s2ram suspend file:
```
sudo ln -s /usr/sbin/s2ram_override /usr/sbin/pm-suspend
```

C4. Try using the menu suspend option.

For the moment i just made a nice programstarter "sleep" in my dock. And then I have hidden the suspend, hibernate buttons so they don't bother me by mistake. It's ok for now I guess, I will try these changes later. Thank you very much for helping :)

---

