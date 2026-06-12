---
title: "No fan Acer Aspire Causes over heating."
date: 2010-10-16
forum: General Help
---

### Post by PyrexKidd on 2010-10-16
Hi,

I have an Acer Aspire 5315-2122 and the fan does not come on causing the computer to overheat and power off.  There is not an available BIOS update from Acer, so I am unable to update as I saw in the 8.10 bug reports.
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/209837](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/209837)

It does not appear that ACPI supports my hardware.

Any suggestions?

---

### Post by filolog on 2010-10-17
Hi dude,

I had the same fan & overheating problem on Acer Aspire 5315 (bought in UK). Although I was a bit weary after reading so many forums, I managed to update my BIOS.

However, instead of using the .exe application with BIOSv1.45 (from this ACER.CO.UK site: [http://www.acer.co.uk/acer/service.do;jsessionid=AB12754677EB7CC33930582BE04AB4BA.public_a_14a?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360](http://www.acer.co.uk/acer/service.do;jsessionid=AB12754677EB7CC33930582BE04AB4BA.public_a_14a?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360)  ), 

I used the live CD ISO (FreeDOS) prepared by Angel Garcia and following Groszman's instructions. Read this post:

[http://ubuntuforums.org/archive/index.php/t-1043129.html](http://ubuntuforums.org/archive/index.php/t-1043129.html)

It helped me, I now have BIOS v1.43  and my fan works perfectly under Ubuntu and LiveUSB with PSlinuxOS e17.

(by the way, v1.43 of BIOS seems to be the latest on ACER.COM site: 
[http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html))

I hope it helps.
:)

---

