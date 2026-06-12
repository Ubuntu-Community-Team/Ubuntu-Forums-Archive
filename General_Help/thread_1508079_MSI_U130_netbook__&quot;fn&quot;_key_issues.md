---
title: "MSI U130 netbook  &quot;fn&quot; key issues"
date: 2010-06-12
forum: General Help
---

### Post by sea_coffee_programmer on 2010-06-12
I am new to ubuntu, and am working to embrace and undersand this for my programming.  My first hurdle is my "fn" key.  the key itself works to turn up and down volume, but when i want to use wireless internet, i need to turn on the wireless adapter.  The quick key to accomplish this is "fn" + f11.

Nothing happens and the wireless card will NOT turn on, so i cant access anything wireless.  Right now i have an ethernet cable running to my netbook to accomplish this.

I looked in keybindings, and there isnt a key in there to turn or of the wireless, so it just stays disconnected/disabled.

---

### Post by sea_coffee_programmer on 2010-06-12
I was looking at my netbooks information from the following command

lspci -v | less

and i found my wireless card:

Network Controller: RaLink RT3090 Wireless 802.11n IT/IR PCIe
Subsystem: Micro-Star International Co., Lrd. Device 6891
Flags: bus master, fast devsel, latency0, IRQ 16
Memory at fe900000 (32-bit nopn-prefechable) [size = 64k]
Capabilities: <acces denied>
Kernel driver in use : rt3090
Kernel modules: rt3090sta

Is there a way to enable this wireless card so it can pick up networks?  I cant seem to find it and there also isnt a hotkey.  Sort of confuses me.

---

### Post by DrMelon on 2010-06-12
I have a laptop which handles the Wireless card's function in this way as well. However, it defaults to being on all the time, even when the LED indicator on the laptop tells me it is off. 

It's possible it is already on, just not turned ready for usage.
Try this in a terminal:

> sudo ifconfig wlan0 up
Replacing wlan0 with other device names, such as wifi0, eth1 (presuming eth0 would be your ethernet port) or ath0.

---

### Post by sea_coffee_programmer on 2010-06-12
Dr. Melon, I typed what you told me
> sudo ifconfig wlan0 upand it said:
> SI0CSIFFLAGS: Operation not permittedLet me test your other ones...

...wifi0 gives an error > ERROR while getting interface flags: No such deviceSame error for all of the other you pointed out.

---

### Post by migsey on 2010-06-26
I have the exact same problem. i have an MSI U210 netbook with the same problem. It also has
the same RT3090 hardware installed, and is coming up as dissabled. I realy would like to use Ubuntu. I think its a great great thing you guys have put together. But if it doesn't work with peoples hardware, then W.T.F?? I dont want to be a programmer. i just want my PC to work.
*haha* what do I do now.
Help Please.

---

### Post by sea_coffee_programmer on 2010-06-26
Well, i managed to figure everything out.  I had to go into terminal and do some tinkering before i could get wireless to work for me.  I will make a post later when i get home from work  (around 1030pm EST) on what i did, and it should help you out.  The only downside is that i need to still go into the terminal and figure stuff out because i am unable to connect to certain wireless things which require certs but i dont think that is something you would really need to worry about.  :)

Later tonight i will tell you what to do, but you will need to plug your computer into the network with your handy cat-5 E cable and get an internet connection that way and we can start downloading DEB files and everything else to make your machine work correctly.

---

### Post by kloparto on 2010-07-06
So, sea_coffee, what have you done to make it work? I have been days with this problem.

---

