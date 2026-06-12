---
title: "Clock Problems"
date: 2006-01-29
forum: General Help
---

### Post by thepocketdrummer on 2006-01-29
Whenever I run Kubuntu it messes up my Windows clock, I have to sync my clock every time I switch back to Windows.

Does anyone know how to fix this problem?

---

### Post by thepocketdrummer on 2006-01-29
Actually, now I'm having a lot of trouble syncing from windows. I'm pretty sure it has something to do with when I set up Kubuntu's clock. Should I have chosen local instead of GMT?

---

### Post by madmetal on 2006-01-29
same problem here.
ubuntu time is right but when switching to winxp its back to UTC.

---

### Post by Rumpty on 2006-01-30
I fixed my Windows/Kubuntu clock disagreements by going to /etc/default/rcS and changing the line UTC=yes to UTC=no. that may help you.

---

### Post by indus49 on 2006-02-01
I had the same issue. I believe it stems from your original install, when the setup program asks you to set up the time. The way I understand it, Windows uses local time, and I set U to use Greenwich Mean Time. The result? My Windows clock was always about 5 hours fast. Solution was as posted above, change UTC to "no" and reset your clock. I followed the instructions below for 5.10 (Breezy Badger:)

Open a terminal and log in as root.
Type: sudo gedit /etc/default/rcS and hit [Enter]
Edit UTC=yes so it reads UTC=no
Save the edited file and close it.
Click System -> Administration -> Time and Date
Set the correct time/date
In the terminal type: sudo /etc/init.d/hwclock.sh restart and hit [Enter]

---

### Post by nrwilk on 2006-02-01
Just to be clear for those who may search on this topic sometime in the furture.

When installing, if you are going to dual-boot, definitely use the "local" option during installation.

If you will be using ubuntu/Kubuntu with no other systems, then you can use either option.

---

