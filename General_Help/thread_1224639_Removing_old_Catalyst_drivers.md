---
title: "Removing old Catalyst drivers"
date: 2009-07-27
forum: General Help
---

### Post by MariusLV on 2009-07-27
Hi all,

I have a problem uprading the drivers for my ATI Radeon HD 4870 graphics card. Having downloaded the latest version of the ATI Catalyst 9.7 Proprietary Linux x86 Display Driver (ati-driver-installer-9-7-x86.x86_64.run), I am unable to proceed because I cannot figure out how to remove, as recommended in the installer instructions, the older version of this driver. The installer instructions provide only the following instructions:

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"

Upon doing this, however, the response in terminal is that "No such file or directory" can be found. Since ATI provides no other instructions I am now at a loss.

I have of course requested help from ATI as well via their web form, but they seem to be taking their sweet time. Since I suspect the solution might be blatantly obvious to anyone with half my ignorance of such matters, and since I figure the solution to my problem might be of use to others, I figure it made sense to post here.

Thank you for your time :-)

---

### Post by MariusLV on 2009-07-27
UPDATE:

I feel a bit stupid, as I clearly didn't follow the instructions to the letter. I missed a space when typing "sudo sh ./fglrx-uninstall.sh", making it "sudo sh./fglrx-uninstall.sh". However, even after correcting that mistake, I still get an error message, though a different one. This time it says "sh: Can't open ./fglrx-uninstall.sh".

So I'm still at a loss.

---

### Post by MariusLV on 2009-07-29
PING

Well, the card manufacturer was no help at all. The response was that "we do not troubleshoot driver or multimedia issues in Linux", and that "all Linux help is self help online".

So if anyone can provide me some help, I would be grateful indeed. Or if not, is there anyone who could point me to some other place where it might make sense to post my question?

Thanks again :-)

---

### Post by Brain-free on 2009-07-30
No worries, your problem is a small one. The "fglrx-uninstall.sh" script you try to execute should be executed as:

```
sudo sh fglrx-uninstall.sh
```

Hopefully that works.

---

