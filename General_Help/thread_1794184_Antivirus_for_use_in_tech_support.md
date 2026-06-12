---
title: "Antivirus for use in tech support"
date: 2011-06-30
forum: General Help
---

### Post by ghosttech on 2011-06-30
I am new to this forum and to Linux so please be gentle. I recently switched from Windows 7 to Ubuntu 10.10, (I chose 10.10 because I was able to make macbuntu work better on it than on 11.04.)I still have Windows 7 on my desktop. My problem is that I take the laptop to client sites and often use it to scan their hdd for viruses and for data recovery projects. I need an antivirus program which I can install on this Ubuntu machine so I can continue scanning client hard drives. Any recommended data recovery software would be great too. I also need simple steps for installing aforementioned software. THANK YOU for your time and help. If this has been posted the link would be a great help.

---

### Post by haqking on 2011-06-30
> **ghosttech said:**
> I am new to this forum and to Linux so please be gentle. I recently switched from Windows 7 to Ubuntu 10.10, (I chose 10.10 because I was able to make macbuntu work better on it than on 11.04.)I still have Windows 7 on my desktop. My problem is that I take the laptop to client sites and often use it to scan their hdd for viruses and for data recovery projects. I need an antivirus program which I can install on this Ubuntu machine so I can continue scanning client hard drives. Any recommended data recovery software would be great too. I also need simple steps for installing aforementioned software. THANK YOU for your time and help. If this has been posted the link would be a great help.


you will get a alot of posts about virus and Linux, because essentially it is not needed for the most part on linux so a client than can also scan other machines from yours is unlikely.

Your best bet is to use virtual box and a virtual machine (or vmware) and carry on using what you currently do ;-)

here are some useful links worth reading.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by oldos2er on 2011-06-30
Some info in the Security sticky, look under 'The Windows Mindset, Viruses'  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)'.

---

### Post by pqwoerituytrueiwoq on 2011-06-30
clamav will work for that
```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo apt-get update
sudo apt-get install clamav clamtk
sudo freshclam
```as for data recovery there is testdisk it has no gui it is command line (sudo testdisk/sudo photorec)
```
sudo apt-get install testdisk
```also since you are using 10.10 you may want to use 10.04 since it is the LTS and will be supported longer (security updates)

---

### Post by haqking on 2011-06-30
> **pqwoerituytrueiwoq said:**
> clamav will work for that
```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo apt-get update
sudo apt-get install clamav clamtk
sudo freshclam
```as for data recovery there is testdisk it has no gui it is command line
```
sudo apt-get install testdisk
```also since you are using 10.10 you may want to use 10.04 since it is the LTS and will be supported longer (security updates)


ok this will work if he is taking the HDD's out and attaching them in caddys yeah.

I was assuming he wanted to scan them whilst connected to the machine or network.

---

### Post by dFlyer on 2011-06-30
Try the avg-rescue cd. It's linux based. Download the iso and burn to cd. They will need an internet connection to complete the scan with a current virus list file, but it works great. I use it on my daughter windows when she trashes it with a virus.

tp://www.avg.com/us-en/avg-rescue-cd-download

---

### Post by ghosttech on 2011-06-30
> **haqking said:**
> ok this will work if he is taking the HDD's out and attaching them in caddys yeah.

I was assuming he wanted to scan them whilst connected to the machine or network.

Yes, I am sorry I should have been more clear, I am removing the hdd and plugging it in via caddy, I find this to be the most effective means of virus disposal. Thank you for all of your speedy replies you guys ROCK

---

### Post by ghosttech on 2011-06-30
> **pqwoerituytrueiwoq said:**
> clamav will work for that
```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo apt-get update
sudo apt-get install clamav clamtk
sudo freshclam
```as for data recovery there is testdisk it has no gui it is command line (sudo testdisk/sudo photorec)
```
sudo apt-get install testdisk
```also since you are using 10.10 you may want to use 10.04 since it is the LTS and will be supported longer (security updates)

Thanks for this info. I am installing it now. If I switch to 10.04 will I lose all settings or is there a way to 'upgrade' and keep all files etc. I currently have?

---

### Post by haqking on 2011-06-30
> **ghosttech said:**
> Yes, I am sorry I should have been more clear, I am removing the hdd and plugging it in via caddy, I find this to be the most effective means of virus disposal. Thank you for all of your speedy replies you guys ROCK


ok, however it is faster to boot the machine to a AV CD/DVD and scan it, you are not booting into windows and not having to take anything apart...there are many available.

or boot the machine to a USB linux distro and do it that way...all alot quicker and dont get your suit dusty from dirty computers ;-)

---

### Post by pqwoerituytrueiwoq on 2011-06-30
> **ghosttech said:**
> Thanks for this info. I am installing it now. If I switch to 10.04 will I lose all settings or is there a way to 'upgrade' and keep all files etc. I currently have?
if you made a separate /home partition it is easy just don't format it during install
otherwise
copy ~/* to a flash drive
after install from the cd copy the context back to your user folder
sudo cp /media/someUSB/ubuntuHome/* /media/somefolder/home/yourname
sudo chown -R yuorname:yourname  /media/somefolder/home/yourname/
it is not urgent 10.10 is supported till early 1012
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

