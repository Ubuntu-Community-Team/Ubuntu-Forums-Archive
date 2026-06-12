---
title: "Modifying Grub to load Vista by default/change countdown time?"
date: 2009-10-23
forum: General Help
---

### Post by Pott on 2009-10-23
Is there a way to modify the bootloader at all?
I want to take down a few of my boot options, and make Vista the default choice, while changing the time it takes before it auto-boots the first option to 5 seconds. 

Any way..?

Thanks!

---

### Post by donsy on 2009-10-23
Open a terminal window and type:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```
Near the top change the number after "default" to "saved" without the quotes. Also change the "timeout" setting from 10 to 5.

Then scroll down near the bottom until you find the entry for Microsoft Windows Vista and make sure there is a line that reads "savedefault" without the quotes. If it's not there add it. Save the file and exit. Reboot to test it. If you don't like it you can always restore your menu.lst from menu.lst.backup.

Hope this helps.

---

### Post by Pott on 2009-10-23
Hey thanks! I actually did some researched and figured it out. I commented all boots I didn't want (all but two), kept the original order and set the default to 1, booting vista by default after 7 seconds. Should do the trick.

Thanks!

---

### Post by narain4u on 2009-10-29
hi pott...
i need ur help regarding modifying the grub
i changed default 0 to default saved 
but i'm unable to save menu.lst file
it warns me that i have no necessary permission to do that....
what should i do?
plz help me

thanks

---

### Post by Pott on 2009-10-29
I THINK You need to access the file as sudo:

sudo gedit /boot/grub/menu.lst
This line should allow you to save as well. It worked ok for me in Jaunty.

---

### Post by tuahaa on 2009-10-29
> hi pott...
i need ur help regarding modifying the grub
i changed default 0 to default saved 
but i'm unable to save menu.lst file
it warns me that i have no necessary permission to do that....
what should i do?
plz help me

thanks

Try
```
sudo nautilus
``` 
and navigate to /boot/grub/menu.lst inside nautilus and then edit it with gedit. Make sure you have a back up though. This should work as you are editing as root

---

### Post by drs305 on 2009-10-29
For users of Grub (legacy) a painless way of changing the default OS is to use StartUp-Manager - a GUI based menu.lst tweaker. You can change the default OS, timeout, splash image, and lots more. Click on the "SUM" link in my signature line for a guide  to SUM.

To the OP:
*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by narain4u on 2009-10-29
hi 
it worked well.. but i got a new pblm
as my grub menu has two many options i decided to reduce them to two
one is ubuntu 9.04 kernel 2.6.28-16-generic
second one is my vista(loader)
so in menu.lst file i modified all the other options using #
for 16 recovery, 15, 15(recovery), 11, 11(recovery) and other operating systems.
i saved the file and restarted my computer
my grub menu is giving me only two options as i needed...
but when i select ubuntu... it is giving me error 11 unrecognised device string....
i'm totally confused...
i dont know what to do...
plz help me in this regard

i'll be thankfull

---

### Post by drs305 on 2009-10-29
If you post your menu.lst we can probably spot what happened and fix things.

You will probably get more responses by removing the SOLVED tag. Fortunately, the tag in Thread Tools is reversible for the rare times when it sadly becomes necessary.  ;-)

---

### Post by narain4u on 2009-10-29
> **drs305 said:**
> If you post your menu.lst we can probably spot what happened and fix things.

You will probably get more responses by removing the SOLVED tag. Fortunately, the tag in Thread Tools is reversible for the rare times when it sadly becomes necessary.  ;-)

hi...
how can i open/publish menu.lst file here if i'm unable to boot my ubuntu 9.04 kernel 2.6.28-16-generic 

i'll explain u wat i did to my menu.lst file
for e.g
before any changes
title ubuntu 9.04 kernel 2.6.28-16-generic(recovery mode) and its related options

after change:
#title ubuntu 9.04 kernel 2.6.28-16-generic(recovery mode)

by doing this i was able to hide this option from grub menu

i did dis same to all other option except ubuntu 9.04 kernel 2.6.28-16-generic and windows vista (loader)

on restart... i'm getting only 2 options as i needed...
vista is loading
but ubuntu is unable to load becoz of error 11 unrecognised device string..
i might have done anything wrong in menu.lst file...

---

### Post by drs305 on 2009-10-29
During boot, highlight the menu entry for your Ubuntu option and type "e". This should open it for editing. There is probably a problem on one or more of the lines, most likely the kernel and/or initrd lines . 

If you don't see anything, try changing the kernel references from 16 to 15 or whatever you were using before. Make sure you make the change in both the "kernel" and "initrd" lines.

---

### Post by narain4u on 2009-10-29
hi drs305...
i need ur help urgently
plz help me....
wat shud i do?

---

### Post by drs305 on 2009-10-29
narain4u,

Have you tried what I suggested in my last post?

We can help you, but the forums aren't really meant for real-time problem solving. And there are lots of people that can help you.

You might get faster results by joining the Ubuntu IRC support channels. If you aren't sure how to do that, here is a link explaining IRC and two links that discuss two apps which can help you connect to the Ubuntu help channels. If you already have xchat or Pidgin installed, there are also instructions on how to connect.

[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")

[https://help.ubuntu.com/community/XChatHowto]("https://help.ubuntu.com/community/XChatHowto")

[https://help.ubuntu.com/community/Pidgin]("https://help.ubuntu.com/community/Pidgin")

---

### Post by narain4u on 2009-10-29
hi drs...
u r not getting my point...
how can i join irc or pidgin when i'm unable to load ubuntu....
can i join irc when i'm operating in vista

---

### Post by drs305 on 2009-10-29
> **narain4u said:**
> hi drs...
u r not getting my point...
how can i join irc or pidgin when i'm unable to load ubuntu....
can i join irc when i'm operating in vista

Yes. How to connect would be the same even from Windows. Did you try manually editing the Ubuntu selection during the boot process? If you see the grub menu, you should be able to check the entry by highlighting the Ubuntu menu item and pressing "e".

If you don't see the grub menu at boot, press the ESC key as the computer starts to display it.

---

### Post by narain4u on 2009-10-29
yes... i'm getting 2 options
ubuntu 9.04, kernel 2.6.28-16-generic
windows vista (loader)
when i press enter for ubuntu i'm getting error 11 unrecognised device string.. press any key to continue
if i press any key...i'm re directed to the same page where i get 2 options
if i press 'e' to edit before booting
i got 
uuid (some no)
kernel /boot/vmlinuz-2.6.28-16-generic root=uuid=(same above no)
initrd /boot/initrd.img-2.6.28-16-generic
quiet
root

so i changed 16 to 15 in both kernel and initrd.... but in main menu it is not changing to 15 from 16
i might have disabled all other options like 16(recovery), 15 and its recovery 11 and its recovery using '#'  in menu.lst file to hide them from grub menu

what should i do nw?
help me

---

### Post by drs305 on 2009-10-29
> **narain4u said:**
> yes... i'm getting 2 options
ubuntu 9.04, kernel 2.6.28-16-generic
windows vista (loader)
when i press enter for ubuntu i'm getting error 11 unrecognised device string.. press any key to continue
if i press any key...i'm re directed to the same page where i get 2 options
if i press 'e' to edit before booting
i got 
uuid (some no)
kernel /boot/vmlinuz-2.6.28-16-generic root=uuid=(same above no)
initrd /boot/initrd.img-2.6.28-16-generic 
[COLOR="Red"]quiet
root
[/COLOR]
so i changed 16 to 15 in both kernel and initrd.... but in main menu it is not changing to 15 from 16
i might have disabled all other options like 16(recovery), 15 and its recovery 11 and its recovery using '#'  in menu.lst file to hide them from grub menu

what should i do nw?
help me

After getting into the edit mode with "e", try making your menu.lst entry look like this (remove "quiet" and "root"), add "ro"  and then boot. If that doesn't work, remove them again and also try changing "16" to "15".

> 
uuid (some no)
kernel /boot/vmlinuz-2.6.28-[COLOR="DarkRed"]16[/COLOR]-generic root=uuid=(same above no) **ro**
initrd /boot/initrd.img-2.6.28-[COLOR="DarkRed"]16[/COLOR]-generic


---

### Post by narain4u on 2009-10-29
hey thnx drs...
it worked..
ubuntu os is loaded....
now shud i replace all the changes i did earlier.... so that i will not face any pblm again
suggest me what shud i do so that i can have only 2 options one for ubuntu and other for vista without any pblm of this kind?

---

### Post by drs305 on 2009-10-29
> **narain4u said:**
> hey thnx drs...
it worked..
ubuntu os is loaded....
now shud i replace all the changes i did earlier.... so that i will not face any pblm again
suggest me what shud i do so that i can have only 2 options one for ubuntu and other for vista without any pblm of this kind?

:p  Glad you were able to restore your system. Put everything back the way it was and make sure it works. In your case, I suggest installing StartUp-Manager. It is a GUI app that can set up how many kernels you see, the default operating system and more. And you won't have to manually edit menu.lst again.

Here is the link explaining how to install and set up StartUp-Manager:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

or the wiki based on the thread above:
[https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")

---

### Post by narain4u on 2009-10-29
thnx drs...
u are so helpful to me...
i'll immediatly restore everything and i'll install startup manager...

---

