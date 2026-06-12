---
title: "Cannot get key for 07DC563D1F41B907 (wanted to watch dvd)"
date: 2012-06-25
forum: General Help
---

### Post by ritchierope on 2012-06-25
I am having a problem with playing a dvd disc (legally bought)... 

I've googled the problem, it seems to be that I have to install a libdvdcss package which I unfortunately cannot, because I have to download it from this repository: [http://www.deb-multimedia.org](http://www.deb-multimedia.org) and the old game starts: 

W: GPG error: [http://www.deb-multimedia.org](http://www.deb-multimedia.org) squeeze Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

I've tried these:
[http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error)

[http://www.hangelot.eu/?p=70&lang=en](http://www.hangelot.eu/?p=70&lang=en)

[http://www.linuxquestions.org/questions/debian-26/w-gpg-error-http-www-debian-multimedia-org-lenny-release-834484/](http://www.linuxquestions.org/questions/debian-26/w-gpg-error-http-www-debian-multimedia-org-lenny-release-834484/) (here due to some hash error, the package cannot be installed, even as untrusted)

I've been googling it for the past 3 hours, but I am not getting further... after exporting the key:

gpg --keyring /usr/share/keyrings/debian-keyring.gpg -a --export 07DC563D1F41B907 (or gpg --keyserver keyserver.ubuntu.com --recv-key and export)

I try using apt-key add - and then in the next line the cursor is blinking and nothing happens, even after 10 minutes. What could be the problem.

EDIT: I've also tried copying the exported key and savind it with gedit and then importing it the GUI way in Software Sources, there I get an error saying that the selected file may not be a GPG file or it might be corrupt...

---

### Post by howefield on 2012-06-25
You could download the deb package from [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Select the one appropriate to your Ubuntu version and double click to install once downloaded.

---

### Post by ritchierope on 2012-06-25
Thank you very much, it solved my problem, DVD is played smoothly. :)

Any idea how to solve these package authentication issues? Thank goodness I rarely confront such issues lately, but when I do, it drives me mad that nothing works to solve it.

---

### Post by howefield on 2012-06-25
You could try these commands for that particular key, or any other for that matter by substituting the numbers for whichever key you need.

It is a long time since I had to worry about getting keys.

```
gpg --keyserver pgpkeys.mit.edu --recv-key  07DC563D1F41B907
```     
```
gpg -a --export 07DC563D1F41B907 | sudo apt-key add -
```

---

### Post by ritchierope on 2012-06-25
Yes, I have tried it in any way possible, but I get stuck after adding the key, I only get the the cursor flashing and nothing happens. (after executing apt-key add -

---

### Post by howefield on 2012-06-25
Do you need that repository for anything else, if not take it out.

---

### Post by ritchierope on 2012-06-25
Yes, that one I've taken out already. I just run into this problem time-to-time and I always spend half a day to figuring something out...

Anyway, thank you very much for helping!

---

### Post by charless1 on 2012-06-25
@ritchierope
do you have any suggestion for me since the suggested solutions didn't work with me!

thanks

---

### Post by ritchierope on 2012-06-26
Unfortunately @howefield could not help with the key either, I have no idea what to do with the authentication problem. My original problem (that is not to be able to play dvds got solved by downloading the package manually) got solved and thus I deleted the repository.

---

