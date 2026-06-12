---
title: "I need a new motherboard"
date: 2010-07-18
forum: General Help
---

### Post by BSG Fan on 2010-07-18
Now that my pc is a mess, where can I buy online a cheap but good & durable Motherboard?  Okay, I don't know if a any motherboard can fix my pc... is there a basic rule of what Motherboard to be bought for each tower(pc case)?

Any site out there u can recommend me?  I am in Puerto Rico and I have the suspect that some of the dealers of electronics/computers are selling Motherboard with problems with the video card, magnetized, etc.  So I am not interested to acquire it here.

Please, help.

Also, the motherboard also brings the video card, right?  but not its respective memory?

Help
(

---

### Post by cascade9 on 2010-07-18
The basic 'rule' is that the bigger the case, the bigger the motherboard you can fit into that case is. 

The main sizes motherboards come in are Mini-ITX (really tiny), Mirco-ATX (small, but not tiny) ATX (bigger again) and E-ATX (extended ATX...they are relly big) 

You can forget about E-ATX, its uncommon. Mini-ITX isnt common either, its normally only found in tiny desktop and htpc cases. You would probably have Micro-ATX or 'full' ATX. 

If you have a 'corporate' computer (dell, compaq, etc), what model computer are you using? If its a 'white box' then do you know what model motherboard you have, and what sized case? (sudo lshw should show the motherboard model).  

Motherboards can have onboard video, but not all of them do. Some of the motherboars with onboard video do have at least some dedicated video memory, but that is rare. Most of the time they use some of the main memory (system RAM).  

I'm pretty sure that newegg ships to Puerto Rico, they have good prices so its worth a look.

---

### Post by BSG Fan on 2010-07-18
> **cascade9 said:**
> The basic 'rule' is that the bigger the case, the bigger the motherboard you can fit into that case is. 

The main sizes motherboards come in are Mini-ITX (really tiny), Mirco-ATX (small, but not tiny) ATX (bigger again) and E-ATX (extended ATX...they are relly big) 

You can forget about E-ATX, its uncommon. Mini-ITX isnt common either, its normally only found in tiny desktop and htpc cases. You would probably have Micro-ATX or 'full' ATX. 

If you have a 'corporate' computer (dell, compaq, etc), what model computer are you using? If its a 'white box' then do you know what model motherboard you have, and what sized case? (sudo lshw should show the motherboard model).  

Motherboards can have onboard video, but not all of them do. Some of the motherboars with onboard video do have at least some dedicated video memory, but that is rare. Most of the time they use some of the main memory (system RAM).  

I'm pretty sure that newegg ships to Puerto Rico, they have good prices so its worth a look.


Hey, thanks a lot for your very informative reply. According the 'sudo' the case is: "PCI (sysfs)".  The case is from "Technology With Power" (PCS).  Also, (laugh) the measures are the following: 6" wide X 15" long X 15" tall.  The motherboard is "Intel".  Any way I can discover my exact motherboard?

About my comment over my island, I am not the only one here with problems with motherboards.  The dealers sell them as good but later they dont want to return the money back or get to us a better board.  That's is another story...  and yes, they seem to be magnetized and the video cards mostly don't work.  I am one of those people who fell in their businesses.

again thanks for ur very informative answer.

---

### Post by BSG Fan on 2010-07-18
here is the sudo information:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: P4M90-M7A
    vendor: BIOSTAR Group
    version: Ver:1.0
    serial: OEM_Serial
    width: 32 bits
  
       description: Motherboard
       product: P4M90-M7A
       vendor: BIOSTAR Group
       physical id: 0
       version: Ver:1.0
       serial: OEM_Serial
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/20/2008)
          size: 128KiB
          capacity: 448KiB
          
          description: CPU
          product: Intel(R) Celeron(R) CPU          430  @ 1.80GHz
          vendor: Intel Corp.

---

### Post by cascade9 on 2010-07-18
You should get the exact motherbaord from this command in terminal- 

sudo lshw 

Here is the 1st few lines I get from that command- 

```
description: Desktop Computer
    product: GA-770T-USB3
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=36434630-3439-3735-3235-3838FFFFFFFF
  *-core
       description: Motherboard
       product: GA-770T-USB3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
```You dont have to post the entire output, just the bit I posed should be enough. By the way, if you post more of the lshw output than I did, please use the 'code' tags (# is icon for adding the code tags).

---

### Post by cascade9 on 2010-07-18
The motherboard is a Biostar P4M90-M7A. 

Seems that was a motherboard that Biostar made for somebody else, so its not mentioned on the Biostar page- 

[http://www.biostar-usa.com/app/en-us/mb/index.php](http://www.biostar-usa.com/app/en-us/mb/index.php)

So I dont know for sure if it is ATX or MicroATX, or if it is DDR1 or DDR2. I would guess that it is a full ATX motherboard, using DDR2.

---

### Post by BSG Fan on 2010-07-18
> **cascade9 said:**
> You should get the exact motherbaord from this command in terminal- 

sudo lshw 

Here is the 1st few lines I get from that command- 

```
description: Desktop Computer
    product: GA-770T-USB3
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=36434630-3439-3735-3235-3838FFFFFFFF
  *-core
       description: Motherboard
       product: GA-770T-USB3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
```

You dont have to posy the entire output, just the bit I posed should be enough. By the way, if you post more of the lshw output than I did, please use the 'code' tags (# is icon for adding the code tags).

I don't know how to use the 'code tags'.  I already eliminated part of the mammoth output.  thanks u.

According I found:
  A-  the size: 900MHz
  B-  capacity: 4GHz
  C-  width: 64 bits

I will seek only these 3 parameters online to buy the motherboard or not?

second, I want to install it by myself.  It's easy to install, right?

---

### Post by BSG Fan on 2010-07-18
> **cascade9 said:**
> The motherboard is a Biostar P4M90-M7A. 

Seems that was a motherboard that Biostar made for somebody else, so its not mentioned on the Biostar page- 

[http://www.biostar-usa.com/app/en-us/mb/index.php](http://www.biostar-usa.com/app/en-us/mb/index.php)

So I dont know for sure if it is ATX or MicroATX, or if it is DDR1 or DDR2. I would guess that it is a full ATX motherboard, using DDR2.

Thanks for ur informative reply.
Okay, so we guess it is a "ATX motherboard with DDR2".  

I will like to buy a full case (tower) with just its motheboard, cables, etc enclosed..

Let see..

---

### Post by cascade9 on 2010-07-18
> **BSG Fan said:**
> I don't know how to use the 'code tags'.  I already eliminated part of the mammoth output.  thanks u.

According I found:
  A-  the size: 900MHz
  B-  capacity: 4GHz
  C-  width: 64 bits

I will seek only these 3 parameters online to buy the motherboard or not?

second, I want to install it by myself.  It's easy to install, right?

The 'code tags are pretty easy, once you know how to use them. You hit the '#' symbol above where you post, and you get 2 'code' tags in square brackets (one is just 'code', the other '/code'). just paste what you want to post between the 2 tags. 

'Width' doesnt matter too much, if the chipset supports your CPU it should support 64bit as well. 

The 'capacity' output on lshw can be wrong. Your CPU wont get close to 4GHz, even overclocked. Standard it runs at 1.8GHz. 

[http://ark.intel.com/Product.aspx?id=29735](http://ark.intel.com/Product.aspx?id=29735)

What you want is a motherboard that has socket 775 and a FSB of at least 800MHz.  

Installation isnt super hard, but it can be annoying for some people. MY general rule is, 'if you can assemble a lego toy and have it look like the picture on the box, you should be OK.'

---

### Post by Cavsfan on 2010-07-18
Here is a link to NewEgg. They are great and they ship to Puerto Rico also!

You can view/compare any and all PC parts on there.

_[http://www.newegg.com/](http://www.newegg.com/)_

I bought my latest system from them. Very :D

---

### Post by BSG Fan on 2010-07-18
> **cascade9 said:**
> The 'code tags are pretty easy, once you know how to use them. You hit the '#' symbol above where you post, and you get 2 'code' tags in square brackets (one is just 'code', the other '/code'). just paste what you want to post between the 2 tags. 

'Width' doesnt matter too much, if the chipset supports your CPU it should support 64bit as well. 

The 'capacity' output on lshw can be wrong. Your CPU wont get close to 4GHz, even overclocked. Standard it runs at 1.8GHz. 

[http://ark.intel.com/Product.aspx?id=29735](http://ark.intel.com/Product.aspx?id=29735)

What you want is a motherboard that has socket 775 and a FSB of at least 800MHz.  

Installation isnt super hard, but it can be annoying for some people. MY general rule is, 'if you can assemble a lego toy and have it look like the picture on the box, you should be OK.'

Hey cascade9:
Thanks you sooooo much for your help and patience.
You rock.  =I will do my search with what u gave me.
Thanks
=)

---

### Post by BSG Fan on 2010-07-18
> **Cavsfan said:**
> Here is a link to NewEgg. They are great and they ship to Puerto Rico also!

You can view/compare any and all PC parts on there.

_[http://www.newegg.com/](http://www.newegg.com/)_

I bought my latest system from them. Very :D


Thanks you
I will check the link now.
=)
:p

---

