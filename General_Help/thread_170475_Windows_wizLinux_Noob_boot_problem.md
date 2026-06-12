---
title: "Windows wiz/Linux Noob boot problem"
date: 2006-05-04
forum: General Help
---

### Post by Phil_McCrackin on 2006-05-04
Hi all!

I look forward to becomming a part of this community. I am a computer science major and very interested in development. Anyway, to the issue at hand...

I have installed Ubuntu after a Windows XP in dual boot (same HD with a 512MB Swap in between). Everything seems to go just fine through initial installation. When I reboot without the install disc everything seems to be in check (option to which OS I want to boot to). I choose Ubuntu, get the boot screen, finishes loading the remaining included apps., and I get a still cursor at the top left and a little drum sound...nothing else. No HD activity, nothing. However, everytime I hit enter, I get the little drum fill. Nice, huh?

Anyway, I'm not sure where to begin. Linux is a totally foreign to me. ANY help or direction as to how to obtain more info would be GREATLY appreciated. I'll list hardware below if there are any known issues there. 
I already know the support here is better than *cough* Micro *cough* soft.

Thank you in advance,
Phil

AMD64FX-55
Biostar nVidia NF4 SLI
2x nVidia 6800 GT
2GB Kingston RAM
2x WD caviar 80GB

---

### Post by Oomska on 2006-05-04
[QUOTE=Phil_McCrackin]Hi all!

I choose Ubuntu, get the boot screen, finishes loading the remaining included apps., and I get a still cursor at the top left and a little drum sound...nothing else. No HD activity, nothing. [/QUOTE]

Similar problem - I just get a little underscore cursor at the top left hand of the screen and no activity. You also have an NVidia card and I'm wondering whether it has something to do with video drivers.

---

### Post by nowadays who knows on 2006-05-04
Are you able to type in anything or is it just locked to a blinking curser? 
If you can type in info type "startx":-k   or "start x" one of those is the line command to start the gui. You could have any number of problems if you cant type info and it is locked up. If it is locked up youll probably have to reinstall since obviosly something got hosed.



Just rembembered something and copied this from someonelses post. but if you selected server install  Then check this out.
Just a black screen with a cursor, or do you see a login? If it's the latter, you may have done a server install. If it's the former, something went wrong (yes, it's a bad install).

If you see a login, log in as the account you created during installation, and then type
Code:

sudo apt-get update 
sudo apt-get install ubuntu-deskop
 sudo /etc/init.d/gdm start

The password is your user password.

---

### Post by Phil_McCrackin on 2006-05-04
No, I'm not able to type anything. The only thing I can get to happen is the drum fill when I press Enter. 

This is actually the second attempt at install. The first time I lost my Windows system (boohoo) and had the same problem when I opened Ubuntu. 
There is no login. immediately after the the boot indicator is completed the screen goes blank and the cursor is top left and blinks initially, I get the drum, then the cursor stops blinking and nothing else. It's freezing right as it's pulling up the desktop.

I have the 64 bit...should I try to download it again or even the 32 bit? I'll hang out and see if there are any more ideas then maybe try that. I am determined ;)

---

### Post by Rasitiln on 2006-05-04
I recently installed ubuntu. I have a nvidia geforce 6600 series card. I had a similar issue the gui would freeze on load up and the entire machine would lock up. Turns out the NV driver was bad. so I went to /etc/X11/xorg.conf and changed the driver line to "vesa" tried it worked like a charm then installed the nvidia 3d accellerated drivers and changed the driver line to "nvidia" and wolla worky worky with 3d accelleration. 

Ive tried to install ubuntu on serveral of my home machines all of them have nvidia cards and each one has the same issue. Seems like the NV driver is severly botched. :mad: 

NOTE this was from the cds I recived from SHIPIT

---

### Post by Phil_McCrackin on 2006-05-04
[QUOTE=Rasitiln] so I went to /etc/X11/xorg.conf and changed the driver line to "vesa" tried it worked like a charm then installed the nvidia 3d accellerated drivers and changed the driver line to "nvidia" and wolla worky worky with 3d accelleration. 
[/QUOTE]
Ok...I'm game. How do I do that? Is that from the restore?

---

### Post by Rasitiln on 2006-05-04
you could do it from restore just 

nano /etc/X11/xorg.conf 

then go down to the section 
```

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "NV"
        BusID           "PCI:1:0:0"
EndSection

```

and change it to
```

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

```

save and exit nano then reboot into ubuntu normally. should boot you up into gnome just fine.

then check out [installing nvidia drivers]("http://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

you may have to manually edit that same section once they are installed to say
```

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection 
```

then restart X and you should be done

---

### Post by ZylGadis on 2006-05-04
Right. A windows "wizard" trying linux is the worst possible combination. You'd have to unlearn a lot of windows-related assumptions you unknowingly hold, so stand firm and be prepared :) 
1. Reboot
2. When prompted, press ESC to bring up the grub menu
3. Choose the "restore" option or whatever it is called, should be the second one.
4. Now you have a single-user root-only console-mode ubuntu. Type the following:
```
nano /etc/X11/xorg.conf
```

This brings up a text editor with xorg.conf in it. Nano is pretty self-explanatory (unlike vi, so shut up you zealots :D) and you should not have problems with it.
5. Find the line with the driver name (starts with "driver"), and change whatever it holds to "vesa", which is really generic and should always work.
6. Save, exit from nano and type "reboot" in the console.
Your system should work fine now. You won't be able to use your nvidia with all the bells and whistles, but it works. Next thing to do is to download the correct driver for it, install it, go back to editing xorg.conf and replace "vesa" with the new driver name. There should be a howto for that around - be careful to match your card version (6600) with it, as my 5200 uses a different driver (I think).

---

### Post by Phil_McCrackin on 2006-05-04
Sweet action! Like I said, I am a computer science student (so I'm completely used to hosing my entire system and starting over from scratch)...half my instructors use Windows and half use linux. I've wanted to get into Linux for awhile, just haven't had the time to dedicate. Well, I took my last final today and am free all Summer, so here goes! I 'Aint Skeerd! I will attempt this and let you know. Thank you very much!

---

### Post by Phil_McCrackin on 2006-05-04
OK, I'm a tard. I'm missing something. I have the editor up...it's empty. I don't know how or where to "Find the line with the driver name". aaaaagghh

---

### Post by Rasitiln on 2006-05-04
you may have misspelled the file path.

Everything almost in linux is case sensitive. I'd guess you forgot to capitialize X11. The xorg.conf is not case sensitive so NV and nv are the same thing as well as NVIDIA and nvidia.

```
nano /etc/X11/xorg.conf
```
is what your looking for.

---

### Post by Phil_McCrackin on 2006-05-04
well, I'm in 1.3.8 and it is blank with a menu at the bottom. The only thing I have been able to find is write->to files I find a devices button there, but nothing nvidia anywhere. I have a feeling I'm a lost puppy.

---

### Post by Rasitiln on 2006-05-04
if you enterd nano /etc/x11/xorg.conf it will still open to a blank file like you described.
exit that and try nano /etcX11/xorg.conf.

1.3.8 is just the version of nano you will always see that when you use nano.

---

### Post by Phil_McCrackin on 2006-05-04
ah thank it's busted... I don't know. I've tried to enter it every way I can think of (most importantly the way you typed it). All I get is a new file. I'm assuming there should be a list there of some kind? 
the command line looks like this right? "root@mycomputername:~# "

BTW: I appreciate your patients and help

---

### Post by Rasitiln on 2006-05-04
type 

```
 cd /etc/X11/ 
```

then 
```
 ls 
```

if xorg.conf is there then type

```
 nano xorg.conf 
```

if all that comes up is a blank file like before then some how you have overwriten your previous xorg.conf

---

### Post by Phil_McCrackin on 2006-05-05
Well, I got excited there for a bit. I found it (I'm embarassed to say what I did wrong). Anyway, it did not fix my problem. I made the changes as indicated, saved and re-booted and got the same results:( 
Back to the drawing board...

Thanks again for your help

---

### Post by JoeMetal on 2006-05-05
Ubuntu plays the drumroll at the login screen.  It seems to me that since you keep getting the drumroll that your comp doesn't freeze but just doesn't output the video to the right place.  Once you hear the drum thing, wait a second and then try entering your username you set up, hit enter, and then your password, and hit enter.  This should log you in and start up Gnome.  You'll know by a serene-ish sound.  If you still have nothing on your screen, let me know.

---

### Post by Rasitiln on 2006-05-05
yes if your 6800s have dual video output it would be displaying video on one of the other vga adapters.

---

### Post by Phil_McCrackin on 2006-05-05
I re-booted and did as you said. interesting, when I typed my username and pressed enter nothing, then after I typed my password and pressed enter I got another drum. Nothing else, though. Everytime I pressed enter I got the drum. maybe I I'll just boot up and plug the monitor in to the other ports and see what I get

---

### Post by Phil_McCrackin on 2006-05-05
SWEEEEET ACTION! That was the issue. See, not only do I have dual video output, but I have dual video cards, so I actually have 4 video outputs all together. Now I will have to resolve this so I don't have to continually unplug and plug in my monitor, but what the hell, UBUNTU is alive.

Thanks so much for your help. I reckon I'll be spending a lot of time here while I get things situated. For all I know, I feel like I don't know jack all over again. Well, it keeps things interesting!

Thanks again! now to get the drivers

---

### Post by Afrique on 2006-05-25
I'm having the exact problem, drum sound and all. ctrl+alt+F1 works fine, but when i turn to the gui i get the blank screen (or frozen).
Specs:

AMD64 3500+
GA-K8NXP-SLI    (Motherboard)
GA 3D1 6800GT

I've reinstalled (about 20 times), i've tried setting the display driver to vesa, nVidia and back to nv and i've even tried plugging the screen into another port. Nothing is working for me. It seems like SLI is the common variable here but unfortunatelly i can't just unplug one card because it's a 3D1 (2 chips on one card).

Please help me out, i'm South African so this is one distro i can't turn my back on.

---

### Post by Phil_McCrackin on 2006-05-25
Well, that was ultimately my problem. Ubuntu was only "seeing" one of my cards and right after boot, it shifted the video to another port. I just went to xorg.conf and entered in the info on my other card and bus and never had another problem. Sorry, that's probably no help. I'm certain someone here will be able to help you. Great community here.

---

### Post by Afrique on 2006-05-28
Doesn't anyone know how to set up a 3D1 in the xorg.conf or even have an idea . The mother board has a PCI-E 1x at the top then the PCI-E 16x with my dual gpu gfx card. Then the same pattern repeated (all empty except obviously for the first PCI-E 16x).

Can someone maybe explain how the bus code works (0:16:0)?

---

### Post by Phil_McCrackin on 2006-05-28
I would be interested in knowing that myself. Initially only one of my cards was detected which was the 4th slot up but is a PCI-E 16x (detected as BusID PCI:4:0:0) next I have a PCI-E 1x and then and my other PCI-E 16x which contains my other GPU. As stated earlier, my video was only coming out of the card at 4:0:0 so I made an edit naming the other slot PCI:5:0:0. I now have video where it should be. However, I get an error message at every boot up about the card which I have not been able to even see because it's only on the screen for a split second. So I would also be very interested to know if anyone else has these answers. Maybe a better question for the gaming forum? Since gamers are most likely to have an SLI capable system?

---

### Post by pjman on 2007-07-02
Howdy Phil / Afrique!

I have a similar problem with my GV-3D1 (Dual 6600GT GPUs on **one card**). I found a work around but I'm now hoping to get a permanent fix. Since Knoppix does not seem to have this problem, I'm hoping the devs can fix it for Ubuntu :-)

My thread with workaround - [http://ubuntuforums.org/showthread.php?t=465064](http://ubuntuforums.org/showthread.php?t=465064)

Another thread with a similar problem - [http://ubuntuforums.org/showthread.php?t=203216](http://ubuntuforums.org/showthread.php?t=203216)

Does anyone know who can fix this or what can be added to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/119114") to make it easier to fix?

---

