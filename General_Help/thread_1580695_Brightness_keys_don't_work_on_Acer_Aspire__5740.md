---
title: "Brightness keys don't work on Acer Aspire  5740"
date: 2010-09-23
forum: General Help
---

### Post by sashoalm on 2010-09-23
I'm reposting here my solution from the [launchpad thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984"), so people having this problem can try the solution. If you have the same laptop and problem try it and post the results:

> SOLVED (for my laptop at least - Acer Aspire 5740)

The trick was to add "acpi_osi=" (without the quotation marks) to the GRUB parameters. Setting the parameter to an empty string means that no OS is reported to the BIOS. By default acpi_osi is set to Windows NT. I had previously tried "acpi_osi=Linux" but it didn't work, apparently it had to be an empty string.

The brightness keys work now :-)


I think it might work for other models as well if they have core i3 processors.

---

### Post by JBud on 2010-10-31
Thank you VERY much for this solution... I have been searching for a solution to this issue for a long time, I can confirm that this works on my Aspire 5740.

Cheers,
-Joe

---

### Post by Quackers on 2010-10-31
Is this for Fn+F5 type key combinations or a dedicated brightness button? I am not familiar with your laptop.
Thanks

---

### Post by JBud on 2010-10-31
> **Quackers said:**
> Is this for Fn+F5 type key combinations or a dedicated brightness button? I am not familiar with your laptop.
Thanks

It solves all of the fn combinations that I know of... fn+f5 for screen options, fn+f6 for turning off the display backlight, fn+f4 for sleep fn+f8 for mute, etc... But the problem I had a huge problem with was fn+left/right for brightness control, and this workaround solved it!

---

### Post by Quackers on 2010-10-31
Ok, thanks for the details :-)

---

### Post by photographer92 on 2010-11-03
Hello Im having similar problems except i cant see the screen to change anything!! Its too dark. Im dual booting Windows 7 and Ubuntu 10.04. I have to get very close to the screen and even then its very hard. Acer Aspire 5741 Laptop

---

### Post by JBud on 2010-11-04
> **photographer92 said:**
> Hello Im having similar problems except i cant see the screen to change anything!! Its too dark. Im dual booting Windows 7 and Ubuntu 10.04. I have to get very close to the screen and even then its very hard. Acer Aspire 5741 Laptop

Hi, did you try the above suggestion? (adding 'acpi_osi=' to grub params)

---

### Post by JBud on 2010-11-30
Okay, I found the best solution. The acpi_osi= is an OK workaround, but does not provide the ability for power management to work. So the best solution is as follows:

Step 1)

Make absolutely sure that this will support your system by running this command:
```
lsmod | grep ^i915
```
If your output is SIMILAR to:
```
i915 331519 3
```
(The i915 MUST show up, the other numbers may vary)
then continue to step 2, otherwise, this patch will not work.

Step 2)

Now you must add the repository for the linux-kamal-mjgbacklight kernel (The patch for intel gma backlights)

Run this command:
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight
```

Run the update manager, and install the new kernel (The current version is 2.6.35-24) that appears, it should show that it is from the above repository. (You should also install any other software from the repository, such as the power management, however, I am fairly sure that only the kernel is required for the patch to work. 

Before you reboot, open up:
/etc/grub.d/10_linux

Find this line:
```
args="$4"
```
Replace it with:
```
args="acpi_backlight=vendor $4"
```

Finally run the command:
```
sudo update-grub
```

Now reboot, and from grub, select the new kernel, you will now have FULL backlight control.


Ref: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

This worked perfectly for my Acer Aspire 5740

---

### Post by theMOTHY on 2011-02-16
Tried your "best" solution for my Acer Aspire 5740 (no suffix) and I needed, in addition to what you suggested, to change the following line in /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

which disables acpi_video0.

This was listed in your reference website ([https://launchpad.net/~kamalmostafa/...l-mjgbacklight]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-mjgbacklight")) towards the bottom of the page but I must have missed the first few times around.

That being said, thanks JBud, my brightness controls are now working perfectly!

---

### Post by robertbub on 2011-06-01
I have an Aspire 5740-5513 and I tried[LIST]
[*]acpi_osi=Linux
[*]acpi_osi=
[*]acpi_backlight=vendor
[/LIST]and none of 'em allow either the brightness applet nor the Fn-left/Fn-right keys to work.

I appear to be running *2.6.32-32-generic-pae* on Lucid Lynx.  The X Windows appears to be```
ii  xserver-xorg-video-intel 2:2.11.0-1ubuntu1~xup  Org X server -- Intel i8xx, i9xx display d
```Does this mean that I'm out of luck?

---

### Post by niko123456 on 2011-08-10
Many thanks to post #8 for solving my issue on my Acer Aspire 5741.

---

### Post by beepyou on 2011-08-13
> **niko123456 said:**
> Many thanks to post #8 for solving my issue on my Acer Aspire 5741.

#8 worked for me as well. The other solutions didn't work.

---

### Post by phuongdt3 on 2011-08-13
> **JBud said:**
> Hi, did you try the above suggestion? (adding 'acpi_osi=' to grub params)

Im having similar problems,thanks

---

