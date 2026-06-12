---
title: "strange messages:desc_count 0x555de, ret 0x7d78, transfer_count 0xf88c"
date: 2010-10-23
forum: General Help
---

### Post by michiedo on 2010-10-23
Hi all, I have an ethernet disk (iomega Home Media Network Hard Drive) that runs debian/lenny.
Telnetting to it, and issuing "dmesg" sometime i see messages like:
 
 desc_count 0xf000, ret 0x96a8, transfer_count 0xf000
 
sometime a single line, sometime a bunch of messages:
 
 desc_count 0xcdb0, ret 0x7c91, transfer_count 0xcdb0
 desc_count 0x890f, ret 0x7c92, transfer_count 0x890f
 desc_count 0x86d52, ret 0x7c9c, transfer_count 0x10000
 desc_count 0x6fd52, ret 0x78c, transfer_count 0x10000
 desc_count 0x5fd52, ret 0x29fc, transfer_count 0x10000
 desc_count 0x5d356, ret 0x7d78, transfer_count 0xf604
 desc_count 0x555de, ret 0x7d78, transfer_count 0xf88c
 desc_count 0x4d866, ret 0x7d78, transfer_count 0xfb14
 desc_count 0x45aee, ret 0x7d78, transfer_count 0xfd9c
 desc_count 0x3dd76, ret 0x7d78, transfer_count 0xf024
 desc_count 0x35ffe, ret 0x7d78, transfer_count 0xf2ac
 desc_count 0x1ed52, ret 0x5bc, transfer_count 0x10000
 desc_count 0x1e796, ret 0x7d78, transfer_count 0xfa44
 desc_count 0x16a1e, ret 0x7d78, transfer_count 0xfccc 

It happens randomly, ususally every other day, but sometimes twice a day.

I've googled for this messages, to no avail.
Anyone can give me a hint: what's that ? is something that require some action ?
it's only some kind of statistic ? 
...obviously my fear is that there is some hardware problem :-(
Thank you in advance !

---

### Post by michiedo on 2010-10-23
someone ("Mijzelf") on the iomega forum has found the source of the messages:
it come fromm from mm/filemap.c, line 1029, in function do_generic_mapping_read:
/** Some debug to test if our assumptions about the transfer length are correct                                             
     * We shouldn't see this message under normal execution
     */
    if ((start_desc_count != ret) && (transfer_count != ret)) {               
        printk("desc_count %#x, ret %#x, transfer_count %#x\n",start_desc_count,ret,transfer_count);                                  }

urg ! :-(

---

