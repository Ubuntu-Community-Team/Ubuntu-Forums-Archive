---
title: "Ubuntu wacked my clock!!"
date: 2010-01-29
forum: General Help
---

### Post by ManyBeers on 2010-01-29
Gateway desktop running Win7 Home Premium 32 bit on Sda1
I recently installed Ubuntu 9.10 64 bit on SDb1(second hd)
They boot independently of each other via my Gateway allowing 
F10 key boot selection. Anyways ever since installing Ubuntu
4-5 days ago when I shutdown and boot into Win7 my clock in 
Windows is ahead 7 hours. Why does Ubuntu **** up my clock? 
And can somebody help me fix this anomaly?

---

### Post by tom.swartz07 on 2010-01-29
> **ManyBeers said:**
> Gateway desktop running Win7 Home Premium 32 bit on Sda1
I recently installed Ubuntu 9.10 64 bit on SDb1(second hd)
They boot independently of each other via my Gateway allowing 
F10 key boot selection. Anyways ever since installing Ubuntu
4-5 days ago when I shutdown and boot into Win7 my clock in 
Windows is ahead 7 hours. Why does Ubuntu **** up my clock? 
And can somebody help me fix this anomaly?

I dont think its Ubuntu thats messing up the clock, but you could check the settings in the BIOS- you have to hit esc, F10, something when you first power up your computer.


My gut reaction would be to say to setting your Win 7 to check internet time.

Either your Win 7 is just not keeping up because its powered off, or the battery on the onboard clock is dead.

---

### Post by ManyBeers on 2010-01-29
> **tom.swartz07 said:**
> I dont think its Ubuntu thats messing up the clock, but you could check the settings in the BIOS- you have to hit esc, F10, something when you first power up your computer.


My gut reaction would be to say to setting your Win 7 to check internet time.

Either your Win 7 is just not keeping up because its powered off, or the battery on the onboard clock is dead.

My Win7 has always been set to synch with Internet servers and has never been off. 

If the onboard clock was dead how come Ubuntu shows the correct time when it boots?

---

### Post by tom.swartz07 on 2010-01-29
> **ManyBeers said:**
> My Win7 has always been set to synch with Internet servers and has never been off. 

If the onboard clock was dead how come Ubuntu shows the correct time when it boots?

Ubuntu also gets the time from a network clock. 

Are you sure that Win 7 is syncing with a network clock? If it was, it should update once youre online. Right?

---

### Post by ManyBeers on 2010-01-29
> **tom.swartz07 said:**
> Ubuntu also gets the time from a network clock. 

Are you sure that Win 7 is syncing with a network clock? If it was, it should update once youre online. Right?

Windows is set to synchronize once a week. It is a scheduled task.
I checked the BIOS clock and it is correct.And then i booted into Ubuntu and it shows the correct time. Then i booted into Windows and it is 7 hours ahead again. 
I have a laptop which dual-boots both WindowsXP and Ubuntu 8.04
and I have never had this problem.

---

### Post by tom.swartz07 on 2010-01-29
> **ManyBeers said:**
> Windows is set to synchronize once a week. It is a scheduled task.
I checked the BIOS clock and it is correct.And then i booted into Ubuntu and it shows the correct time. Then i booted into Windows and it is 7 hours ahead again. 
I have a laptop which dual-boots both WindowsXP and Ubuntu 8.04
and I have never had this problem.

My best guess would be to simply change the update interval for the NTP to every time you boot up.

Quite honestly, I cant see any reason that your clock is screwing up in Windows.

One cannot say that Ubuntu is changing the clock, as Ubuntu has no reason (or permissions) to access your Windows 7 partition. It must be something going on with your Windows OS.

---

### Post by ManyBeers on 2010-01-29
> **tom.swartz07 said:**
> My best guess would be to simply change the update interval for the NTP to every time you boot up.

Quite honestly, I cant see any reason that your clock is screwing up in Windows.

One cannot say that Ubuntu is changing the clock, as Ubuntu has no reason (or permissions) to access your Windows 7 partition. It must be something going on with your Windows OS.

Well what I've done is set Ubuntu to manual in the Time&Date settings, and Not to Synchronize with an Internet time server.
Maybe that will help. 

I just booted Windows twice to make sure it's Time was correct
OK. Then i booted ubuntu and changed it's time setting to manual
rebooted and checked the Bios clock and it was ahead 7 hours.
But this time since I have added an additional task to Windows Time Synch task(Synch on Startup) I watched the clock change from incorrect time to correct time as the desktop loaded.

Hopefully it is fixed. 

I have just noticed another problem when booting Ubuntu9.04
before it proceeds with the boot sequence it displays this stuff
Disabling IRQ11 or IRQ11. It varies. Do you know why
And after a minute or two of this it boots normally.

---

### Post by tom.swartz07 on 2010-01-29
> **ManyBeers said:**
> Well what I've done is set Ubuntu to manual in the Time&Date settings, and Not to Synchronize with an Internet time server.
Maybe that will help. 

I just booted Windows twice to make sure it's Time was correct
OK. Then i booted ubuntu and changed it's time setting to manual
rebooted and checked the Bios clock and it was ahead 7 hours.
But this time since I have added an additional task to Windows Time Synch task(Synch on Startup) I watched the clock change from incorrect time to correct time as the desktop loaded.

Hopefully it is fixed. 

I have just noticed another problem when booting Ubuntu9.04
before it proceeds with the boot sequence it displays this stuff
Disabling IRQ11 or IRQ11. It varies. Do you know why
And after a minute or two of this it boots normally.

Great! Glad to hear it!

Let it do its thing for a few days and see if anything changes.

If not, thread solved!

---

### Post by ManyBeers on 2010-01-30
> **tom.swartz07 said:**
> Great! Glad to hear it!

Let it do its thing for a few days and see if anything changes.

If not, thread solved!

I found out what the problem was. Ubuntu was using UTC time when it should be set to use local time. Anyways it's complicated but here is a screenshot of what needed to be changed. 
The UTC entry must be set to NO.

---

### Post by jamesisin on 2010-01-31
Alternatively you could fix Windows.  Windows doesn't know, by default, that your BIOS is set using UTC.  You can fix that with a registry change:

[http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx)

Pretty easy.  The advantage of fixing Windows is that should you decide to boot up any other operating systems you will not have to break them to conform to Windows.

---

