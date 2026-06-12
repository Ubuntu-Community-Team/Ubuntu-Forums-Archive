---
title: "Restart Ubuntu Everyday"
date: 2010-01-09
forum: General Help
---

### Post by TiuTalk on 2010-01-09
Hi there!

I need to **restart** my computer **everyday** at **06:10**.

I tried to create a cronjob with **my user** and nothing happend... Then I tried to create a cronjob with **sudo** user and nothing happend again.

The cronjob:
> 10 6 * * * reboot

Somebody can help me with it? :D

---

### Post by iponeverything on 2010-01-09
```

sudo echo 10 6 * * * reboot >> /etc/crontab

```

---

### Post by TiuTalk on 2010-01-09
> **iponeverything said:**
> ```

sudo echo 10 6 * * * reboot >> /etc/crontab

```

Is there a way that I can check if it worked?

> **gedit /etc/crontab**> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


**[COLOR=Red]10 6[/COLOR]** Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos **[COLOR=Red]reboot[/COLOR]**

---

### Post by iponeverything on 2010-01-09
That command should have just appended the line to /etc/crontab

If you look at /etc/crontab and don't see the line, it didn't work..

---

### Post by HiImTye on 2010-01-09
you can use
```
gnome-session-save --shutdown-dialog
```
also, if it is not working

---

### Post by TiuTalk on 2010-01-09
> **HiImTye said:**
> you can use
```
gnome-session-save --shutdown-dialog
```also, if it is not working
As command of the cronjob?

---

### Post by HiImTye on 2010-01-09
as the command, instead of 'reboot', yes

---

### Post by TiuTalk on 2010-01-09
> **HiImTye said:**
> as the command, instead of 'reboot', yes
This will restart the computer or just shutdown it?

---

### Post by scrooge_74 on 2010-01-09
> **TiuTalk said:**
> Hi there!

I need to **restart** my computer **everyday** at **06:10**.

I tried to create a cronjob with **my user** and nothing happend... Then I tried to create a cronjob with **sudo** user and nothing happend again.

The cronjob:


Somebody can help me with it? :D

I'm courious, why you need to reboot at all or at that specific time? :???:

---

### Post by TiuTalk on 2010-01-09
> **scrooge_74 said:**
> I'm courious, why you need to reboot at all or at that specific time? :???:
Here's the reason:
[http://ubuntuforums.org/showthread.php?p=8592833](http://ubuntuforums.org/showthread.php?p=8592833)

I can't completely terminate the process... so I reboot the computer and problem solved. xD

*dust under the carpet*

:P

---

### Post by TiuTalk on 2010-01-09
> **iponeverything said:**
> That command should have just appended the line to /etc/crontab

If you look at /etc/crontab and don't see the line, it didn't work..

Look the last line of my quote:
> **[COLOR=Red]10 6[/COLOR]** Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos Aladion.sh Área de Trabalho Documentos Downloads examples.desktop Imagens Modelos Música Público servidor Vídeos **[COLOR=Red]reboot[/COLOR]**Seem like the command was inserted on the cronjob file.. But not the right way.

---

### Post by QLee on 2010-01-09
[QUOTE=TiuTalk]Look the last line of my quote:
Seem like the command was inserted on the cronjob file.. But not the right way.[/QUOTE]

Well, the * character in bash is a wild card character that matches every filename in the directory and that looks like what you have.

Try the command this way to have what you want interpreted correctly, echo "10 6 * * * reboot" >> /etc/crontab.

---

### Post by iponeverything on 2010-01-09
my oh my.. 

Yea, remove all that junk starting with 10 and ending with reboot.

just use gedit to add the line. I should have you use quotes when doing the echo..

Make sure that your /etc/crontab ends on a newline..

---

### Post by TiuTalk on 2010-01-09
Yay! I got it:

> 10 6    * * *    root    reboot
at the end of **/etc/crontab**


Thank you guys! :D

---

