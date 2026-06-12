---
title: "disk space problems"
date: 2006-05-29
forum: General Help
---

### Post by blckfx on 2006-05-29
hi everyone,

i have a fujitsu siemens t series tablet pc that doesnt have any sort of removable media and doesn't support usb booting. it came with a xp tablet edition preinstalled onto it. i wanted to install ubuntu so i did a network install but i overlooked the version i was downloading and realized that i had set up hoary instead of breezy. then, i changed the sources.list to contain the breezy repositories rather than the hoary ones, and performed the dist upgrade command. breezy was up and running with no problems at all. i then installed some additional packages using synaptic.

a week after i first set up breezy, today that is, i booted the computer and the gnome login screen appeared. i entered my username and password and it gave an error saying "GDM could not write to your authorization file. This could mean that you are out of disk space, or that your Home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your systems administrator."

i switched to the regular command line with ctrl+alt+f1 and logged in with no problem. then i entered the "sudo apt-get clear" command. after that, i switched back to the x display and logged in without any problems. i opened the disk manager and to my surprise saw that 99% of my hard disk was used.

now, my hard disk is 55 GB. the packages downloaded for hoary and breezy were each around 600 MB. the pakages i installed after breezy was running only held about 1 GB at the most. When i add up all the sizes of all the folders under / , it is about 2 GB. my home folder is only 100 MB.

let alone all of these calculations, as i said before, the only way i can install new stuff is via my network connection. there is no way i downloaded anything close to 51 GB (that is the size of the hd partition). not even half of it considering that it may have been compressed.

can someone please help me? i really dont know what is taking up so much space and its rendering the computer unusable. 

thnx,
blckfx

---

### Post by mcduck on 2006-05-29
[QUOTE=blckfx]hi everyone,

i have a fujitsu siemens t series tablet pc that doesnt have any sort of removable media and doesn't support usb booting. it came with a xp tablet edition preinstalled onto it. i wanted to install ubuntu so i did a network install but i overlooked the version i was downloading and realized that i had set up hoary instead of breezy. then, i changed the sources.list to contain the breezy repositories rather than the hoary ones, and performed the dist upgrade command. breezy was up and running with no problems at all. i then installed some additional packages using synaptic.

a week after i first set up breezy, today that is, i booted the computer and the gnome login screen appeared. i entered my username and password and it gave an error saying "GDM could not write to your authorization file. This could mean that you are out of disk space, or that your Home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your systems administrator."

i switched to the regular command line with ctrl+alt+f1 and logged in with no problem. then i entered the "sudo apt-get clear" command. after that, i switched back to the x display and logged in without any problems. i opened the disk manager and to my surprise saw that 99% of my hard disk was used.

now, my hard disk is 55 GB. the packages downloaded for hoary and breezy were each around 600 MB. the pakages i installed after breezy was running only held about 1 GB at the most. When i add up all the sizes of all the folders under / , it is about 2 GB. my home folder is only 100 MB.

let alone all of these calculations, as i said before, the only way i can install new stuff is via my network connection. there is no way i downloaded anything close to 51 GB (that is the size of the hd partition). not even half of it considering that it may have been compressed.

can someone please help me? i really dont know what is taking up so much space and its rendering the computer unusable. 

thnx,
blckfx[/QUOTE]
first thing I'd check is all the log files in /var/log.. If somethings wrong with your setup, error messages could make some log file to grow to insane sizes..

---

### Post by blckfx on 2006-05-29
[QUOTE=mcduck]first thing I'd check is all the log files in /var/log.. If somethings wrong with your setup, error messages could make some log file to grow to insane sizes..[/QUOTE]

the total size of /var/log is 10.3 MB. i doubt that that's the problem...

---

