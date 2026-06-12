---
title: "AVG Free downloading error"
date: 2009-12-20
forum: General Help
---

### Post by LoganM2009 on 2009-12-20
I am new to ubuntu and not sure what this error means.

I am trying to download AVG Free thru the wine application.
When downloading, I get this error:

/tmp/avg_free_stb_all_9_40_cnet-1.exe could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Im not sure what I need to due to fix this.

Any help would be nice

Thanks

---

### Post by sports fan Matt on 2009-12-20
Is there a folder on the desktop? where in Firefox Prefs/downloads say the download is? Inm thinking if you can find the indiviual folder then if you click on it it will bring up the paackage install (Gdebi on gnome) and then it would install.

---

### Post by odranoelson on 2009-12-20
Hi,
first of all: why are you trying to install AVG with wine?
1. Linux doesn't need anti-virus
2. If you really want, there's a version of avg for linux (google it)


But if you really wanna go on,
try clicking it with the right button and choosing open with (if you are using kde). With gnome there should be some option like that.

If not, open a terminal and type wine avg_free_stb_all_9_40_cnet-1.exe

Good luck

---

### Post by Marlonsm on 2009-12-20
You don't really need an antivirus for Ubuntu.

But if you share lots of data with Windows computers and want to protect them from viruses, take a look at the Software Centre and you'll find ClamAV (or KlamAV), with works very well.

---

### Post by odranoelson on 2009-12-20
Ah, you are doing it from firefox? First of all go to the folder where it is downloaded (and try what I've posted)

---

### Post by 73ckn797 on 2009-12-20
You are downloading a Windows "exe" file. The Gdebi installer will not work. Are you running only Ubuntu? You would need to get their Linux program. I could not find a Linux version on their website (a quick search). 

I use the Avast Linux version. It is free and installs with the Gdebi installer. If you are running Ubuntu 64 bit they do not have AV for that.

The Gdebi installer is in Applications/System Tools. If you do not see it go to System/Preferences/Main Menu. From there you can enable it to show in the Applications/System Tools menu.

---

