---
title: "Help on Ubuntu Virus Scanner"
date: 2011-05-15
forum: General Help
---

### Post by sandy0594 on 2011-05-15
Can someone kindly guide how to scan the whole computer using **clam virus scanner**.

Thanks in advance!!

---

### Post by wilee-nilee on 2011-05-15
Follow this for the gui and all you need .
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

I would be more inclined o use this though it is a top rated scanner.
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)

Or this, which if you choose needs a easy file modification to open every time, it is a mod from there forums standard stuff.
[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

---

### Post by sandy0594 on 2011-05-15
I already have clam installed..but,the thing is it doesn't have the option to scan the **whole computer**..It just as the option of scanning **full home scan**

---

### Post by wilee-nilee on 2011-05-15
> **sandy0594 said:**
> I already have clam installed..but,the thing is it doesn't have the option to scan the **whole computer**..It just as the option of scanning **full home scan**

I don't use clam but the other two sorry.

---

### Post by sandy0594 on 2011-05-15
So,what av do u use and kindly guide me how to scan all the partitons

---

### Post by wilee-nilee on 2011-05-15
> **sandy0594 said:**
> So,what av do u use and kindly guide me how to scan all the partitons

See my post 2 get the bitdefender

---

### Post by wilee-nilee on 2011-05-15
Download this.
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)

install gdebi in a terminal run
sudo apt-get install gdebi

When you have the key sent to your email right click the downloaded deb choose gdebi to install.

---

### Post by WorMzy on 2011-05-15
```
clamscan -r -i --exclude-dir=^/sys --exclude-dir=^/dev --exclude-dir=^/proc /
```

---

### Post by sandy0594 on 2011-05-15
> **WorMzy said:**
> ```
clamscan -r -i --exclude-dir=^/sys --exclude-dir=^/dev --exclude-dir=^/proc /
```

The scan is happening..But,what if i want to delete the viruses i found..should i manually explore them or is there anyway to delete

---

### Post by sandy0594 on 2011-05-15
@wilee-nilee~I tried to get bit defender..How to download it,i don't find any link...I got this link [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)
to my mail..But when i click them just a script is opening..

---

### Post by WorMzy on 2011-05-15
> **sandy0594 said:**
> The scan is happening..But,what if i want to delete the viruses i found..should i manually explore them or is there anyway to delete

You can do it manually, or you can use the --move=/path/to/destination or --remove=yes flags. I'd recommend that you remove the problem files manually, so you can use your own judgement on whenever they're false positives or not.

---

