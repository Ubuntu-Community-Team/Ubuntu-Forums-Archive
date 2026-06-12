---
title: "Ubuntu 10.04 LTS freezing"
date: 2011-02-08
forum: General Help
---

### Post by ShadowVegan on 2011-02-08
I am running Ubuntu 10.04 LTS. As of 20-30 minutes ago it has frozen multiple times. The screen goes purple and it says Ubuntu 10.04 in the top left corner. The capslock light on my laptop flashes whenever this happens. When I power off and restart my laptop it turns on fine, and it restores my firefox tabs, but it continues to freeze every few minutes. It might be something really easy to fix, I've only had Ubuntu for a few months, any suggestions on how to fix this are very much appreciated.
Also, I doubt it has anything to do with it, but just in case, my laptop is dual partitioned with Ubuntu 10.04 LTS and Windows Vista SP2.
Thanks for any help.

---

### Post by dcstar on 2011-02-09
> **ShadowVegan said:**
> I am running Ubuntu 10.04 LTS. As of 20-30 minutes ago it has frozen multiple times. The screen goes purple and it says Ubuntu 10.04 in the top left corner. The capslock light on my laptop flashes whenever this happens. When I power off and restart my laptop it turns on fine, and it restores my firefox tabs, but it continues to freeze every few minutes. It might be something really easy to fix, I've only had Ubuntu for a few months, any suggestions on how to fix this are very much appreciated.
Also, I doubt it has anything to do with it, but just in case, my laptop is dual partitioned with Ubuntu 10.04 LTS and Windows Vista SP2.
Thanks for any help.

Install the lmsensors package and set it up to see if it is overheating:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by P4man on 2011-02-09
Can you give the exact type of laptop?
Assuming you have no issues with windows, and the hardware is fine, then it could be a BIOS/Linux compatibility issue. You might want to check the link in my signature for some possible workarounds, particularly you may want to try *acpi_osi="Linux"*

---

### Post by ShadowVegan on 2011-02-14
Thanks for the suggestions. I am on Ubuntu now and have been for a while with no issues, but if it starts freezing again I'll look into both of those. And yes, Windows has been running fine, but I don't think it's a compatibility issue, because Ubuntu was fine until a few days ago. I'm using an Asus G50-VT, but don't bother looking into the details right now because at the moment I'm not having any problems.

---

