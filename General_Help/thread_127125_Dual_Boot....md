---
title: "Dual Boot..."
date: 2006-02-08
forum: General Help
---

### Post by chopsbuntu on 2006-02-08
I'm in a little bit of rush (need to leave for work in a few minutes), so I'll be quick about it...

What all do I need to do in order to install Ubuntu on my laptop for dual boot? Unfortunately, I need WinXP on there for network and remote desktop purposes, and for Photoshop CS and Dreamweaver.

So, what do I need to do? Do I need two partitions? If so, that may be a problem since I only have one on my laptop at the moment. I do however have 30GB of free space on the drive though.

Thanks in advance! ;)

---

### Post by frodon on 2006-02-08
All is explained here : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The install process will endeed create a partition for ubuntu with the free space you have if you wish.

---

### Post by chopsbuntu on 2006-02-08
[QUOTE=frodon]All is explained here : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The install process will endeed create a partition for ubuntu with the free space you have if you wish.[/QUOTE]

Thanks frodon!

That's looks simple enough. Very simple to be exact. :mrgreen: 

I wonder is I'll have any problems getting my Proxim wifi card to work. Hmm... :-k

---

### Post by cotcot on 2006-02-08
Have a look to GIMPshop (unless you are addicted to CMYG colors). It is Gimp with customised templates in order to facilitate Photoshop user to switch to Gimp.

---

### Post by chopsbuntu on 2006-02-08
[QUOTE=cotcot]Have a look to GIMPshop (unless you are addicted to CMYG colors). It is Gimp with customised templates in order to facilitate Photoshop user to switch to Gimp.[/QUOTE]

GIMPshop? Is that something different from GIMP? Just curious.

Like I said earlier, I still need Dreamweaver too. I don't know how well those Windows emulators for Linux are, so I don't know if I'd be able to completely go away from MS or not.

---

### Post by chopsbuntu on 2006-02-08
BTW, is installing and doing a dual boot with Kunbutu the same as with Unbuntu? I think I'm going to try installing Kunbuntu on the laptop right from the beginning just for the heck of it. I already have it DL'ed.

---

### Post by chopsbuntu on 2006-02-08
[QUOTE=chopsbuntu]BTW, is installing and doing a dual boot with Kunbutu the same as with Unbuntu? I think I'm going to try installing Kunbuntu on the laptop right from the beginning just for the heck of it. I already have it DL'ed.[/QUOTE]

I just answered my own question. LOL :mrgreen:

---

### Post by chopsbuntu on 2006-02-08
Alright, I have Kubuntu installed on my laptop, but durring the installation, it didn't detect the network hardware, neither the built-in LAN or wifi card. 

So what can I do now to get both to work?

My laptop is an HP Pavilion ze4600 series.

Thanks. ;)

---

### Post by chopsbuntu on 2006-02-09
HELLOOO!!! I NEED SOME HELP HERE!!!

I uninstalled Kubuntu and installed Ubuntu because the other one was messing up.

Anyway, why in the world are both the wifi and CAT5 connections working (both are sending and receiving packets) but everytime I try to go online with the browser, it keeps coming up saying...

"www.website.com could not be found. Please check the name and try again."

None of this makes sense! If both network connections are sending and reveiving packets, then I should be able to go online.

What gives?!?!

---

### Post by chopsbuntu on 2006-02-09
BTW, I can even log into my router via wifi, but it will NOT let me go on the internet. :evil:

---

### Post by nanotube on 2006-02-09
hmm. try opening up a terminal and do "nslookup www.google.com" or something, and see if it comes up with an ip address.
if it does not, then try accessing google directly by ip (216.239.37.99) and seeing if that works.
basically, try narrowing down the problem to see if its just dns-related.

---

### Post by cotcot on 2006-02-09
GIMPShop is GIMP. Only the interface (icons and menus) are changed to look like Photoshop.
For your internet connection : hope you have checked that your network card is activated (>system>administration>network).

---

### Post by chopsbuntu on 2006-02-09
What has it been, about 12 hours now? And after all this time, the only thing I had to do was remove my name from the "Host" window in the network settings and now the wifi works flawlessly. \\:D/ 

What a major pain in the you know what. LOL 

BTW, I need to know where I can download that Automatix again. The link that **beerorkid** provided doesn't work anymore.

> sudo apt-get install xterm

wget [http://beerorkid.com/automatix/automatix_5.3-3_i386.deb](http://beerorkid.com/automatix/automatix_5.3-3_i386.deb)

sudo dpkg -i automatix_5.3-3_i386.deb

---

### Post by cjazz on 2006-02-10
Chopsbuntu,

The current address for Automatix is

[http://beerorkid.com/automatix/automatix_5.4-1_i386.deb](http://beerorkid.com/automatix/automatix_5.4-1_i386.deb)

---

### Post by chopsbuntu on 2006-02-10
[QUOTE=cjazz]Chopsbuntu,

The current address for Automatix is

[http://beerorkid.com/automatix/automatix_5.4-1_i386.deb](http://beerorkid.com/automatix/automatix_5.4-1_i386.deb)[/QUOTE]

Great! Thanks cjazz! ;)

---

### Post by nanotube on 2006-02-10
hey
you might want to try [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) instead of automatix... it gives you greater choice of what you want to install, and does not mess with your system so much. 
fwiw...

---

### Post by chopsbuntu on 2006-02-10
[QUOTE=nanotube]hey
you might want to try [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) instead of automatix... it gives you greater choice of what you want to install, and does not mess with your system so much. 
fwiw...[/QUOTE]

Thanks **nanotube**. 

After downloading that program, how do I go about installing it? 

Sorry, I'm still a "linux" nOObie! LOL :mrgreen:

---

### Post by nanotube on 2006-02-11
extract everything from the tar.gz archive into some directory, and then doubleclick on easyubuntu.desktop... or if that doesnt work, open up a terminal, cd to the dir where you have it extracted, and type  
"gksu ./easyubuntu.py"
(without the quotes).

---

### Post by chopsbuntu on 2006-02-12
[QUOTE=nanotube]extract everything from the tar.gz archive into some directory, and then doubleclick on easyubuntu.desktop... or if that doesnt work, open up a terminal, cd to the dir where you have it extracted, and type  
"gksu ./easyubuntu.py"
(without the quotes).[/QUOTE]

Well that doesn't work. Every time I enter my password, it says that it failed and that it is the wrong password.

It's NOT the wrong password because it's the ONLY password on my computer. :mad:

---

