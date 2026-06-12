---
title: "Lucid Lynx experience"
date: 2010-06-02
forum: General Help
---

### Post by rajn on 2010-06-02
Fresh install of Lucid is a nightmare for computers with intel815 chipsets.

1. For those lucky after fresh install to get a blank purple screen and nothing else. 


2. For those whose Cap and Scroll lock indicators flash while logging out on a blank lighted screen


*Working with an older version of kernel during boot did not help and the above patterns reappeared.
*I doubt changing modeset to 1 will help because i915.kms file does not exist in the latest Lucid install.
*xorg needs to be changed to be able to get the desired screen resolution. see [http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466](http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466)


Work around for 1: alt-F2 and then 'killall gnome-panel'.


work around for 2: from term type "sudo shutdown -h now".

I will appreciate if someone can help with a better solution than these workaround.

---

### Post by dino99 on 2010-06-02
remove xorg.conf if it exist: sudo rm -f /etc/X11/xorg.conf

add this ppa to synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

use i915.modeset=0 into /etc/default/grub, then update-grub

---

### Post by rajn on 2010-06-02
Thanks Dino,
I am away from my computer but will try your solution in the evening.

Why are you asking me to remove xorg.conf.
I made this new file both in Karmic and in Lucid because I was getting a 480x640 screen size instead of 786x1024. After making the new xorg.conf with appropriate modifications I am now able to get full screen.

However, as I have posted earlier, when I boot up, immediately after grub gets loaded I get a black screen saying:

No mode found
No terminal found

But it proceeds to launch me into a desktop (for Karmic) while for (Lucid) I have to kill gnome-panel and restart it. 
Moreover, I am also curious to know why the Caps and Scroll lock LED blink during log out which never happened in Karmic.

Thanks

---

### Post by rajn on 2010-06-02
Made changes as recommended by Dino99.

removed xorg.conf

Then: $sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 Next :$sudo apt-get update

Next modified grub file in /etc/default/grub 
commented the line 'quiet splash' and replaced it with 'i915. modeset =0'

then:$sudo update-grub.

Rebooted.
Now the screen is back to 640x480 and with no options for 1024x786.:(

Also as usual only purple Lucid background is seen and only when I right click I see a menu to make new folders etc. But nothing else. It is blank as ever.

Tried i915.modeset =1 but no difference.

Had to resort to the magical 'killall gnome-panel'
Had to resort to the magical 'xorg.conf' to get back the screen.

Did the changes do anything?:)

Yes one positive change so far and "keeping my fingers crossed" is that on logging out; 
- no more Cap and Scroll LED blinking with a glowing blank screen i.e., able to get a good complete shutdown.



I have a Vaio FX220, 500Mb RAM and 80Gb hard-disc with only Lucid on it.Graphics card is VGA Intel 815 chipset.

Thanks Dino99.

---

### Post by JustinR on 2010-06-02
If I'm not mistaken, Ubuntu doesn't use Xorg.conf anymore.

---

### Post by rajn on 2010-06-02
Quite correct. I did not have xorg.conf. And therefore I created it. It seems that if it exists then Ubuntu does use it because my screen resolution problem is resolved. 

However, I said a few things in my last post a bit too hastily.

1. The blinking and hangup while logging out has reappeared. So what caused it to reappear? Re-installing xorg.conf? 

Again I removed xorg.conf and I get a proper shutdown but no good screen resolution. Even changed the screen resolution to 1024x768 in the grub file but no change.

2. instead of commenting "quiet splash" and replacing by "i915.modeset=0" I have now
"quiet splash i915.modeset=0" and now the screen is no more Lucid purple background but I have all the menu bars I need + purple background of Lucid and no more "killall gnome-panel". 

Therefore, looks like one problem solved. Can someone please help me with the screen resolution without having to create an xorg.conf file? 
Thanks

---

### Post by chupachups on 2010-06-26
was there a fix for this problem ?

I have a compaq en sff, pentium 3, with intel 815 graphics onboard

fresh install of lucid results in a purple screen and mouse pointer but with no menus (unless I right click, and then options appear)

was working correctly on jaunty and karmic, although I needed a NoAccel fix to xorg.conf in jaunty, but no changes needed for karmic (if I remember correctly)

tried some of the suggestions with grub2/kms/modeset etc, but nothing works

---

### Post by rajn on 2010-06-28
> **chupachups said:**
> was there a fix for this problem ?

I have a compaq en sff, pentium 3, with intel 815 graphics onboard

fresh install of lucid results in a purple screen and mouse pointer but with no menus (unless I right click, and then options appear)

was working correctly on jaunty and karmic, although I needed a NoAccel fix to xorg.conf in jaunty, but no changes needed for karmic (if I remember correctly)

tried some of the suggestions with grub2/kms/modeset etc, but nothing works

If you see a purple screen looks like everything is fine. Just do this
Alt-F2.
Then type
killall gnome-panel.
If it gets corrected then go to system>preferences>startup apps>options and then choose
"remember configuration after logging out"
And you should be running fine.
I may not have accurately written the commands above but I hope you will not have any problems. Please post if the problem is solved

---

