---
title: "slow start up and loss of wireless"
date: 2011-07-06
forum: General Help
---

### Post by u4ric on 2011-07-06
Hello

I switched to Ubuntu from Windows a few months ago and have had it all working fine since.

I turned on my system today and did some updates, then restarted but after the boot selection screen which I cant use as I have a USB keyboard the screen went to that purple/pink colour and froze for ages. Eventually my desktop appeared so I tried restarting it again and the same thing happened. Before from the boot selection to my desktop would only take 5 seconds or so but now it takes about 3 minutes.

Also since the updates I can't connect to my wireless network. I was using the Windows Wireless Networks software from the Ubuntu Software Centre, now when I try opening it manually it just hangs. I tried removing it and reinstalling it but still no joy.

I'm sorry to say that I may have been too trusting with the updates so didn't read the list, I just updated and restarted and thats when the problems started.

I'm not quite sure what information you need but here are the bits from the System Monitor:
Release 11.04(natty)
Kernel Linux 2.6.38-8-generic
GNOME 2.32.1

On windows I would have considered myself an intermediate user but since switching to Ubuntu I feel like a beginner again although im learning fast.

Any help would be very much appreciated and thank you for your time.

---

### Post by u4ric on 2011-07-06
Ok upon further investigation I believe that the Windows Wireless Networks software fault is the reason I can't connect to a wireless connection. Some thing in the update has caused it not to function. I tried the "ndiswrapper -l" command in the terminal and that just hangs too.

So does anyone know how I can find the cause of the fault or if not does anyone know of an alternative method to get my windows wireless driver working?

I was also thinking that the Windows Wireless Networks Software usually starts itself when I get into Ubuntu so maybe the reason its hanging is because of the fault with the software.

I'm really just guessing here though.

---

### Post by u4ric on 2011-07-06
Just a couple of corrections. The software I believe to be at fault is Windows Wireless Drivers (not Networks) and maybe this thread would be better in the network section, I don't know how to move it.

---

### Post by u4ric on 2011-07-06
Sorry for the multiple posts but i'm just desprate to get this fixed and trying to provide as much information as I can.

So after doing some research I found that the Windows Wireless Drivers software uses some thing called NDISWrapper. I'm guessing the software is a GUI for what ever NDISWrapper is. Like I said, I don't get any error message, it just hangs so i'm not too sure if the Windows Wireless Drivers software is the fault or NDISWrapper, but if it is the software then maybe if I setup NDISWrapper manually it may work. I've searched online on how to do this but not found any thing I understand. Can anyone help me with this or at least point me in the right direction to a beginners guide?

Thanks

---

