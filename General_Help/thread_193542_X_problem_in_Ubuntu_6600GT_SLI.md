---
title: "X problem in Ubuntu 6600GT SLI"
date: 2006-06-10
forum: General Help
---

### Post by Namgyel on 2006-06-10
After running my Win XP for sometime now I decided I need to instal something more reliable on my computer - chose Linux of course :rolleyes:. Now that I finally got around to installing Linux (Ubuntu 6.06 64-bit) I'm having a really strange issue with X.

Whenever I boot into linux, I see the Ubuntu splash and the list of checks that the system goes through as it is booting. However, once that is done and I see a dash in the upper left hand corner flash a few times, then it stays solid. I am pretty sure at this point X has fully loaded, and is just showing on my screen what was shown last (the dash). The reason I've come to this conclusion is because I can hear all the sounds comming from various things that I do. If I just hit enter, I hear an error-esque sound. However, if I blindly enter my login, hit tab, then type in my password, I hear a very pleasant sound, which I'm guessing is the shell loading up.

Now, I can go into terminals 1-6 with no problem and work various commands, but if I try to enter terminal 7, I basically have the same problem as in the beginning and just see what was last on the screen. 

This also does with Ubuntu 5.10 .... I tried installing 6.06 with server install and then used this command:

```
sudo apt-get install ubuntu-desktop
```

Because the live cd install does the black out already on the beggining... 


Here are the basic specs of my machine:


Biostar N4SLI-A9-A01
2 x MSI 6600GT video cards
AMD 3200+ socket 939 proccy

Any help would be very appreciated:confused: 



PS: I'm still a begginer so I don't know a lot more then atp-get:p

---

### Post by Namgyel on 2006-06-10
Forgot to write - would be helpful if anyone has seen the answer and just writes where it was if he doesn't know it.:-({|=

---

### Post by mejy on 2006-06-10
First, try plugging you monitor into the other graphics card - only one will work under Linux (since SLi is unsupported apart from with the latest official nVidia drivers, and its a bother even then) and you may have you monitor plugged into the secondary graphics card without realising it.

I've written the rest now so I'll leave it there, but this is probably the most likely explanation if your hearing sounds since this suggests X is working... (as does the lack of error messages).  Should have read your original post more closely.





If that doesn't work:
The reason you get the problem on terminal 7 is because this is where x is running.  In one of your terminals, try logging in and
```
sudo nano /etc/X11/xorg.conf
```
Under the video card device section, change the driver from 'nv' to 'vesa'.  Then type control + x to exit and 'y' to save it.  You should then be able to see x but with very poor graphical performance.  To get to the login screen, stay in the terminal and type
```
sudo killall gdm
sudo gdm
```
If this works, you can try installing the official nvidia drivers by opening a terminal window and typing
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```
Wait for it to install, and then:
```
sudo nano /etc/X11/xorg.conf
```
Change 'vesa' (which you previously entered) to 'nvidia'.  Restart GDM as mentioned before and should have 3d acceleration.

If this doesn't work, change back to vesa.

---

### Post by Namgyel on 2006-06-10
Thank you :D 

I'll try it and let you know:) 


best regards 

Namgyel

---

### Post by Namgyel on 2006-06-12
Tried the procedure you told me to - but now it says that x has problems and wont work properly....  and it still doesn't work:-( 

What can I do?

---

### Post by Namgyel on 2006-10-15
HI!

Since it's been a long time I've tried a thing or two. Looks like that the configuration works with [Kanotix]("http://kanotix.com/") however I would like to work with Ubuntu since I'm more used to it. Is there any way that I could use Ubuntu??? Does anyone know if there will be better detection for SLI 6600GT in 6.10 release (tried the beta Live CD - doesn't even work... the screen goes black almost instantaniously after the boot up)?

Can I use Kanotix as the main install and then add the download links?

Best regards,
Namgyel

---

### Post by Kacey on 2006-10-16
I had the same problem, what I did was change the pci from 4:0:0 to pci 5:0:0 Ubuntu seems to grab the first video card it comes across

---

### Post by Namgyel on 2006-10-17
tried that... didn't work :confused: what exactly did you do?

---

### Post by mushr00m on 2006-10-18
A good place to start at the CLI try:
```

lspci | more

```

it will list the PCI devices including AGP and PCI-e cards.  At least you will be able to determine which card is going to be the one you work with.

Good Luck.

---

### Post by Kacey on 2006-10-18
```
lspci | more
``` after that I tried PCI 4:0:0, this wass what was in my xorg.conf, nothing chnaged. Then I tried PCI 3:0:0 and nothing happend. So after that I went back to 4:0:0 and pluged my monitor into the second card, and there she was but only for console 7 so I went back and changed it to 5:0:0 pressed ctrl+alt+backspace and switched the monitor back to the main card and there was my desktop :P

---

### Post by Namgyel on 2006-10-19
> **mushr00m said:**
> A good place to start at the CLI try:
```

lspci | more

```

it will list the PCI devices including AGP and PCI-e cards.  At least you will be able to determine which card is going to be the one you work with.

Good Luck.

Do I write only ```
lspci | more
``` this in the console?

---

### Post by Namgyel on 2006-10-19
OK, done all the things with the ```
lspci | more
``` and the switching and changing the card from 4 to 3 to 5... switching monitor from one card to another (on the second card all I see is yellow garbled picture on all the terminals.... This really isn't working at my place. When I press CTRL+ALT+Backspace .. do I do that in any terminal? Tried all and looks as if it doesn't work on any. BTW I'm doing this with the live version Ubuntu 6.10 since all the other versions were deleted during the downfall of the stupid thing called windows ;) . Is it the same if I do it during the live version or must I install the server version which should be then upgraded to desktop version?

---

### Post by Namgyel on 2006-10-19
First I coppied the codes I asked you about: 
```
cp /etc/X11/xorg.conf /var/log/Xoerg.0.log /place of the usb key
```
after that I tried changing PCI:4:0:0 to PCI:5:0:0 and save it in the file. then ```
sudo /etc/init.d/gdm restart
```
and it goes 
*Stopping GNOME Display Manager...    [ok]
*Starting GNOME Display Manager...    [[COLOR="Red"]fail[/COLOR]]

then we did ```
ps -ef | grepX
``` (forgot what it does).

And also tried these 

sudo apt-get install nvidia-glx
sudo apt-get install linux-restricted-modules-(something - needed to add something here, don't know the original what he said)
these two worked however it stopped at the last one
sudo nvidia-glx-config enable

and then sudo /etc/init.d/gdm restart and the same failure again...


best regards...

---

### Post by mushr00m on 2006-10-23
perhaps you should look into the 9626 series of Nvidia drivers.

It has solved most of my problems, though I'm not attempting to get a sli (dual monitor?) setup going.... yet.

good luck.
mushr00m

PS - I thought the command `lspci` would help locate the pci address of your video cards... the `|more` part just breaks up the output of lspci into readable screens.

---

### Post by mushr00m on 2006-10-23
> **Namgyel said:**
> 
And also tried these 

sudo apt-get install nvidia-glx
sudo apt-get install linux-restricted-modules-(something - needed to add something here, don't know the original what he said)
these two worked however it stopped at the last one
sudo nvidia-glx-config enable

and then sudo /etc/init.d/gdm restart and the same failure again...


best regards...

the something you need to add is the version of your current kernel. It can be found by the command ```
uname -r
``` 

for me ```
echo linux-restricted-modules-`uname -r`
``` outputs "linux-restricted-modules-2.6.17-10-386"

---

### Post by Greg Knight on 2006-12-07
Hi,

Have you managed to get your system working yet??

I have two 6600GTs in SLI as well, and I did...

1) I physically removed both cards
2) set the sli switch back to normal on the motherboard
3) put one card back in
4) booted live cd - worked a treat.
5) installed to Hard disk
6) turned PC off
7  removed single installed 6600
8) switched back to SLI mode
9) added both cards
10 rebooted
11) then installed Automatix and used it to install nVidia drivers

A royal pain in the butt.. although atleast I have dapper running now.

From what I read [here]("http://www.ubuntuforums.org/showthread.php?t=283419&highlight=black+screen+live+cd+SLI"), it seems as if I could have just disabled the SLI in BIOS and reenabled it after install (and not had to bother putting my hands inside the case).

---

### Post by Namgyel on 2007-03-08
It's been a while since I've been on my computer thats also one of the reasons not reporting what happened... So this is what is going on;

1. I deleted any trace of windows on my computer :-\" (Linux has about 250GB space + 3GB swap)
2. I installed the latest version of Ubuntu 6.10
3. I did sudo apt-get update and upgrade
4. Graphics still aren't working... I will try to upgrade graphics from nvidia and I will try to upgrade X interface... anyone has an idea how?

Greg I can't do that :cry: since my computer is still in waranty (hope I said it right) and I'm forbbiden to open the computer... I wish there was another way...

One question beside the 4h... How come this still continues to be the problem?? The graphic cards are at least a year old or even more... why isn't this fixed with 6.10??

Hope anyone can help me,
best regards,

Namgyel

---

