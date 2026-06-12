---
title: "Partition help/resources and PartImage"
date: 2010-05-11
forum: General Help
---

### Post by bkann on 2010-05-11
Hi -

I consider myself an advanced Linux user in some aspects, but there are several things I still struggle with.  Partitions top that list.  I have two questions on the subject -

First, does anyone know of any resources that can help me better understand partitions, what they're used for, and what an ideal mix might look like.  For example, why is linux-swap contained within an extended partition instead of just being a stand-alone partition?  Also, I've heard of some people setting up a separate '/home' partition.  Is this recommended?

Second, a more tactical question.  I started to back up using PartImage before upgrading to 10.04.  What partitions do I need to include? Just the main ext3 one?  Should I include the swap?

Thanks in advance for any help!

---

### Post by srs5694 on 2010-05-11
Some pointers and brief answers:


[list]
[*][A piece I wrote on partitions/filesystems for IBM developerWorks](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) provides general background on the philosophy behind partitioning
[*]The [Filesystem Hierarchy Standard (FHS)](http://www.pathname.com/fhs/) describes where things go in a Linux directory tree
[*]The Wikipedia entry on [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) describes the most common partitioning system used on Linux systems
[*]The Wikipedia entry on [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) describes the next-generation partitioning system
[*][An article I wrote on GPT for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) describes Linux's GPT capabilities
[*]Swap can go in a primary partition or in a logical partition; it makes no difference. I can't be sure what was in the minds of Ubuntu's developers, but they probably put swap in a logical partition just to minimize the use of primary partitions, since they're a limited resource. (MBR supports just four primary partitions in total.)
[*]Splitting off /home in a separate partition is a good idea because it enables you to do a completely fresh re-install of your OS without damaging your user files. IMHO, Ubuntu should use such a configuration by default, but for whatever reason they don't.
[/list]

---

