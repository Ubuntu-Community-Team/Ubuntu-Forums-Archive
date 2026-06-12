---
title: "how to get to grub menu during boot?"
date: 2010-06-30
forum: General Help
---

### Post by spydeyrch on 2010-06-30
hey guys, I did something really stupid. I have a triple boot system: Mint 9, Ubuntu 10.04, and Win7 Pro. All of them x64. Anywho, I was messing around in Mint and using the startup manager, I set win7 as my default OS and the selection time to 0. I thought that if it was set to 0, it would wait for input. I set win7 as default for my wife. Well, I was wrong about the 0 as unlimited. The machine starts in win7 right off the bat. Before, it would show the grub menu and then I could choose. Now, nothing. I have tried getting to the menu by hitting ESC but that gets me to the menu for like 3 nanoseconds and then restarts the machine. At least I can get into win 7, if that is a plus, hehehe.

Does anyone know what button I can press to get to the grub menu? It is grub 2. Or should I use a live usb and do some file editing? If so, what files, where are they located, and what values should I change them to? thanks for your help. 

I feel really dumb. I mean, obviously 0 would mean 0 time to input and therefore it would startup the default OS right away. I guess that I remember reading somewhere something similar but it was for windows and 0 did mean unlimited time.

Thanks!

-Spydey

---

### Post by mikewhatever on 2010-06-30
Press 'shift' for Grub2.

---

### Post by garvinrick4 on 2010-06-30
Once in choose 
```
gksudo gedit /etc/default/grub
```

-1 will have no time limit the rest you know.

save and you are done with it.

I do not know if startupmanger -1 will give no time limit.

---

### Post by spydeyrch on 2010-06-30
OK, I will try the 'shift' thing. Do I hold it or just press it at a certain point? I was pretty sure that shift would do it and thought that I had already tried it w/out success, but I will try it again. I will let you know how it goes.

Thanks!

-Spydey

---

### Post by dino99 on 2010-06-30
hold it down at end of bios process

---

### Post by spydeyrch on 2010-06-30
alright, so I tried a number of things: pressing it once right after POST, continually pressing it after POST, holding it down after POST, alternating 'shift' and the 'up' key, holding the 'shift' key while I am continually pressing the 'up' key, all of the above during post from power-on during POST and to win7. None of them worked.

Here is what I am seeing:

If I power-on and don't press a thing, my machine goes through a normal POST then right into loading win7. If I press ESC or 'shift' during or right after post, when GRUB would normally load, in the upper left corner I see for maybe a total of 1 second, "Loading Grub", or something to that affect (basically it states that it is loading the grub menu, that is the jist) but then win7 starts to load. I don't see the menu. I don't see the splash screen, nothing. Just those words then BAM, win7 loading.  Now, if I continually press the 'shift' key after post and when grub should load, I will see those words but if I continue to press it, then I will get the windows bootloader with only windows 7 showing. If I do the same with the ESC key, it shows "loading grub" then the machine restarts.

I am thinking, if I were to boot into a live usb, what terminal commands would I need to edit the gub.cfg? I seems to me that I would be able to use garvinrick4's advice but I would have to correctly point it to the hdd where that file is located. That might get a little complicated. Perhaps not but maybe, considering my setup.

So originally, I installed my three OS's on separate HDDs while none of the others were connected. i.e. Installed win7 to my 1TB but no other HDD was connected. Then disconnected 1TB, connected 1st 500GB, installed Mint 8, disconnected 1st 500GB, connected 2nd 500GB, installed Ubuntu 10.04, connected other 2 HDD, booted into mint 8, updated grub to include the other two OS's.

I did this so that if at any time, I removed a HDD (which I do frequently), or pressed F8 for the boot select menu during POST, I could just select the HDD and it would still contain it's own bootloader located on it's drive. i.e. I could press F8 during post, with all three drives connected, select the 1TB drive, and Win7 would load. No need to boot to grub then to windows 7. Plus, if I ever messed up grub, I could still boot it just fine.

I did that a while ago. Then last night I decided to install mint 9 x64 to the old mint 8 hdd. I made the mistake of not disconnecting the other two HDD so as to keep their bootloaders intact. Mint 9 installed to the correct HDD but even though that drive is connected to the first SATA connector on the mobo and placed into first place in the BIOS, it still installed GRUB2 to the windows hdd and overwrote the windows bootloader. I said "no big deal, I will fix it later." But now, I caused this issue with the grub menu timing-out.

I guess that I could try and select the ubuntu hdd during post and see if I can still boot into it, perhaps that will allow me to then edit mint's grub menu. Oh, and just in case it is not known, mint 9 is based off of ubuntu 10.04.

Thanks everyone for your helps so far.

-Spydey

P.S. I am at work right now so I can't really try any suggestions but perhaps if we work through them here first, then I can try them at home and see what works. :guitar:

---

### Post by varunendra on 2010-06-30
You need to edit the grub.cfg file from a live cd (although there's a warning on the file that you shouldn't edit it manually, yet editing only timeout value wouldn't do any harm).

Boot from LiveCD. Go into 'computer' & identify the label of the drive where mint is installed (if it is not already labeled, do it now for convenience). Say it is labeled as "mint", then enter this command in terminal
```
sudo gedit /media/mint/boot/grub/grub.cfg
```

Look for the line that says timeout=0, and replace 0 with 10.

Now reboot normally. You should get 10 sec. on the grub menu this time. Boot into mint and follow what garvinrick4 suggested.

And don't forget to run```
sudo update-grub
```after editing the /etc/default/grub file. :)

---

### Post by spydeyrch on 2010-06-30
@ varunendra

Thank you very much! I was quite sure that it would be something like that but couldn't connect the dots, so to say. Thanks for pointing it out.

If I can get into my ubuntu desktop, which I am pretty confident I can, I should be able to do it via there too. I will just need to check the label of the drive.

I will come back later to let you know how it turns out. :p

-Spydey

Thanks again! :guitar:

---

### Post by spydeyrch on 2010-06-30
Alright, so I got it fixed. I didn't really do it the way that others had mentioned, even though I am sure that they would have worked. Also, their recommendations did steer me down the right path.

So, like I previously mentioned, I had installed all three OS's on separate drives without the other drives connected. That way I could maintain each drive's boot-loader separately from the other boot-loaders on the other drives. Well, at least up until last night.

What I did was that I hit the F8 key during POST, selected my Ubuntu 10.04 drive and got to that drive's boot menu. It showed Ubuntu 10.04, Win7, and Mint 8. Mint 8 no longer was present so I booted into ubuntu, ran 

```

sudo update-grub2

```

then reboot.

During POST, I hit the F8 key again, selected my ubuntu drive, waited for the boot menu to showup, then selected thenewly found mint 9. It booted up no problem. I then used the startup manager to return the count down to 10 seconds.

I rebooted, and let everything run like normal. When the mint 9 grub menu came up, mint was at the top, windows selected as default in the middle, and ubuntu 10.04 at the bottom. I selected mint 9, and bam, I was in. Everything just fine.

Then I had to get win7 to boot properly. Apparently my wife thrashed win 7 while I was at work. :evil:

So I had to do some work to get it to boot. It kept freezing during the load up of win7. So after about 45 mins of working with a few different items, I have all three up and running about. I am going to leave mint's grub on my win7 drive and not restore the win7 boot loader. Too much hassle. I will just have to be careful.

Thanks everyone for your suggestions and help.

-Spydey:lolflag:

):P

---

### Post by varunendra on 2010-07-01
I'm too happy to see you got it fixed, especially given the way you did it! :lol:

While it was definitely the better way around (damn! I missed it!! :(), it was also quite a fun reading how you got it working :lolflag:

Maybe I don't need to mention, but shouldn't this thread be marked as [Solved] now? ;)

---

### Post by Kleenux on 2010-08-21
SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 
SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 

Ok it took me a #@$#$@#&^ time to find that SHIFT key from another PC browser, while the server is down and cannot boot.
Guys, make it simpler (ESC for instance), and don't tell me to change the config in theky, I want something that works also on other computers.


SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 
SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 

Maybe I'll remember this time.

---

### Post by skidzo on 2011-07-06
> **Kleenux said:**
> SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 
SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 

Ok it took me a #@$#$@#&^ time to find that SHIFT key from another PC browser, while the server is down and cannot boot.
Guys, make it simpler (ESC for instance), and don't tell me to change the config in theky, I want something that works also on other computers.


SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 
SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT SHIFT 

Maybe I'll remember this time.

*grin* you are right! ESC was also the only thing I could remember

---

### Post by OldManRiver on 2012-01-17
All,

I have a 10.04 server and having problems with obtaining root from "sudo".

I hold down the "Shift" key, get the menu and enter 'e' to edit the options.  I've entered the rw init=/bin/bash, but does nothing for me.

My problem is I have no sudoers users, so can not get to any root functions and everything I tried from the HOWTO at:

[http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/#comment-4385](http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/#comment-4385)

Does not allow me to get to and edit the /etc/sudoers file to add users with admin rights.

Open to suggestions on getting around this!

All help appreciated!

Thanks!

OMR

---

### Post by OldManRiver on 2012-01-17
All,

I finally got into my /etc/sudoers file using the HOWTO at:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

but find that I have defined the 3 users of:

user1 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
user2 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
user3 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

but when logging in as one of these users still get the error:

"No sudoers users found"

Can someone explain what is up with this?

Thanks!

OMR

---

### Post by coffeecat on 2012-01-17
Thread closed for:

1 - necromancy, and

2 - @OldManRiver, you have started a fresh thread with a relevant title, here:

[http://ubuntuforums.org/showthread.php?t=1910755](http://ubuntuforums.org/showthread.php?t=1910755)

---

