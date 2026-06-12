---
title: "Samba to Windows / Force New User Password"
date: 2012-03-23
forum: General Help
---

### Post by HornedBeast on 2012-03-23
Hello,

I have Samba currently installed on my Ubuntu server and have the usernames and passwords synching nicely. If I change the Unix password for a user, its changed in Samba immediately - lovely. So, via webmin, I click on "Force New Password on Next Login" assuming then, that when a user logs in to a Samba Share via Windows it would ask you for a new password before continuing. It does do this (it asks), but I can never actually change it and I get warnings in my logfiles about it. However, if that user logs in via SSH or or that server itself, they get asked to change the password and all is well. So I think it's something to do with Windows communicating the password, or the fact that the password is not set so the account isn't active!? Hopefully you know better than I!

My Samba configuration is posted below, along with snippets of the logs from Samba. Maybe someone can guide me in the right direction on how to add or change user passwords and force them to be changed on next login.


Samba Configuration:
```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	lanman auth = Yes
	load printers = no
	obey pam restrictions = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	client plaintext auth = Yes
	dns proxy = no
	netbios name = Server01
	writeable = yes
	server string = OurServer
	unix password sync = yes
	workgroup = OurWorkgroup
	os level = 255
	client lanman auth = Yes
	syslog = 0
	security = user
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes
	domain logons = yes

[Finance]
	valid users = @finance
	path = /home/public/Finance

[Holding]
	path = /home/public/Holding

[Procedures]
	path = /home/public/Procedures

```

Log File
```

[2012/03/23 11:11:30.398694,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: andrewb
[2012/03/23 11:11:30.398873,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User andrewb!
[2012/03/23 11:11:30.408225,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: andrewb
[2012/03/23 11:11:30.408394,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User andrewb!
[2012/03/23 11:11:32.597417,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: andrewb
[2012/03/23 11:11:32.597613,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User andrewb!

```

---

