---
title: "Ubuntu 10.4 boot error"
date: 2010-06-23
forum: General Help
---

### Post by Taiga-kaka on 2010-06-23
Hey, guys! I'm new to Ubuntu and all this Linux stuff, so I'm a big newbie.

I'm using a Sony VAIO laptop and installed Desktop edition Ubuntu 10.4 on and I'm facing some issues.

First off, the main big issue is the booting part. Yesterday, when I tried to boot it, it was that big black screen with the blinking Underscore ( _ ) and then after a full minute or two, it starts to spam with "error" or something. Then, it boots to ubuntu screen, and tells me that it needs to run on low graphic, OR goes to the desktop screen with everything all super zoomed in.

Then, this morning, when I tried to turn it on, it began to boot and took longer than usual. After that, I turned it off and back on and it was like "something something /dev/ file not found." And couldn't even log in or anything.

Help?

---

### Post by davidmohammed on 2010-06-23
Hi there,
  welcome to ubuntu linux.

Can you try the following?

when booting, press shift to display a list of kernel entries - this is the grub menu. highlight the entry you want to boot, and hit the e key. Go to the kernel line - its the line with "quiet splash" at the end. add nomodeset immediately before quiet splash

i.e. ... nomodeset quiet splash --
Then hit CTRL-X to boot.

---

### Post by Taiga-kaka on 2010-06-23
Well, it does kind of log me in, but it still shows me a large long list of messages that says "error" and something like "open/dev/null: File not found" and such.

Also, I can't access Grub Menu any more neither. When I do press shift, it says Grub Opening or something, then goes back to all that error messages. Then, it says:

"Ubuntu is running in low-graphics mode"
"The following error was encountered, you may need to update your configurations to solve this.

(EE) Jun 23 22:43:42 NVIDIA(0): No display devices found for this X Screen.
(EE) Screen(s) found, but none have a usable configuration."

Also, I would like to make all these "errors" and something Killed message list on my boot screen to be fixed, thanks!

---

### Post by fragos on 2010-06-24
To get the optimum graphics drivers you need to run System-> Administration-> Hardware Drivers. Your system will be scanned and recommendations for video drivers will be made if available. Select the recommendation and it will be installed and set up for you. Boot times should be consistent on a given PC but every so often, every 30 boots I think, it will take longer while it checks your hard drive.

---

