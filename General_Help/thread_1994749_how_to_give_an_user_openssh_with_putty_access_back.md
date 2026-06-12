---
title: "how to give an user openssh with putty access back?"
date: 2012-06-03
forum: General Help
---

### Post by Gabberhead on 2012-06-03
i removed from an user with 
sudo usermod -s /bin/false USERNAME

the openssh login over putty. how can i give that user the login back? i deleted the user and add it again but no success. thanx for your answers in advance ;)

---

### Post by lisati on 2012-06-03
*Support request moved to **General Help**.*

Please read [this thread]("http://ubuntuforums.org/showthread.php?t=677396") before posting in [Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")

---

### Post by codemaniac on 2012-06-03
> **Gabberhead said:**
> i removed from an user with 
sudo usermod -s /bin/false USERNAME

the openssh login over putty. how can i give that user the login back? i deleted the user and add it again but no success. thanx for your answers in advance ;)

Have you tried adding a entry in the server side /etc/ssh/sshd_config file to allow user USERNAME .
Try adding an entry in the above mentioned file .
```
AllowUsers USERNAME
```

Please note that beofre making any changes to the above mentioned file you should take a backup of the original file .

<edit>Just noticed that the above user has no shell access , you can try modifying the mentioned user and give him a shell
```
sudo usermod -s /bin/bash USERNAME
```
</edit>

---

### Post by Gabberhead on 2012-06-03
i tried it but it doesnt work. its the same i try to login type username and password and then nothing happend. no error nothing. after a time the putty window closes. sftp over ssh via flashfxp works with that user. and also the root login via putty and flashfyp also. but no putty login for my user.

with the usermod i get:

root@TerrorCorp:~# sudo usermod -s /bin/bash gabberhead
usermod: no changes

---

### Post by codemaniac on 2012-06-03
> **Gabberhead said:**
> i tried it but it doesnt work. its the same i try to login type username and password and then nothing happend. no error nothing. after a time the putty window closes. sftp over ssh via flashfxp works with that user. and also the root login via putty and flashfyp also. but no putty login for my user.

with the usermod i get:

root@TerrorCorp:~# sudo usermod -s /bin/bash gabberhead
usermod: no changes

Have you tried to log in after giving the user with a shell (/bin/bash) with usermod .

---

### Post by Gabberhead on 2012-06-03
yes.

i have tried also to add a new user and with the new user i have shell access.

---

### Post by codemaniac on 2012-06-03
i am not sure but have you by any chance modified your firewall, as a result ssh connections are getting dropped ?

---

### Post by Gabberhead on 2012-06-03
no i didnt modify the firewall or anything else. the only thing i did was tis (is in german) and after that i didn't have putty access for the user before that i worked:

**openssh konfigurieren**

 Zu allererst müssen wir **openssh** mitteilen, dass es den **SFTP Zugang** für Benutzer der Gruppe “**sftp**” anders behandeln soll, als den Zugang anderer User. Hierzu nehmen wir in der Datei */etc/ssh/sshd_config* 2 Einstellungen vor:
  [COLOR=#666666]*#Subsystem sftp /usr/lib/openssh/sftp-server*[/COLOR] Subsystem sftp internal-sftp   Match Group sftp         ChrootDirectory [COLOR=#000000]**%**[/COLOR]h         ForceCommand internal-sftp         AllowTcpForwarding no

  Die erste Konfigurationsanweisung ändert das **SFTP**-Subsystem auf den internen **SFTP**-Server der für das **Chroot**ing besser funktioniert. Hierbei entfällt auch das Installieren bestimmter Bibliotheken im **Chroot**-Verzeichnis.
 Die zweite Anweisung greift jedes mal wenn sich ein Benutzer der Gruppe **sftp**  authentifiziert. Er wird in sein Home-Directory (%h) eingesperrt und es  wird nochmal explizit der internal-sftp geforced. TCP-Forwarding wollen  wir auch deaktiviert wissen.
 **Usereinstellungen für den Chroot-SFTP-Zugang**

 Um das ganze nun zu testen legen wir den User “sftptest” an. Es soll  sein Home-Dir automatisch angelegt werden (-m), er soll keinen  Shell-Zugang bekommen (-s /bin/false) und er soll der Gruppe sftp  angehören (-G sftp):
  addgroup sftp useradd [COLOR=#660033]-m[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#c20cb9]**false**[/COLOR] [COLOR=#660033]-G[/COLOR] sftp sftptest

  Ein Passwort sollte der User sftptest auch bekommen:
  [COLOR=#c20cb9]**passwd**[/COLOR] sftptest

  Es folgt ein Prompt bei dem ein Passwort angegeben werden muss. Anschließend muss das Passwort nochmal bestätigt werden.
 Hast Du bereits einen User angelegt und möchtest diesem sftp-Zugang gewähren führst Du folgendes aus:
  usermod [COLOR=#660033]-G[/COLOR] sftp sftptest usermod [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#c20cb9]**false**[/COLOR] sftptest

  **Das Home-Dir**

 Hier müssen wir noch eine Änderung durchführen, die untypisch für das  Home-Dir ist. Wir müssen dem root-User den Besitz über das Home-Dir  übertragen, andernfalls wird ein Login nicht möglich sein:
  [COLOR=#c20cb9]**chown**[/COLOR] root:root [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]sftptest[COLOR=#000000]**/**[/COLOR] [COLOR=#c20cb9]**chmod**[/COLOR] 0755 [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]sftptest[COLOR=#000000]**/**[/COLOR]

  Damit der User Dateien samt Ordnern hochladen kann, müssen wir ihm noch ein Verzeichnis anlegen das ihm gehört.
  [COLOR=#c20cb9]**mkdir**[/COLOR] [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]sftptest[COLOR=#000000]**/**[/COLOR]upload [COLOR=#c20cb9]**chown**[/COLOR] sftptest:sftptest [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]sftptest[COLOR=#000000]**/**[/COLOR]upload

---

### Post by Gabberhead on 2012-06-03
but with this i couldnt login with flashfxp. after that i deleted the user. and add it back and tried another solution. with that solution i managed to get sftp access but the shell access sill dont work:

It is possible that ssh is not installed, so:
 $ sudo apt-get install ssh We need to configure the sftp subsystem to use the internal sftp module. Open
 /etc/ssh/sshd_config in a text editor (you will probably have to use “sudo”), and find the  line that starts with “Subsystem sftp”. Comment out (or delete) this  line, and replace it with:
 Subsystem sftp internal-sftp Save and exit your editor.
 _(2) User Setup_
 This section should be repeated for each user to whom you grant sftp-only access.
 Because sftp (as included with openssh) wraps around ssh, your users  are going to need system accounts. Let’s prepare a user named “johndoe”  (replace “johndoe” with whatever new user account you wish). The user  “johndoe” should, in this case, only be able to log in using sftp (as  opposed to ssh) once we’re done.
 $ sudo mkdir /home/johndoe $ sudo useradd johndoe We’ll have to set their home directory permissions appropriately.  It’s important that root owns this and that its group ID is identical to  the username, and that the permissions are set so that only root can  write:
 $ sudo chown root:johndoe /home/johndoe $ sudo chmod 755 /home/johndoe Force the normal login directory just in case:
 $ sudo usermod -d /home/johndoe johndoe Now give him a password:
 $ sudo passwd johndoe Set the new user a dummy shell (so they don’t have real shell access).
 $ sudo usermod -s /bin/false johndoe Now we need to indicate that this particular user must be jailed into  their home directory. Once again, open /etc/ssh/sshd_config in a text  editor, and add the following at the end of the file:
 Match User johndoe       ChrootDirectory /home/johndoe       ForceCommand internal-sftp Now, user johndoe should have read access to his home directory. Let’s give him a place to upload stuff:
 $ sudo mkdir /home/johndoe/upload $ sudo chown johndoe:johndoe /home/johndoe/upload $ sudo chmod 755 /home/johndoe/upload Done! Restart the ssh daemon (run this any time you want changes to become effective):
 sudo /etc/init.d/ssh restart

---

### Post by Gabberhead on 2012-06-03
i tried something more. now i get if i try to login with the user and a wrong password i get access denied. when i type in the right password nothing happend. no error nothing. putty window doesn't close.

here is the log. maybe this helps:

Jun  4 02:52:52 TerrorCorp sshd[699]: Server listening on 0.0.0.0 port 11225.
Jun  4 02:52:52 TerrorCorp sshd[699]: Server listening on :: port 11225.
Jun  4 02:53:16 TerrorCorp sshd[1041]: pam_sm_authenticate: Called
Jun  4 02:53:16 TerrorCorp sshd[1041]: pam_sm_authenticate: username = [root]
Jun  4 02:53:16 TerrorCorp sshd[1041]: Accepted password for root from 192.168.0.2 port 59503 ssh2
Jun  4 02:53:17 TerrorCorp sshd[1041]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jun  4 02:53:21 TerrorCorp sshd[1041]: pam_unix(sshd:session): session closed for user root
Jun  4 02:53:34 TerrorCorp sshd[1267]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=terrorcorp.fritz.box  user=gabberhead
Jun  4 02:53:36 TerrorCorp sshd[1267]: Failed password for gabberhead from 192.168.0.2 port 59504 ssh2
Jun  4 02:53:44 TerrorCorp sshd[1267]: pam_sm_authenticate: Called
Jun  4 02:53:44 TerrorCorp sshd[1267]: pam_sm_authenticate: username = [gabberhead]
Jun  4 02:53:44 TerrorCorp sshd[1267]: Accepted password for gabberhead from 192.168.0.2 port 59504 ssh2
Jun  4 02:53:44 TerrorCorp sshd[1267]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 02:54:06 TerrorCorp sshd[1645]: pam_sm_authenticate: Called
Jun  4 02:54:06 TerrorCorp sshd[1645]: pam_sm_authenticate: username = [gabberhead]
Jun  4 02:54:06 TerrorCorp sshd[1645]: Accepted password for gabberhead from 192.168.0.2 port 59505 ssh2
Jun  4 02:54:06 TerrorCorp sshd[1645]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 02:54:06 TerrorCorp sshd[1710]: subsystem request for sftp
Jun  4 02:54:23 TerrorCorp sshd[1267]: pam_unix(sshd:session): session closed for user gabberhead
Jun  4 02:54:34 TerrorCorp sshd[1890]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=terrorcorp.fritz.box  user=gabberhead
Jun  4 02:54:36 TerrorCorp sshd[1890]: Failed password for gabberhead from 192.168.0.2 port 59506 ssh2
Jun  4 02:54:48 TerrorCorp sshd[2035]: pam_sm_authenticate: Called
Jun  4 02:54:48 TerrorCorp sshd[2035]: pam_sm_authenticate: username = [root]
Jun  4 02:54:48 TerrorCorp sshd[2035]: Accepted password for root from 192.168.0.2 port 59507 ssh2
Jun  4 02:54:48 TerrorCorp sshd[2035]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jun  4 02:55:27 TerrorCorp passwd[2482]: eCryptfs PAM passphrase change module retrieved a NULL passphrase; nothing to do
Jun  4 02:55:35 TerrorCorp passwd[2482]: pam_unix(passwd:chauthtok): password changed for gabberhead
Jun  4 02:55:35 TerrorCorp passwd[2482]: Error attempting to parse .ecryptfsrc file; rc = [-13]
Jun  4 02:55:35 TerrorCorp passwd[2482]: Passphrase file wrapped
Jun  4 02:55:35 TerrorCorp passwd[2482]: eCryptfs PAM passphrase change module retrieved at least one NULL passphrase; nothing to do
Jun  4 02:55:44 TerrorCorp sshd[1890]: pam_sm_authenticate: Called
Jun  4 02:55:44 TerrorCorp sshd[1890]: pam_sm_authenticate: username = [gabberhead]
Jun  4 02:55:44 TerrorCorp sshd[1890]: Accepted password for gabberhead from 192.168.0.2 port 59506 ssh2
Jun  4 02:55:44 TerrorCorp sshd[1890]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 02:55:54 TerrorCorp sshd[2035]: pam_unix(sshd:session): session closed for user root
Jun  4 02:56:03 TerrorCorp sshd[2806]: pam_sm_authenticate: Called
Jun  4 02:56:03 TerrorCorp sshd[2806]: pam_sm_authenticate: username = [root]
Jun  4 02:56:03 TerrorCorp sshd[2806]: Accepted password for root from 192.168.0.2 port 59570 ssh2
Jun  4 02:56:03 TerrorCorp sshd[2806]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jun  4 02:56:26 TerrorCorp sshd[3086]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=terrorcorp.fritz.box  user=gabberhead
Jun  4 02:56:28 TerrorCorp sshd[3086]: Failed password for gabberhead from 192.168.0.2 port 59571 ssh2
Jun  4 02:56:42 TerrorCorp sshd[1645]: pam_unix(sshd:session): session closed for user gabberhead
Jun  4 02:56:46 TerrorCorp sshd[3300]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=terrorcorp.fritz.box  user=gabberhead
Jun  4 02:56:48 TerrorCorp sshd[3300]: Failed password for gabberhead from 192.168.0.2 port 59572 ssh2
Jun  4 02:56:50 TerrorCorp sshd[3300]: Failed password for gabberhead from 192.168.0.2 port 59572 ssh2
Jun  4 02:56:50 TerrorCorp sshd[3300]: PAM 1 more authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=terrorcorp.fritz.box  user=gabberhead
Jun  4 02:57:06 TerrorCorp sshd[3468]: pam_sm_authenticate: Called
Jun  4 02:57:06 TerrorCorp sshd[3468]: pam_sm_authenticate: username = [gabberhead]
Jun  4 02:57:06 TerrorCorp sshd[3468]: Accepted password for gabberhead from 192.168.0.2 port 59577 ssh2
Jun  4 02:57:06 TerrorCorp sshd[3468]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 02:57:06 TerrorCorp sshd[3533]: subsystem request for sftp
Jun  4 02:57:09 TerrorCorp sshd[3468]: pam_unix(sshd:session): session closed for user gabberhead
Jun  4 02:57:13 TerrorCorp sshd[3594]: pam_sm_authenticate: Called
Jun  4 02:57:13 TerrorCorp sshd[3594]: pam_sm_authenticate: username = [root]
Jun  4 02:57:13 TerrorCorp sshd[3594]: Accepted password for root from 192.168.0.2 port 59578 ssh2
Jun  4 02:57:13 TerrorCorp sshd[3594]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jun  4 02:57:13 TerrorCorp sshd[3594]: subsystem request for sftp
Jun  4 02:58:34 TerrorCorp sshd[1890]: pam_unix(sshd:session): session closed for user gabberhead
Jun  4 02:58:44 TerrorCorp sshd[4374]: pam_sm_authenticate: Called
Jun  4 02:58:44 TerrorCorp sshd[4374]: pam_sm_authenticate: username = [gabberhead]
Jun  4 02:58:44 TerrorCorp sshd[4374]: Accepted password for gabberhead from 192.168.0.2 port 59585 ssh2
Jun  4 02:58:44 TerrorCorp sshd[4374]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 03:00:01 TerrorCorp CRON[5137]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  4 03:00:01 TerrorCorp CRON[5137]: pam_unix(cron:session): session closed for user root
Jun  4 03:06:45 TerrorCorp sshd[4374]: pam_unix(sshd:session): session closed for user gabberhead
Jun  4 03:06:47 TerrorCorp sshd[2806]: pam_unix(sshd:session): session closed for user root
Jun  4 03:07:02 TerrorCorp sshd[8628]: pam_sm_authenticate: Called
Jun  4 03:07:02 TerrorCorp sshd[8628]: pam_sm_authenticate: username = [gabberhead]
Jun  4 03:07:02 TerrorCorp sshd[8628]: Accepted password for gabberhead from 192.168.0.2 port 59684 ssh2
Jun  4 03:07:02 TerrorCorp sshd[8628]: pam_unix(sshd:session): session opened for user gabberhead by (uid=0)
Jun  4 03:13:11 TerrorCorp sshd[8628]: pam_unix(sshd:session): session closed for user gabberhead

---

