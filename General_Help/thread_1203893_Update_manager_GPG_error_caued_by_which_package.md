---
title: "Update manager GPG error caued by which package?"
date: 2009-07-03
forum: General Help
---

### Post by Coder68 on 2009-07-03
When I run the update manager, I get this error.  If I click by it, everything seems OK and I can get updates.  I understand PKI and the error messages its self... but how do I know what "program" is causing this?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

Coder68

---

### Post by synapsys on 2009-07-03
Google is your friend.

[http://gentoo-blog.de/ubuntu/ubuntu-gpg-error-httpppalaunchpadnet-intrepid-release/](http://gentoo-blog.de/ubuntu/ubuntu-gpg-error-httpppalaunchpadnet-intrepid-release/)

---

### Post by hansdown on 2009-07-04
Hi Coder68.

Read through this thread, and see if it may point to something.

Sorry to be cryptic, but a search turns up a lot of different things.

---

### Post by Coder68 on 2009-07-04
> **synapsys said:**
> Google is your friend.

[http://gentoo-blog.de/ubuntu/ubuntu-gpg-error-httpppalaunchpadnet-intrepid-release/](http://gentoo-blog.de/ubuntu/ubuntu-gpg-error-httpppalaunchpadnet-intrepid-release/)


synapsys, 
 
I did find the fix by using the exact error text and google.

My question was how to know what package was causing this, not how to fix it.  I wanted to learn  how to tell what package was causing the issue so I could diagnose the issue myself.  And in the process, hope to learn a littel about troubleshooting Linux.


Thanks though.

hansdown, what thread?

C68

---

### Post by synapsys on 2009-07-04
How many ppa's do you have? A gpg key is used to verify a repository or archive... not a specific package.

Adding the ppa as a repository without adding gpg key to your keyring could have caused this.....

---

### Post by Coder68 on 2009-07-06
I am running the default install of Ubuntu 8.10 that Dell put on my 15n.  I did add MPlayer in an attempt to get .asf files to play.

Thanks for your help,

C68

---

### Post by raymondh on 2009-07-06
you might also want to add the public key.  The format is (in terminal), one at a time:

```
gpg --keyserver subkeys.pgp.net --recv 00000000000000000
gpg --export --armor 0000000000000000 | sudo apt-key add -
sudo apt-get update
```

Changing the 0000000000000's with the pubkey listed in the error.

Happy Ubuntu-ing.

---

### Post by fooman on 2009-07-06
open a terminal and type or copy/paste the following command into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 58B3AFA9
```that should fetch the missing GPG key and the warning will go away.

to break it down....this command : "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com" + the last 8 characters of the missing key (in this case "58B3AFA9") will fetch it for you.

hope that helps.

---

### Post by forger on 2009-07-06
> **fooman said:**
> open a terminal and type or copy/paste the following command into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 58B3AFA9
```that should fetch the missing GPG key and the warning will go away.

to break it down....this command : "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com" + the last 8 characters of the missing key (in this case "58B3AFA9") will fetch it for you.

hope that helps.

Correct, but the original key mentioned in the error message works as well, no need to get the last 8 characters only ;)

---

