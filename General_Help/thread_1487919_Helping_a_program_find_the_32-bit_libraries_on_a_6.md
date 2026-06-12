---
title: "Helping a program find the 32-bit libraries on a 64-bit system"
date: 2010-05-19
forum: General Help
---

### Post by andrewkk on 2010-05-19
A 32-bit program (Cisco AnyConnect VPN Client) appears to be trying to load a library from /usr/lib even though the 32-bit library is installed in /usr/lib32:

[FONT="Courier New"]ak@myo5a:~$ /opt/cisco/vpn/bin/vpnui
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

ak@myo5a:~$ locate libgvfsdbus.so
/usr/lib/gio/modules/libgvfsdbus.so
/usr/lib32/gio/modules/libgvfsdbus.so[/FONT]

Short of editing the program's source, is there anything I can do to make it find the 32-bit library instead?


EDIT: I've attached the output from ldd. Curiously, the offending library isn't even listed. What could that mean?

---

### Post by klemes on 2010-05-19
Try :

```
sudo ldconfig
```

---

### Post by Dougie187 on 2010-05-19
You can't use network-manager-vpnc instead of that Cisco app?

---

### Post by andrewkk on 2010-05-19
Thanks for the suggestions.

The problem still happens after running sudo ldconfig.

My university "does not support" VPN connections made using any other client software, and Network Manager fails to connect with the error message "VPN Connection Failed". I would love to be able to use it instead of the Cisco client, but I don't know where to begin to troubleshoot it.

What do you think about the fact that the library isn't listed by ldd?

---

### Post by casevh on 2010-05-20
See this [thread]("http://ubuntuforums.org/showthread.php?t=1485432") for instructions on getting the AnyConnect client to work on 64-bit 9.10. 

I have never seen your particular error message before. What version of Ubunutu and what version of the client are you using?

casevh

---

### Post by 3Miro on 2010-05-20
Try
```
linux32 your_program
```

I remember couple of years ago, there was only 32-bit Skype and on a 32-bit machine it had to be started with "linux32" command.

---

### Post by andrewkk on 2010-05-20
I'm using Ubuntu 10.04 LTS with Cisco AnyConnect VPN Client 2.4.0202, but I think I should clarify: I'm not looking for support with getting the client to run; aside from the libgvfsdbus.so terminal output, the program is running fine. I just found it peculiar that any program would choose the wrong library when the correct one is present, and thought to investigate it in the interest of furthering my general understanding of 64-bit Linux since I just started using it with this Ubuntu release.

I should also have mentioned earlier that I followed [casevh's instructions]("http://ubuntuforums.org/showpost.php?p=9315106&postcount=2") (packages and symlinks) immediately prior to installation of the client.

Using linux32 doesn't seem to make a difference.

Thanks, all.

---

### Post by Dougie187 on 2010-05-20
The network-manager-vpnc package is the cisco app (i don't know if it's the anyconnect one or not) so thats why I suggested it. It's what I have to use to VPN into my university.

Either way, I'm looking for some more information so, once I find it I can tell you. But this sounds very similar to what happened with libstdc++5. I can't remember what it was needed for, but something needed libstdc++5 (32 bit) and it's only available in older versions of ubuntu, so you have to download it and put it (and the 64 bit version) in specific places. So I'll let you know if I find it.

---

