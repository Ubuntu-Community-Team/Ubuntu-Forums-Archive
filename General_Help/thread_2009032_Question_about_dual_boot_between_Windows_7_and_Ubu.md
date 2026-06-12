---
title: "Question about dual boot between Windows 7 and Ubuntu"
date: 2012-06-23
forum: General Help
---

### Post by portage on 2012-06-23
I made an 80 gb Windows 7 partition to only use for installing games and nothing else. Do I need to make a storage partition to get Windows and Ubuntu to work or can I just use the remaining free space for Ubuntu. The remaining space is about 800-something gb which I want to use all for Ubuntu since it will be my main.

So Windows 7 = games only
Ubuntu = everything

Do I need a storage partition that I saw on guides in google?

---

### Post by rk0r on 2012-06-23
you can partition your drive 

40gb - windows 
40gb - ubuntu 

When you install ubuntu you have the option to partition the drive. 
Or if you have ubuntu installed you can use the Gparted to create the partition space on the drive.

---

### Post by portage on 2012-06-23
I know but my question was whether I need to create such a small a partition for Ubuntu? Can I just use the entire free space for Ubuntu only

---

### Post by elliotn on 2012-06-23
if Ubuntu is your primary OS then u don't have to make anymore partitions, but if you gonna play music in windows7 u must remember that your music in Ubuntu partition wont be accessible as windows can't read ext partition thus I always make an extra NTFS partition for media so when I am on either OS n have to indulge on music I don't have to reboot

---

### Post by patrickceg on 2012-06-23
A storage partition is not needed, unless you want to have some space to share files between Windows and Ubuntu without mounting your Windows system partition. (This was necessary in the past when Linux's NTFS drivers made a mess of the Windows partition but that isn't the case anymore, at least in my experience.)

You can go ahead and fill the whole remaining space with Ubuntu (I believe there's a "use free space" option in the installer), but if I were you I'd leave some space at the end in case you do want to give Windows, or more specifically your games, more breathing room.

---

### Post by holycow131415 on 2012-06-24
I feel like 80 gb for windows 7 is too small. youll only have 60 gb to play with, and games take alot of space too, but i dont know how many games you have.

like everyone else said, if you want to use files you may have on your ubuntu partition while on windows, then you should make a 3rd ntfs partition for both OSes to access.

---

### Post by blackflame2996 on 2012-06-24
> **portage said:**
> I know but my question was whether I need to create such a small a partition for Ubuntu? Can I just use the entire free space for Ubuntu only

yes, but that is a TON of space for Ubuntu. 100 GiB is quite large, for that matter

---

### Post by nipunshakya on 2012-06-24
In my opinion, make 3 partitions. one 80 gb for windows, leave as it is... another extended partition with around 100 gb for ubuntu(which will further include /,/home and swap too each of 15,83 and 2 gb resp.) and format the rest as a whole NTFS primary drive so that you can share data among windows and ubuntu. Who knows for what purpose you will be booting windows in nearby future....

---

### Post by blackflame2996 on 2012-06-24
> **WinuxUser said:**
> In my opinion, make 3 partitions. one 80 gb for windows, leave as it is... another extended partition with around 100 gb for ubuntu(which will further include /,/home and swap too each of 15,83 and 2 gb resp.) and format the rest as a whole NTFS primary drive so that you can share data among windows and ubuntu. Who knows for what purpose you will be booting windows in nearby future....
I agree that this this configuration is ideal.

---

### Post by mastablasta on 2012-06-24
and as a plus of such configuraiton you can easilly backup home to NTFS storage partition, freshly install the whole Ubuntu OS and then move home back.

you should know that Ubuntu doesn't really take so much space (even if you fill it with programmes). i have a 60 GB disk and mostly it is still free despite putting quite a few porgrammes and even some wine games (such as Diablo2) on it. i have a separate new storage disk now. i doubt i will ever fill the main 60 GB disk unless i put some movies there or plenty of pictures ... which is data and hasn't got much to do with OS. i could also fill it with windows games in wine for example, but since you have a dual boot you will be using widnows part for that.

edit on a side note i have a virtual box Xubuntu install on 8GB virtual drive. and i still have about 2GB free. and i also added a few porgrammes ot it already. so you will have more than enough with 30 GB Ubuntu partition.

---

