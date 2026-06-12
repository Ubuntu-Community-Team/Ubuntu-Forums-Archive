---
title: "Ubuntu 10.04 Live USB Problem?"
date: 2010-05-04
forum: General Help
---

### Post by dannyamayay on 2010-05-04
Hi, I created a 10.04 live usb several times, but can't get into the desktop nor see the ubuntu loading screen when I boot off the flashdrive. I created it with Universal USB Installer, but like I said when I boot off of it it doesn't work. It gives me some text I'd normally see when i boot off it before I can see before I actually get into the desktop, but see a black screen.

Boots off USB --> text scrolls ---> monitor going to sleep ---black screen for several minutes until I reboot and see the same thing.

However if I boot a live Ubuntu 9.10 it works perfectly so I don't know why I can't use this release as a live usb. If anyone can shed any light on this problem or tell me if I can upgrade 9.10 live usb to 10.04 it would be very much appreciated. 

Thank you.




Goku?---->:lolflag:

---

### Post by ironic.demise on 2010-05-05
I tried several live usb creators to get 10.4 but I eventually had no choice but to burn a cd. If you really really can't boot from cd then I suggest using the "pendrive linux" livecd creator as I've known it to be the most successful for myself.

---

### Post by sarin_cv on 2010-05-05
How did you create the live usb? Is it by using System-->Administration-->Create a USB startup disk option? I have created one myself and it is working perfectly...

---

### Post by ironic.demise on 2010-05-05
> **sarin_cv said:**
> How did you create the live usb? Is it by using System-->Administration-->Create a USB startup disk option? I have created one myself and it is working perfectly...

I *believe* he's using a windows program?
May be wrong, not sure...

...I used the ubuntu main one and I don't believe it worked for me :(

---

### Post by P4man on 2010-05-05
Right after the bios, when you get the first purple screen, press escape or space  key to show additional boot options. Press F6 and select nomodeset.

---

### Post by ironic.demise on 2010-05-05
> **P4man said:**
> Right after the bios, when you get the first purple screen, press escape or space  key to show additional boot options. Press F6 and select nomodeset.

Didn't even get a purple screen? Straight to the installed version

---

### Post by sarin_cv on 2010-05-05
Try booting in to 9.10 using the live cd and use System-->Administration-->Create a USB startup disk utility to create the disk... it should work...

ref: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
check 'creating a bootable usb drive' section... the screenshot given is that of kde...

---

### Post by P4man on 2010-05-05
> **ironic.demise said:**
> Didn't even get a purple screen? Straight to the installed version

I was replying to the original poster who does seem able to boot from usb, only that karmic blanks his monitor. Hence my suggestion to boot with nomodeset.

In your case, I suggest you have a look if your USB sticks do not have a U3 firmware. (sandisk cruzer by any chance?)

[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

You have to remove u3 before you can use it as a bootable device.

---

### Post by ironic.demise on 2010-05-05
> **P4man said:**
> I was replying to the original poster who does seem able to boot from usb, only that karmic blanks his monitor. Hence my suggestion to boot with nomodeset.

In your case, I suggest you have a look if your USB sticks do not have a U3 firmware. (sandisk cruzer by any chance?)

[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

You have to remove u3 before you can use it as a bootable device.

Thankyou for the help anyway, apologize for butting in a bit.

Nope, I have a U3 but it isn't what I was trying to boot off of, I'll look at the guides posted, no rush until I need a new install ^_^

---

### Post by amayayx3 on 2010-05-05
Hi, if I install through Window's Universal USB Installer I only get the scrolling text and it'll normally immediately go straight to the Live Desktop, but yes goes black. However I installed this time around using Ubuntu Startup Disk Creator and saw the purple screen. I took P4man's instruction using " nomodset" and the Desktop appeared successfully. 

:p Thank you very much. Hope someone else finds this helpful as well.

 EDIT: Oh  yes I created another account and plan to discontinue the other since I forgot the password and it took an excessive amount of time to get the changed password by email.

---

