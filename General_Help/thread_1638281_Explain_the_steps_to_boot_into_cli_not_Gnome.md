---
title: "Explain the steps to boot into cli not Gnome"
date: 2010-12-05
forum: General Help
---

### Post by e24ohm on 2010-12-05
Folks:
I am having a hard time understanding how to boot into the CLI, and not GNOME.

Do I use the following 
**sudo update-rc.d -f gdm remove**

Is there a special keyboard key like in windows (F8), to drop into the CLI before GNOME loads, and modify the xorg.conf file?

thanks.

---

### Post by sikander3786 on 2010-12-05
Do you permanently want to boot into command line instead of GUI? Or just on and off...

Pressing Ctrl + Alt + F1 upto F7 gives you a tty to work with. Even you can do that from your desktop.

Or do you want to remove the GUI permanently?

---

### Post by e24ohm on 2010-12-05
> **sikander3786 said:**
> Do you permanently want to boot into command line instead of GUI? Or just on and off...

Pressing Ctrl + Alt + F1 upto F7 gives you a tty to work with. Even you can do that from your desktop.

Or do you want to remove the GUI permanently?

I want to boot into the CLi with the option to load GNOME, I do not want to remove GNOME permanentaly. I want to just boot into the CLI and only load GNOME when I must need it...I think I use **startx &**, but i could be wrong.

----background information----
I have an older system, which doenes't run GNOME or XFCE to well. I have been getting items working in the CLI and that is really all that I need. 

For example: I do a lot with Cisco and Juniper equipment so MiniCom is all I really need, in addition to Vi, but recently I was able to add the needed Kernel and get sound drivers working in the Ubuntu mini install, so I am now using MP3Blaster to listen to my tunes from the cli, and I was even able to get mplayer to play my Audio cds and my .avi files; however, it plays my .avi in ASCII art - talk about a Surrealist art work.

---

### Post by sikander3786 on 2010-12-05
If thats the case, the command you mentioned above should do it.

```
sudo update-rc.d -f gdm remove
```

---

### Post by e24ohm on 2010-12-05
> **sikander3786 said:**
> If thats the case, the command you mentioned above should do it.

```
sudo update-rc.d -f gdm remove
```

I originally install Ubuntu mini, and then installed gnome; however, now when the machien boots, I get a black screen.

Is there a keyboard key that I can hit during boot, to drop me to a cli before the GNOME boots, so I can modify the needed files?

---

### Post by sikander3786 on 2010-12-05
Try to press and hold down Shift key at your Bios screen until you see the Grub menu. There is a Recovery option (2nd on the list), select that and Drop to Root Shell.

However, I'm a bit confused by your problem as I actually don't understand what the problem is. You want to get rid of Gnome or your want to repair Gnome? You are getting a black screen? Means you can neither see Gnome, nor the Terminal?

Recovery mode should work regarless of any queries above ;-) If you are using Grub Legacy, your desire key might be Esc. Newer versions of Ubuntu come with Grub2 so Shift key would work most probably.

---

### Post by sisco311 on 2010-12-05
> **e24ohm said:**
> I originally install Ubuntu mini, and then installed gnome; however, now when the machien boots, I get a black screen.

Is there a keyboard key that I can hit during boot, to drop me to a cli before the GNOME boots, so I can modify the needed files?

Assuming that you are using Grub2, hold down the Shift key during the bootup. When the Grub screen appears use the arrow keys to highlight the kernel you want to boot. Press e for edit and append the **linux** line with the **text** kernel parameter (you may want to remove the quiet and splash options in order to make the boot process verbose and disable the splash screen). Press Ctrl+x to boot.

To make the changes permanent, edit the file /etc/default/grub and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then run:
```
sudo update-grub
```
to generate a grub2 config file.

---

### Post by sisco311 on 2010-12-05
> **e24ohm said:**
> and I was even able to get mplayer to play my Audio cds and my .avi files; however, it plays my .avi in ASCII art - talk about a Surrealist art work.

Try using the framebuffer:
```
mplayer -vo fbdev -fs -vf scale=1024:768 path/to/file
```

You have to add your user to the video group:
```
sudo gpasswd -a username video
```
log out and log back in.

And you may have to change the resolution of the virtual consoles. Edit /etc/default/grub to something like:
```
...
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Resolution of the virtual consoles
GRUB_GFXPAYLOAD_LINUX=1024x768
...

```

run:
```
sudo update-grub
```
and reboot.

---

