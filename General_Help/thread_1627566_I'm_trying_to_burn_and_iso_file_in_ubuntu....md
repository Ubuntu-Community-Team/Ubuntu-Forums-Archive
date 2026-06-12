---
title: "I'm trying to burn and iso file in ubuntu..."
date: 2010-11-21
forum: General Help
---

### Post by gismo93 on 2010-11-21
As the title says I've been trying to burn a windows 7 iso to a blank disc in ubuntu.

I've tried right click-write to disk, it writes it but the disc won't boot and when I look inside the disc there's no files present.

I tried doing it with cd creator and it gives me some messages like.

"Do you want to create a disc from the contents of the image or with the image file inside?"

"There is only one selected file

("xxxxxx.iso") It is the image of a disc and its contents can be burnt."

I click "burn as file"

Then I get a message saying "Do you really want to add
"xxxxxx.iso to the selection and use the version of ISO9660 standard to support it"?

"the size of the file is over 2gb. Files larger than 2gb are not supported by iso9660 standard in its first and second versions. it is recommended to use the third version of iso9660 standard which is supported by most operating systems including linux and all versions of windows."

I click add file.

Then it starts "estimating the file size" It says please wait untill this operation is completed, but it never does, I left it for 2 hours.

I also tried burning with infra record in windows and get some error messages, and I also tried brasero in ubuntu with no success.

Does anyone know what I have to do to get this working?

Thanks in advance.

---

### Post by sohlinux on 2010-11-21
I had a similar problem only yesterday, I fixed it by extracting the iso file to a folder then copying the files to the dvd with cd creator. if you cant see inside the iso then install a program like gmount which you will find in the ubuntu software center.

---

### Post by gismo93 on 2010-11-21
Installed gmount and tried to mount the iso, got an error and a file names iso with a disc icon appeared on my desktop, went inside it and i just see a readme file. it says "This disc contains a "UDF" file system and requires an operating system 
that supports the ISO-13346 "UDF" file system specification."

what now?

---

### Post by pbpersson on 2010-11-21
I always use the feature in K3B called "burn image" and point it to the file.

---

### Post by devondashla on 2010-11-21
> **gismo93 said:**
> As the title says I've been trying to burn a windows 7 iso to a blank disc in ubuntu.

I've tried right click-write to disk, it writes it but the disc won't boot and when I look inside the disc there's no files present.

I tried doing it with cd creator and it gives me some messages like.

"Do you want to create a disc from the contents of the image or with the image file inside?"

"There is only one selected file

("xxxxxx.iso") It is the image of a disc and its contents can be burnt."

I click "burn as file"

Then I get a message saying "Do you really want to add
"xxxxxx.iso to the selection and use the version of ISO9660 standard to support it"?

"the size of the file is over 2gb. Files larger than 2gb are not supported by iso9660 standard in its first and second versions. it is recommended to use the third version of iso9660 standard which is supported by most operating systems including linux and all versions of windows."

I click add file.

Then it starts "estimating the file size" It says please wait untill this operation is completed, but it never does, I left it for 2 hours.

I also tried burning with infra record in windows and get some error messages, and I also tried brasero in ubuntu with no success.

Does anyone know what I have to do to get this working?

Thanks in advance.

Instead of burning it as a file, you should have burnt it as an image. All I can say is try it with a different CD. I've always had issues with Brasero, as once I burn a disc it is unreadable. Try using Gnomebaker, it's what I use now.

---

### Post by gismo93 on 2010-11-21
Ok, just tried burning with gnomebaker, didn't get any errors, write was succesful, still won't boot though and there seems to be nothing on the disk.

don't think trying k3b will work, there's something wrong with the file, i really dont want to download it again though, I tried it with a different disk too.

---

### Post by sohlinux on 2010-11-21
> **gismo93 said:**
> Ok, just tried burning with gnomebaker, didn't get any errors, write was succesful, still won't boot though and there seems to be nothing on the disk.

don't think trying k3b will work, there's something wrong with the file, i really dont want to download it again though, I tried it with a different disk too.

normally you can easily extract all the files from any iso so if you cant even extract the files maybe you have a corrupt iso file. there are a few more tools for extracting iso files you could try before you download again. search for iso in the ubuntu software center.

---

### Post by gismo93 on 2010-11-22
Think I might have found the problem, there's a chance it may have been the disks I was using, gonna mount the iso in windows and install from the desktop.

Thanks for everyone's help.

---

### Post by carolina on 2011-05-05
I have tried Brasero & K3b and both get write errors . Installed Gnomebaker and it gives the following message:

-( /dev/sr0: media is not recognized as recordable DVD: 0

Have tried several cd's  and even a dvd , all newly purchased so wondering if i have a cd/dvd softwear issue ?

Thoughts anyone

---

### Post by jramshu on 2011-05-05
I've burned iso's with brasero over the past few days. I've even been burning them from my mounted windows partition with no problems. Getting ready to burn 10.04 after it finishes downloading.

I did have a problem with 11.04 beta iso, kept getting i/o errors, ran a lens cleaner and haven't had any problems since.

---

