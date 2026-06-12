---
title: "Help getting past login"
date: 2011-10-15
forum: General Help
---

### Post by jcbconway on 2011-10-15
Hello, i have been using ubuntu 11.10  and it has been working fine up untill i restartd it yesterday. What happens is when i turn the computer on and get to the log in screen, i type in my pass and instead of going to my dektop, it goes too a black screen with text on it. And if i hit the power button, it turns it off right away. 
Here is what i am seeing. [IMG]http://i119.photobucket.com/albums/o128/popkitty3/comp.jpg[/IMG]

---

### Post by effenberg0x0 on 2011-10-15
Try this:

Press Ctrl+Alt+F2 to switch to another VT. See if you can use your login and password to get to a prompt.

If not: reboot and hold shift to see grub options. Choose recovery mode (generally the second option) and go to a root console.

Run this code:
```

sudo mount -oremount,rw /
sudo killall -s KILL /usr/bin/X
sudo killall -s KILL /usr/bin/lightdm
sudo killall -s KILL /usr/bin/gdm
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm
echo "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf
if [ ! -d "/run" ]; then sudo mkdir /run && sudo mkdir /run/lock && sudo rm -rf /var/run && sudo rm -rf /var/lock && sudo ln -s /run /var/run && sudo ln -s /run/lock /var/lock; fi
sudo sed -i s'/quiet[[:space:]]splash/ /g' /etc/default/grub && sudo update-grub
sudo reboot now
```

Please report back.

Effenberg

---

### Post by jcbconway on 2011-10-15
Sorry, that didnt work, the first command "sudo mount -oremount,rw /" Came back with and error. saying mount: cannot remount block device /dev/sda1 read-write, is writeprotected

---

### Post by effenberg0x0 on 2011-10-15
> **jcbconway said:**
> Sorry, that didnt work, the first command "sudo mount -oremount,rw /" Came back with and error. saying mount: cannot remount block device /dev/sda1 read-write, is writeprotected

Ok, disregard that command and proceed with the other ones. Not mandatory.

regards,
Effenberg

---

### Post by jcbconway on 2011-10-15
Im running through them but they dont seem to be working.  i am typeing exactly what you typed, so when you sau usr, do you mean my user, or literally usr? and same with other veriables here.

---

### Post by effenberg0x0 on 2011-10-15
> **jcbconway said:**
> Im running through them but they dont seem to be working.  i am typeing exactly what you typed, so when you sau usr, do you mean my user, or literally usr? and same with other veriables here.

Exactly as it is there. I expect the first 4 to fail. They're there just in case these things were running. They're not, the cmd fails, which is good. Commands 5, 6 will give you output. The other won't. It's normal. The last one will reboot your PC after changes were made.

Effenberg

---

### Post by jcbconway on 2011-10-15
ahhh that makes sense! i will finish runing throught these, and let you know the outcome of your help.

---

### Post by jcbconway on 2011-10-15
It keeps sending things back like read -only file system.... 

cammands 5, and 6 both send back 

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt/ 
E: the package list or status file could not be parsed or opened 

Hmm....

---

### Post by effenberg0x0 on 2011-10-15
Run mount, no parameters, and copy the output here please.

Effenberg

---

### Post by jcbconway on 2011-10-15
Just run "sudo mount" ?

---

### Post by effenberg0x0 on 2011-10-15
yes, it will show us what is mounted and how.

---

### Post by jcbconway on 2011-10-15
I get this...

```

/dev/sda1 on/type ext3 (rw,relatime,errors=remount-r0,commit=0)
proc on /proc type proc (rw) 
none on /sys type sysfs (rw, noexec, nosuid, nodev)
fusect1 on sys/fs/fuse/connections type fusect1 (rw)
none on /sys/kernal/debug type debugfs (rw) 
none on /sys/kernal/security type securityfs(rw) 
none on /dev type devtmpfs (rw, mode = 0755)
none on /dev/pts type devpts (rw, noexec, nosuid, gid = 5, mode=0620)
none on /dev/shm type tmpfs (rw, nosuid, nodev)
none on /var/run type tmpfs (rw, nosudi, mode=0755)
none on /var/lock type tmpfs (rw, noexec, nosuid, nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfms_misc (rw, noexec,nosuid,nodev)

mount: warning: /etc/mtab is not writable (e.g. read-only  filesystem). 
its possible that information reported by mount(8) is not up to date. 
for actual information about system mount points check the /proc/mount files 

```

---

### Post by effenberg0x0 on 2011-10-15
Is /dev/sda1 really mounted with errors=remount-r**0**? or did you mistype that?

Anyway, please try this:
```
mount -f -o remount,rw -t ext3 /dev/sda1 /
```Then fix /etc/fstab:
```
sudo nano /etc/fstab
```Replace the line for sda1, the one with errors=remount-r0 in it for:
```
/dev/sda1 / ext3 errors=remount-ro 0 1
```Press Ctrl+X, Y and <Enter> to save the file and exit.

Now run each of this commands in the terminal.
```

if [ ! -d "/run" ]; then sudo mkdir /run && sudo mkdir /run/lock  && sudo rm -rf /var/run && sudo rm -rf /var/lock  && sudo ln -s /run /var/run && sudo ln -s /run/lock  /var/lock; fi
sudo apt-get update
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm
echo "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf
sudo sed -i s'/quiet//g' /etc/default/grub 
sudo sed -i s'/splash//g' /etc/default/grub 
sudo update-grub
sudo reboot now
```

---

### Post by jcbconway on 2011-10-15
oops. ro not r0.

---

