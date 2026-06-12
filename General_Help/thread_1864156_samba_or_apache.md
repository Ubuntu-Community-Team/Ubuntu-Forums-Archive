---
title: "samba or apache?"
date: 2011-10-18
forum: General Help
---

### Post by pgp_protector on 2011-10-18
I've got a Samba & Apache System running on the same box (both working)

The web site (from root) is /var/www/clients/client1/web4/web

I want a php script from that service to access a file located at
/home/shares/allusers/Videocapture

smb.conf for allusers
```

[allusers]
	guest account = 
	writeable = yes
	delete readonly = yes
	path = /home/shares/allusers
	force group = users
	comment = All Users
	public = yes
	create mode = 0660
	directory mode = 0771
```

but if my php script tries to access the file I get the error.
imagecreatefromwbmp(\\\\SERVER\\allusers\\VideoCapture\\Up.bmp): failed to open stream: No such file or directory in /var/www/clients/client1/web5/web/upimage.php on line 6

---

### Post by pgp_protector on 2011-10-18
Added 

    Alias /videoimages "/home/shares/allusers/VideoCapture"
    <Directory /home/shares/allusers/VideoCapture>
        Allow from all
    </Directory>
To the Directives file, now it tries to get the image, but I'm getting a 403 Error.

(13)Permission denied: file permissions deny server access: /home/shares/allusers/VideoCapture/Down.bmp

---

### Post by pgp_protector on 2011-10-18
Solved: Permissions error on the samba file (wasn't allowing OTHER to read)

---

