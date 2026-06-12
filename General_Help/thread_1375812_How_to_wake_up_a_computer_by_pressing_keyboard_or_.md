---
title: "How to wake up a computer by pressing keyboard or mouse click?"
date: 2010-01-08
forum: General Help
---

### Post by PrvSAT on 2010-01-08
Hello,

I have a dual core with an Intel integrated video HTPC (ubuntu 9.2). The suspend mode works for me and by pressing the power button, it wakes up the computer fine. 
**How could I do the wake up from a keyboard, mouse or even a remote control, please?**
Does anyone know or has this issue?
When in sleep, keyboard and mouse seem to be dead, no response at all.

---

### Post by chewearn on 2010-01-08
Wake up from remote control?  I don't know.
Wake up from keyboard or mouse?  Some motherboard require the appropriate settings to be enable in BIOS.

---

### Post by PrvSAT on 2010-01-08
I have tried in BIOS the S1, S3 and Auto mode and to "wake up on keyboard/mouse". I have exhausted all possibilities. 

Then I read somewhere that some motherboards shuts down the USB hubs (part of the MB) during the suspend mode so the mouse, keyboard or any device would not be powered in order to wake up the system. This seems logic so far but the exact same system I used it under Windows and the suspend was never a problem. 

On another note: I am surprised how Linux developers made such a huge steps in developing an OS like ubuntu but some very basic things were not taken care of like SUSPEND and HIBERNATE modes.
I read in few forums the same problems related to suspend and how many people stepped back from ubuntu going back to windoze, exact for this issue with suspend, especially those with laptops.

---

### Post by chewearn on 2010-01-08
> **PrvSAT said:**
> On another note: I am surprised how Linux developers made such a huge steps in developing an OS like ubuntu but some very basic things were not taken care of like SUSPEND and HIBERNATE modes.
I read in few forums the same problems related to suspend and how many people stepped back from ubuntu going back to windoze, exact for this issue with suspend, especially those with laptops.

You have to appreciate the difficulty.  Traditionally, Linux is used in servers, which don't need suspend or hibernate feature.  Then, suddenly, Linux became popular in the desktop within a short period of time.

On the other side, consumer hardware makers (both Desktop PC and Laptop) generally still do not see Linux OS as a market to cater for.  Hence, there is little support when the open source people approach the companies for technical data or specifications.  A lot of the work required reverse engineering of the BIOS, etc.

So, it's not like the developers don't take care of suspend or hibernate; I'm sure they would be very happy to solve all these problems.

---

### Post by PrvSAT on 2010-01-08
Good points chewearn. Thank you. It is however a bit frustrating when you go over different problems one by one and then suddenly you find yourself stuck with a simpler problem that you would think it would give you so much headache. Not that I am saying that power management is an easy problem, but I did not expect to have it. 

Since I use this as HTPC, I can not let it run all the time like a server. Or I could turn the TV and sound system by remote and then move my but and turn HTPC by hand? So much for the modern world surrounded by modern technology, eh?  If any key or muse movement would wake up the puter, I would assign it to the remote, that is the reason it is frustrating...

While in suspend, the keyboard does have power, the LED is ON.

---

### Post by chewearn on 2010-01-08
I just remember, my netbook is only able to wake up from sleep when I press the FN key.  Why only this key specifically I don't know.  Perhaps, your keyboard might have one such key too.

---

### Post by chewearn on 2010-01-08
I just discovered something else.  There is this setting under:
System > Preferences > Keyboard shortcuts > Desktop > Suspend

---

### Post by Mark Phelps on 2010-01-08
> **PrvSAT said:**
> I have tried in BIOS the S1, S3 and Auto mode and to "wake up on keyboard/mouse". I have exhausted all possibilities. 

The "wake on keyboard/mouse", when set in the BIOS, refers to PS/2 keyboard/mouse connections, not USB.

I discovered that when I went to a USB keyboard/mouse combo and lost these features.

---

### Post by PrvSAT on 2010-01-08
Thank you bud! I will look into it and get back. :popcorn:

---

### Post by PrvSAT on 2010-01-08
Unfortunately it doesn't work...
In BIOS I set the option of keyboard PS2/mouse and further I had the possibility to set three keys:
Ctrl+Esc, Space Bar, Power Button. I have tried all of them one by one but no wake up.

While I set Ctrl+Esc in BIOS, in ubuntu at keyboard shortcuts under Suspend, I set the the same keys Ctrl+Esc. After it went in suspend mode, I tried these keys but still no wake up. In keyboard shortcuts it doesn't allow you to set Space Bar since it tells you that it must be a combination of keys, so you don't put the puter in sleep by typing some text. 

Now coming back at the System/Pref/Keyboard shortcuts, if you set under Suspend option a certain keys, I believe that while you are in desktop, no application open, when you press that combination, the system should go in sleep. It is is basically a request/command, right? But it doesn't work. 
I tried few key combinations so by typing them, it should initiate the suspend mode, but it seems that this Suspend option doesn't do anything... Can you get it to work and request a suspend mode whenever you want?

You mentioned the Fn key. I have replaced my regular keyboard with an Apple keyboard (wired) that does have this key. I tried to use it while in sleep and with different combinations but no luck, the system was well suspended. 

I guess this issue is important, not only for me using a HTPC but for all the folks using a laptop that need this suspend to work (at least by querying the suspend mode whenever they want). I think it is a good idea for someone knowledgeable into this matter to take a look at that and help us out.
I am ready to donate if I can make this feature work. ;)

---

### Post by PrvSAT on 2010-01-09
I tried very hard to make it work but no success. Then I moved my HTPC to the TV and found that the sound that is out coudl be send only in analog to my amp. No digital, no optical...
I am sorry to say that and I really hate it, but I will have to move back to Windoze for this.

---

### Post by chewearn on 2010-01-09
> **PrvSAT said:**
> 

Now coming back at the System/Pref/Keyboard shortcuts, if you set under Suspend option a certain keys, I believe that while you are in desktop, no application open, when you press that combination, the system should go in sleep. It is is basically a request/command, right? But it doesn't work. 
I tried few key combinations so by typing them, it should initiate the suspend mode, but it seems that this Suspend option doesn't do anything... Can you get it to work and request a suspend mode whenever you want?

I double check this setting and indeed it failed to work.  Not sure what's going on there.

Actually, I don't have this problem in my desktop PC, because my keyboard happened to have a special sleep key on the top left corner.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142977&stc=1&d=1263023464[/IMG]


> I guess this issue is important, not only for me using a HTPC but for all the folks using a laptop that need this suspend to work (at least by querying the suspend mode whenever they want). I think it is a good idea for someone knowledgeable into this matter to take a look at that and help us out.
I am ready to donate if I can make this feature work. ;)Fortunately, this is not a big issue for laptop.  Because like my keyboard, all laptops have a dedicated suspend key (usually Fn+F1) that works.

---

### Post by chewearn on 2010-01-09
> **PrvSAT said:**
> I tried very hard to make it work but no success. Then I moved my HTPC to the TV and found that the sound that is out coudl be send only in analog to my amp. No digital, no optical...
I am sorry to say that and I really hate it, but I will have to move back to Windoze for this.

Sorry to see you go.  Use what works for you; no problem with that.

---

### Post by PrvSAT on 2010-01-09
And thank you for your help chewearn. I already run ubuntu on my MAC,using Parallels software, so I am not quite gone. :)

---

### Post by PrvSAT on 2010-01-09
However, I found this bug report that shows an identical problem since two years ago. It appear that things did not improved in regards of this matter.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37243](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37243)

---

### Post by nunovi on 2010-02-28
Hi,

In order for the system to be enabled to wake from sleep, you need to enable the corresponding ACPI device. You can do this with a script which can be run at startup on init.d with the following code:

```


echo "USB0" > /proc/acpi/wakeup


```

You need to enable the specific USB port your keyboard is connected to, or enable all USB ports. To check your USB ports use the following command

```

cat /proc/acpi/wakeup

```

This works for me, although I find it too sensitive as I have a keyboard with trackball and any movement of the mouse will wake the computer up. Sometimes it will wake up right after sleep if I just throw the keyboard into the sofa. Anyway, hope this helps.

Nuno

---

### Post by codebitch on 2011-01-16
I tried to run the command to enable wakeup from usb but it said permission denied. I put sudo in front of it but it didn't even ask for my password. do you know how to gain permission to enable this?

---

### Post by sehe on 2011-06-18
> **nunovi said:**
> 
```

echo "USB0" > /proc/acpi/wakeup

```

You need to enable the specific USB port your keyboard is connected to, or enable all USB ports. To check your USB ports use the following command
...
Nuno

That fixed it for me! THANKS

I now have this in my /etc/rc.local:

```

for a in $(awk '/^USB/ &&  ""!=$4 { print $1 }' /proc/acpi/wakeup); do echo $a > /proc/acpi/wakeup; done

```

---

### Post by sehe on 2011-06-18
> **codebitch said:**
> I tried to run the command to enable wakeup from usb but it said permission denied. I put sudo in front of it but it didn't even ask for my password. do you know how to gain permission to enable this?

Run as root entirely. With sudo, only the command runs as root, the rest of the pipe (the important bit) is run in a separate shell (process) as the current user...: No permission

You can also get around that with the well-known trick:

```
echo USB0 | sudo tee -a /proc/acpi/wakeup
```

---

