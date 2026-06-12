---
title: "Problem installing Kubuntu after Wubi uninstallation"
date: 2011-12-29
forum: General Help
---

### Post by antiedman on 2011-12-29
Ok Here's a head scratcher that makes grown mean weep.

Computer:

Acer Aspire 7551-7422
amd

Prolog
Successfully installed Ubuntu Ubuntu environment under Wubi for duel boot.

A few weeks later uninstalled Ubuntu as via Wubi

Now Trying to Install Kubuntu

Problem:

Kubuntu Install Message

Ubuntu still present

How do I fully remove Ubuntu so I can get Kbuntu.

I'm lost because unlike my other computers I have know Idea how to get to the partion menu.

---

### Post by Rubi1200 on 2011-12-30
> **antiedman said:**
> Ok Here's a head scratcher that makes grown mean weep.

Computer:

Acer Aspire 7551-7422
amd

Prolog
Successfully installed Ubuntu Ubuntu environment under Wubi for duel boot.

A few weeks later uninstalled Ubuntu as via Wubi

Now Trying to Install Kubuntu

Problem:

Kubuntu Install Message

Ubuntu still present

How do I fully remove Ubuntu so I can get Kbuntu.

I'm lost because unlike my other computers I have know Idea how to get to the partion menu.
Even though you had Wubi this problem needs to be addressed in a separate thread.

Thanks for understanding.

---

### Post by jcer93705 on 2012-05-24
> **antiedman said:**
> Ok Here's a head scratcher that makes grown mean weep.

Computer:

Acer Aspire 7551-7422
amd

Prolog
Successfully installed Ubuntu Ubuntu environment under Wubi for duel boot.

A few weeks later uninstalled Ubuntu as via Wubi

Now Trying to Install Kubuntu

Problem:

Kubuntu Install Message

Ubuntu still present

How do I fully remove Ubuntu so I can get Kbuntu.

I'm lost because unlike my other computers I have know Idea how to get to the partion menu.

You ever gotten you're laptop going under linux?

---

### Post by Rallg on 2012-05-30
Even though the original question is old, the answer is useful:

When you use WUBI on Windows XP, here is what happens:

1. WUBI creates a folder "ubuntu" in the location you requested. The folder is called "ubuntu" even if your version is Kubuntu. Inside that folder, WUBI places some files that will be used after reboot.

2. WUBI creates two files "wubildr.mbr" and "wubildr" (or similar names) and places them at the top level of drive C. This is the same location where Windows XP has its own boot loader, called "ntldr" (ntldr is not visible unless you tell Windows to make hidden system files visible). Note that the new files have the same name regardless of whether you are using Ubuntu or Kubuntu.

3. WUBI adds a line to your Windows "boot.ini" file, providing you the choice to boot into Ubuntu (it will be called Ubuntu no matter what).

4. After reboot into Ubuntu, the peviously-placed ubuntu folder has its files go nto action, and many mystical things happen. All of it takes place within that folder.

Now, If you use WUBI's own uninstaller, it is supposed to do the following: Delate the "ubuntu" folder, delete "wubildr" and "wubildr.mb" files, and remove the Ubuntu entry from "boot.ini" file. That's all. You can do this yourself, manually. But if anything is left behind, WUBI senses that a previous installation is present.

I do not know what WUBI does for Vista or 7. Sorry.

Now, suppose you installed Ubuntu via WUBI on XP, and want to try Kubuntu via WUBI (placed at the same location). The installer complains about a prior installation. I have successfully done this: In Windows, re-name the "ubuntu" folder to "ubuntu-other" (or something), re-name "wubldr" and "wubildr.mbr to something else, and delete the Ubuntu entry from boot.ini. Warning: If you fumble the edit to boot.ini, then you won't be able to boot into Windows! So you should make a copy of boot.ini before you edit it. In case of fumble, use Ubuntu from CD to get into C: and change the file name (I advise against editing a Windows file from Ubuntu, due to possible line ending incompatibilities).

Then, install Kubuntu via WUBI. Later, if you wish to go back to non-K Ubuntu, re-name the folder and files. You don't have to re-run WUBI.

I have tried this, and it worked for me. YOUR RESULTS MAY DIFFER, so I would only do this if you are testing, NOT if you have valuable files within Ubuntu, because I know of no way they could be extracted from the WUBI-installed file system.

---

