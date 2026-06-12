---
title: "uninstalled programs"
date: 2009-10-03
forum: General Help
---

### Post by gadolinio on 2009-10-03
Hello. I'm running ubuntu from a 2GB SD card and want to have more free space. I removed several packages from synaptic, which were supposed to give me 175 MB extra space, but i seem to have the same amount of free disk space, as Nautilus shows the same number of MB. I wonder that could be due to the removed programs still being stored somewhere, although uninstalled. Even after rebooting, free space remains the same.
Does anyone know where those files are, in order for me to erase them?
Thanks in advance!

---

### Post by bumanie on 2009-10-03
You need to do a 'complete removal' to get rid of the config files. It may also help to try > sudo apt-get autoclean and maybe > sudo apt-get autoremove to try to free up some space

---

### Post by ibuclaw on 2009-10-03
Four things you could try.
```
sudo apt-get install localepurge gtkorphan
```
Setup localepurge for your language, and what will happen is that after installing software, any unneeded locale manuals will be removed, loosing potentially 50MBs+ of unneeded files.

Run gtkorphan by going to **System->Administration->Remove Orphaned Packages**
In Options, selected "Show uninstalled packages with orphaned configuration" and "Show all orphaned packages".

Select the packages you wish to remove, and press 'OK'. Your mileage may vary on how much is removed, as it is dependant on how long you have had Ubuntu installed/how many apps you've tried.

Next, the obvious thing:
```
sudo apt-get clean
```
To remove all the downloaded packages cache.

Lastly:
```
gksudo gedit /etc/fstab
```
And put this at the bottom of the file:
```

tmpfs /var/log tmpfs defaults,noexec,nosuid 0 0
tmpfs /tmp tmpfs defaults,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,mode=1777 0 0

```
Save, then reboot.

The directories /tmp, /var/tmp and /var/log will now be on a temporary filesystem to whom's data will not be persistent after rebooting.

This means you can delete all data kept in there too. from another OS.

That should give you plenty food for thought.
The only other alternative after that is having a good look at what you use/don't use and just removing what you do not require.

Regards
Iain

---

### Post by gadolinio on 2009-10-06
Thanks a lot! that let me free a nice amount of space... Thanks, both of you.

---

