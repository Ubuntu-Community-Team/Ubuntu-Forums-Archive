---
title: "unbuntu doesnt do anything"
date: 2011-03-01
forum: General Help
---

### Post by matti626 on 2011-03-01
OK so I have sony Vaio VPC-CW195s which I bought about about 3 months ago and unfotunatley now my hard drive has been defected by I-astor.sys, I was told that i have to zero fill the hard drive which after doing lots of research I found out that the best way is using UNBUNTU I should use the command prompt to zero fill the drive. I downloaded Unbuntu 10.10 from its own website and burned on a DVD. I put in the CD-drive and the laptop Used the CD to boot and as a matter of fact the unbuntu logo came up, asked for the language (I said english) and then I pressed to use unbuntu without installing then the cursor came up on the top left and screen went black and nothing happened(the laptop was still on it was working). I restarted and this time pushed it to install the same thing happened, the third time I pushed to test for hard drive defects and the same thing again.
So please help me with this, I really need to get thing going.....

---

### Post by lisati on 2011-03-01
I'm not sure I understand fully - your post almost reads as if you hit the "Submit" button too soon.

Are you asking how to use Ubuntu to zero fill your disk?

Edit: Ah, OP's question edited since I last looked in. Makes a bit more sense to me now. Someone else has taken the time to respond.

---

### Post by Hedgehog1 on 2011-03-01
> **matti626 said:**
> OK so I have sony Vaio VPC-CW195s which I bought about about 3 months ago and unfotunatley now my hard drive has been defected by I-astor.sys, I was told that i have to zero fill the hard drive which after doing lots of research I found out that the best way is using UNBUNTU I should use the command prompt to zero fill the drive. I downloaded Unbuntu 10.10 from its own website and burned on a DVD. I put in the CD-drive and the laptop Used the CD to boot and as a matter of fact the unbuntu logo came up, asked for the language (I said english) and then I pressed to use unbuntu without installing then the cursor came up on the top left and screen went black and nothing happened(the laptop was still on it was working). I restarted and this time pushed it to install the same thing happened, the third time I pushed to test for hard drive defects and the same thing again.
So please help me with this, I really need to get thing going.....

I think I can help here.  I still speak a little teenager (to communicate with my grand daughter):  

[I][B]OP needs to Zero Fill the Laptop's hard drive.

OP got as far as the 'try' option, but then she just got the mouse; the rest of Ubuntu did not come up.

OP Downloaded and is running 10.10[/B][/I]

I think the LiveCD's is a bad burn, or the choice of video driver the LiveCD is making is causing it to hang.

**Matti626: Please burn the CD again on the slowest possible speed.  Your other steps were fine.  If the slow-burned CD does the same thing, let us know and we will help you with the next step.**

---

### Post by lisati on 2011-03-01
> **Hedgehog1 said:**
> I think I can help here.  I still speak a little teenager (to communicate with my grand daughter):  

Thanks. The OP has edited the question since I last read it, and it makes more sense to me now.

---

### Post by matti626 on 2011-03-02
> **Hedgehog1 said:**
> I think I can help here.  I still speak a little teenager (to communicate with my grand daughter):  

[I][B]OP needs to Zero Fill the Laptop's hard drive.

OP got as far as the 'try' option, but then she just got the mouse; the rest of Ubuntu did not come up.

OP Downloaded and is running 10.10[/B][/I]

I think the LiveCD's is a bad burn, or the choice of video driver the LiveCD is making is causing it to hang.

**Matti626: Please burn the CD again on the slowest possible speed.  Your other steps were fine.  If the slow-burned CD does the same thing, let us know and we will help you with the next step.**

Well ok, I was a bit confused after I read hundreds of forums trying to burn the iso file on a dvd, and now here is my question am I supposed to burn the file with a particular software???? Last time I used roxie!

---

### Post by franchoy on 2011-03-02
> **matti626 said:**
> Well ok, I was a bit confused after I read hundreds of forums trying to burn the iso file on a dvd, and now here is my question am I supposed to burn the file with a particular software???? Last time I used roxie!

no particulars... just burn it as a .iso file and that should work...

---

### Post by Hedgehog1 on 2011-03-02
Have you burned an ISO file before?  You downloaded and booted Ubuntu 10.10, so I think you have.

An ISO file is an entire CD compressed into the smallest data file we can squeeze it into to.  

Most burning software has a 'Burn ISO' option, that converts the compressed ISO file into a fully populated CD.

:KS

---

### Post by sidzen on 2011-03-02
> **matti626 said:**
> Well ok, I was a bit confused after I read hundreds of forums trying to burn the iso file on a dvd, and now here is my question am I supposed to burn the file with a particular software???? Last time I used roxie!

Recommend using System Rescue CD to write the drive with zeros -- 
Download the iso and either a) burn to CD at no more than 8X  or DVD at no more than 4X or
b) use UNetbootin to make a bootable USB drive (Iuse an old 512MB flash drive).

Then get to the multi-colored prompt on page where user is asked to enter either "wizard" or "startx" &
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]

---

### Post by Hedgehog1 on 2011-03-02
Good thought - OP really wants a zeroed out hard drive.

Here is the link:

[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

This will get you back into Windows faster.

:KS

---

### Post by sidzen on 2011-03-02
Is there a Linux User Group in PDX, Hedgehog1?

BTW, thanks for the link to sysresccd!

---

### Post by Hedgehog1 on 2011-03-02
I have not looked for one.  I work with a bunch on Linux nerds, so I sorta-get-one-for-free. We use it heavily at work.

I think the forum works best for most folks. They can drop in at lunch break and such.

:KS

---

### Post by matti626 on 2011-03-03
> **sidzen said:**
> Recommend using System Rescue CD to write the drive with zeros -- 
Download the iso and either a) burn to CD at no more than 8X or DVD at no more than 4X or
b) use UNetbootin to make a bootable USB drive (Iuse an old 512MB flash drive).
 
Then get to the multi-colored prompt on page where user is asked to enter either "wizard" or "startx" &
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]
 
alright buddy, so far ur recommendation has worked the best. So I have the CD and I tried the '64bit kernelwith default options. Can u give me a step by step instruction on how to zero the drive please. ???
when I choose the '64bit kernel option it loads and I guess it asks me to enter something but I dont know what it is......

---

### Post by matti626 on 2011-03-04
> **sidzen said:**
> Recommend using System Rescue CD to write the drive with zeros -- 
Download the iso and either a) burn to CD at no more than 8X  or DVD at no more than 4X or
b) use UNetbootin to make a bootable USB drive (Iuse an old 512MB flash drive).

Then get to the multi-colored prompt on page where user is asked to enter either "wizard" or "startx" &
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]

Ok well i guess i did something! In TERMINAL I entered the command 'dd if=/dev/zero of=/dev/hda bs=1M'
And it then said ' dd writing no space left on device 
10+0 records in
9+0 records out
9.8 copied, 0.0148677 s, 662 Mb/s 
Is the hard drive zero filled now?

---

### Post by sidzen on 2011-03-10
> **matti626 said:**
> Ok well i guess i did something! In TERMINAL I entered the command 'dd if=/dev/zero of=/dev/hda bs=1M'
And it then said ' dd writing no space left on device 
10+0 records in
9+0 records out
9.8 copied, 0.0148677 s, 662 Mb/s 
Is the hard drive zero filled now?

(Sorry to be absent for so long --  too many diversions)

No, it's not filled with zeros -- too short of a duration.  Command was entered incorrectly.  Just cut and paste from the forum to your command line, if nothing else.  (This is how I began to learn how2 here at this forum!)

Dban is a utility which does this, too.  But it is quicker to use the dd command.  Google it!  Other forums have had very good tutorials on it, like linuxforums or linuxquestions

---

