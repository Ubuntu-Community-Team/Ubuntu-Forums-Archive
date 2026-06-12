---
title: "weird update manager issue"
date: 2006-02-10
forum: General Help
---

### Post by iconoclasm on 2006-02-10
My update notification list is getting longer and longer... but trying to update results in this sweet error:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu2_all.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2_3.4.3-0ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2_3.4.3-0ubuntu2_i386.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.4.3-0ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.4.3-0ubuntu2_i386.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.2_all.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

I've since tried shutting down any proxies I was running, have checked and double checked my lists file... but for some reason, it's trying to resolve these addresses at well... the wrong place! Can anyone help?

Also on the side -- is it normal to get the "unverified" warning when updating kernel source from the repositories?

Cheers.

---

### Post by Murgle on 2006-02-10
I'm not sure about the unverified thingy but I suggest trying to remove the "ca." from the front of your repos...  There were alot of errors like this right about when Breezy came out, I think it's just that the server is kinda wonky, unless you can download anyother packages.

---

### Post by iconoclasm on 2006-02-10
thanks for the fast reply. 

I've tried removing the ca.

but the problem is that it's resolving the server address to 127.0.0.1:80 ... which is obviously not right. I've removed all proxies, but I think it's something deeper. I'm just not experienced enough with the package manager to fix it on my own. :(

---

### Post by wargames on 2006-02-10
Don't know if this will help. But I had a weird problem with the Update Manager as well. It would always complain about update packages not being verified. But if I used just the terminal and did "sudo apt-get update" and then "sudo apt-get upgrade" it would install all of my security updates, etc. without giving me any verified error problem. I just assumed that Update Manager has a bug in it, so I stick with the terminal and it works just fine.

Hope this helps.

---

### Post by iconoclasm on 2006-02-10
Thanks wargames. I tried, but alas -- still the same error. It's still trying to resolve the repository URL to 127.0.0.1:80  ...  which is not right because that's my machine. The "default localhost" address I guess you could say.

---

### Post by iconoclasm on 2006-02-10
Trying to reload the update list from the update manager results in:

[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

and

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

... all I want is vgagl .. and my system updates. :)

---

### Post by iconoclasm on 2006-02-10
Still no luck. Able to resolve archive.ubuntu.com using ping and host... but synaptic tries to resolve it as 127.0.0.1

This is driving me crazy. There's nothing wrong with my hosts or resolv.conf files. I have all proxies turned off. I just booted up and this starts happening.

I'm at my wits unfortunately and short end. And I think the IRC people are too.

Blah... and I was just sitting down to get cozy developing games for linux.

---

### Post by iconoclasm on 2006-02-10
SOLUTION:

-remove 'anon-proxy' and restart, you should be good to go from there.

IRC is a big help. thanks to _jason who helped me dig around for this solution. Cheers.

---

