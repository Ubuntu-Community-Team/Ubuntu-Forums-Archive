---
title: "Toshiba Satellite L775D Keyboard and Sleep Issue  - 12.04"
date: 2012-06-11
forum: General Help
---

### Post by 2defmouze on 2012-06-11
Hi all... New to the community and Ubuntu here. I've recently set up dual boot for Windows 7 and Ubuntu 12.04 (64bit) on my Toshiba Satellite L775D laptop. While almost everything is working fine I have 2 nagging issues I'm hoping someone can help with:

Issue 1: Somewhere around 50% of the time I boot into Ubuntu, the keyboard does not work at all. Seems as if the driver just does not load maybe (?). Cannot login or anything and have to just reboot and hope it works the next time, which again is like a 50/50 gamble (And yes I know I could login using the on screen keyboard, but even afterwards there is no way to really keep using the laptop with only that working).

Issue 2: If I close the laptop lid the system sleeps and is completely unwakeable. I'll have to do a battery pull, and pressing Power after will not even boot up anything.. one light will come on the front but No screen, boot menu, anything. I have to hold F8 and power a couple times to force boot the laptop into recovery, then leave it without recovering/formatting anything, and it will go back to working fine. As you can imagine it scared the heck out of me first time as I thought I completely corrupted the computer, lol.

Hoping someone can help with suggestions to correct these issues. Let me know if any more info is needed. As said, I'm pretty new to Ubuntu and linux in general, but am a quick learner. Thanks in advance! :)

---

### Post by 2defmouze on 2012-06-12
Hey guys just wanted to bump this one time if that's alright, hope I've posted it in the right section and nobody minds a bump, just really need some help with these two issues.

For the Keyboard working only on some boots problem.. I have tried what sounded like a good solution involving a simple grub edit, posted here: [http://ubuntuforums.org/showpost.php?p=11928459&postcount=42](http://ubuntuforums.org/showpost.php?p=11928459&postcount=42)
However the results are still inconsistent. Entering the command manually seemed to work better than saving it as a permanent grub edit (second half of the post)... and when it was saved I actually found the keyboard working only if I edited it out during boot, so its hard to really say if it had any effect.

Thanks again, and again, my bad if I'm not posting in the right area for these issues, please let me know so I can correct myself going forward.

---

### Post by Ghostmn on 2012-06-12
I've read both of your posts and while I don't have an immediate solution to your problem, I'll look into it. Give me 24 hours to find a solution, if i don't find anything i apologize.

For less headaches in the future, I would recommend not buying toshiba laptops. The amount of driver issues since 8.04, hasn't entirely improved.

---

### Post by 2defmouze on 2012-06-12
> **Ghostmn said:**
> I've read both of your posts and while I don't have an immediate solution to your problem, I'll look into it. Give me 24 hours to find a solution, if i don't find anything i apologize.

For less headaches in the future, I would recommend not buying toshiba laptops. The amount of driver issues since 8.04, hasn't entirely improved.

Gotcha, and thanks I very much appreciate you checking into it!
Wasn't planning on running anything but Windows when I was shopping for it unfortunately, lol, but it's definitely something I'll keep in mind going forward.
Thanks again! :)

---

### Post by Ghostmn on 2012-06-12
Does your touchpad work?

If you have a usb keyboard, and or usb mouse, can you please tell me if they work?

---

### Post by Ghostmn on 2012-06-12
While looking into your problem, I found documentation on the Arch Wiki. Both of your problems are listed, so please refer to it.

[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340)

---

### Post by 2defmouze on 2012-06-12
> **Ghostmn said:**
> Does your touchpad work?

If you have a usb keyboard, and or usb mouse, can you please tell me if they work?
When the keyboard does not work, no the touchpad will not either.. and unfortunately no I don't have a usb keyboard to test. My usb mouse works just fine all the time though.

> **Ghostmn said:**
> While looking into your problem, I found documentation on the Arch Wiki. Both of your problems are listed, so please refer to it.

[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340)

Sounds like both might be able to help! However, I'm still noobish at these things.. and figuring out how to try those corrections using terminal is taking longer than I'd like, lol.

I don't suppose you'd mind spelling it out in noobie terminal commands for me? Working on building my knowledge of this stuff :)

EDIT: Well for the first edit, I do not see the file "menu.lst" at /boot/grub.. perhaps it is named differently in this system version? For the 2nd I'm just not sure how to create the requested file ..

---

### Post by 2defmouze on 2012-06-12
Well, I was able to complete the suggestion for the Sleep/Hibernation issue, but still to no avail. Hibernation on its own requires a hard power off to wake up from, and closing the laptop lid still requires a battery pull and force-boot to even get to the bios. I'm pretty positive I created the file correctly, and changed permissions correctly, so not sure what else it could be.

The Keyboard fix I'm not sure how to apply as the file, menu.lst, does not exist in the directory pointed to in the link you provided. If you could suggest anything I'd appreciate it.

Anything else you can find I'd be willing to try.. doing some research on my own as well, of course. Thanks again for your assistance!

---

### Post by Ghostmn on 2012-06-13
I'm disappointed in hearing that that the arch wiki documentation didn't work.

I'll keep looking as well. I suggest finding out whether menu.lst exists anywhere in ubuntu, or if it was renamed to something else.

---

### Post by ADDpillz on 2012-06-25
Hello,
I have the exact same computer (Toshiba L775D) and I am running Zorin 6 Linux.

I am having the exact same problems that you have described.  I have plugged in a USB mouse and a USB Keyboard and both seem to work when the Toshiba keyboard or the touch pad are unresponsive. 

I also can get it to work correctly 50% of the time after a hard shut down and reboot.

This may just be a coincidence, but as the linux is booting up I continually will run my finger over the touch pad while also pressing a random key on my keyboard and it seems to work...  

I Think it is either a Toshiba driver issue or it is an issue where the keyboard and touchpad hardware will periodically go into some sort of sleep mode.

---

### Post by Noggin on 2012-07-02
I also have an L775D and having the same issues with Ubuntu 12.04.  I noticed one of the posts above has a link to a Wiki that may have some helpful suggestions.  I'll try to run through them tonight and see if anything helps.  If I do go through them, I'll post my results here.

As far as the keyboard and mouse not working on start-up, In the last hour or so, every time I've rebooted the mouse and keyboard haven't worked.  Every time I've shut down and booted, the mouse and keyboard have worked.

**Edit:**  Good news in that the suspend fix works.  It isn't perfect, but it is now usable.  The only issue I've noticed so far after testing for 30 seconds is that if I select "Suspend" from the menu, the screen flickers and it goes into suspend.  It then wakes up a few seconds later.  However, if I close my lid, it appears to sleep properly until I open the lid.  

Here's noobie code, written for a noobie, by a noobie...

Open a terminal window and type the following commands
1. cd /etc/pm/sleep.d
2. sudo gedit 20_custom-ehci_hcd
3. if asked for password, enter it
4. Copy the text from [here](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340#Hibernate.2FSuspend) and paste it into the gedit window
5. Click the gedit Save button
6. Close gedit
7. sudo chmod 755 20_custom-ehci_hcd

You shouldn't be asked for your password here

**Edit 2:** Still no luck with the keyboard/mouse.  I think the menu.lst has been replaced by grub.cfg in the recent versions of grub, but I can't find the appropriate line in there to edit.

**Edit 3:** I've confirmed that grub.cfg has replaced menu.lst.  Also, I may have found the solution for the keyboard/mouse issue [here](https://bugs.launchpad.net/ubuntu/+bug/1014240).  I'm dual booting Ubuntu 12.04 with Windows 7 and I used Grub Customizer to set up my booting options.  I *think* these were the commands I used to install it:

1. sudo add-apt-repository ppa:danielrichter2007/grub-customizer
2. sudo apt-get update
3. sudo apt-get install grub-customizer

Once it is installed, run it.  It'll take a few seconds to load.  Once loaded, click the "Preferences" button.  You should see a text box labeled, "Kernel options."  Add "i8042.reset i8042.nomux" to it then save it.

Lastly, Fn F9 toggles the keyboard and mouse on and off.  Clicking that sometimes fixes it, but I THINK it only fixes it if it booted "properly" but was already disabled.  Take this with a grain of salt please.

---

### Post by 2defmouze on 2012-07-10
> **Noggin said:**
> I also have an L775D and having the same issues with Ubuntu 12.04.  I noticed one of the posts above has a link to a Wiki that may have some helpful suggestions.  I'll try to run through them tonight and see if anything helps.  If I do go through them, I'll post my results here.

As far as the keyboard and mouse not working on start-up, In the last hour or so, every time I've rebooted the mouse and keyboard haven't worked.  Every time I've shut down and booted, the mouse and keyboard have worked.

**Edit:**  Good news in that the suspend fix works.  It isn't perfect, but it is now usable.  The only issue I've noticed so far after testing for 30 seconds is that if I select "Suspend" from the menu, the screen flickers and it goes into suspend.  It then wakes up a few seconds later.  However, if I close my lid, it appears to sleep properly until I open the lid.  

Here's noobie code, written for a noobie, by a noobie...

Open a terminal window and type the following commands
1. cd /etc/pm/sleep.d
2. sudo gedit 20_custom-ehci_hcd
3. if asked for password, enter it
4. Copy the text from [here]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340#Hibernate.2FSuspend") and paste it into the gedit window
5. Click the gedit Save button
6. Close gedit
7. sudo chmod 755 20_custom-ehci_hcd

You shouldn't be asked for your password here

**Edit 2:** Still no luck with the keyboard/mouse.  I think the menu.lst has been replaced by grub.cfg in the recent versions of grub, but I can't find the appropriate line in there to edit.

**Edit 3:** I've confirmed that grub.cfg has replaced menu.lst.  Also, I may have found the solution for the keyboard/mouse issue [here]("https://bugs.launchpad.net/ubuntu/+bug/1014240").  I'm dual booting Ubuntu 12.04 with Windows 7 and I used Grub Customizer to set up my booting options.  I *think* these were the commands I used to install it:

1. sudo add-apt-repository ppa:danielrichter2007/grub-customizer
2. sudo apt-get update
3. sudo apt-get install grub-customizer

Once it is installed, run it.  It'll take a few seconds to load.  Once loaded, click the "Preferences" button.  You should see a text box labeled, "Kernel options."  Add "i8042.reset i8042.nomux" to it then save it.

Lastly, Fn F9 toggles the keyboard and mouse on and off.  Clicking that sometimes fixes it, but I THINK it only fixes it if it booted "properly" but was already disabled.  Take this with a grain of salt please.

Dude.. I believe the keyboard fix seems like it worked! Applied using the onscreen keyboard and rebooted.. so far just one time but its working, crossing my fingers that it sticks, lol. Thank you a ton for that!

Will try out the sleep fix later on... been wicked busy the last 2 weeks and haven't had any time to work on these issues, great to see the community coming through though, thanks again! :)

---

### Post by taihlo on 2012-07-20
I have had the keyboard issue a few times after installing 12.04 LTS AMD64 on my new Toshiba L775D/S7340B. But when trying to attempt sleep (or hibernate actually) the machine will no longer seem to boot.  If I do get it up in recovery, it seems to be fine, but then will not boot into the GUI at all.  After having it working so well after the first reboot into the new system, it's amazing to me that I can't seem to get it to work at all since.  Anyone have any advice? or should I just start over? only 5 hours into it so far and I really really want to keep my Windows free streak going...

---

### Post by Jakin on 2012-10-06
Sorry to resurrect this topic, but it is relevant;

I purchased a new Toshiba Satellite L875D, and i have Ubuntu 12.04.1 installed.

I have never messed with kernal options before, i never had any need- obviously im experiencing the same keyboard issues as everyone has described, and sleep, which by the way- Thanks Noggin, that fixes the SLEEP issue i had :)

I want to give the keyboard fix a try, however the current version of Grub Customizer is different. (by which i mean there is no "preferences")

Here is what i have- I just want to make sure it looks right before applying and then well- problem is made worse..

"quiet splash" was already there when i brought it up to add "i8042.reset i8042.nomux".

---

### Post by twilmore on 2013-01-04
> **Ghostmn said:**
> While looking into your problem, I found documentation on the Arch Wiki. Both of your problems are listed, so please refer to it.

[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340)

Where is menu.lst located in Ubuntu 12.04.1? The document you list above says that it is in /boot/grub, but it is not there on my system. I have duel boot 12.04.1/Win 7.

---

### Post by bigmoneyhat on 2013-05-20
Hey all,

I was having the same problem as well earlier, and just used the fix from the arch wiki on the /etc/default/grub file and put the arguments at the end of the GRUB_CMDLINE_LINUX_DEFAULT="..." line.

It hasn't happened to me since, so I hope this helps y'all out.

---

### Post by tnsilver on 2014-01-09
It's 2014 now, and I installed Kubuntu 13.10 on my Toshiba Satelite A665-145 laptop (It's the same A665 but with an I7 processor). Guess what? No keyboard backlit issue all over again. I sometimes teach students using a big screen TV or a projector and I need the keyboard backlight because my class room is usually too dark for my comfort (students have a better screen view in a dim lit class room).

I've decided to turn ACPI off and review the consequences. It's easy to turn off ACPI. You can do it temporarly at the grub boot menu (you can force it to show by using the shift key after the boot splash) or you can update grub for a permanent configuration. See how to do it [here]("http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-bootinghttp://")

The **good news** is the keyboard lights up and so is everything else. You can dim the screen, use the other nifty functions and it's all right now.
The **bad news** is that if you hook up a monitor using an HDMI cable, you cannot view your laptop's LED screen at the same time. 
You can choose which is the default screen in the advanced system properties in the BIOS (v1.8) menu but you can't have both. 
All other stuff seems to work.

Tom

---

### Post by cwoolf63 on 2014-05-06
I've been having the same problems even with ubuntu 14.04 install, the hibernate problem can be fixed thru the power setting simply set it to "do nothing" when lid is closed, so when the lid is closed the screen will shut off automatic and when opened will come right back on. now the keyboard issue was solved/working fine with 14.04 but recent update keyboard did not work..... But I found that during reboot hitting the space bar a couple times will keep it working. hope this helps

---

### Post by squakie on 2014-05-06
But that isnt a hibernate - hibernate is when it swaps everything out to the swap file and powers off.  Upon power on it restores from swap and continues.  The method you describe does nothing more than turn off the screen - the system is still running and will use up the battery - that is unless something has greatly changed.

The OP wa asking about standby, which is what you are talking about - the power is still on, nothing swapped (any more than normal).

---

