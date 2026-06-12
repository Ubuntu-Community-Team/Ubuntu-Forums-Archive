---
title: "Unable to operate MD5Sum."
date: 2011-05-30
forum: General Help
---

### Post by OldBoy44 on 2011-05-30
Hi all,

I have been trying to check on a ISO file as in - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). When I enter in a terminal "cd download_directory" the following error occurs.
bash: cd: download_directory  No such file or directory. Can somebody kindly assist?

The ISO file has been downloaded to /home/user1/Downloads/ubuntu-11.04-desktop-amd64.iso 
I will be purchasing a new computer soon with which I hope to burn the ISO file to CD. I don't have a burner on my present computer. 

Any assistance will be appreciated.

Cheers,

---

### Post by plucky on 2011-05-30
> **aussiebean said:**
> Hi all,

I have been trying to check on a ISO file as in - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). When I enter in a terminal "cd download_directory" the following error occurs.
bash: cd: download_directory  No such file or directory. Can somebody kindly assist?

The ISO file has been downloaded to /home/user1/Downloads/ubuntu-11.04-desktop-amd64.iso 
I will be purchasing a new computer soon with which I hope to burn the ISO file to CD. I don't have a burner on my present computer. 

Any assistance will be appreciated.

Cheers,

Try in a terminal

```
cd Downloads
md5sum ubuntu-11.04-desktop-amd64.iso
```

Linux is case sensitive

Good Luck

---

### Post by dFlyer on 2011-05-30
First if I understood you correctly your trying to cd into Download_directory. I think you might want to try to cd Downloads. Than run md5sum enter.name.of.iso.

---

### Post by OldBoy44 on 2011-05-30
Thanks so much for your expertize plucky. You are a genius.

The Hash sum was spot on - I am rapt!

Cheers and many thanks, :popcorn:

Thanks to you too dFlyer.

---

