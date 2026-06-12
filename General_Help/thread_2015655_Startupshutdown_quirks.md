---
title: "Startup/shutdown quirks"
date: 2012-07-03
forum: General Help
---

### Post by cipherboy_loc on 2012-07-03
While generally I would post each of these separately, I have the feeling they are all related somehow.

Firstly, I don't get a "graphical" start with an Ubuntu loading screen. Instead, I get a black screen with text scrolling.
Secondly, around 11.04 (I update, not reinstall), the halt and shutdown commands stopped work (shutdown -h). Instead, the system would shut down normally, and at the end of the shutdown process, would just print "system halted" and hang, power light still on, etc. Only way to fix this was to hold the power button (disks were shut off, so no data was ever lost). Since I run fluxbox and not gnome (too heavy for my system), I have to exit fluxbox to the login page and shut down from there if I want to completely power it off.
Thirdly, just like on start, stop doesn't have a graphical shutdown. Instead, I see more white text on a black background. 

System specs:
```

$ lspci | grep VGA
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
$ dpkg --list | grep nvidia
ii  nvidia-96-modaliases                                        96.43.19-0ubuntu1                       Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-cg-toolkit                                           3.0.0016-0ubuntu1                       Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                                               1:0.2.44                                Find obsolete NVIDIA drivers

```Relevant part of /boot/grub/grub.cfg:
> 
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-l
inux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 0a55d619-7f9c-419e-b955-04ccaa26
e54d
        linux   /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=0a55d619-7f9c-419e-
b955-04ccaa26e54d ro   
        initrd  /boot/initrd.img-3.2.0-25-generic-pae
}
Any ideas?

Thanks,
Cipherboy

---

### Post by matt_symes on 2012-07-03
Hi

Do you have plymouth installed ? Do you have it configured to run in grub ?

Can you post the output of 

```
cat /etc/default/grub
```

To shutdown your PC try the poweroff option

```
sudo shutdown -P now
```

or 

```
sudo poweroff
```

Kind regards

---

### Post by cipherboy_loc on 2012-07-03
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Looks like the GRUB_TERMINAL line is commented out. 


As for plymouth, it is installed, not sure how to check whether it is enabled or not. 


Cipherboy

---

### Post by matt_symes on 2012-07-03
Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Enter your password. It will not be echoed to the screen.

Scroll down to the line that says...

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```and change it so it says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Pres ctrl + o to save and ctrl + x to exit.

The type 

```
sudo update-grub
```Wait for that to finish.

Then reboot your PC. You you see the plymouth splash screen ?

Kind regards

---

### Post by cipherboy_loc on 2012-07-03
Ah, thank you. Forgot about that option.

---

### Post by matt_symes on 2012-07-03
Hi

Did poweroff or shutdown -P help ?

Kind regards

---

### Post by cipherboy_loc on 2012-07-03
Yes, both things worked, thank you.

Marking as solved,
Cpherboy

---

