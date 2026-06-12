---
title: "Problem with plymouth themes"
date: 2011-11-29
forum: General Help
---

### Post by vat with tux on 2011-11-29
Hi all.... 

I tried to change my plymouth theme using plymouth manager. 

But unfortunately after changing the theme now the only thing i can see while booting is black screen....

Please tell me that how can I fix this???

---

### Post by vat with tux on 2011-11-30
bump..... Atleast tell me that how to bring back default plymouth theme?

---

### Post by vat with tux on 2011-12-02
One more bump.... I have enabled debugging of plymouth and here are few lines of the log file which are causing trouble according to me.... please have a look and tell me any solution..... I'll be really thankful to u...:)


[HTML]
[main.c]                           show_default_splash:Showing splash screen 
[main.c]                    find_system_default_splash:Trying to load /etc/plymouth//plymouthd.conf 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory 
[main.c]                    find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf 
[main.c]              find_distribution_default_splash:Trying to load /lib/plymouth//plymouthd.defaults 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth//plymouthd.defaults: No such file or directory 
[main.c]              find_distribution_default_splash:failed to load /lib/plymouth//plymouthd.defaults 
[main.c]                           show_default_splash:Trying old scheme for default splash 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/default.plymouth' 
[ply-key-file.c]                      ply_key_file_load_groups:key file has no groups 
[ply-key-file.c]                             ply_key_file_load:was unable to load any groups 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[ply-boot-splash.c]                               remove_displays:removing pixel displays 
[ply-boot-splash.c]                               remove_displays:removing text displays 
[main.c]                           show_default_splash:Could not start default splash screen,showing text splash screen 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/text.plymouth' 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth/themes/text.plymouth: No such file or directory 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[ply-boot-splash.c]                               remove_displays:removing pixel displays 
[ply-boot-splash.c]                               remove_displays:removing text displays 
[main.c]                          show_detailed_splash:Showing detailed splash screen 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/details/details.plymouth' 
[ply-key-file.c]                       ply_key_file_load_group:trying to load group Plymouth Theme 
[ply-key-file.c]                      ply_key_file_load_groups:key file has no more groups 
[./plugin.c]                                 create_plugin:creating plugin 
[main.c]                             start_boot_splash:attaching plugin to event loop 
[main.c]                             start_boot_splash:attaching progress to plugin 
[main.c]      add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash 
[main.c]      add_displays_and_keyboard_to_boot_splash:adding pixel display on boot splash 
[main.c]      add_displays_and_keyboard_to_boot_splash:adding text display on boot splash 
[ply-terminal.c]                             ply_terminal_open:terminal /dev/tty7 is already open 
[main.c]                             start_boot_splash:showing plugin 
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen
[/HTML]

---

### Post by oldtimer7777 on 2011-12-03
Something is missing from your plymouth directory it seems..

Have you done a quick 

sudo apt-get install ubuntu-desktop 

to see if that reinstalls the missing packages?

> **vat with tux said:**
> Hi all.... 

I tried to change my plymouth theme using plymouth manager. 

But unfortunately after changing the theme now the only thing i can see while booting is black screen....

Please tell me that how can I fix this???

---

### Post by stinkeye on 2011-12-03
Had the same problem using plymouth-manager.

If you use the option "Make compatible with closed source video driver" it changes the original line in /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` 

to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=[COLOR="Magenta"]1680x1050-24[/COLOR],mtrr=3,scroll=ywrap  
```
[COLOR="magenta"]Your chosen vid res[/COLOR]


Changing back to original showed plymouth again, for me.
```
gksudo gedit /etc/default/grub
```

Then run..
```
sudo update-grub
```

You can change plymouth themes with
```
sudo update-alternatives --config default.plymouth
```

The default theme is
```
ubuntu-logo/ubuntu-logo.plymouth
```

After changing run...
```
sudo update-initramfs -u
```

---

### Post by vat with tux on 2011-12-07
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

line is as it is because i haven't used the option "Make compatible with closed source video driver".

---

### Post by vat with tux on 2011-12-14
Finally reinstalled system....:)

---

