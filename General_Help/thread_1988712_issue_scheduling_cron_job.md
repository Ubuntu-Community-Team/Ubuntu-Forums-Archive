---
title: "issue scheduling cron job"
date: 2012-05-28
forum: General Help
---

### Post by rganesh tivoli on 2012-05-28
Hello Everyone,

I have written the following shell script and trying to schedule the same under cron job.
```

cd /data/logs/apache/
ls -trl | grep access-icecast.log.* | tail -1 | awk '{print $8}' | while read temp; 
do         
      echo "This is before scp" > /tmp/before.txt         
      scp $temp itmuser@192.168.201.138:/home/itmuser/XLMEDIA_Logs/jetedgede         
      echo "This is after scp" > /tmp/after.txt 
done

```This code works perfectly when I run it directly from the command prompt. However when I schedule this script under cron jobs, ***"scp $temp itmuser@192.168.201.138:/home/itmuser/XLMEDIA_Logs/jetedgede***" part of the script does not work.

The following is the entry in the cron jods:
```

0,5,10,15,20,25,30,35,40,45,50,55 * * * * sh /data/scripts/copylog.sh >/dev/null 2>&1

```Can anyone please suggest me what modification is required in the script so that it works when scheduled under cron jobs?


Thank you.

---

### Post by papibe on 2012-05-28
Hi rganesh tivoli.

scp will ask you a either the password or a passphrase. In order to do unattended scp scripts (or any ssh based protocol), I would recommend setting up passwordless authentication through Public-Keys.

Take a look at this [tutorial]("http://principialabs.com/beginning-ssh-on-ubuntu/") to accomplish that.

I hope that points you in the right direction.
Regards.

---

### Post by rganesh tivoli on 2012-05-28
Hi papibe,

Thank you very much for your reply. I have already set-up passwordless authentication through Public-Keys using below commands.
```

ssh-keygen
ssh-copy-id -i ~/.ssh/id_rsa.pub itmuser@192.168.201.138

```

Any help is really appreciated.


Regards.

---

### Post by papibe on 2012-05-28
Test your keys by using ssh from where you are running the script to '192.168.201.138'. If you are able to connect without any password or passphrase, then scp will work that way to.

Regards.

---

### Post by rganesh tivoli on 2012-05-28
Hi papibe,

I am able to SSH the destination system without any password.

Kindly find the attached documents for your reference.

Awaiting your reply.


Thank you.

---

### Post by Azdour on 2012-05-28
Hi,

Could it be that you need to use the full path to scp - /usr/bin/scp?

---

### Post by rganesh tivoli on 2012-05-28
Hi Azdour,

I even tried giving absolute path to scp (/usr/bin/scp), but it not worked.. 


Thank you.

---

### Post by papibe on 2012-05-28
Make sure they have the proper permissions:
```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
```
From your attachment I see that you are running as root. I imagine then that the local keys are under the root (/root) directory? if not, where?

Try then adding explicitly the key to the scp command using an absolute path:
```
scp -i /path/to/id_rsa  ...
```
Tell us how it goes.
Regards.

---

### Post by rganesh tivoli on 2012-05-28
Hi papibe,

The following is logged when ever cron job is executed.
```
ssh: connect to host 21 port 22: Invalid argument
```I will update you once I make the changes as suggested by you when I reach office tomorrow.

Thank you.

---

### Post by rganesh tivoli on 2012-05-29
Hello Everyone,

I thank one and all for helping me out in editing the script as per my requirement. I am able to fulfill my requirement by the script given below.
```

cd /data/log/apache/ 
/usr/bin/stat -c '%Y %n' access.icecast.log.* | /usr/bin/sort -r -k1,1n |
{
    read date filename;
    /usr/bin/scp "$filename" itmuser@192.168.201.138:/home/itmuser/XLMEDIA_Logs/jetedgede;
}

```My requirement is fullfilled..   :guitar:
Regards,
Ravi.

---

