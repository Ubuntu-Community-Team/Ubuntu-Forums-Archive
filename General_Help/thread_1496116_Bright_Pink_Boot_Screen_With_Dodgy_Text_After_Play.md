---
title: "Bright Pink Boot Screen With Dodgy Text After Playing With Startup Manager In 10.04"
date: 2010-05-28
forum: General Help
---

### Post by Jakiejake on 2010-05-28
Hi Guys today while using 10.04 Lucid Lynx 64 bit I decided to do something about the low resolution boot screen, I've seen the bugs thread but I thought startup manager would be the way to go
Anyway I changed the resolution and the bits to the highest they would go
I rebooted and I got the normal coloured boot screen but no logo just text, then I tried disabling text and enabling the boot logo
Then I rebooted and the same thing again
Then I removed startup manager and the whole boot screen turned bright pink and still had a text logo!
Please Help!

---

### Post by Jakiejake on 2010-05-29
> **Jakiejake said:**
> Hi Guys today while using 10.04 Lucid Lynx 64 bit I decided to do something about the low resolution boot screen, I've seen the bugs thread but I thought startup manager would be the way to go
Anyway I changed the resolution and the bits to the highest they would go
I rebooted and I got the normal coloured boot screen but no logo just text, then I tried disabling text and enabling the boot logo
Then I rebooted and the same thing again
Then I removed startup manager and the whole boot screen turned bright pink and still had a text logo!
Please Help!

Pink screen now gone but no logo just text

---

### Post by inso_741 on 2010-05-29
do you have an nvidia card and have you installed prop. drivers

---

### Post by Jakiejake on 2010-05-29
> **inso_741 said:**
> do you have an nvidia card and have you installed prop. drivers

No It is an ATI card
It was working fine before

---

### Post by inso_741 on 2010-05-29
sorry don't know much about ati cards

---

### Post by Jakiejake on 2010-05-29
> **inso_741 said:**
> sorry don't know much about ati cards

Simple Answer... :(

---

### Post by Jakiejake on 2010-05-29
Can Anyone Help
PLEEAAASSSEEE :confused:

---

### Post by Jakiejake on 2010-05-29
Here is startup-manager
[IMG]http://img10.imageshack.us/img10/8710/screenshotstartupmanage.png[/IMG]

---

### Post by WorMzy on 2010-05-29
You modified the resolution, didn't you? I don't know what sizes plymouth themes need to be displayed at, but I've encountered a similar problem on my PC. Setting the boot resolution to my monitor's native resolution (1440x900) makes Plymouth show the text theme, but removing the configuration that changes the boot resolution lets plymouth show the correct boot "ubuntu" theme (albeit in a terribly pixilated and unsightly way).

---

### Post by Jakiejake on 2010-05-29
> **WorMzy said:**
> You modified the resolution, didn't you? I don't know what sizes plymouth themes need to be displayed at, but I've encountered a similar problem on my PC. Setting the boot resolution to my monitor's native resolution (1440x900) makes Plymouth show the text theme, but removing the configuration that changes the boot resolution lets plymouth show the correct boot "ubuntu" theme (albeit in a terribly pixilated and unsightly way).

Ok ill put it back to 640X480 With 8 Bits

---

### Post by bildr on 2010-05-29
turn the resolution down a bit and make sure the splash image resource is appropriately sized for the resolution you are using.  hot pink sounds like the color used by computers to denote transparency in image formats that don't support transparency, i.e. the image for that resolution does not exist.

---

### Post by Jakiejake on 2010-05-29
> **bildr said:**
> turn the resolution down a bit and make sure the splash image resource is appropriately sized for the resolution you are using.  hot pink sounds like the color used by computers to denote transparency in image formats that don't support transparency, i.e. the image for that resolution does not exist.

This is what I now get
The Hot Pink Is Back
[IMG]http://img256.imageshack.us/img256/6715/img5018c.jpg

---

### Post by Joe-ubunt on 2010-05-29
I had the same thing happen to me before when I messed with the startup manager resolution settings. What happened to me is that the startup manager added depreciated values to the /etc/default/grub. It added a vga=769 or something in the GRUB_CMDLINE_LINUX="" between the quotes. I just removed the vga=769 in between the quotes using

gksudo gedit /etc/default/grub

and saved and did sudo update-grub and all was well again. You may have to add something in between the quotes but mine was always blank before startup manager added the vga=769.

---

### Post by inso_741 on 2010-05-30
> **bildr said:**
> turn the resolution down a bit and make sure the splash image resource is appropriately sized for the resolution you are using.  hot pink sounds like the color used by computers to denote transparency in image formats that don't support transparency, i.e. the image for that resolution does not exist.

> **WorMzy said:**
> You modified the resolution, didn't you? I don't know what sizes plymouth themes need to be displayed at, but I've encountered a similar problem on my PC. Setting the boot resolution to my monitor's native resolution (1440x900) makes Plymouth show the text theme, but removing the configuration that changes the boot resolution lets plymouth show the correct boot "ubuntu" theme (albeit in a terribly pixilated and unsightly way).


I've seen people using 1920x1200 so the default splash resource is more than enough to run on 1600x1200
but thats not a widescreen resolution...why dont you try using you native resolution
also try [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

and if the screenshot/pic is larger than 1024x768 please post it as a link

---

### Post by jagmeet on 2010-05-30
i had the same problem too ...but can't fix it

---

### Post by Jakiejake on 2010-05-30
> **inso_741 said:**
> I've seen people using 1920x1200 so the default splash resource is more than enough to run on 1600x1200
but thats not a widescreen resolution...why dont you try using you native resolution
also try [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

and if the screenshot/pic is larger than 1024x768 please post it as a link

Sorry
I tried your link
A bit to hard
Any Other suggestions to get a High Res Boot Screen

---

### Post by Jakiejake on 2010-05-30
> **Joe-ubunt said:**
> I had the same thing happen to me before when I messed with the startup manager resolution settings. What happened to me is that the startup manager added depreciated values to the /etc/default/grub. It added a vga=769 or something in the GRUB_CMDLINE_LINUX="" between the quotes. I just removed the vga=769 in between the quotes using

gksudo gedit /etc/default/grub

and saved and did sudo update-grub and all was well again. You may have to add something in between the quotes but mine was always blank before startup manager added the vga=769.

That worked
Thanks!
It's Still low res though

---

### Post by inso_741 on 2010-05-30
run 'vbeinfo' at the grub prompt(press c at the grub menu)
it will list the modes(resolutions that are supported)
note the hexa value against the desired mode
convert it to decimal and replace it where you put 'vga=xxx'

---

### Post by Claus7 on 2010-10-08
Hello,

no matter what I did I was not able either to get rid of the text logo or the pink screen, while tampering with the resolution or grub or startupmanager. 

So using this plymouth theme with the fixed resolution option I was able finally to get rid of the text logo (the simple one) and the black screen and the pink screen.

[http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696](http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696)

Regards!

---

