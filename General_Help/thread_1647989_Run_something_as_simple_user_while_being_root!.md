---
title: "Run something as simple user while being root!?"
date: 2010-12-18
forum: General Help
---

### Post by hakermania on 2010-12-18
Yes! I want to do this! Is it possible?

---

### Post by TeoBigusGeekus on 2010-12-18
Try
```
su yourusername && command
```

Greetings patrioti!

---

### Post by hakermania on 2010-12-18
So If I'm root and I run
```

su alex && rm -rf /

```
it will output a message "permission denied" ?

---

### Post by mcduck on 2010-12-18
you can use "sudo" (unlike people often like to say, it's not "Super User DO", but actually "Substitute User DO")

sudo -u *username* *somecommand*

---

### Post by mcduck on 2010-12-18
> **hakermania said:**
> So If I'm root and I run
```

su alex && rm -rf /

```
it will output a message "permission denied" ?

Actually, no. Don't do that...

It would open a terminal session as user "alex", and *once that session is closed* run the rm command. So you'd be able to run some commands as "alex" in between, but in the end the rm would execute as root.

edit:
If you want to do it with su instead of sudo, you can't use the &&. Instead you'd need to run the rm command once the terminal session for alex is opened.
```

root@localhost:/# su alex
alex@localhost:/$ rm somefile
alex@localhost:/$ exit
root@localhost:/#

```

---

### Post by hakermania on 2010-12-18
I'm missing something. Why does it let me to write at / ??
```
root@MaD-pc:/home/alex# sudo -u **alex** echo "1" > /HAHA
root@MaD-pc:/home/alex# l /
bin/    etc/         initrd.img.old@  mnt/   sbin/     tmp/      vmlinuz.old@
boot/  ** HAHA **        lib/             opt/   selinux/  usr/
cdrom/  home/        lost+found/      proc/  srv/      var/
dev/    initrd.img@  media/           root/  sys/      vmlinuz@
root@MaD-pc:/home/alex# 
```

---

### Post by mcduck on 2010-12-18
Check the contents of the file. It's writing the output of the sudo command to that file, not the output of the echo command.

Output redirection with sudo is a bit more tricky. You pretty much need to use the "tee" command to do it:

```
echo "1" | sudo -u alex tee /HAHA > /dev/null
```

edit:
[http://en.wikipedia.org/wiki/Tee_%28command%29]("http://en.wikipedia.org/wiki/Tee_%28command%29")

---

### Post by hakermania on 2010-12-18
thank you

---

