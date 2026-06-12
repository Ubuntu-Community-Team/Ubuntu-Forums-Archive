---
title: "subversion"
date: 2006-06-30
forum: General Help
---

### Post by sirhan on 2006-06-30
Actually I'm setup one svn server at ubuntu server. The server running on local network and I don't want to set any password for staff to access it.
The configuration is like this:

this is the /home/svn/repos/LMS/conf/svnserve.conf configuration:

anon-access = read
auth-access = write
password-db = passwd
realm = LMS

this is the /etc/xinetd.d/svnserve configuration

service svnserve
{
disable = no
port = 3690
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/svnserve
server_args = -i -r /home/svn/repos
}

this is the /etc/services

svnserve 3690/tcp subversion # Subversion protocol

when i ran this command:

development@development:~$ netstat -na | grep 3690
tcp 0 0 0.0.0.0:3690 0.0.0.0:* LISTEN
tcp 0 0 192.168.0.4:3690 192.168.0.25:1134 TIME_WAIT
tcp 0 0 192.168.0.4:3690 192.168.0.25:1133 TIME_WAIT

---

### Post by jazzgossen on 2006-06-30
Sorry, I couldn't find a question there. What is it that you're wondering?

Edit:
Oh, now I saw your other post on this topic. It would be easier to follow if you posted everything that relates to the same problem in the same thread.

> I got this error message when I was trying to checkout the file from the svn server:

error /home/svn/repos/LMS/conf/svnserve.conf:32: Option expected

so how do I solve this problem?

Which line is the offending line (line 32) of svnserve.conf?

---

### Post by sirhan on 2006-06-30
[QUOTE=jazzgossen]Sorry, I couldn't find a question there. What is it that you're wondering?

Edit:
Oh, now I saw your other post on this topic. It would be easier to follow if you posted everything that relates to the same problem in the same thread.



Which line is the offending line (line 32) of svnserve.conf?[/QUOTE]

Sorry...
Nobody reply my question at the first thread so I create the new one.
Ermm... the offending line is 

anon-access = read

I already tried other option like write/none but still prompt the same error

---

### Post by jazzgossen on 2006-07-03
Could you post the entire svnserve.conf file? Maybe the error is before line 32.

---

### Post by hecato on 2006-10-08
Somewhat old, but anyway, you have a space before the line... ie, you only uncommented it, and let the space between the 
```

#  anon-access = read

```Untouched.. some like
```

  anon-access = read

```See the space, aparently at less has happened to me, that the parser dosent like spaces at start ;)

should be without space at start
```
anon-access = read
```

---

