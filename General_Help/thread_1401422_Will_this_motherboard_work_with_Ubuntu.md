---
title: "Will this motherboard work with Ubuntu?"
date: 2010-02-08
forum: General Help
---

### Post by waloshin on 2010-02-08
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16856119015](http://www.newegg.ca/Product/Product.aspx?Item=N82E16856119015)

And what motherboard is in this Foxconn case? 

The reason why I ask is : [http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux)

---

### Post by Spectre5 on 2010-02-08
> **waloshin said:**
> [http://www.newegg.ca/Product/Product.aspx?Item=N82E16856119015](http://www.newegg.ca/Product/Product.aspx?Item=N82E16856119015)

And what motherboard is in this Foxconn case? 

The reason why I ask is : [http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux)

From wikipedia:
ACPI functionality with Linux

On July 25, 2008, a user of Ubuntu Linux claimed that the BIOS in the G33M and G33M-S motherboards from Foxconn contained references to Linux in its ACPI DSDT and interpreted this as an attempt to change behaviour under the Linux kernel.[16] Further investigation showed that the only Linux-specific code in the BIOS had not been run since Linux version 2.6.9.[17]

Foxconn customer support initially claimed that "the motherboard only supported Windows Vista".[18] This caused a wave of protest, resulting in Foxconn releasing an updated BIOS to improve Linux compatibility.[19][20] Foxconn has also said that it plans to repair all other Foxconn-branded motherboards, and to test Linux alongside Windows in the future.[21]

Investigation revealed the issue was caused by the American Megatrends BIOS assuming that the operating system would clear the ACPI WAK_STS flag on resume, causing the BIOS to interpret a reboot as an attempted resume from memory.[22] The same issue was present in motherboards from other manufacturers using the same BIOS. A short patch to the Linux kernel to work around this issue was submitted upstream.[22]


[http://en.wikipedia.org/wiki/Foxconn#ACPI_functionality_with_Linux](http://en.wikipedia.org/wiki/Foxconn#ACPI_functionality_with_Linux)

---

### Post by waloshin on 2010-02-08
Bump

---

### Post by snowpine on 2010-02-22
The Digg article you linked to is ancient history. (Check the date on the article!)

I have a very similar Foxconn barebones (the R10-S4) and it runs Linux pretty well. The only complaint I have is that the graphics card is not well supported by Ubuntu 9.10 (enabling Compiz freezes the system). Happy to answer any specifc questions you might have. :)

---

