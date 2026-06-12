---
title: "firefox weird in lucid"
date: 2010-06-12
forum: General Help
---

### Post by God Of Atheism on 2010-06-12
Hi,

My wife has some trouble with firefox in lucid. Often it does not react or after a delay, this includes typing - for example a url, and switching tabs. At first I thought a hardware problem to be the cause, since her computer is old. After checking I did find at least one of her usb ports not working which could be an indicator of more general motherboard issues. Furthermore there are some boot and reboot issues every now and then. The issues in firefox do not appear in opera however, nor in typing in other applications.

I also thought of her keyboard connector being problematic, I already changed her keyboard a short while ago because of these issues and the new one seemed to behave a bit better. Now using my usb keyboard the same problems are still present though. But can hardware issues affect only firefox? The computer does seem rather hot as well, but again, I'd expect issues also in, for example, Opera.

Furthermore, when starting firefox, 3 processes start running, firefox, run-mozilla.sh and firefox.bin, the latter taking a lot of cpu time (never below 50%) and thus probably being part of the problem. Is this normal? I can't recall having seen this in other oses including karmic and windoze.

---

### Post by lovinglinux on 2010-06-12
The high CPU usage is not normal, unless you have a page already opened with some heavy javascript or flash videos. The processes opened are normal tho.

I would check if there isn't any extension causing the problems. For instance Ghostery was causing low performance when switching tabs recently. Additionally, check if you have the proper hardware driver for your video card installed.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by pete1983 on 2010-06-12
I had many of the same problems and had to optimize my flash and java, but first check your extensions and make sure they are not causing the problems. Try removing them and see what happens next try changing video drivers if that fails this might work for you to. . 
below is what i had to do in order for firefox to run properly on my computers.

[COLOR="Yellow"]In terminal type[/COLOR]
sudo gedit /etc/init.d/ondemand

[COLOR="Yellow"]then paste inside the file[/COLOR]

for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
do
[ -f $CPU_THRESHOLD ] || continue
echo -n 40 > $CPU_THRESHOLD
done

[COLOR="Yellow"]It Should look like this when u finish [/COLOR]

case "$1" in
    start)
     start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
 sleep 60 # probably enough time for desktop login

 for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
 do
  [ -f $CPUFREQ ] || continue
  echo -n ondemand > $CPUFREQ
 done

 for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
 do
  [ -f $CPU_THRESHOLD ] || continue
  echo -n 40 > $CPU_THRESHOLD
 done
 ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

Firefox does run a bit heavy on my computers however you can reduce its usage by not running multiple windows.

Good luck hope this is a help.

---

### Post by Adela on 2010-06-12
Try running Firefox in Safe Mode - open the folder for Mozilla Firefox  in your Start menu and choose Mozilla Firefox 9Safe mode). If this  works, then try disabling all of your add-ons and clearing your  temporary internet files in Firefox.

---

### Post by God Of Atheism on 2010-06-12
> **pete1983 said:**
> I had many of the same problems and had to optimize my flash and java, but first check your extensions and make sure they are not causing the problems. Try removing them and see what happens next try changing video drivers if that fails this might work for you to. . 
below is what i had to do in order for firefox to run properly on my computers.

[COLOR="Yellow"]In terminal type[/COLOR]
sudo gedit /etc/init.d/ondemand

[COLOR="Yellow"]then paste inside the file[/COLOR]

for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
do
[ -f $CPU_THRESHOLD ] || continue
echo -n 40 > $CPU_THRESHOLD
done

[COLOR="Yellow"]It Should look like this when u finish [/COLOR]

case "$1" in
    start)
     start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
 sleep 60 # probably enough time for desktop login

 for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
 do
  [ -f $CPUFREQ ] || continue
  echo -n ondemand > $CPUFREQ
 done

 for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
 do
  [ -f $CPU_THRESHOLD ] || continue
  echo -n 40 > $CPU_THRESHOLD
 done
 ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

Firefox does run a bit heavy on my computers however you can reduce its usage by not running multiple windows.

Good luck hope this is a help.

I'll try this. Now Opera has started to exhibit the same behaviour. After a restart it does however not increase immediately to those cpu usage levels. However, top shows a process named backend at high usage levels. What is that?

edit:
I found backend is the result of a bug in the system test (something I ran earlier on). A simple killing did the job.

Your solution does improve things greatly. Thanks.

Just to be sure I also added better privacy and deleted the lso cookies. I don't think it has an impact, but there where quite a few from the same site.

---

