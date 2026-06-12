---
title: "Freenx configuration problem"
date: 2006-04-27
forum: General Help
---

### Post by 3str on 2006-04-27
I'm using ubuntu5.10. The HOW-TOs I read about freenx installation seems quite simple. But after I "sudo apt-get install freenx", it doesn't work for me. I tried "sudo dpkg-reconfigure freenx", choosing manual setup. Then run nxsetup. I got the following message:

sudo nxsetup --install --setup-nomachine-key
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=startkde"
Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

Warnings occured during config check.
To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is b6:bf:f8:91:0a:45:bd:d2:8d:34:c0:40:d7:7e:ab:55.
Are you sure you want to continue connecting (yes/no)? Fatal error: Could not connect to NX Server.

Please check your ssh setup:

- Make sure "nx" is one of the AllowUsers in sshd_config.
- Make sure your sshd allows public key authentication.
- Make sure your sshd is really running on port 22.
- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
liuyuan-17:25:33:~$Host key verification failed.

The SSH is working. I can use PuTTy to connect to my box. And the 4 requirements about ssh setup listed there has already been followed. What can I do?

---

### Post by Soarer on 2006-05-03
Hi,
THis is a while ago, and you may have found it already but...
there s a thred which soeifies you need to answer 'yes' to the question posed above VERY QUICKLY otherwise it will time out & give you the errors you describe. I only had about 3 seconds to respond, but it (sort of) worked.

---

### Post by 3str on 2006-05-04
Thank you very much. It really works!!!

---

### Post by Soarer on 2006-05-06
Great! I wasn't quick enough first time either :).

---

