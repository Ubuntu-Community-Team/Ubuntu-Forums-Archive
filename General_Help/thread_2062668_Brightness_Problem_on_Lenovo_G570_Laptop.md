---
title: "Brightness Problem on Lenovo G570 Laptop"
date: 2012-09-25
forum: General Help
---

### Post by amjjawad on 2012-09-25
Hi,

Lenovo G570, Core i5 2nd generation with 4GB RAM and Intel Graphics Card.

I have Lubuntu 12.04 x86_64 with 3.2.0-31-generic Kernel.

Tried this: [http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart)

and this: [http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g](http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g)

That did not work.

If I remember correctly, before I format and re-install, I managed to save the brightness so that when I reboot, I don't need to press Fn+Low Brightness Button.
Now, it is either TOO dim that I almost can see or TOO high which I hate.

I think there is some kind of conflict between:

acpi_video0
and
intel_backlight

/sys/class/backlight/acpi_video0
/sys/class/backlight/intel_backlight

However, not sure how to fix it?

I've seen some solutions to edit GRUB File but I didn't have to do that before, I just don't remember how it worked before without editing anything in GRUB File.

Thanks in advance!

---

### Post by amjjawad on 2012-09-30
It's been 4 days now :)

---

### Post by amjjawad on 2012-10-13
Two weeks now!!!

---

### Post by pqwoerituytrueiwoq on 2012-10-13
which of theses maxes your screen brightness
```
sudo basch -c "echo `cat /sys/class/backlight/acpi_video0/max_brightness` > /sys/class/backlight/acpi_video0/brightness"
``````
sudo bash -c "echo `cat  /sys/class/backlight/intel_backlight/max_brightness` >  /sys/class/backlight/intel_backlight/brightness"
```or which of theses turns it dim
```
sudo bash -c "echo 0 >  /sys/class/backlight/acpi_video0/brightness"
``````
sudo basch -c "echo 0 >  /sys/class/backlight/intel_backlight/brightness"
```

if you have to do both just say so

---

### Post by amjjawad on 2012-10-13
> **pqwoerituytrueiwoq said:**
> which of theses maxes your screen brightness
```
sudo basch -c "echo `cat /sys/class/backlight/acpi_video0/max_brightness` > /sys/class/backlight/acpi_video0/brightness"
``````
sudo bash -c "echo `cat  /sys/class/backlight/intel_backlight/max_brightness` >  /sys/class/backlight/intel_backlight/brightness"
```or which of theses turns it dim
```
sudo bash -c "echo 0 >  /sys/class/backlight/acpi_video0/brightness"
``````
sudo basch -c "echo 0 >  /sys/class/backlight/intel_backlight/brightness"
```

if you have to do both just say so

There is extra "c" in your commands but it's ok.

The first two both maximize the brightness.

The last one makes it TOO dim so the third is better.

Now, I don't think any of these will save the brightness until I reboot and login again, right? the whole point is, I can't save the brightness. Everytime I login, I need to reduce the brightness.

Thanks for your reply :)

---

### Post by pqwoerituytrueiwoq on 2012-10-13
i only expected one to work so i wanted to know how to write the commands
if you run a script at shutdown to store the brightness and then set it in /etc/rc.local

shutdown:
```
echo `cat /sys/class/backlight/acpi_video0/brightness` > /var/log/brightness
```boot (/etc/rc.local)
```
echo `cat /var/log/brightness` > /sys/class/backlight/acpi_video0/brightness
```let me know if that does not work, there is a way to have lightdm run commands at logout/login/boot/right after boot
edit:
```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#display-setup-script= #script runs at about to display login
#greeter-setup-script= #script runs at ready to login
#session-setup-script= #script runs at about to login
#session-cleanup-script= #script runs at about to logout
```

---

### Post by amjjawad on 2012-10-14
> **pqwoerituytrueiwoq said:**
> i only expected one to work so i wanted to know how to write the commands
if you run a script at shutdown to store the brightness and then set it in /etc/rc.local

shutdown:
```
echo `cat /sys/class/backlight/acpi_video0/brightness` > /var/log/brightness
```boot (/etc/rc.local)
```
echo `cat /var/log/brightness` > /sys/class/backlight/acpi_video0/brightness
```let me know if that does not work, there is a way to have lightdm run commands at logout/login/boot/right after boot
edit:
```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#display-setup-script= #script runs at about to display login
#greeter-setup-script= #script runs at ready to login
#session-setup-script= #script runs at about to login
#session-cleanup-script= #script runs at about to logout
```

```
bash: /var/log/brightness: Permission denied

```

Last time I did it, it was MUCH more simpler than all this and I just don't remember how I did that? I followed one answer on AskUbuntu and it worked like a charm. I couldn't find that. I should have bookmarked.

---

### Post by amjjawad on 2012-10-14
[http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot](http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot)

That is it. I had bookmarked it indeed but because I formatted my laptop, I forgot to import my bookmarks from my external HDD.

Everything is perfect now.

Thank you :)

---

### Post by pqwoerituytrueiwoq on 2012-11-10
what i was suggesting would have it reset the brightness to the level it was when you shutdown
```
sudo apt-get install xbacklight
```
add these lines to [FONT=Courier New]/etc/lightdm/lightdm.conf[/FONT]
```
display-setup-script=sh -c "if [ -f /var/log/xbacklight ];then xbacklight -set $(cat /var/log/xbacklight);fi"
session-cleanup-script=sh -c "xbacklight -get > /var/log/xbacklight"

```
then if you shutdown with 20% back-light you get 20% back-light when the login screen appears

---

