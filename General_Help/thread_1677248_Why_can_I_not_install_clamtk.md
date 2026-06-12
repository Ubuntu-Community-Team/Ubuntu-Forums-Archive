---
title: "Why can I not install clamtk?"
date: 2011-01-28
forum: General Help
---

### Post by Jammanuser on 2011-01-28
Hi all.
I have tried to install clamtk 4 different ways now, and was unable to. :(
I first tried Add/Remove Programs, typed in "virus" in the Search box, clicked on "Virus Scanner", checked the box right beside it, hit the Apply Changes box, and it started downloading stuff, and then quickly produced the following error:

> 
An error occurred

The following details are provided:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb)
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/clamtk/clamtk_3.11-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/clamtk/clamtk_3.11-1_all.deb)
  404 Not Found [IP: 91.189.88.30 80]


Next, I tried Synaptic, typed in "clam" in the Quick Search box, checked the box beside "clamtk", selected "Mark for installation", and hit the Apply button.

This produced the same error as that when I tried installing through Add/Remove Programs. Next, I tried downloading the ubuntu .deb clamtk installer, and double-clicked it on the desktop to run it. I then pressed Install Package, and it soon reported:

> 
Could not download all required files

Please check your internet connection or installation medium.

Details:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb) 404 Not Found [IP: 91.189.92.167 80]

My internet connection is fine btw.
I then tried "sudo apt-get install clamtk" from the Terminal, and it produced:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libraw1394-dev libavutil-dev libdc1394-22-dev
  linux-headers-2.6.27-16-generic libtheora-dev
  linux-headers-2.6.27-11-generic linux-headers-2.6.27-11
  linux-headers-2.6.27-14 linux-headers-2.6.27-15 linux-headers-2.6.27-16
  linux-headers-2.6.27-14-generic ocaml-base-nox
  linux-headers-2.6.27-15-generic libgsm1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  clamav clamav-base clamav-freshclam libclamav6
Suggested packages:
  clamav-docs libclamunrar6
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam clamtk libclamav6
0 upgraded, 5 newly installed, 0 to remove and 45 not upgraded.
Need to get 25.3MB of archives.
After this operation, 27.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libclamav6 clamav-base clamav-freshclam clamav clamtk
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libclamav6 0.95.3+dfsg-1ubuntu0.09.04~intrepid3
  404 Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe clamtk 3.11-1
  404 Not Found [IP: 91.189.92.170 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libclamav6 0.95.3+dfsg-1ubuntu0.09.04~intrepid3
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main clamav-base 0.95.3+dfsg-1ubuntu0.09.04~intrepid3
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04~intrepid3
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main clamav 0.95.3+dfsg-1ubuntu0.09.04~intrepid3
  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_all.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.95.3+dfsg-1ubuntu0.09.04~intrepid3_amd64.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/clamtk/clamtk_3.11-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/clamtk/clamtk_3.11-1_all.deb)  404 Not Found [IP: 91.189.92.170 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


So what gives? Why can I not install clamtk?

My current Ubuntu version is 8.10.

Thanks in advance to anyone who replies and tries to help.

-Jam Man

:guitar:

---

### Post by oldos2er on 2011-01-28
8.10 is no longer supported. You could try the old releases repositories: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

### Post by tgm4883 on 2011-01-28
You can't install it because it can't find the address.

```
404 Not Found [IP: 91.189.88.30 80]
```

Can you ping it? What happens if you do an apt-get update?

---

### Post by Jammanuser on 2011-02-08
> **tgm4883 said:**
> You can't install it because it can't find the address.

```
404 Not Found [IP: 91.189.88.30 80]
```

Can you ping it? What happens if you do an apt-get update?
I pinged it, and the results are in the attached screenshot.

As for an apt-get update, doesn't that command try to update everything?
I didn't want to run it, because I have 42 available updates in the Update Manger, and most of them I don't particularly want or feel like I need to install. And I'm still planning to go through them again one of these days, and install just the ones I may need.

Thanks.

---

### Post by Jammanuser on 2011-02-08
> **oldos2er said:**
> 8.10 is no longer supported. You could try the old releases repositories: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)
How about the latest version of Ubuntu? Will clamtk install and work in that?

I have a 9.10 version of Ubuntu installed in a multiboot on the same computer as 8.10, and I'm planning to update it to the latest version of Ubuntu just as soon as I [get my wireless internet working in it]("http://ubuntuforums.org/showthread.php?t=1682340"). :)

Thanks for the reply, btw.

---

### Post by holycow131415 on 2011-02-08
If you are going to update, you might as well update to the LST (10.04) because 9.10 wont be supported for too much longer. And who knows, maybe your wireless will work out of the box.

---

### Post by tgm4883 on 2011-02-08
> **Jammanuser said:**
> I pinged it, and the results are in the attached screenshot.

As for an apt-get update, doesn't that command try to update everything?
I didn't want to run it, because I have 42 available updates in the Update Manger, and most of them I don't particularly want or feel like I need to install. And I'm still planning to go through them again one of these days, and install just the ones I may need.

Thanks.

Nope, apt-get update basically just grabs the list of available packages that can be updated.

---

### Post by Jammanuser on 2011-02-12
> **holycow131415 said:**
> If you are going to update, you might as well update to the LST (10.04) because 9.10 wont be supported for too much longer. And who knows, maybe your wireless will work out of the box.
The thing is, I wanted to do the update from inside Ubuntu 9.10, which I can't do if I can't get my wireless to work first.
That's why I was hoping someone could point me to a driver I need to install to get the wireless working on a Dell Studio 1535. I already did some Googling, but was unable to find anything yet, though I will continue to look.

---

