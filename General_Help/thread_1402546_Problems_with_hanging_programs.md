---
title: "Problems with hanging programs"
date: 2010-02-09
forum: General Help
---

### Post by Magwish on 2010-02-09
Been a long time fan off ubuntu and never had any real problems.

Recently however i am starting to get some problems when using a usb harddisk mounted on /media/disk under 9.04(i want to update but not while there are problems, too scared the updater will hang and i lose my stuff).

The first time was when i downloaded a movie on usenet(legal in my country so please don't judge) that was split up in partX.rar files
but when i wanted to extract them (using the build in fileroller thing or unrar from a terminal screen/ctrl-alt-F1) it would hang without any error on a specific part of the extraction. I then tryd copying the files to my home drive but the copying would akso hang on a specific file. I found this strange since i used par2 files to check the files.
the process rar would stay until i rebooted(on shutting down it said that filemanager was still doing something and asked if i really wanted to logg of)
I decided to delete the file that was giving me problems copying and used PyPar2 to repair.
Afterwards there were no more problems with this so i soon forgot it.

Now with a diferent movie i was able to extract and play.
However on specific parts of the movie VLC hangs(no errors).
Then i tried to close the vlc screen that has the buttons on it, it would close but the XVideo output screen stays.
Afterwards i can open vlc again but cant play any files.
So i tried running it in a terminal, this gave me the same problems but no errors(exept 6 versions of libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 10) for PID 256) these errors where there before the hang.
So i closed the terminal screen thinking this would get rid of the XVideo since it was running under the terminal.
However on closing the terminal it transfered to init with the state futex_wait.
When i try to kill it it goes to state do_exit as a zombie for a couple off minutes before finaly going away(if i'm lucky).
I tried using the systemmonitor thing, htop, sudo killall vlc, sudo kill -KILL id, sudo kill -9 id.
But nothing seems to kill it.

In both cases when i try to go to /media/disk after this i get nothing. And the only way i could get vlc to go away was to shut down my computer(logging off did nothing).
I also ran a fsck on the disk since i had similar symptoms once where x would crash that was caused by a corrupt filesystem.

Please help me.

edit: it seems that if i wait a while /media/disk becomes accesable again

---

### Post by Magwish on 2010-02-10
[bump]

anyone?

---

### Post by Magwish on 2010-02-11
I am starting to think it is ether my usb disk or my cpu

yesterday i reconnected my /dev/md0 to transfer some files

the first time i started everything was alright but i had to go someplace so i turned my computer down.
Next when i start it up it gives I/O errors on on /dev/sdf1(the usb disk) and when booted into ubuntu and clicking on "160gb medium" to mount it, it tells me it cannot mount.
Thinking there may be some corruption on the disk i tried "sudo fsck /dev/sdf1 -f" and got a reply about it not being able to check it cus it tought it was a array.
So i go to the partition manager and this reported me that my disk was 2tb large(the size of the array) but the in use and free space were correct.

So as a last resort i rebooted and everything was fine.... until i tried to coppy the files from the usb disk to the array.  It hangs AGAIN at a certain file(actualy the same video file that made vlc hang).

So i would think there is something with the usb disk.

The other posibility would be the cpu.
I have a Q6600 2.4Ghz overclocked to 3Ghz with watercooling. A while ago my computer turned off and i saw that my water was almost gone.

So it might have gotten a hit.
But then again so could my primairy harddisk since that was also watercooled at the time so that might have gotten a hit too.

so 
CPU
USB disk
primairy disk
software

what do you guys suspect?

---

