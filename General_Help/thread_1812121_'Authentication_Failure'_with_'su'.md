---
title: "'Authentication Failure' with 'su'"
date: 2011-07-25
forum: General Help
---

### Post by airspoon on 2011-07-25
For some reason, the su command isn't working. Well, it seems to be working but for some reason I keep getting:
```
su: Authentication failure
```

I was initially trying to edit my php.ini file to include the progressupload module with the following command:
```
echo -e "extension=uploadprogress.so" > /etc/php5/apache2/conf.d/uploadprogress.ini
```

When entering that into my term, is says:
```
bash: /etc/php5/apache2/conf.d/uploadprogress.ini: Permission denied
```

So when I did the same command with "sudo" in front, it kicks back the same 'permission denied'. So, I try to do the 'su' command, which is what is bringing me to the 'Authentication failure' mentioned up top.

Does anyone know what's going on and how I can fix it? I'm using Ubuntu 11.04.

Any and all help would be greatly appreciated.

---

### Post by Kira_Belka on 2011-07-25
> **airspoon said:**
> For some reason, the su command isn't working. Well, it seems to be working but for some reason I keep getting:
```
su: Authentication failure
```

I was initially trying to edit my php.ini file to include the progressupload module with the following command:
```
echo -e "extension=uploadprogress.so" > /etc/php5/apache2/conf.d/uploadprogress.ini
```

When entering that into my term, is says:
```
bash: /etc/php5/apache2/conf.d/uploadprogress.ini: Permission denied
```

So when I did the same command with "sudo" in front, it kicks back the same 'permission denied'. So, I try to do the 'su' command, which is what is bringing me to the 'Authentication failure' mentioned up top.

Does anyone know what's going on and how I can fix it? I'm using Ubuntu 11.04.

Any and all help would be greatly appreciated.

probably root in your system has parameter "nologin"

[http://www.thegeekstuff.com/2009/09/ubuntu-tips-how-to-login-using-su-command-su-gives-authentication-failure-error-message/](http://www.thegeekstuff.com/2009/09/ubuntu-tips-how-to-login-using-su-command-su-gives-authentication-failure-error-message/)

---

### Post by bodhi.zazen on 2011-07-25
Ubuntu uses sudo, but sudo does not allow redirection of output like that.

Use sudo -i and run the command as root or:

```
sudo bash -c "echo -e "extension=uploadprogress.so" > /etc/php5/apache2/conf.d/uploadprogress.ini"
```

---

### Post by airspoon on 2011-07-25
Thanks, I wound up creating the progressupload.ini file with nano, which allowed me to achieve my original goal, though I was unaware that I couldn't use the 'su' command with Ubuntu. I thought I remembered using 'su' (just after I installed Ubuntu) without a problem.

---

### Post by bodhi.zazen on 2011-07-26
You can use su, but the root account is locked.

---

