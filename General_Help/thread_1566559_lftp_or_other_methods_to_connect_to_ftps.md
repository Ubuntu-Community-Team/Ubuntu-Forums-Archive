---
title: "lftp or other methods to connect to ftps://"
date: 2010-09-02
forum: General Help
---

### Post by Muscovy on 2010-09-02
I recently made a script to automatically download a directory from my webserver using ftps (required by hosting company). It seems policy has changed again or something, because trying to download files gets the following error:

mirror: Access failed: 521 Data connection cannot be opened with this PROT setting.

I can access the files just fine with Filezilla, but not lftp. I didn't change the code, but here it as anyway:

lftp -f ~/the/file/below
> open -u USERNAME,PASSWORD DOMAIN
lcd /local/place/to/put/files
mirror
quit

I tried manually, login works fine, but nothing can be done after that. Help is appreciated, until this works again I've broken a backup system of mine.

---

### Post by scorp123 on 2010-09-02
Are you sure you're really using FTPS with FileZilla and not SFTP?

---

### Post by Muscovy on 2010-09-02
I tried using sftp from the terminal, and it failed. When they said sftp was also usable, I assume it's for those who have purchased ssh access or something.

---

### Post by scorp123 on 2010-09-02
> **Muscovy said:**
> I assume it's for those who have purchased ssh access or something. I'd definitely recommend that, to be honest. FTPS is just a horrible non-standard rig where SSL got glued on top of good ol' unsafe and outdated FTP. SFTP however is a standard sub-protocol of SSH and it just works. So if there is a way you can get SSH access I'd recommend you try that.

---

### Post by Muscovy on 2010-09-02
I'm not too worried about security. None of the files are secret, it's just the fastest way to download all of them (I don't fancy making a wget bot ;)). I looked up the lftp error, and discovered:

"LIST will return '521 data connection cannot be opened with this PROT setting' when a client tries to list the content of a secured folder over a clear data connection."

---

### Post by scorp123 on 2010-09-02
> **Muscovy said:**
>  it's just the fastest way to download all of them (I don't fancy making a wget bot  Never heard of **rsync**? Works tip top.

[B]rsync -av --progress ssh-login@remote-location:/remote/files/* /path/to/local/destination/

[/B]

---

### Post by Muscovy on 2010-09-02
I got this working by adding the following in the instructions file:

> set ftp:ssl-force true
set ftp:ssl-protect-data true

---

