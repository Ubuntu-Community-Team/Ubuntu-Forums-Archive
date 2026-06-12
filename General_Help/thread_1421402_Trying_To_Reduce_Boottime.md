---
title: "Trying To Reduce Boottime"
date: 2010-03-04
forum: General Help
---

### Post by jsriz on 2010-03-04
Splashtop caught my imagination of my own tv like computer-"1button and ready to go "
have tried puppy xpud_[COLOR=Black][]("http://webconverger.com/")[/COLOR]_WebConverger still unhappy 
Now lucid aming for 10 sec boot-Keeping ma fingers crossed 
installed a minimal karmic and am getting a decent 27 sec
I Jus Wanted to ask: 
Is there a way to _**remove**_ the grub an directly boot into ubuntu -not just hiding it by editing grub.d files 
and plz suggest any other ways to reduce boot time.......

---

### Post by jsriz on 2010-03-04
bump

---

### Post by jsriz on 2010-03-05
bumpity bump

---

### Post by jsriz on 2010-03-12
wow a new bump

---

### Post by Enigmapond on 2010-03-12
Try this thread and it's instructions. It helped me out hope it helps you...;)

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by jsriz on 2010-03-14
Ha a reply at last Thanx a ton lemme try

---

### Post by H4F on 2010-03-14
removing grub sounds weird

---

### Post by jsriz on 2010-03-14
Why while having a single boot of the best linux why should i wait for the bios to load the grub and then ask grub to load kernal at some location.Cant i just write the location of the kernal into the mbr so that it can boot it directly......
p.s i have a basic idea about the loading process please correct me if i am wrong

---

### Post by H4F on 2010-03-14
"  When booting from the hard disk, the code in the master boot record will examine the partition table (also in the master boot record), identify the active partition (the partition that is marked to be bootable), read the boot sector from that partition, and then start the code in that boot sector. The code in the partition's boot sector does what a floppy disk's boot sector does: it will read in the kernel from the partition and start it. The details vary, however, since it is generally not useful to have a separate partition for just the kernel image, so the code in the partition's boot sector can't just read the disk in sequential order, it has to find the sectors wherever the filesystem has put them. There are several ways around this problem, but the most common way is to use a boot loader like LILO or GRUB. (The details about how to do this are irrelevant for this discussion, however; see the LILO or GRUB documentation for more information; it is most thorough.) When booting, the bootloader will normally go right ahead and read in and boot the default kernel. " - [http://www.iitk.ac.in/LDP/LDP/sag/html/boot-process.html](http://www.iitk.ac.in/LDP/LDP/sag/html/boot-process.html)

---

### Post by jsriz on 2010-03-16
> **H4F said:**
> "  When booting from the hard disk, the code in the master boot record will examine the partition table (also in the master boot record), identify the active partition (the partition that is marked to be bootable), read the boot sector from that partition, and then start the code in that boot sector. The code in the partition's boot sector does what a floppy disk's boot sector does: it will read in the kernel from the partition and start it. The details vary, however, since it is generally not useful to have a separate partition for just the kernel image, so the code in the partition's boot sector can't just read the disk in sequential order, it has to find the sectors wherever the filesystem has put them. There are several ways around this problem, but the most common way is to use a boot loader like LILO or GRUB. (The details about how to do this are irrelevant for this discussion, however; see the LILO or GRUB documentation for more information; it is most thorough.) When booting, the bootloader will normally go right ahead and read in and boot the default kernel. " - [http://www.iitk.ac.in/LDP/LDP/sag/html/boot-process.html](http://www.iitk.ac.in/LDP/LDP/sag/html/boot-process.html)
yes thats how a boot loader works.
mbr->bootsector of active partition->bootloader ->kernal in some position in filesystem.

mbr size=512kb (cant do anything over here)

boot sector (i generally put background picture and it also loads pics and scripts in grub.d and /etc/default folders)--hence can we write a sctipt (or something of that sort to just redirect to the position of kernal in the file system)
since i am single booting into ubuntu why do i need this extra step of boot loader......?
chrome os (jus a stripped down version of linux is doing this Source:[http://www.youtube.com/watch?v=mTFfl7AjNfI](http://www.youtube.com/watch?v=mTFfl7AjNfI)) hence i believe it can be done here 
plz correct meeeee.....

---

### Post by jsriz on 2010-03-16
oops a bump

---

### Post by jsriz on 2010-03-17
a very patient bump

---

### Post by jsriz on 2010-03-17
wow where are the linux geeks and ubuntu gurus

---

### Post by kngofbuntu on 2010-03-18
+1 bump

---

### Post by jsriz on 2010-03-18
thanks for the bump this is another bump

---

### Post by linuxman94 on 2010-03-18
> Is there a way to remove the grub an directly boot into ubuntu -not just hiding it by editing grub.d files 

No you can't remove grub.  Without grub, you cannot boot Ubuntu.  

Do you have a dual boot set up or just Ubuntu?

---

### Post by jsriz on 2010-03-18
> **linuxman94 said:**
> No you can't remove grub.  Without grub, you cannot boot Ubuntu.  

Do you have a dual boot set up or just Ubuntu?
Nope I was dual booting with windows7
now just using ubuntu

---

### Post by linuxman94 on 2010-03-18
Ok so on boot the grub menu shows up and you hit enter to boot, right?

---

### Post by Flareside on 2010-03-18
To put it in simple terms, GRUB executes the kernel and loads the initrd. Without GRUB (or another bootloader), your computer would just sit there doing nothing after the bios was finished it's steps. 

Although, I'm sure if you were really good at machine code and computer science you could probably modify your master boot record to directly execute the kernel, but I have a feeling that doing that is beyond the abilities of most people, or may not even be possible at all.

---

### Post by jsriz on 2010-03-18
> **Flareside said:**
> To put it in simple terms, GRUB executes the kernel and loads the initrd. Without GRUB (or another bootloader), your computer would just sit there doing nothing after the bios was finished it's steps. 

Although, I'm sure if you were really good at machine code and computer science you could probably modify your master boot record to directly execute the kernel, but I have a feeling that doing that is beyond the abilities of most people, or may not even be possible at all.
Thanks for correcting me 
i generally record my boot time every now and then
it takes a solid 5-8sec (form poweron to grub) out of about 27-30 secs
thats what makes me think about a way to remove it.........stupid me.
guess more knowledge is the only key
 		> Ok so on boot the grub menu shows up and you hit enter to boot, right?
ha ha very funny i could have set the time out to zero....

---

### Post by jsriz on 2010-03-18
lemme mark it solved

---

