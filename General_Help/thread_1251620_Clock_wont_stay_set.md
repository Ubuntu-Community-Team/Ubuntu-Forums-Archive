---
title: "Clock wont stay set"
date: 2009-08-27
forum: General Help
---

### Post by MistaMista on 2009-08-27
My clock in ubuntu wont stay set in ubuntu or vista.......i am going nuts....can anyone help!!!

---

### Post by blueridgedog on 2009-08-27
Is it random or only on a reboot?

If it is on a reboot, then it could be a bad/buggy/off hardware clock in the bios of your system.

You can compare the two (your hardware/bios clock and your system clock) with:
```

~$ sudo hwclock 
Thu 27 Aug 2009 10:29:45 PM EDT  -0.062622 seconds
~$ date
Thu Aug 27 22:30:05 EDT 2009
```

 You can use the hwclock command (with sudo) to set your hardware clock to the system clock or vis versa:
```

       hwclock -w or hwclock --systohc 
       hwclock -s or hwclock --hctosys
```

---

### Post by MistaMista on 2009-08-27
i think i am typing these commands wrong


  hwclock -w or hwclock --systohc 
       hwclock -s or hwclock --hctosys

---

### Post by Villiam on 2009-08-27
You can try unchecking synchronize time. "administration- untick periodically syncronize clock with internet servers"

---

### Post by blueridgedog on 2009-08-27
They would be:

```
sudo hwclock --systohc
```

To set the system clock to the hardware clock (pc time to bios time if you will)

```
sudo hwclock --hctosys
```

To set the hardware clock to the system clock (the most common use of the command, assuming you have set your system time to suit you).

---

### Post by MistaMista on 2009-08-27
ok.............i typed in the commands now it says only the superuser can change the clocks

---

### Post by MistaMista on 2009-08-27
ok.........i didnt have the internet sync checked......so  i checked it and i got this message when trying to download the ntp sumthing.......E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

---

### Post by sailthesea on 2009-08-27
Thats OK Enter your password It won't show up 
Be careful what you type in terminal after sudo though You will have root privilege for a few minutes Typos BAD!
 And welcome:)

---

### Post by MistaMista on 2009-08-27
where do i go from here






mista@mista-laptop:~$ hwclock systohc
hwclock - query and set the hardware clock (RTC)

Usage: hwclock [function] [options...]

Functions:
  --help         show this help
  --show         read hardware clock and print result
  --set          set the rtc to the time given with --date
  --hctosys      set the system time from the hardware clock
  --systohc      set the hardware clock to the current system time
  --systz        set the system time only
  --adjust       adjust the rtc to account for systematic drift since 
                 the clock was last set or adjusted
  --getepoch     print out the kernel's hardware clock epoch value
  --setepoch     set the kernel's hardware clock epoch value to the 
                 value given with --epoch
  --version      print out the version of hwclock to stdout

Options: 
  --utc          the hardware clock is kept in coordinated universal time
  --localtime    the hardware clock is kept in local time
  --rtc=path     special /dev/... file to use instead of default
  --directisa    access the ISA bus directly instead of /dev/rtc
  --badyear      ignore rtc's year because the bios is broken
  --date         specifies the time to which to set the hardware clock
  --epoch=year   specifies the year which is the beginning of the 
                 hardware clock's epoch value
  --noadjfile    do not access /etc/adjtime. Requires the use of
                 either --utc or --localtime
  --adjfile=path specifies the path to the adjust file (default is
                 /etc/adjtime)
hwclock takes no non-option arguments.  You supplied 1.
mista@mista-laptop:~$

---

### Post by jasonsjunk on 2009-08-27
I think this will fix the issue you are having.  Windows and Linux use the hardware clock in different ways and they are fighting each other.  

[http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/](http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/)

---

### Post by MistaMista on 2009-08-27
i solved the clock problem ubuntu...now my clock jus wont stay set in vista

---

### Post by MistaMista on 2009-08-27
ok...now when i started ubuntu my clock was right and then  seconds later it jumped back  2 hrs

---

