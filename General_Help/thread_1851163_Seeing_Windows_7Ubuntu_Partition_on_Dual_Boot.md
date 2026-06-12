---
title: "Seeing Windows 7/Ubuntu Partition on Dual Boot"
date: 2011-09-27
forum: General Help
---

### Post by Serson_Person on 2011-09-27
Hi,

I've searched for two days without finding a solution.

I've installed Ubuntu 11.04 alongside my Windows 7, everything works fine.  I remember when I used to dual-boot Ubuntu the Windows Partition would pop right up on my desktop, now I can't find it.

Any easy-to-follow guidelines on how I can see my Windows Partition on Ubuntu and Vice Versa?

Also, does anybody know a safe and easy way to extend my Ubuntu partition?

Thanks,
Sorry for the n00b question.

- Jordan

---

### Post by garvinrick4 on 2011-09-27
> I've installed Ubuntu 11.04 alongside my Windows 7, everything works  fine.  I remember when I used to dual-boot Ubuntu the Windows Partition  would pop right up on my desktop, now I can't find it.
Open a nautilus window and is on the left side panel.

> Any easy-to-follow guidelines on how I can see my Windows Partition on Ubuntu and Vice Versa?
You can only see windows from linux you cannot see linux from windows.
Windows does not read ext formats. Linux does read NTFS format.
> 
Also, does anybody know a safe and easy way to extend my Ubuntu partition?
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition") 
Always a risk when partitioning drive better you are at it the less the risk.

## If you have a WUBI install look in file system under /host

---

### Post by Serson_Person on 2011-09-27
> **garvinrick4 said:**
> Open a nautilus window and is on the left side panel. 

It is not there, that's my problem.  I know normally I would see it, but it's not showing up.

---

### Post by garvinrick4 on 2011-09-27
What does this say is there a windows entry
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by Serson_Person on 2011-09-27
sersonperson@ubuntu:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {

---

### Post by garvinrick4 on 2011-09-27
Is the sidebar missing?
How about nautilus to view to sidebar to places marked.

---

### Post by Serson_Person on 2011-09-27
The sidebar is there.

Says the usual:

sersonperson (which is home)
Desktop
File System (which seems to have all the ubuntu stuff on it)
Network
System Reserved (which is only 100mb)
Trash

Etc...

---

### Post by Serson_Person on 2011-09-27
Also, thank you for the time you have given thus far :)

---

### Post by garvinrick4 on 2011-09-27
What happens does it show up on Desktop or in file system in media with this. (if you have desktop set to show mounted drives it will show up on Desktop) if not go to /media in file system open and then open windows folder should be mounted in there.
```
sudo mkdir /media/windows
``````
sudo mount /dev/sda2 /media/windows
```when done with below;
```
sudo umount /media/windows
```

I am just wondering why it is not in places? This above will see what is there.

---

### Post by Mark Phelps on 2011-09-28
> **Serson_Person said:**
> ... I've installed Ubuntu 11.04 alongside my Windows 7, ...

You mean side-by-side -- as in a Wubi installation?

If so, your Windows filesystem is mounted under /host

---

### Post by Serson_Person on 2011-10-22
When I try to access the root file it says I don't have permissions.

---

### Post by garvinrick4 on 2011-10-22
Open "gparted" and take a screenshot and upload it with paper clip icon on top of message
box. If not installed
```
sudo apt-get install gparted
```

---

### Post by Serson_Person on 2011-10-22
Here's a screenshot.

---

### Post by Serson_Person on 2011-10-22
Does anybody know how I can get permission to view the root folder?

Thanks,
Jordan

---

### Post by cryptotheslow on 2011-10-22
As your GParted screen shows sda3 mounted at /host just open up your file browser and navigate to /host

Seems like you have a Wubi install i.e. you installed Ubuntu from within Windows using Wubi.

---

### Post by Serson_Person on 2011-10-22
> **cryptotheslow said:**
> As your GParted screen shows sda3 mounted at /host just open up your file browser and navigate to /host

Seems like you have a Wubi install i.e. you installed Ubuntu from within Windows using Wubi.

I did use Wubi.  Does that nullify my attempts?  Is there a way around it?

When I do navigate to the folder that's when it tells me I don't have permission to access.

---

### Post by cryptotheslow on 2011-10-22
Are you attempting to browse to /host as suggested or /root ? The latter is not accessible.

---

### Post by Serson_Person on 2011-10-22
> **cryptotheslow said:**
> Are you attempting to browse to /host as suggested or /root ? The latter is not accessible.

Ah.

Thank you.  Much dismay over a little mistake, lol.  Seems to always be the way.

Thanks again.

---

