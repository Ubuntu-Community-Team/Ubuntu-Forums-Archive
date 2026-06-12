---
title: "using cdrom locks up system"
date: 2010-02-19
forum: General Help
---

### Post by chumley1970 on 2010-02-19
whenever i try to burn mp3 from a disk in the cdrom, the system will freeze up solid, keyboard, screen, mouse, the whole shebang. ubuntu will see an audio disk in the cdrom, and i can play some tracks off it (sometimes), but trying to copy it to mp3s will crash everything after about 2-3 minutes. somewhere between tracks 2 - 4. anyone else have issues? i have tried a different cdrom, and cables... and i hate to say it but it works under windows. anyone?

---

### Post by MooPi on 2010-02-19
What program are you using to burn your audio CD ? Are you using mp3's or ogg files ?
Next time you start up your burning software start the application from terminal. This way when or if it has trouble the terminal will give error reports.

---

### Post by chumley1970 on 2010-02-19
i tried ripit in a terminal. same results.

---

### Post by MooPi on 2010-02-20
I'm not familiar with "ripit" but it sounds as if your CD is damaged or marred and the CD-rom is have trouble reading. Try to turn off error correction in ripit to see if you can finish. Another alternative would be to try an app called "cdparanoia". You can install cdparanoia with synaptic or in terminal with apt-get. The command in terminal to rip a CD is ```
cdparanoia -B -Z
``` This command will ignore error correction during the rip of the CD.

---

### Post by chumley1970 on 2010-02-20
tried cdparanoia -A to analize the drive, it started well, then locked everything up. the end of syslog says ominous things:


Feb 20 12:38:25 tim-desktop kernel: [  207.398678] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 20 12:38:25 tim-desktop kernel: [  207.398687] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Feb 20 12:38:25 tim-desktop kernel: [  207.398693] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Feb 20 12:38:25 tim-desktop kernel: [  207.398705] end_request: I/O error, dev sr0, sector 0
Feb 20 12:38:25 tim-desktop kernel: [  207.398711] __ratelimit: 3 callbacks suppressed
Feb 20 12:38:25 tim-desktop kernel: [  207.398714] Buffer I/O error on device sr0, logical block 0
Feb 20 12:38:25 tim-desktop kernel: [  207.398719] Buffer I/O error on device sr0, logical block 1
Feb 20 12:38:25 tim-desktop kernel: [  207.398724] Buffer I/O error on device sr0, logical block 2
Feb 20 12:38:25 tim-desktop kernel: [  207.398728] Buffer I/O error on device sr0, logical block 3
Feb 20 12:38:25 tim-desktop kernel: [  207.398731] Buffer I/O error on device sr0, logical block 4
Feb 20 12:38:25 tim-desktop kernel: [  207.398735] Buffer I/O error on device sr0, logical block 5
Feb 20 12:38:25 tim-desktop kernel: [  207.398738] Buffer I/O error on device sr0, logical block 6
Feb 20 12:38:25 tim-desktop kernel: [  207.398742] Buffer I/O error on device sr0, logical block 7
Feb 20 12:38:25 tim-desktop kernel: [  207.398745] Buffer I/O error on device sr0, logical block 8
Feb 20 12:38:25 tim-desktop kernel: [  207.398748] Buffer I/O error on device sr0, logical block 9
Feb 20 12:38:25 tim-desktop kernel: [  207.400256] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 20 12:38:25 tim-desktop kernel: [  207.400262] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Feb 20 12:38:25 tim-desktop kernel: [  207.400266] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Feb 20 12:38:25 tim-desktop kernel: [  207.400273] end_request: I/O error, dev sr0, sector 0
Feb 20 12:38:25 tim-desktop kernel: [  207.442074] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 20 12:38:25 tim-desktop kernel: [  207.442083] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Feb 20 12:38:25 tim-desktop kernel: [  207.442090] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Feb 20 12:38:25 tim-desktop kernel: [  207.442101] end_request: I/O error, dev sr0, sector 0
Feb 20 12:38:25 tim-desktop kernel: [  207.443586] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 20 12:38:25 tim-desktop kernel: [  207.443591] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Feb 20 12:38:25 tim-desktop kernel: [  207.443595] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Feb 20 12:38:25 tim-desktop kernel: [  207.443601] end_request: I/O error, dev sr0, sector 0
Feb 20 12:38:25 tim-desktop kernel: [  207.446166] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 20 12:38:25 tim-desktop kernel: [  207.446172] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Feb 20 12:38:25 tim-desktop kernel: [  207.446177] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Feb 20 12:38:25 tim-desktop kernel: [  207.446184] end_request: I/O error, dev sr0, sector 0
Feb 20 12:38:59 tim-desktop pulseaudio[1938]: ratelimit.c: 8 events suppressed
Feb 20 12:39:42 tim-desktop ntpd[1623]: synchronized to 128.118.25.3, stratum 2
Feb 20 12:39:42 tim-desktop ntpd[1623]: kernel time sync status change 2001

any ideas?

---

### Post by MooPi on 2010-02-20
Have you tried to rip a CD yet ? Try that and see what happens. Do you have any other CD's to test?

---

### Post by chumley1970 on 2010-02-20
tried to rip another cd. same results.

---

### Post by brent_weaver on 2010-03-02
Hey guys - did this ever get resolved? I cannot use my cdrom drive.

---

### Post by chumley1970 on 2010-03-13
still cant use cdrom. i waited for a kernel update, hoping against hope that that would fix it. still no joy.

---

