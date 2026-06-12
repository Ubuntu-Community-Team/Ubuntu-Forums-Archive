---
title: "Can't boot : fsck error at splash screen"
date: 2011-04-27
forum: General Help
---

### Post by circumbendibus on 2011-04-27
I was just doing a normal Google image search and Ubuntu froze.  Now that I've rebooted, I can't get it to start at all.  Before starting it prints about a hundred "^[[26~" then loops flashes of the splash screen and different combinations of the following errors every time I reboot: 

```

fsck from util-linux-ng 2.17.2
/dev/sda1 has been mounted 26 times without being checked, check forced
/dev/sda1: clean, 329069/3588096 files, 7562/2432652
*Speech-dispatcher configured for user sessions
*Starting the Windbind daemon windbind

```

I had to type those myself (since I can't get my computer to do anything), so that might not be perfect. Evidently my <Scroll> button works, which is the only way I could see the errors. The only other response I can get is Ctrl-Alt-Delete to reboot, and sometimes those buttons individually slow the scrolling down. On one of the reboots the errors between splash screens were about four pages of different things like "can't open splash screen," but I haven't been able to reproduce it.

A Knoppix attempt did the same ^[[26~ thing interspersed with the loading info, then gets stuck in a loop of  6~6~6~6~.  At this point, hitting Ctrl-v seemed to reproduce the ^[[26~.  I also tried a live boot of Ubuntu, which did the same thing as before, and recovery mode made it to the standard language selection page for installation but got stuck in a loop there, so it seems like the system interprets a jammed key, though that doesn't physically seem to be the case.

Sorry if that was long, but that's about everything I can get.  To be honest, my computer is too old for Lucid, and I think I will do a clean install of Hardy, so I wouldn't mind just being able to recover the data.  Can I do that easily from another computer?

Thanks folks! :p

---

### Post by Hedgehog1 on 2011-04-28
If you boot your computer from a LiveCD/LiveUSB, you should be able to mount the hard drive and copy you data to another USB stick or USB drive.

Just a thought - if your hardware is that old, perhaps a new(er) PC might be advisable so you can join the rest of us in this century?  *Think of all the new UIs you can play with then...*   [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by circumbendibus on 2011-04-28
Thanks for the quick reply! That hedgehog clearly has an apatite.

So far nothing I've tried with a live boot has worked.  A normal live boot from a CD exhibited the same behavior and even the rescue option didn't get very far (yes, strangely the initial menu from the CD operated normally). I've had Ubuntu for more than a year, but I'm no expert.  So far I have found no way to mount anything or get to a terminal of any kind; it is simply not responsive.  Is there a trick I'm missing? I can't even find the GRUB menu.

The hardware itself seems to be fine: F2 and F10 at boot, for example.

---

### Post by Sceiron on 2011-04-28
How about trying to connect the disk to a windows machine and run chkdsk on it from the cmd-prompt?

---

### Post by circumbendibus on 2011-04-28
Seemed to me the "jammed key" issue might only affect a unix based system that way anyway, so connecting to a windows machine was one of my first thoughts. However I have no idea how to do it. I thought you needed firewire or something. I've not had any luck figuring out how to connect one computer to another. Maybe I should have starred in the beginners' forum. :shock:

---

### Post by circumbendibus on 2011-04-29
Update: for whatever reason, Knoppix now boots up if I wait long enough. However I can't manage to mount my hard drive: it thinks it's hda, but it is sda.  Clicking on the icon gives me "wrong fs type, bad option, bad superblock."  Running $locate sda claims sda exists in /dev, but it is clearly not there when I check.  Changing /etc/fstab didn't seem to do much, but I don't know if I'm doing it right. 

What is interesting now that I can type in the terminal every once in a while, it starts typing a bunch of c's, 9's, or ~'s.  Circuit City replaced my broken keyboard with an even worse one (turned out to be a sham on all fronts), but the physical keyboard doesn't seem to be causing the problem. Maybe there's a way to disable it during boot?

When I tried Ubuntu again (and the live boot does the same thing) it showed the same errors, but mashing Ctrl-c and Ctrl-v out of curiosity gets it to reproduce the other errors I mentioned.  I'll try to get these as best I can before my computer dies, but I have to tap the scroll button to get them and type them out by hand.

```

oup script
[ply-key-file.c]                           ply_key_file_load_groups:key file has no more groups
[main.c]                            start_boot_splash:attaching plugin to even loop
[main.c]                            start_boot_splash:attaching progress to plugin
[main.c]   add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash
[main.c]      add_displays_and_keyboard_to_boot_splash:adding pixel displays on boot splash
[main.c]          add_displays_and_keyboard_to_boot_splash:adding text display on boot splash
[main.c]                          start_boot_splash:showing plugin
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen

[./plugin.c]                              show_splash_screen:starting boot animation
[./plugin.c]                                    start_animation:parsing script file
[./plugin.c]                            start_script_animation:executing script file
[ply-label.c]                                   ply_label_free:Unloading label control plugin
[ply-label.c]                                   ply_label_free:Unloading label control plugin
[ply-label.c]                                   ply_label_free:Unloading label control plugin
[ply-label.c]                                   ply_label_free:Unloading label control plugin
[ply-label.c]                                   ply_boot_splash_free:freeing splash
[ply-event-loop.c]       ply_event-loop_stop_watching_for_timeout:no matching timeout found for removal
[ply-boot-splash.c]                       remove_displays:removing pixel displays
[ply-boot-splash.c]                       remove_displays:Removing 640x480 pixel display
[ply-boot-splash.c]                       remove_displays:Removing node
[ply-boot-splash.c]                       remove_displays:Removing text displays
[ply-boot-splash.c]                       remove_displays:Removing 80x30 text displays
[ply-boot-splash.c]                       remove_displays:Removing node
[main.c]                         show_detailed_splash:Showing detailed splash screen
[main.c]                           start-boot-splash:Loading boot splash theme '/lib/plymout/themes/details/detail.plymouth'
[ply-key-file.c]                             ply_key_file_load_group:trying to load group Plymouth Theme
[ply-key-file.c]                             ply_key_file_load_groups:key file has no more groups
[./plugin.c]                                            create_plugin:creating plugin
[main.c]                                      start_boot_splash:attaching plugin to eevnt loop
[main.c]                                      start_boot_splash:attaching progress to plugin
[main.c]                                add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash
[main.c]                                add_displays_and_keyboard_to_boot_splash:adding pixel display on boot splash
[main.c]                                add_displays_and_keyboard_to_boot_splash:adding tesxt display on boot splash
[ply-terminal.c]                          ply_terminal_open:terminal /dev/tty 7 is already open
[main.c]                              start_boto_splash:showing plugin
[ply-boot-spalsh.c]                     ply_boot_splash_show:showing splash screen

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 329069/3588096 files, 8027756/14326528 blocks
[ply-keyboard.c]                    process_keyboard_input:end escape key handler
[ply-keyboard.c]                    process_keyboard_input:escape key!
[main.c]                             on_escape_pressed:escape key pressed
[main.c]                 toggle_beteen_splash_and_details:hiding and freeing current splash
[./plugin.c]                      hide_splash_screen:hiding splash screen
[./plugin.c]                  detach_from_even_loop:detaching from event loop
[ply-boot-splash.c]           ply_boot_splash_free:freeing splash 
[ply-boot-splash.c]                       remove_displays:removing pixel displays
[ply-boot-splash.c]                       remove_displays:Removing 640x480 pixel display
[ply-boot-splash.c]                       remove_displays:Removing node
[ply-boot-splash.c]                       remove_displays:Removing text displays
[ply-boot-splash.c]                       remove_displays:Removing 80x30 text displays
[ply-boot-splash.c]                       remove_displays:Removing node
[main.c]                         show_default_splash:Showing detailed splash screen
[main.c]                        find_system_default_splash:Trying to load /etc/plymouth//plymouthd.conf
[ply-key-file.c]                      ply_key_file_open_filed:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory
[main.c]          find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf
[main.c]       find_distribution_default_splash:Trying to load /lib/plymouth//plymouthd.defaults
[ply-key-file.c]                      ply_key_file_open_filed:Failed to open key file /lib/plymouth//plymouthd.defaults: No such file or directory
[main.c]       find_distribution_default_splash:failed to load /lib/plymouth//plymouthd.defaults
[main.c]                     show_default_splash:Trying old scheme for default splash
[main.c]                start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/default.plymouth'
[ply-key-file.c]               ply_key_file_load_group:trying to load group Plymouth Theme
[ply-key-file.c]               ply_key_file_load_group:trying to load group script
[ply-key-file.c]               ply_key_file_load_group:key file has no more groups
[main.c]                start_boot_splash:attaching plugin to evetn loop
[main.c]                start_boot_splash:attaching progress to plugin
[main.c]   add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash
[main.c]      add_displays_and_keyboard_to_boot_splash:adding pixel displays on boot splash
[main.c]          add_displays_and_keyboard_to_boot_splash:adding text display on boot splash
[main.c]                          start_boot_splash:showing plugin
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen

```

There are a couple lines on either end of that, but I'd have to time the scroll button better, because the ends of it are where the splash screen flashes and then it loops.  Is that useful at all? It seems to be complaining about the splash not working, which does not seem to be the root of the problem.  

Is there an easy way to plug another computer into mine and treat mine like an external?  

Sorry Hedge, but you are talking to a poor soon-to-be-grad student who can't even afford the trip to school. (Although I think they give new laptops to their Phd students... ;))
_******_

---

### Post by circumbendibus on 2011-05-10
Maybe that was far too much information! I'll try once more for some advice on how to save the data on my drive.  I am almost completely unfamiliar with the details of mounting anything.  Knoppix confusing sda for hda seems like it would be a fairly common issue. Ideas?

---

