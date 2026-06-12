---
title: "Shell script writing help"
date: 2011-05-05
forum: General Help
---

### Post by thexnightmare on 2011-05-05
Dear all,
I want to write a shell script which have will erase a usb flash memory then copy the entire content of a cdrom to the usb flash frive then restart ubuntu.
Anybody can help?
thx

---

### Post by TeoBigusGeekus on 2011-05-05
```
rm -rf /media/usb_mountpoint
cp -r /media/cd_mountpoint/* /media/usb_mountpoint/
reboot
```
You'd have to run it with sudo because of reboot and I think the contents of the usb will be owned by root because of this. Try it and post back.

---

### Post by thexnightmare on 2011-05-05
You are the best my friend.
I was asking and searching for alooooooooooooooooooooooooong time for this solution, u r really expert, and I am so glad to meet you and got helped by you.
 
Last thing, do you know how can I make this running on system startup?
and how can I print a message on the terminal things before each step?

---

### Post by TeoBigusGeekus on 2011-05-05
> **thexnightmare said:**
> and how can I print a message on the terminal things before each step?
```
echo "Deleting everything from usb now"
rm -rf /media/usb_mountpoint
echo "Copying the contents of the cd to usb"
cp -r /media/cd_mountpoint/* /media/usb_mountpoint/
echo "Rebooting"
reboot
```

> **thexnightmare said:**
> Last thing, do you know how can I make this running on system startup?

Save your script, say, as script (I'm the most imaginative guy, I know).
Then make it executable
```
chmod +x /path/script
```
To make it run on startup, since it needs root priviledges, put it into your /etc/init.d directory. Then run
```
sudo update-rc.d script defaults
```

---

### Post by thexnightmare on 2011-05-05
Thx for ur help again.
I did what u said exactly
but after lasy step, this message appears:
{
update-rc.d: warning: /etc/init.d/script missing LSB information
update-rc.d: see <[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)>
}
and when restarting nothing shown on screen and script didn't started up!!!
Any solution?

---

### Post by thexnightmare on 2011-05-07
Solution is found here:
[http://ubuntuforums.org/showpost.php?p=10780000&postcount=9](http://ubuntuforums.org/showpost.php?p=10780000&postcount=9)

---

