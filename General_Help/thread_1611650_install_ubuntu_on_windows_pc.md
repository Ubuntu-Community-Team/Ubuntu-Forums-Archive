---
title: "install ubuntu on windows pc"
date: 2010-11-02
forum: General Help
---

### Post by Chelidze on 2010-11-02
I have windows installed on my pc and i have my hdd partition into C and D
 Windows is installed on partition C and have important  data stored on D
Here what i want : I want to delete windows and install ubuntu on c  Drive but keep D partition and use  its files in future and is there a  way to do so  8-[

---

### Post by ragnar_123 on 2010-11-02
Yes, it is no problem. When installing Ubuntu, you'll be asked, which partition you want to install to, just select the one that was c: drive.

(If they are different in size, it should be easy to choose the right one :-))

---

### Post by Chelidze on 2010-11-02
i will choose the partition 
 but when it asks my ,,Type, mount point"  what should i choose ??

---

### Post by TheAnachron on 2010-11-02
> but when it asks my ,,Type, mount point" what should i choose ??
"/"

---

### Post by Chelidze on 2010-11-02
> **TheAnachron said:**
> "/"
but what should i choose for d drive ?????
and swap what drive should i chose for it and C and D are ntfs format is that a problem ???

---

### Post by matt_symes on 2010-11-02
Hi

Dont worry about the D drive at the moment. All you have done so far is tell the installer where you want your root system mounted to. (Just make sure you select the XP partition)
During install Ubuntu should detect your D drive (if its internal) and will mount it for you.
If its external then when you plug it in it should find it.
If it does not then there are plenty of people here who can tell you how to update your fstab file to ensure you can use it.

Keep your swap on the same drive as ubuntu.

NTFS is not a problem, don't worry. Ubuntu will format the partition it uses to a different type.

Kind regards

---

### Post by Chelidze on 2010-11-02
> **matt_symes said:**
> Hi

Dont worry about the D drive at the moment. All you have done so far is tell the installer where you want your root system mounted to. (Just make sure you select the XP partition)
During install Ubuntu should detect your D drive (if its internal) and will mount it for you.
If its external then when you plug it in it should find it.
If it does not then there are plenty of people here who can tell you how to update your fstab file to ensure you can use it.

Keep your swap on the same drive as ubuntu.

NTFS is not a problem, don't worry. Ubuntu will format the partition it uses to a different type.

Kind regards
when i am installing ubuntu it gives me a drop box of options which include EXT 4  ntfs  swap and many more which one should i choose swap ???????

---

### Post by snowpine on 2010-11-02
A couple of things:

1. **BACK UP** your important data on D: to an external drive (then disconnect the external drive from the computer). I cannot stress this enough! 

2. ext4 is a good filesystem choice for the Ubuntu / (root) partition.

3. If you plan to use swap, you'll need to create a 3rd partition. The size will depend on how much RAM you have; 2x your RAM was the old recommendation, but if you have 1 GB or more of RAM, you can probably get away with 1x your RAM (and some people don't use swap at all).

4. Ubuntu has a "Guided Install" option to resize your existing partitions and install side-by-side. This is the safest option to choose if you are nervous about partitioning (but does not replace a proper backup as I urged above).

---

### Post by Chelidze on 2010-11-02
:)ok i finally installed ubuntu and didn't Delete any files from d but now i do not have any swap space is there a way to create a 2 gigabytes swap with cmd or terminal in the same volume where the ubuntu is installed ](*,)

---

### Post by wilee-nilee on 2010-11-02
I think this link is what your basically looking for. 
[https://help.ubuntu.com/community/SwapFaq#addswap](https://help.ubuntu.com/community/SwapFaq#addswap)

Be very careful it may be that you could do this easier by resizing the Linux partition and just making a swap partition.

---

### Post by Swagman on 2010-11-02
lol

I've got 4gb Ram but have a 10gb swap partition.

[img]http://localhostr.com/files/ada386/Ubuntu100.jpeg[/img]

---

### Post by wilee-nilee on 2010-11-02
> **Swagman said:**
> lol

I've got 4gb Ram but have a 10gb swap partition.


How do you have the vm.swappiness swap set. You wont be doing any paging I guess.
[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

---

### Post by Swagman on 2010-11-02
Default 60

Sys is fast enough.

---

### Post by Chelidze on 2010-11-03
It works thank you all for your posts been very helpful  :)

---

