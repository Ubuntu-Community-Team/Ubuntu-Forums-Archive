---
title: "error with update manager"
date: 2010-04-24
forum: General Help
---

### Post by robthompson on 2010-04-24
#Hi, just did latest update and I get the following error message
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://www.sourceslist.eu/repository/karmic/binary/Packages.gz](http://www.sourceslist.eu/repository/karmic/binary/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Any ideas how to solve this thanks

---

### Post by wojox on 2010-04-24
Go into System > Admin > Software Sources and change your server to a different one.

---

### Post by 2hot6ft2 on 2010-04-24
Welcome to the forum

Sometimes running ```
sudo apt-get update
``` a couple times in a terminal
Applications > Accessories > Terminal
will fix it

---

### Post by robthompson on 2010-04-24
thanks for your reply, I have tried both options but neither seems to have done the trick.

When I try the terminal server option I get the following message

W: Failed to fetch [http://www.sourceslist.eu/repository/karmic/binary/Packages.gz](http://www.sourceslist.eu/repository/karmic/binary/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Is it a big problem or just something I can safely ignore.

Thanks for your help.

---

### Post by wojox on 2010-04-25
Does your network have anything to do with a proxy?

---

### Post by andreasdelpaso on 2010-04-26
Hello,since late last night i get this message when trying to Check for Update @ Update manager...Any suggestions?

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by ubuntu1sttimer on 2010-04-26
Getting about the same thing. Thought I had checking medibuntu.org removed but still get an error that the system can't find the PGP key. 

Understand that the medibuntu.org update system is not always working. 

Must still be a reference to the site in a config file somewhere. Anyone have an idea where I should look?

---

### Post by wojox on 2010-04-26
> **andreasdelpaso said:**
> Hello,since late last night i get this message when trying to Check for Update @ Update manager...Any suggestions?

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Sure, you just need the key:

```
gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783

```

```
gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by robthompson on 2010-04-26
> **wojox said:**
> Does your network have anything to do with a proxy?

No it does not, I have only been using Linux a coupke of months but know a bit about computers.  It looks like the url address of one of the update files is incorrect because of the 404 part of the error message.

But I understand, that there is an upgrade to 'ubuntu in the next few days, so I will just wait for that and hopefully everything will be sorted.

thanks for your help though it is appreciated.  Am really enjoying Linux rather than Windows.

---

