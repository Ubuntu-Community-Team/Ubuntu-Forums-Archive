---
title: "duplicity:how to use email as userid in ftp url?"
date: 2011-03-30
forum: General Help
---

### Post by RussellEngland on 2011-03-30
I'm trying to set up a backup routine using the instructions at
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I tried duplicity but I it wouldn't connect
```

PASSPHRASE='xxx' FTP_PASSWORD='password' duplicity /etc ftp://russ@ftpsite.com/etc

```so tried

```

ncftpls -d russ.log -p password -u russ ftp://ftpsite.com

```wouldn't connect either, then realised the user id should be an email address

```

ncftpls -d russ.log -p password -u russ@ftpsite.com ftp://ftpsite.com

```this works! yey!

but how do I use the email address in the url?

```

PASSPHRASE='xxx' FTP_PASSWORD='password' duplicity /etc ftp://russ@ftpsite.com@ftpsite.com/etc

```just throws an error

---

### Post by RussellEngland on 2011-04-12
bump

---

### Post by SeijiSensei on 2011-04-12
Maybe single or double quotes will work like  ftp://'russ@ftpsite.com'@ftpsite.com/

On the other hand, a quick browsing of the [RFC that defines URL syntax]("http://www.ietf.org/rfc/rfc1738.txt") doesn't show much support for a user@site type of username.

---

