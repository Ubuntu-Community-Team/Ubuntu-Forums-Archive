---
title: "Root.disk on ubuntu desktop"
date: 2009-09-12
forum: General Help
---

### Post by alex1001 on 2009-09-12
Hello. I would like to know how to access a root.disk file from a previous Ubuntu installation. It is currently sitting on my new Ubuntu desktop and I need to pull some files from it.

Up until a day ago, I was using Ubuntu 8.04 and Windows XP on the same 75GB laptop hard drive. All of a sudden, I started up and I was unable to boot Ubuntu. It told me that the partition could not be found. I was, however, able to boot into Windows XP. I took a look at the partitions, and to my amazement, it seems my Windows XP partition swallowed my Ubuntu partition. I have no idea how this happened as I had done nothing unusual with my computer and I had used it with no problem just an hour before. No one else had access to my computer.

I spoke with a computer technician who had some experience with Ubuntu and he too was amazed that not only did my Ubuntu partition disappear, but it seems that it had all moved to my rarely-used Windows XP partition. In the C drive I had a 28GB "ubuntu" folder with the subfolders disks, docs, install, winboot. In the "disks" subfolder, I had a 27GB root.disk file. I can only surmise that my entire Ubuntu partition is that root.disk file, with everything I need in that file.

I copied the entire ubuntu folder with the root.disk file onto another computer, and after much frustration, I completely cleaned out everything and started anew with a LiveCD installation of Ubuntu 9.04. I currently have one partition of 75GB with 9.04 on that partition, with no Windows or older Ubuntu. After copying the 28GB "ubuntu" folder with the root.disk file back onto my Ubuntu 9.04, I need to somehow access the documents in the root.disk file.

I would greatly appreciate some ideas or advice. I searched around, but could not find anything with similar facts.

Thanks!

---

### Post by ckonestroh on 2009-09-12
So what does computer say about the owner of the folder... The permissions ????

---

### Post by ckonestroh on 2009-09-12
Go to this link

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

---

### Post by alex1001 on 2009-09-12
The folder "ubuntu" is located in "Desktop":

alex@ubuntu:~$ cd ~/Desktop/ubuntu/
alex@ubuntu:~/Desktop/ubuntu$ ls -l
total 172
-rwxrwxrwx 1 alex alex   2446 2009-02-13 15:05 curl_log.txt
drwxrwxrwx 4 alex alex   4096 2009-09-10 17:37 disks
drwxrwxrwx 2 alex alex   4096 2009-09-10 17:09 docs
drwxrwxrwx 2 alex alex   4096 2009-09-10 17:08 install
-rwxrwxrwx 1 alex alex   3129 2009-02-13 15:05 metadl_log.txt
-rwxrwxrwx 1 alex alex  25214 2008-10-27 10:37 Ubuntu.ico
-rwxrwxrwx 1 alex alex 118608 2009-02-13 13:36 Uninstall-Ubuntu.exe
drwxrwxrwx 2 alex alex   4096 2009-09-10 17:08 winboot


The owner of the "ubuntu" folder is "alex - ubuntu"
The 27GB root.disk file is located in /Desktop/ubuntu/disks. I checked Properties->Permissions for the root.disk file and the owner is alex - ubuntu with access to Read and Write with a box checked for "Allow executing file as a program."

Is this what you were looking for? I hope it helps.

---

### Post by ckonestroh on 2009-09-12
> **alex1001 said:**
>  After copying the 26GB "ubuntu" folder with the root.disk file back onto my Ubuntu 9.04, I need to somehow access the documents in the root.disk file.

Thanks!

Ok,

This is where I loss you what do you mean?????

You have read/write permissions???????

---

### Post by alex1001 on 2009-09-12
> **ckonestroh said:**
> Ok,

This is where I loss you what do you mean?????

You have read/write permissions???????

My original Ubuntu 8.04 (Hardy) system had 27GB of files on it. After I could not boot in Ubuntu, I looked on my Windows XP partition and found a folder titled "ubuntu" with several files and subfolders, including a file called "root.disk" which was 27GB in size. I assumed this was a collection of all my data from my Ubuntu system.

I copied this entire "ubuntu" folder from my Windows XP partition onto a friend's computer in case I had to wipe my entire drive clean. In fact, I did end up wiping my entire drive clean and installing the new Ubuntu 9.04. I no longer have the old Hardy system nor the Windows XP system. I now just have the new Ubuntu 9.04 (Jaunty) system all on one partition.

After installing Jaunty, I copied my old "ubuntu" folder back from my friend's computer so I would be able to work with it over the weekend.

So this brings me to my current predicament. I have the entire 28GB "ubuntu" folder from my Hardy system sitting on my Jaunty desktop. In this folder is a root.disk which I assume has all my old files in it. I need to access some of the documents on this file.

Regarding permissions, here's what I have:

alex@ubuntu:~/Desktop/ubuntu/disks$ ls -l
total 29325540
drwxrwxrwx 3 alex alex        4096 2009-09-10 17:37 boot
-rwxrwxrwx 1 alex alex 29000000000 2009-09-09 17:36 root.disk
drwxrwxrwx 2 alex alex        4096 2009-09-10 17:37 shared
-rwxrwxrwx 1 alex alex  1000000000 2009-02-13 07:11 swap.disk

The "root.disk" I assume is the large file with everything on it. I understand this to mean that it's a regular file because I have a "-" sign, and re: "user", "group", and "others" access, I have read, write, and execute permissions.

I am not too experienced with Ubuntu, but I would be happy to provide any additional information.

---

### Post by alex1001 on 2009-09-13
I guess put simply:

How can I access the files inside a root.disk?

I know there is a thread about the issue: [http://ubuntuforums.org/showthread.php?t=1024693]("http://ubuntuforums.org/showthread.php?t=1024693")

However, that thread is unresolved. There is a recommendation to put it on a liveCD, but my root.disk file is much too big for a liveCD.

---

### Post by alex1001 on 2009-09-13
On the IRC chat, alkisg2 offered an excellent and simple piece of advice:

I directed my terminal to where the file was located

cd ~/Desktop/ubuntu/disks/

and then I entered the following:

sudo mount -o loop root.disk /mnt

This unpacked my root.disk file in the /mnt folder. I was able to save all of my documents. Problem solved!

---

