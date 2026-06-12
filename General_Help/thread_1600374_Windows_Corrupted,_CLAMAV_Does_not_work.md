---
title: "Windows Corrupted, CLAMAV Does not work"
date: 2010-10-18
forum: General Help
---

### Post by abdusamed on 2010-10-18
My Windows Installation is infected even with Eset installed! I don't know how to clean it. Already tried safe mode scan, but that doesn't even clean it. The only reason I installed ubuntu was so that I could download infected files without any conserns of my windows parition being infected. When ever I download a file, I move it to the NTFS partition from where windows can access it. 

But just about a week ago when I booted into Windows, my whole drive was infected, not only windows installed partition but also all my NTFS partition. Can anyone please tell me how can I CLEAN the files rather than qurantine all the files which CLAMAV does! 

Also, what steps should I take in advance before downloading a virus infected file? I know the virus could've have gotten in when I disable eset for some software installation but it should clean after boot or after being booted... 

But there should be a way to clean all my NTFS partition .... how? I don't know how to used CLAMAV properly because whenever I try to scan anything, it always returns with '0 files scan' because I think the directory scan doesn't work the way it should!

---

### Post by Pollox on 2010-10-19
> The only reason I installed ubuntu was so that I could download infected files without any conserns of my windows parition being infected. When ever I download a file, I move it to the NTFS partition from where windows can access it.

Wait a second. Are you saying you download files you think might be infected using Ubuntu, but then go and open them in Windows? If you open an infected file in Windows, you can get a virus, regardless of how you downloaded it.

This isn't really a Windows support site, so I can't provide much help in that area. You should consider reinstalling Windows and using better antivirus software in the future (also Spybot is helpful for removing things antivirus programs miss). You can use Ubuntu to access and backup files from your NTFS partition you know are safe. Your options in the future are:
* don't download files from sites you don't trust
* access untrusted files *only* from Ubuntu (maybe consider switching OSes if viruses are an issue for you)

---

### Post by 3rdalbum on 2010-10-19
> **abdusamed said:**
> 
Also, what steps should I take in advance before downloading a virus infected file?

1. Think.about what you're doing
2. Decide not to download virus-infected files, or any files you don't trust.

These steps should be followed all the time.

Honestly - don't touch any files that you know to be infected, except to get rid of them.

---

### Post by abdusamed on 2010-10-19
I just realized what a pointless thread this... I don't mind mods deleting this out of existence! Only thing I should do in the future is to scan it with CLAM and then access it.

But in this situation, I can't do that because of the file size my ext4 partition size, I have to download the risky infected file into my NTFS partition which is a risk... but I have no choice...

thread solved............

---

