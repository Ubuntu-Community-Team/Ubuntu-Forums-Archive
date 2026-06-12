---
title: "Directory full with symbolic links"
date: 2009-12-10
forum: General Help
---

### Post by RonRN18 on 2009-12-10
I have Karmic 64-bit installed on my desktop on a 250 GB hard drive. I didn't really care about the size as I also have a 3 TB NAS in the house to store media and data files I'm likely going to want to access from multiple computers in the house. I automatically mount the NAS shares at startup, but mount them in the /mnt directory. To make things easier for me, I created symbolic links of several folders on the NAS to my /home directory... /home/bigron in my case. This was working fine ***EXCEPT*** Ubuntu said that I was out of space for the directory. Sure, if I *actually* had all the files physically in my /home directory, it *would* be full. At first, I figured the operating system would recognize that is not where the files actually were and when I deleted the symbolic links, I was back to less than a GB of space taken for the directory. Why is the system not intelligent enough to realize that files through the symbolic link are actually being physically stored elsewhere?

---

### Post by hwttdz on 2009-12-10
Can you share the command that you're using to create the links.  It sounds like there is a problem here.

On my machine
dd if=/dev/urandom of=a.log bs=1M count=2 #make a random 2M file
du . 
> 2056
ln -s a.log link_to_a
du .
> 2056

So I didn't increase the size of the folder by adding a link to a file.  Even better I tried
ln -s /media/windows_drive/pagefile.sys  link_to_windows_page_file
du .
> 2056
which more accurately simulates the situation you're in.  Of course it's not identical, as that's a drive actually in my box, but a different partition, should be the same as a NAS?

---

### Post by RonRN18 on 2009-12-11
I created my links from within Nautilus.

---

### Post by hwttdz on 2009-12-11
So when you were using nautilus, you got a couldn't create link error because out of space?  out of space where? i.e. did it read out of space on /media/sda1? Then how were you testing the amount of space used?

---

