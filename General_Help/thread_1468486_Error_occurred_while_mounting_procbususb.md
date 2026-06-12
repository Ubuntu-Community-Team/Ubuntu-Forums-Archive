---
title: "Error occurred while mounting /proc/bus/usb"
date: 2010-05-01
forum: General Help
---

### Post by dosox on 2010-05-01
I upgraded my Ubuntu from 9.10 to 10.4 LTS via** CD (alternate). **Everything went okay while upgrading but after restarting I found a problem.


[COLOR=DarkOrange]An error occurred while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery
[/COLOR]
And so I have to press S everytime I turn on my laptop. Can someone tell me what I should do..
Thanks in advance.

---

### Post by dosox on 2010-05-01
Waiting for help.. :(

---

### Post by joham34 on 2010-05-01
I upgraded from karmic and have exactly the same problem but appart from this , everything appears to be O.K 
In a greek forum (it is in Greek, thats why I dont quote there) , I found a solution that has worked for me . If you comment the last line ( the one that says ¨none /proc/bus/usb usbfs devgid=123,devmode=664 0 0¨ ), it doesnt appear again and USB drives work normally in Ubuntu and within VIrtualbox guest OS

---

### Post by kyo on 2010-05-01
Same thing here...  

You can fix this by removing this live from /etc/fstab:

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```

That was added in Karmic to get USB support in VirtualBox, and it seems it's not needed anymore.

But to be honest, I thought I'd have more problems than that!  My installation is originally a 7.04 install, which went through all releases up to Lucid, and **it's still working!**

Can't say the same of my seldom-used XP partition, which has problems staying functional with only MS Updates...

97% in Ubuntu, 2% in OSX, 1% in XP and proud of it!

---

### Post by rick_diculous on 2010-05-01
> **kyo said:**
> Same thing here...  

You can fix this by removing this live from /etc/fstab:

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```That was added in Karmic to get USB support in VirtualBox, and it seems it's not needed anymore.


Thanks Kyo you saved my skin.

i too had this line added to /etc/fstab to fix Virtualbox USB support. commenting this line out has fixed the error on boot and indeed Virtualbox still works with USB drives.

---

### Post by dosox on 2010-05-02
> **kyo said:**
> Same thing here...  

You can fix this by removing this live from /etc/fstab:

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```That was added in Karmic to get USB support in VirtualBox, and it seems it's not needed anymore.

But to be honest, I thought I'd have more problems than that!  My installation is originally a 7.04 install, which went through all releases up to Lucid, and **it's still working!**

Can't say the same of my seldom-used XP partition, which has problems staying functional with only MS Updates...

97% in Ubuntu, 2% in OSX, 1% in XP and proud of it!


Thank you for the information.. BUT how do I remove that code.. And that is another major problem for me.. (Not Knowing how to do):confused:

---

### Post by Toon Macharis on 2010-05-02
> **dosox said:**
> Thank you for the information.. BUT how do I remove that code.. And that is another major problem for me.. (Not Knowing how to do):confused:

This is how you can remove it:

1. open a terminal window from the menu: Applications > Accessories > Terminal

2. enter "sudo nano /etc/fstab" and enter your password when prompted.

3. add # in front of the line "none /proc/bus/usb usbfs devgid=123,devmode=644 0 0"

4. press <Ctrl> + <X> to exit

5. press <Y> to confirm saving the changes

6. Leave the file name to write "fstab" and press <Enter>

---

### Post by OzzyFrank on 2010-05-06
Yeah **dosox**, whenever you see anyone telling you to "edit code", it's as easy editing a text file (which is what most of these are - no need to know how to edit Hex code, hehe!). Only difference is that if they are in a system folder, you will need to open them as *root/superuser* (unlike config files in your home folder), which you'd do in the terminal with a command like **sudo gedit /etc/fstab** (and guys - for newbies I wouldn't recommend your CLI-junkie choice of **nano** as the text editor to use! A GUI one like Gedit is way more easier to use, and anyone who's ever used Windows Notepad can use it).

---

### Post by OzzyFrank on 2010-05-06
> **rick_diculous said:**
> Thanks Kyo you saved my skin.

Was it THAT bad having to type S, hehe? At least the fix is easy.

---

### Post by billythekid on 2010-05-08
+1 props kyo.

nice one.

---

### Post by PeterOakland on 2010-05-09
Thanks a million to Joham34 and Kyo.
That did the trick nicely.
Greatly appreciate the help.

---

### Post by wall-e1 on 2010-05-12
If I erase that line from /etc/fstab, then I can not mount any USB device in the guest OS in Virtualbox.
I have Virtualbox 3.1.8 and Ubuntu 10.04 (upgraded from Karmic)
More details: I can see the USB device in virtualbox but it appears grayed out.
If i leave the line as it is, then the USB support in Virtualbox functions very well.
Help please!

---

### Post by OzzyFrank on 2010-05-12
> **wall-e1 said:**
> If I erase that line from /etc/fstab, then I can not mount any USB device in the guest OS in Virtualbox.
I have Virtualbox 3.1.8 and Ubuntu 10.04 (upgraded from Karmic)

Yeah, I've run into a couple of people who have this happening, yet I also upgraded my system to 10.04, removed the offending line so my system could boot all the way without me having to be there to hit S, and USB support in my VBox guests is fine. I'm actually running VBox 3.0.14 and am assuming if I updated that to 3.1.8 it would still be fine, so am interested to see if someone has an answer for this. After all, apparently VBox in Lucid no longer needs USB support forced via fstab.

---

### Post by RainKap on 2010-05-15
Good stuff kyo - I upgraded to lucid on my laptop this afternoon, and hit the "error while mounting ...". Simple edit to /etc/fstab fixed it. Now I have to puzzle out why the connection to the wireless access point is v.flaky...

Ian

---

### Post by ntekupal on 2010-05-16
Hi Guys,

As suggested by our experts I deleted the line [COLOR="Red"]none /proc/bus/usb usbfs devgid=46,devmode=664 0 0[/COLOR] from /etc/fstab but still on re-booting my lap-top(having Ubuntu 10.04) I see the same error.

I appreciate your help.

Thanks,
Raj.

---

### Post by Sale on 2010-05-18
I don't have the:

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

line in my fstab, but I'm still getting the error message (I was getting it in Karmic occasionally but now in Lucid it seems to happen every time). VirtualBox seems to work fine after upgrade to Lucid.

The only USB-related line in fstab that I have is:

```
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
```

What else should I be looking for?

Thanks.

---

### Post by uncertain on 2010-05-21
> **Sale said:**
> I don't have the:

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```line in my fstab, but I'm still getting the error message (I was getting it in Karmic occasionally but now in Lucid it seems to happen every time). VirtualBox seems to work fine after upgrade to Lucid.

The only USB-related line in fstab that I have is:

```
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
```What else should I be looking for?

Thanks.

Sale, I had the same USB line in fstab (upgrading 9.10 to 10.04).  Deleting/commenting it seems to have fixed the boot error.

However, now I cannot mount usbs.  If I plug in a usb key, I get a pop-up window telling me 
```
Unable to mount 1.0 GB Filesystem
Not Authorized
```
Anyone have any idea how to fix this?

---

### Post by Sale on 2010-05-21
> **uncertain said:**
> Sale, I had the same USB line in fstab (upgrading 9.10 to 10.04).  Deleting/commenting it seems to have fixed the boot error.

However, now I cannot mount usbs.  If I plug in a usb key, I get a pop-up window telling me 
```
Unable to mount 1.0 GB Filesystem
Not Authorized
```
Anyone have any idea how to fix this?

Funny...I've commented out the

```
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
```

line and my USB keys work fine **within Ubuntu**. I just can't mount/use them in VirtualBox (VB 3.1.8 )

I can't offer any help, but maybe this info will mean something to someone else :)

---

### Post by dosox on 2010-05-23
Thanks everyone for your tips.. Learned a lot.
I just did a fresh install of Lucid & it's working great except Gwibber & some update problems.

---

### Post by sonofusion82 on 2010-05-27
removing the "none /proc/bus/usb...
from fstab works great for me, thanks!

---

### Post by code_linux on 2010-05-28
Had the same problem here.. now its all good, i think! Thank you.

---

### Post by cfmunster on 2010-06-04
> **kyo said:**
> 
But to be honest, I thought I'd have more problems than that!  My installation is originally a 7.04 install, which went through all releases up to Lucid, and **it's still working!**

Can't say the same of my seldom-used XP partition, which has problems staying functional with only MS Updates...

97% in Ubuntu, 2% in OSX, 1% in XP and proud of it!

Thanks for the fix, Kyo. My desktop system is running strong since 7.04 as well. Go Ubuntu!

---

### Post by marianom on 2010-06-11
Thanks here too!!!

---

### Post by honkanen on 2010-06-29
Thanks for the solution which is to comment out this line:
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
In my *fstab* file, I don't see that line though.  The only similar line which I have is:
usbfs /proc/bus/usb usbfs defaults 0 0

Should I comment this one out instead?

Thanks.

---

### Post by mirchichamu on 2010-06-30
> **OzzyFrank said:**
> Yeah, I've run into a couple of people who have this happening, yet I also upgraded my system to 10.04, removed the offending line so my system could boot all the way without me having to be there to hit S, and USB support in my VBox guests is fine. I'm actually running VBox 3.0.14 and am assuming if I updated that to 3.1.8 it would still be fine, so am interested to see if someone has an answer for this. After all, apparently VBox in Lucid no longer needs USB support forced via fstab.

Hi all,

At terminal command I got the following. There is no such line. What should I do? I am also having problem with USB non detection. Can anyone help please?

[# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=941ec615-e371-4ef2-84cc-fab3ed07f9f2 none            swap    sw              0       0 ]

---

### Post by EllyBilateralCI on 2010-07-22
Hi thanks to Tony at post #7 - it really helped to have a step by step even if I've used Linux for a few months.

I have to say though it is bizarre to have this line in /etc/fstab when we're told to do so in the first place in order to rectify the USB connections (greyed out previously) and now we don't need it but that the virtualbox sees the USB connection now....weird!

Anyway thanks to kyo and everybody else - it's helped me!  Phew!  I thought it was a problem cos I did a fresh install of lucid (had the alpha and betas of lucid before but it caused mayhem with not letting sound to work and so a re-install of lucid did the trick with sound).

Cheers! :popcorn:

---

### Post by frikker on 2010-08-13
Hey guys.  Just wanted to add my two cents.  I as well had this identical error after manually adding the line to /etc/fstab for virtualbox support.  I had this line in /etc/fstab on 9.04 so I didn't even try using usb with virtualbox without the /etc/fstab line in 10.04.

Want to know the real problem with this? The "Press S to skip / Press M to manually mount" only shows up on the ubuntu splash, not on the console.  When you press 'esc' twice, and come back to the splash, the message is gone.  The system will not continue unless you press s or m.  This splash screen just feels hokey; the little circles keep lighting up back and forth implying the system is working when in reality it is doing nothing but waiting for a keyboard input.

Last week I was running 9.10 happily until I upgraded to 10.04 (bad mistake).  My system upgrade went well, and upon reboot I saw the *exact* same screen that I see now when I boot (regarding /proc/bus/usb not mounting, followed by fsck clean, followed by a ureadahead-other message).  The only thing missing was the "Press S / Press M" on the splash screen.  There was nothing to indicate it was waiting on a key press.  So I couldn't get into my system and ended up doing a wipe and reinstall.  A real pain in my butt! As it turns out, apparently all I had to do was press "s" and I had no idea.  The reason I was confused was because the /proc/bus/usb error, in the console, was buried about 15 lines high while the most recent line said "ureadahead-other exited with status 4" (status 4 means all went well I think).  All my googling was regarding the ureadahead, not /proc/bus/usb. Doh.

So... just a heads up to anyone upgrading 9.10 => 10.04; if you have virtualbox usb support and don't see the message on the splash screen, try pressing "s" and see what happens.

---

### Post by tulcak on 2010-09-04
Its all crap.  After hours of reading posts about disabling your floppy in the bios, and uninstalling pmount and usbmount and blah blah blah... this is what i did to solve it for me:

for Ubuntu lucid:

1.  install through synaptic package manager: usbmount (which automatically installs pmount and associated files)

2. make a mount point:  sudo mkdir /media/floppy

3. then, edit the fstab file:  sudo gedit /etc/fstab

add this line:

/dev/sdb /media/floppy auto noauto,users 0 0

for me, /dev/sdb is my usb floppy drive

That's it, case closed, and what a bunch of drivil I have been reading... geesh, and I'm a newbie !!!!!

---

### Post by OzzyFrank on 2010-09-04
> **tulcak said:**
> "Its all crap."  "what a bunch of drivil I have been reading... geesh, and I'm a newbie !!!!!

Well, to some of us reading this thread it's obvious that what works for one in this issue doesn't mean it will work for the other. For me, it had nothing to do with the floppy whatsoever, which makes your tip absolutely useless to most of us. But we accept all advice, and don't hang it on anyone who tries to give friendly help... even newbies... who try their hardest not to be friendly, hehehe!

PS: And if you wanna throw insults,  maybe spellcheck first lest you "drivel" typos, hehe.

---

### Post by dcstar on 2010-09-05
> **tulcak said:**
> Its all crap.  After hours of reading posts about disabling your floppy in the bios, and uninstalling pmount and usbmount and blah blah blah... this is what i did to solve it for me:
........
That's it, case closed, and what a bunch of drivil I have been reading... geesh, and I'm a newbie !!!!!

Considering that this thread has **absolutely nothing to do with** USB floppy drives, I can see why you believe that it "drivil" (sic).

---

### Post by ilomo on 2010-12-13
Thank you,
it worked for me!!!!:P

---

### Post by northd_tech on 2011-10-26
> **kyo said:**
> Same thing here...  

You can fix this by removing this live from /etc/fstab:

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```That was added in Karmic to get USB support in VirtualBox, and it seems it's not needed anymore.

But to be honest, I thought I'd have more problems than that!  My installation is originally a 7.04 install, which went through all releases up to Lucid, and **it's still working!**

I believe that I'm having similar trouble getting a Backpack External USB CDRW drive to work due to **usbfs** being removed from the Ubuntu 10.04 Lucid Lynx kernel by the development team (something about a conflict with udevd from what I read briefly).  Unfortunately, I don't have any lines remotely similar to the above fix in my **/etc/fstab/ **file.

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda4 :
UUID=6A8D626A5A721890    /media/CommonSpace1    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=608A329A8A326CA2    /media/Vista64_JimHD    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=732636ca-5163-4be5-b549-7cd02d7c5dcd    none    swap    sw    0    0


---

### Post by panamabill on 2012-01-30
When I boot up lately, I keep getting "An error occurred while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery"

When I type "sudo gedit /etc/fstab" in the Terminal, this is the only line I get 
	"usbfs			/proc/bus/usb		usbfs	devgid=14 0 0." 
There is no "none /proc/bus/usb usbfs devgid=123,devmode=664 0 0"
I'm pretty green at terminal, commands, etc. so I need easy instructions.

---

