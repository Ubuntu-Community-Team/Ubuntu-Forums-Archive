---
title: "boot-up issues"
date: 2009-11-21
forum: General Help
---

### Post by kammce on 2009-11-21
I am not sure where to put this thread so I put it here.

Desktop = Gnome
Version  = 9.04
x32
Experience = Little to none
I have TWO linux kernels

When I turn on my computer, Grub loads up, the Gnome loading bar comes up, and the computer attempts to render the desktop but the screen stays blank(black pretty much).

So, to fix this issue I press "esc" button and boot the latest linux kernel I have and it works fine. I even boot from an older linux kernel and it works fine. Yes I have two kernels. I did an update and i had two linux kernels. What should I do. One says "linux-kernal- *some numbers* - 16 and 11" I really don't know what to do to fix this. I have tried updating grub using the "restore mode" and tried "xfix." 

I don't want to have to press "esc" every time i turn on my computer to get it to load up properly. Please help.

---

### Post by mechro on 2009-11-21
Having more than one kernel after updates is normal. Use the latest kernel. The others are there if the latest doesn't work. You can uninstall kernels but it's not worth it unless you're short of space or you're meticulous about tidying up.

---

### Post by kammce on 2009-11-21
So what do I do to get my computer to boot up Gnome after the loader finishes?

---

### Post by kammce on 2009-11-21
I might not have explained this properly

If I start up my computer just by pressing the button and allow GRUB to load by itself then Gnome doesn't start up. It a black screen with no cursor.

If I start up my computer by selecting a kernel in GRUB (I have found that it doesn't matter which one old or new), Gnome starts up fine. No issue. Is there a way to get the computer to just load Gnome by itself?

---

### Post by Scott753 on 2009-11-21
I have a similar problem with gnome not booting unless I do it manually. Some other people said it might be a chipset issue, but I don't think that's you're problem. My guess is that it will have to do with your having two kernels, but I don't really have to technical knowledge to help you.

Bump.

---

### Post by kammce on 2009-11-21
Still need help

bump

---

### Post by oldfred on 2009-11-21
I am not sure I totally understand what is different between you choosing a kernel and grub's default. Normally grub boots from the first/newest kernel unless you change settings in menu.lst or use SUM - startup manager to change the settings.

Do you see grub highlighting a menu item different than the one's you manually select?

---

### Post by kammce on 2009-11-21
If I press the power button and allow GRUB run manually, Gnome doesn't start up. It just a blank black screen with out a cursor and I can use my keyboard. All I have really done to test my keyboard out to see if input works is press the "Num Lock" button. And that doesn't work

Now, when I go to GRUB's boot menu and select a kernel it boots fine. I have no idea why.

The menu item highlighted is the one I usually use. The latest kernel. But I have been using the kernel "recovery mode" then I select "xfix" or "resume normal boot" They do the same thing pretty much. Maybe I should prolong the amount of time grub has before it load the kernels... All I need now is the location of the GRUB menu.lst file.

---

### Post by scouser73 on 2009-11-21
For **Kammce**

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by kammce on 2009-11-21
Well before I do this. Can you tell me if this will turn on Gnome at start up with out me having to manually select a kernel to boot. That's my only issue. I don't want to delete the other kernel because Ubuntu leaves it there so I can boot from it if anything happens to the first one. If I can not find any other way to get this issue fixed then I will resort to deleting the older kernel.

Thanks for reply

---

### Post by kammce on 2009-11-21
bump

---

### Post by oldfred on 2009-11-21
I always keep at least 2 kernels but set menu.lst to only show the 2 most recent. I have not figured out how to do that yet for Karmic. I do not think the number of kernels has anything to do with your problem.

I am wondering if this is a grub/boot issue or a graphic card/graphic software issue. 

Are you starting from a cold boot every time you have the problem. Have you tried rebooting so all the hardware is warm and let grub auto boot to see if it is different? The only other thing I might try is to modify the boot stanza in menu.lst to remove the quiet entry so you can see if the boot process shows any errors. You also could check log files in system, administration, log file viewer.

---

### Post by kammce on 2009-11-21
thanks I will try that tomorrow and see what happens. But from memory, I can remember Gnome booting up after a restart but not after a cold boot. I will edit this reply thread if something else comes up.

---

### Post by kammce on 2009-11-22
Just BUMBing this to the front to see if anyone has the same problem.

---

### Post by kammce on 2009-11-22
[SIZE=2]I have fixed the issue. I have found that 9.04 boots up my computer so fast that it doesn't have enough time to warm up. Sounds weird but that is what happened.

I figured out how to fix this issue after doing these steps.

step 1) I found that, if I restart my computer, Gnome fires up fine without issue. My only guess was that because of the fact that my computer was still active, it allowed Gnome to start up.

step 2) To get Gnome to work I had to select which kernel to boot from. This made me take time out to select a kernel. Allowing my computer to warm up and run Gnome.

step 3) The next thing I did to check if the second step was true. I went into "Choose Boot Device" mode on my computer (I have a COMPAQ computer so I pressed the "esc" key), waited 10 seconds then told my computer to boot from the master boot drive (my hard drive). This time I did not select a kernel but let GRUB run freely. Then, out of nowhere, Gnome fires up without an issue.

My main guess is that 9.04's boot is so fast that when my **old** computer gets to the point where it has to run Gnome, Gnome stops responding and stalls out. The fix to this is extremely simple:

All you need to do is increase GRUB's timeout time. I changed it from 3 seconds to 6 seconds.
If you are new to linux, grub, or ubuntu then this tutorial will help to fix this issue. The file you are looking for is: "/boot/grub/menu.lst"
[B]
First enter the directory[/B]
```
cd /boot/grub/
```[B]
Create a back up file just in case something happens[/B]
```
cp menu.lst menu.lst.bak
```
**Now use VI, gedit, kate or any other text editor to edit the file menu.lst. I generally use vi.**
```
vi menu.lst
```[B]
locate a line that says :[/B]
timeout        3
**and change 3 to something higher. I chose 6.**

save and exit from the editor you are in and restart your computer.
If this works then good for you!!!!

 If this doesn't work then increase the amount of time that GRUB waits for. 

If this doesn't work also, then you might have another problem. This might be an update issue. I haven't tried this solution but other have. I suggest this as a last resort because you are required to remove a X.org driver. The link to the tutorial is:

[http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

I hope this helps anyone how has the same issue!!![/SIZE]

---

