---
title: "Cannot edit config file"
date: 2011-06-28
forum: General Help
---

### Post by maulynvia on 2011-06-28
Hi 
I need to edit the value in

sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

(from 6000 to 160000)

I try the following and get no error, but the file is not changed.

[INDENT]root@bears-laptop:/# sudo echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
[/INDENT]

If I try to use sudo gedit to edit the file, when I save I get the following error:
[INDENT]** (gedit:9269): WARNING **: Hit unhandled case 13 (Error writing to file: Invalid argument) in parse_error.
[/INDENT]

It would be great to get this machine processing at a faster speed, so any help with this much appreciated.
Maulynvia

---

### Post by trizrK on 2011-06-28
> **maulynvia said:**
> Hi 
I need to edit the value in

sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

(from 6000 to 160000)

I try the following and get no error, but the file is not changed.
[INDENT]root@bears-laptop:/# sudo echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
[/INDENT]If I try to use sudo gedit to edit the file, when I save I get the following error:[INDENT]** (gedit:9269): WARNING **: Hit unhandled case 13 (Error writing to file: Invalid argument) in parse_error.
[/INDENT]It would be great to get this machine processing at a faster speed, so any help with this much appreciated.
Maulynvia
Did you try to edit the file as a super user?

---

### Post by Ozymandias_117 on 2011-06-28
This may or may not help, but on Arch Linux, I have to actually log into root to be able to modify things in /sys and /proc - Just using sudo doesn't work.  You can artificially do the same in Ubuntu by using ```
sudo su -
``` then attempt to echo it in.

---

### Post by nothingspecial on 2011-06-28
Why are you using sudo as root?

---

### Post by maulynvia on 2011-06-29
Thanks for suggestions, still no joy. Perhaps the file is in use? how would I find that out and free it?

Here are the attempts I've made to edit this config without success:


```
bears@bears-laptop:~$ echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: Permission denied
bears@bears-laptop:~$ 

bears@bears-laptop:~$ sudo echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: Permission denied
bears@bears-laptop:~$


bears@bears-laptop:~$ sudo su -
[sudo] password for bears: 
root@bears-laptop:~# echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000

bears@bears-laptop:~$ sudo nano /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
bears@bears-laptop:~$ sudo su -
root@bears-laptop:~# nano /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
root@bears-laptop:~# 

bears@bears-laptop:~$ sudo "echo '1600000' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"
[sudo] password for bears: 
sudo: echo '1600000' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: command not found
bears@bears-laptop:~$ sudo "echo '1600000' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"

bears@bears-laptop:~$ sudo sh -c "echo '1600000' >> /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"
bears@bears-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000
bears@bears-laptop:~$ 

root@bears-laptop:~# sudo sh -c "echo '1600000' >> /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000

root@bears-laptop:~# sudo bash
root@bears-laptop:~# echo "1600000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000


root@bears-laptop:~# ls -ai /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
7539 /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

bears@bears-laptop:~$ sudo -s
[sudo] password for bears: 
root@bears-laptop:~# echo "1600000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000
root@bears-laptop:~# echo '1600000' >> /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000

bears@bears-laptop:~$ echo '1600000' | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1600000
bears@bears-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq600000


root@bears-laptop:~# echo '1600000' | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1600000
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000


bears@bears-laptop:~$ echo '1600000' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq' sudo
> echo '1600000' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq' sudo
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq sudo
echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: No such file or directory
bears@bears-laptop:~$ 

bears@bears-laptop:~$ sudo  1600000 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
sudo: 1600000: command not found
bears@bears-laptop:~$ sudo '1600000' | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
sudo: 1600000: command not found
bears@bears-laptop:~$ sudo "1600000" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
sudo: 1600000: command not found
bears@bears-laptop:~$ 


```

---

### Post by maulynvia on 2011-07-03
I think this is bug and not really about whether I have rights to edit a config.
[https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429](https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429)

---

