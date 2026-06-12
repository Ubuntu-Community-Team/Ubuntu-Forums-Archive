---
title: "help with crontab, please"
date: 2010-05-01
forum: General Help
---

### Post by aalinovi on 2010-05-01
The following command:

/usr/bin/vlc [http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u](http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u)

starts up vlc and connects to radio station wwoz in New Orleans.

My crontab is:

pts/1 % Sat  1 9:19 /home/aalinovi >crontab -l
# m h  dom mon dow   command
SHELL=/usr/bin/zsh
15 9 * * sat '/usr/bin/vlc [http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u](http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u)'

tail -f /var/log/syslog shows me:

May  1 09:15:01 plan9 CRON[2684]: (aalinovi) CMD ('/usr/bin/vlc [http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u](http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u)')
May  1 09:15:01 plan9 CRON[2682]: (aalinovi) MAIL (mailed 93 bytes of output but got status 0x0001#012)

I have no idea what the mail error is. The crontab file seems to be running but nothing happens.

Any help would be appreciated.

(I'm running lucid having upgraded last night).

---

### Post by Vishal Agarwal on 2010-05-01
My crontab looks like this.
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

In yours one the user is missing. And for every crontab event it generates the mail to root. Your mail log entry can be for that.

---

### Post by dino99 on 2010-05-01
have to say that i've no experience with such issue but first i think to watch the logs to detect some usefull errors.

maybe you'll have better chance into programming forum as it need script knowledges

---

### Post by Paddy Landau on 2010-05-01
> **Vishal Agarwal said:**
> In yours one the user is missing.
I've never put the user. According to the manual, you don't need it.
[FONT=Courier New]man 5 crontab[/FONT]

> And for every crontab event it generates the mail to root. Your mail log entry can be for that.It won't be to root, if the OP used his normal crontab.

To find your system mail, go to a terminal and enter
[FONT=Courier New]mail[/FONT]
You may see one of more emails preceded by a number. Enter the number to read the email, and enter the letter [FONT=Courier New]d[/FONT] to delete it. Enter [FONT=Courier New]quit[/FONT] to leave mail.

To see root's email, use
[FONT=Courier New]sudo mail[/FONT]

There is a sort-of GUI for mail, but I find it difficult to use, called [FONT=Courier New]mutt[/FONT].

---

### Post by Paddy Landau on 2010-05-01
> **aalinovi said:**
> My crontab is:
```
15 9 * * sat '/usr/bin/vlc http://wwoz-sc.streamguys.com/wwoz-hi.mp3.m3u'
```
Get rid of the quotes. They don't belong there.

---

### Post by aalinovi on 2010-05-01
My thanks to all who replied. The mail error was due to the fact that I did not have the mailx package installed. 

I removed the quotes around the command as suggested and changed vlc to cvlc. All seems to be working OK.

Thanks again

---

