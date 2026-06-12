---
title: "Dual boot and switchable graphics"
date: 2010-01-01
forum: General Help
---

### Post by zine92 on 2010-01-01
I am using a lenovo w500, installed are windows 7 and ubuntu 9.10 but the problem is, linux does not support the switchable graphics at this point in time and because i need to do my school work in windows but i prefer ubuntu. The problem is when i boot into ubuntu, i need to set the bios settings to internal display else my computer will run 2 graphics card at the same time which is redundant and hot and of course uses a lot more electricity. And if i boot into windows, it will automatically change the setting from internal/dedicated back to switchable. The catch is that, is there a script/programmes of sort to help me disable the running of my dedicated graphics when i boot up ubuntu without manually tweaking my bios everytime i use ubuntu.

---

### Post by avilella on 2010-01-02
It is quite possible that the ACPI calls to switch on/off the discrete graphics card on the Lenovo W500 are similar to other models that already have hybrid graphics support in Linux ([http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)).

Could you please submit your DSDT.dsl information as an attachment to this bug report?

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:

sudo apt-get install acpidump iasl

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat
ls -l DSDT.dsl

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

Finally, for posting the information in the bug report, you can check the model and generation identifier for your computer with this command:

sudo dmidecode -s system-product-name

And the model of the graphics card/s with this command:

lspci | grep VGA


> **zine92 said:**
> I am using a lenovo w500, installed are windows 7 and ubuntu 9.10 but the problem is, linux does not support the switchable graphics at this point in time and because i need to do my school work in windows but i prefer ubuntu. The problem is when i boot into ubuntu, i need to set the bios settings to internal display else my computer will run 2 graphics card at the same time which is redundant and hot and of course uses a lot more electricity. And if i boot into windows, it will automatically change the setting from internal/dedicated back to switchable. The catch is that, is there a script/programmes of sort to help me disable the running of my dedicated graphics when i boot up ubuntu without manually tweaking my bios everytime i use ubuntu.

---

