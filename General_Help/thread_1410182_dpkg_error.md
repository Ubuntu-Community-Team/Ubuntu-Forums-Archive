---
title: "dpkg error"
date: 2010-02-18
forum: General Help
---

### Post by Coach_Mark on 2010-02-18
haven't had this crop up before.

"An Error Occurred
The following details are rovided:

E:dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report."

I did run the sudo.  there was a slight delay before it gave me my prompt again, but there was no output.

bell4@bell4-laptop:~$ sudo dpkg --configure -a
bell4@bell4-laptop:~$ 

I still have the little red circle with a line through it at the top of my screen, so I don't think anything got changed/fixed.  can someone explain what that means, and what I need to do?  I am running 9.10.

Thanks!

---

### Post by nothingspecial on 2010-02-18
> **Coach_Mark said:**
> haven't had this crop up before.

"An Error Occurred
The following details are rovided:

E:dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report."

I did run the sudo.  there was a slight delay before it gave me my prompt again, but there was no output.

bell4@bell4-laptop:~$ sudo dpkg --configure -a
bell4@bell4-laptop:~$ 

I still have the little red circle with a line through it at the top of my screen, so I don't think anything got changed/fixed.  can someone explain what that means, and what I need to do?  I am running 9.10.

Thanks!

When bash gives no output it meant that the operation(s) completed successfully. You should be good to go.

---

### Post by Coach_Mark on 2010-02-18
[UPDATE]I went to run the update manager manually, and got the following output:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb)
  404  Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.0-3ubuntu5.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.0-3ubuntu5.3_i386.deb)
  404  Not Found [IP: 91.189.88.46 80]"

I also got the following message:

You have 1 broken package on your system!
Use the "Broken" filter to locate it.

that check shows that libc6 is broken. how do I reinstall that package? do i uninstall and reinstall, or mark for upgrade, or is there another step(s) I should follow?

---

### Post by nothingspecial on 2010-02-18
First try

```
sudo apt-get install -f
```

---

### Post by oldos2er on 2010-02-18
To fix a broken package either run **sudo apt-get install -f** in a terminal, or in Synaptic Package Manager click Edit, Fix Broken Packages.

---

### Post by Coach_Mark on 2010-02-18
ah!  missed the fix broken packages option.  so, now the little red cirlec thing is gone.  but, when i run the update manager, i get the following message:

"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?" No/Yes

i click no, i get the following message again:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb)
  404  Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.0-3ubuntu5.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.0-3ubuntu5.3_i386.deb)
  404  Not Found [IP: 91.189.88.45 80]"

do i want to ignore those (unspecified) packages?  I would think not, but...

---

### Post by nothingspecial on 2010-02-18
Next I would do a ```
sudo apt-get update
``` to see if it sorts itself out.

---

### Post by Coach_Mark on 2010-02-18
I got it.  I ran the check for packages from the package manager, then clicked install.  I got no error messages and all isntalled!

thanks for all the help.

---

