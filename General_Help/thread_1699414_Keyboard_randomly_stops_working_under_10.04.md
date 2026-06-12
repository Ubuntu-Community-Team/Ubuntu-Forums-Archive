---
title: "Keyboard randomly stops working under 10.04"
date: 2011-03-03
forum: General Help
---

### Post by frabailies on 2011-03-03
I'm using Ubuntu 10.04 since several months and I randomly have problems with the keyboard (PS2). Maybe 2-4 times per week the keyboard stops working all in a sudden. The symptoms related to this can be
- the keyboard simply does not react any more to key press
- during typing the keyboard gets crazy and fills the lines with the last typed character
- opened windows move to the left when touching them at the top bar, keyboard does not react any more. When clicking on a panel menu the focus line is running permanently quickly through all items, and it's practically impossible to click on any of those (so even shutdown is difficult to achieve, and I might need to use a hard reset).

In nearly all cases the problem only disappears after reboot, just very rarely a logout is sufficient to get the keyboard working again. 

I googled for similar problems and found quite some people having problems with keyboard (and/or mouse) not working correctly under Ubuntu, but I have not stumbled over a similar error description as I have. Just some config parameters on my box: amd64, XOrg uses an Nvidia driver, 3D and Compiz are activated.

Any ideas what could solve this annoying problem?

---

### Post by linuxrev on 2011-04-27
My keyboard gets annoyed when the batteries are low. Maybe yours as well?

---

### Post by frabailies on 2011-04-27
there are no batteries in a desktop... the problem remains. Deactivating Compiz or using XFCE had no effect as well. Maybe I should go back to Windows ;-) at least these stupid types of errors did never appear there...

---

### Post by paul_will on 2011-04-28
Sounds like something has got stuck inside your keyboard (key repeating). Have you tried other keyboards esp a usb one? Have you tried this keyboard on another computer? Even with a ps2 keyboard you can often unplug and replug it to revive. If you are careful you can take it apart and check or wash with water the contact sheet inside. The other weak point more typical with a mouse is a broken wire just at the point of entry into the body. These hardware suggestions will affect every OS in a similar way, but key repeating can be controlled by either software or the bios.

---

### Post by frabailies on 2011-04-28
The keyboard worked fine on the same PC for several years - until I installed Ubuntu... It is for sure not a key that gets stuck, it happens arbitrarily with +/- any type of key pressed. It's not always that the last pressed key gets printed continuously, sometimes the keyboard just does not react any more to inputs. It also can affect the menus like the "Application" menu with the focus bar scrolling through all items.

And I don't think it's related to other hardware problems like cables, etc. A after a reboot the error always disappears. I have not tried yet a USB keyboard since I have none available. Also the error does not occur everyday, but sometimes 2 times per day.... So I need to test it for several days. 

I could try upgrading to a new Ubuntu, but I'd prefer to stick to a LTS release since I do not want to upgrade every 6 months, or have 3 consecutive upgrades every 2 years.

---

### Post by guedesav on 2012-09-27
Ok, I'm reviving this thread because I have exactly the same problem with my Ubuntu. Long story:

I've first noticed this problem while playing Minecraft. Thinking this was exclusively a Minecraft issue(usuall the W key would be stuck) I searched their forums and tried some solution. None worked.

Next I tried dealing with Compiz. "Bounce Keyboard" was turned off by default(it was one common suggestion) but nothing worked.

I decided to try upgrading my Ubuntu from 10.10 to 12.04. The problem continued. I stopped playing Minecraft on Linux for good. =/

And then a few minutes ago it happend again, no Minecraft. I can't really say what's happening underneath, I haven't taken any logs. xev shows me nothing, lswh and lsmod don't really show anything that's obvious.

Mouse works, Wacom tablet still works, I can even use the virtual accessibility keyboard to type, but the actual keyboard won't work. If I had Bluetooth, I could confirm if another keyboard works, too. Disconnecting and reconnecting it doesn't work, though.

So, the problem remains: I have a keyboard(PS2, not USB) that works perfectly fine on Windows 7 but randomly either sticks or simply stops working in Ubuntu. Not even the Lock keys work

---

### Post by guedesav on 2012-10-06
I'm bumping this topic becasue it happened again. TWICE. First it happened when I was using Gimp(stuck with letter Z) and then when I was writing a reply here it happened again. The keyboard simply stopped responding, and I can't find a solution. I'll keep bumping this topic until some conclusive asnwer is given because this is the most stupid bug I've ever seen in an OS.

Seriously.

---

### Post by guedesav on 2012-10-07
Hello, this is me again bumping this topic because, guess what? It happened again about now. I was editing a file in gEdit and my keyboard locked. How marvelous.

I'm definitely not the only person with this problem, so does anyone have a solution? ANYONE?!

---

### Post by guedesav on 2012-10-09
Bump. Same as usual. Playing Dwarf Fortress this time.

---

### Post by pqwoerituytrueiwoq on 2012-10-09
honestly i am surprised this is not locked for thread necromancy 
that said 
1. wireless or hardwire
2. PS/2 or USB
3. if usb output of [FONT=Courier New]lsusb[/FONT]
4. does it happen with a different keyboard using the same plug?

---

### Post by guedesav on 2012-10-10
Well, thanks. So, answering your queries: it's a PS/2 wired keyboard. Didn't have the opportunity to test another keyboard in this PC,but considering it is working perfectly well in Windows 7 in the same machine, I doubt it's a problem with the keyboard.

---

### Post by pqwoerituytrueiwoq on 2012-10-10
purpose for other keyboard was to see if the os hates the motherboard's controller or the keyboard itself
what is the keyboard's model

---

### Post by guedesav on 2012-10-10
It's a 104(?)-key keyboard so generic I don't even remember the brand. I'll get back to you when I'm home again.

I'll have to try and get a free PS/2 keyboard for testing. The only other one I have at home stopped working a year or so ago. The best I can try now is try using an USB/Bluetooth keyboard I have around. I'll let you know how it goes when the next freeze happens.

---

### Post by guedesav on 2012-10-16
Ok, so long time without any news because the weirdest thing happened. I did find an old functioning keyboard here, and after I tested it I spent the last 6 days without having keyboard glitches again. Even playing Dwarf Fortress and using keyboard normally. I was ecstatic.

And then it happened again. While playing Minecraft. No, the other keyboard didn't work either. And before anyone suggests: using Ctrl+Alt+F1 to switch to terminal and back doesn't work because a) no key works when this happens; and b) if I use the OnScreen keyboard to press that combination, I effectively lock myself out of my own graphical session.

And btw, this keyboard isn't even listed in lshw, but apparently is a 104-key Mtek keyboard(model K291-something, someone put a sticker over the number)

Any other suggestions?

---

### Post by wbrgmnn on 2012-12-02
I've been following the thread and thought I'd weigh in here.  I've had the same problem of the keyboard dropping out for no reason for some time.  First under Kubuntu 10.04 LTS and now under Kubuntu 12.04 LTS.

I have 4 computers connected through a KVM switch using ps2 connections for the mouse and keyboard.  When I lose the keyboard, I can switch the KVM to another machine and it works just fine, so it's not the keyboard.  If I just log off and back in, the keyboard still doesn't work - I have to re-boot.  The virtual keyboard does work, though.

When the keyboard is inop, I can plug in a USB keyboard and that works, but nothing seems to bring the keyboard back.

So, it's not the keyboard and it's not the GUI.  However, it usually seems to happen when I'm filling out a form in my browser (Firefox).

Could it be that HTML forms are passing something to HAL or the OS that adversely affects keyboard input from the existing keyboard?

---

### Post by ncornelisse3@hotmail.com on 2012-12-05
I've the same problem (locked keyboard) with a wired USB keyboard on 10.04 Desktop.

---

### Post by carvis on 2013-01-20
Same behavior observed here, adding my experience so I'll be updated if this turns out to have a fix:
Keyboard (kensington model K64365) randomly drops out, most often while gaming (Dungeon Defender most recently), but not always.
USB through a KVM.
Switch to another machine and the keyboard comes right back up, but switching over to the Ubuntu (12.10) machine and it's still dead or back to intermittent.

I'm making plans to disassemble and clean the kbd since it has been a while, so a stuck key isn't out of the question.

---

### Post by guedesav on 2013-02-16
Venting mode on...

This is still happening. I've reinstalled the system to use the newest nVidia drivers, so now it's 64bits. Even with a new system I still have this problem where my PS/2 keyboard simply sticks a key and then I have to open up a virtual keyboard to make the key go unstuck, but that means my keyboard won't work until I restart the system.

Which leads me to scream at my computer wondering how the **** can an OS in goddamn 2013 still screw up a goddamn KEYBOARD?!

And this problem isn't even new, I see bug reports and forum threads from years ago complaining about this, and yet there's no clue of a solution. What the hell happened to Ubuntu to get so goddan fickle and fragile to the point where IT CAN'T HANDLE A GODDAMN KEYBOARD.

Venting mode out, the only solution I have is to sleep the system and turn it back on. And pray I wasn't doing anything too important, because even that won't always work. Again, Ubuntu has got so complicated sometimes my mouse can't click right.

Holy crap.

---

