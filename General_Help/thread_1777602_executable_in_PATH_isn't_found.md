---
title: "executable in PATH isn't found"
date: 2011-06-07
forum: General Help
---

### Post by csar1020 on 2011-06-07
Hi,

I was hoping someone may be able to explain the following to me.  I have an executable (ssh) in a directory (/usr/local/krb5/bin) in my PATH as shown below. However when I simply type *ssh* into the command prompt the executable is not found.  When I type in the directory preceding the executable it runs fine.  Why is the executable not found when simply typing in *ssh*. 

>>~$ echo $PATH
/usr/local/krb5/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

>>~$which ssh
/usr/local/krb5/bin/ssh

>>~$ssh -v
bash: /usr/bin/ssh: No such file or directory


>>~$ /usr/local/krb5/bin/ssh -v
OpenSSH_5.6p1b, OpenSSL 1.0.0b 16 Nov 2010
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]

Thanks

---

### Post by noah++ on 2011-06-07
Was it maybe necessary to *[FONT=Fixedsys][SIZE=1][COLOR=black]export [/COLOR][/SIZE][/FONT][FONT=Fixedsys][SIZE=1][COLOR=black]PATH[/COLOR][/SIZE][/FONT]* and you didn't do it?

---

### Post by seawolf167 on 2011-06-08
> **csar1020 said:**
> >>~$ssh -v
bash: /usr/bin/ssh: No such file or directory

>>~$ /usr/local/krb5/bin/ssh -v
OpenSSH_5.6p1b, OpenSSL 1.0.0b 16 Nov 2010
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]

Thanks

Did you move the default ssh binary? Normally this is installed in /usr/bin/ssh not /usr/local/username/bin


> **noah++ said:**
> Was it maybe necessary to *[FONT=Fixedsys][SIZE=1][COLOR=black]export [/COLOR][/SIZE][/FONT][FONT=Fixedsys][SIZE=1][COLOR=black]PATH[/COLOR][/SIZE][/FONT]* and you didn't do it?

Export is only needed if you want to add a binary tree to your $PATH variable

EDIT: after you exported the path did you log-out/log-in or close and reopen your terminals?

---

### Post by csar1020 on 2011-06-08
My problem was fixed by restarting my computer.

I put the new ssh into a directory that was already in the PATH, so I don't think not exporting PATH was an issue.

I did move the default ssh from the /usr/bin.  I was installing a different version of ssh that I wanted to be used by default.  But it was executing the default ssh (in /usr/bin) instead of the new version I install (in /usr/local/krb5/bin) even though the 'which' command said it would execute the new version.  I moved the ssh executables out of the /usr/bin directory to debug the problem and also because I thought it illustrated my problem better.  It looks like you are right seawolf, I just had to restart the terminals.

Thanks for your help

---

### Post by seawolf167 on 2011-06-09
> **csar1020 said:**
> My problem was fixed by restarting my computer.

Just as an FYI, if you make changed like exporting a $PATH variable, or editing your ~/.bashrc file, etc. etc., you'll need to close all currently open terminals and reopen them for the changes to take effect. A logout/login or restart does this, but it takes longer (even though it definitely does work)

Glad it's working!

---

