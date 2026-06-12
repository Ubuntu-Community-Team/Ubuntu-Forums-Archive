---
title: "Internet Connection - Need Help"
date: 2006-04-12
forum: General Help
---

### Post by pittpantherfan92 on 2006-04-12
Hello,

I recently installed Ubuntu on my PC.  I have two hard-drives, one that has my XP and all those files, and the other is dedicated fully to Ubuntu.  I installed Ubuntu successfully, but the internet is not working.  I tried to manually configure it, but had no success.  I saw on another forum to run pppoeconf, but that didn't work either.  I am really frustrated because I cannot get online with Ubuntu at all.  Any help would be greatly be appreciated.

Thank you in advance.

---

### Post by mscman on 2006-04-12
Are you using dial-up or broadband?

---

### Post by pittpantherfan92 on 2006-04-12
I'm using broadband.

I'm connected with a router that is on another computer in the house.  So my computer doesn't have a modem.

I'm using a Linksys WRT54G Router.

---

### Post by mscman on 2006-04-12
My next question for you is what type of connection to the network are you trying to make?  Wireless or wired?  Also, what Brand/Model card do you have?  (i.e. Intel ProWireless 2200, Realtek LAN, etc...)  If anyone more experienced than me catches this thread, feel free to jump in at any time!

---

### Post by pittpantherfan92 on 2006-04-13
im connnected wirelessly, im not exactly sure what card im using, it is the one that goes with my router. it came with it.

oh wait here it is.  it says "Wireless-G PCI adapter Model No. WMP54G"

hopefully that helps

---

### Post by mscman on 2006-04-13
Have you tried using the network manager included in Ubuntu?  If you go to System>Administration>Networking and see if your card is showing up in there.  If it is, you shouldn't have too many problems.  Next you'll want to select the card, click on Properties and then check "Enable this connection."  If there is a specific network in range, select it under Network name and enter the corresponding WEP Key if you have one.  On a personal note, my network name is left to any, since in my home only my router is accessible.  Also, unless you want to specify an IP (not recommended unless you know what you're doing), make sure under connection settings to change Configuration to DHCP.  Then click ok to get rid of that window.  Make sure your wireless card is still selected and click "Activate."  After a few seconds, the card should be up, then just click "OK" to close that window.

Let me know if any of the above steps don't seem to work, or if your network card isn't showing up in the Network Settings dialogue.

---

### Post by pittpantherfan92 on 2006-04-13
wow! it works now.

im posting using linux right now!! thank you soo much!!

one more question before you go..
on grub (the bootloader thing) is there a way to make windows xp the default os that loads?

thanks again for all the help

---

### Post by phil66 on 2006-04-13
[QUOTE=pittpantherfan92]wow! it works now.

im posting using linux right now!! thank you soo much!!

one more question before you go..
on grub (the bootloader thing) is there a way to make windows xp the default os that loads?

thanks again for all the help[/QUOTE]

You need to change the default number in /boot/grub/menu.lst

Count the lines down to windows xp the first line will be 0

Open a terminal type"sudo gedit /boot/grub/menu.lst" without the quotes

scroll down until you see default and a number change that number to the one you counted save and you should be ok

---

### Post by mscman on 2006-04-13
[QUOTE=pittpantherfan92]wow! it works now.

im posting using linux right now!! thank you soo much!!

one more question before you go..
on grub (the bootloader thing) is there a way to make windows xp the default os that loads?

thanks again for all the help[/QUOTE]
I'm glad to hear that!  I hope you enjoy Linux as much as I do, and wish you the best of luck!  Let me know if you have any more questions... I'll try my best to help!

---

### Post by rabidphage on 2006-04-13
hope it doesn't f*&^ up again.
I've been through that for weeks

---

