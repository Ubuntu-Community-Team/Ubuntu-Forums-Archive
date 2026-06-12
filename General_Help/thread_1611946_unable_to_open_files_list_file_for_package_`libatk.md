---
title: "unable to open files list file for package `libatk1.0-data': Input/output error"
date: 2010-11-02
forum: General Help
---

### Post by Calgon on 2010-11-02
**RESOLVED. Re-installed Ubuntu. **

Whenever I try to get anything with apt-get (or the Ubuntu Software Centre), I receive an error which stops me from continuing with installation:

```
(Reading database ... dpkg: unrecoverable fatal error, abor
 unable to open files list file for package `libatk1.0-data
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Could I have some help, please?

A similar issue [here]("https://answers.launchpad.net/ubuntu/+question/116981") is something I used to attempt to remedy the issue, but it didn't help.

---

### Post by rcayea on 2010-11-02
Quick question that may help us help you...

Did you abort a previous installation while in mid-installation?

---

### Post by Calgon on 2010-11-02
I think I may have, my power ran out half way through an installation a while ago, but I can't even remember what I was installing.

---

### Post by rcayea on 2010-11-02
I got this from another website, a person with a similar issue:


"I would go and explore the file mentioned and look for
corruption. It seems to imply line 2 so it should be near the
beginning. Perhaps there is a blank line or something near the
beginning.

Did you run out of disk space sometime recently?

There should be a /var/lib/dpkg/available-old file too (at least I have
one)"

---

### Post by rcayea on 2010-11-02
try this:

dpkg --clean-avail
apt-get update

---

### Post by Calgon on 2010-11-02
> dpkg: unknown option --clean-avail

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
Doesn't seem to have worked. Anyone? I've tried to to purge the package that returns an error to receive:

```

sudo dpkg --purge libatk1.0-data

```

to no success as it springs up the same error, again... Anyone?

---

### Post by Calgon on 2010-11-03
Anyone else? This is a pretty big issue for me as I can't do a lot without continuing to install the basics.

---

### Post by Calgon on 2010-11-03
I've decided to re-post my question in this forum, seeing as it's probably a bit over the heads of people who usually post in the 'absolute beginners help' as it seems to be an uncommon issue. 

```
[B]unable to open files list file for package `libatk1.0-data': Input/output error
```
[/B]...occurs every single time that I try to do something that executes dpkg. I've tried to purge libatk1.0-data (with command 'sudo dpkg --purge libatk1.0-data') but that hasn't worked, I've also tried the following (but the solutions haven't worked):

The first:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
```

The second (suggested by rcayea):
```

dpkg --clean-avail
apt-get update

```

Neither of the attempts worked. Could someone please help me?

---

### Post by sisco311 on 2010-11-03
What's the output of:
```
ls -l /var/lib/dpkg/info/libatk1.0-data.list
```
and
```
cat /var/lib/dpkg/info/libatk1.0-data.list
```?

---

### Post by Calgon on 2010-11-03
> **sisco311 said:**
> What's the output of:
```
ls -l /var/lib/dpkg/info/libatk1.0-data.list
```and
```
cat /var/lib/dpkg/info/libatk1.0-data.list
```?
Thanks for your response.

```
frederick@ubuntu:~$ ls -l /var/lib/dpkg/info/libatk1.0-data.list
ls: cannot access /var/lib/dpkg/info/libatk1.0-data.list: Input/output error
frederick@ubuntu:~$ cat /var/lib/dpkg/info/libatk1.0-data.list
cat: /var/lib/dpkg/info/libatk1.0-data.list: Input/output error
```

---

### Post by sisco311 on 2010-11-03
Try renaming the corrupted file and reinstall the package:
```
sudo mv /var/lib/dpkg/info/libatk1.0-data.list{,.bad}
```
```
sudo apt-get install --reinstall libatk1.0-data
```

---

### Post by Calgon on 2010-11-03
> **sisco311 said:**
> Try renaming the corrupted file and reinstall the package:
```
sudo mv /var/lib/dpkg/info/libatk1.0-data.list{,.bad}
``````
sudo apt-get install --reinstall libatk1.0-data
```
Unfortunately, the first command didn't work:

```

sudo mv /var/lib/dpkg/info/libatk1.0-data.list{,.bad}
```

Nor did the last

```

frederick@ubuntu:~$ sudo apt-get install --reinstall libatk1.0-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 128 not upgraded.
Need to get 14.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main libatk1.0-data 1.30.0-0ubuntu2.1 [14.6kB]
Fetched 14.6kB in 0s (84.9kB/s)       
Selecting previously deselected package libatk1.0-data.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `libatk1.0-data': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by sisco311 on 2010-11-03
Check the filesystem for errors. Find the device name of the root (/) partition:
```
df -h /
```
i.e. /dev/sda1. Run:
```
sudo tune2fs -C 50 **/dev/sda1**
``` and reboot.

---

### Post by Calgon on 2010-11-03
> **sisco311 said:**
> Check the filesystem for errors. Find the device name of the root (/) partition:
```
dh -h /
```i.e. /dev/sda1. Run:
```
sudo tune2fs -C 50 **/dev/sda1**
``` and reboot.


The first command returns
```

The program 'dh' is currently not installed.  You can install it by typing:
sudo apt-get install debhelper

```
*If I try to install the package, I get the same libatk error. *

The other command returns:

```
[B]tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
[/B]
```

---

### Post by sisco311 on 2010-11-03
Sorry, it's: ```
**df** -h /
```.

---

### Post by Calgon on 2010-11-03
> **sisco311 said:**
> Sorry, it's: ```
**df** -h /
```.

That command returns:
```

frederick@ubuntu:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             19G  3.3G   15G  19% /

```

If it helps, I think the cause may be due to losing power during installation of something.

---

### Post by sisco311 on 2010-11-03
Oh, it's a Wubi installation. You have to check the Windows partition. If you can boot in Windows, then run:
```
chkdsk /r
```in the msdos console.

---

### Post by Calgon on 2010-11-03
Before I signed on earlier, Windows forced me to perform a CHKDSK test and it fixed a few things. But I still have this dpkg issue. I'll try chkdsk again.

---

### Post by sisco311 on 2010-11-03
I think, you have to run:
```
sudo tune2fs -C 50 /host/ubuntu/disks/root.disk
```
to force Ubuntu to check the root filesystem on reboot. Assuming that the Windows partition is mounted in /host and Ubuntu is installed in C:\ubuntu

---

### Post by Calgon on 2010-11-03
> **sisco311 said:**
> I think, you have to run:
```
sudo tune2fs -C 50 /host/ubuntu/disks/root.disk
```to force Ubuntu to check the root filesystem on reboot. Assuming that the Windows partition is mounted in /host and Ubuntu is installed in C:\ubuntu
Yeah, that's right. 

I typed that command, rebooted, came back and found that it still didn't work.  When I submitted the command, this was returned:

```
tune2fs 1.41.11 (14-Mar-2010)
Setting current mount count to 50

```

---

### Post by sisco311 on 2010-11-03
> **Calgon said:**
> Yeah, that's right. 

I typed that command, rebooted, came back and found that it still didn't work.  When I submitted the command, this was returned:

```
tune2fs 1.41.11 (14-Mar-2010)
Setting current mount count to 50

```

Try to check the filesystem manually. Boot a Live CD (or Live USB), from the Places menu select the Windows partition and navigate to the ubuntu/disks directory. Open a terminal and type:
```
sudo e2fsck -C0 -f -v
```
type a space, drag the root.disk file and drop it into the terminal window. Press enter to run the command.

---

### Post by Calgon on 2010-11-03
I don't have any Ubuntu Discs. I just downloaded the Wubi Installer on Windows and installed it. Is there any other way that I can get ahold of that file?

---

### Post by Calgon on 2010-11-04
Anyone?

```

sudo e2fsck -C0 -f -v
``` returns the usage and doesn't do anything

---

### Post by s.fox on 2010-11-04
Threads merged. Please do not create duplicate threads. Thank you.

---

### Post by Calgon on 2010-11-04
Resolved, reinstalled Ubuntu.

---

