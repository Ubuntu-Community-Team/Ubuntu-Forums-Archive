---
title: "Ultra Secure Remote Access: Is it possible?"
date: 2006-02-23
forum: General Help
---

### Post by klepto on 2006-02-23
I am looking for a way to open my box up so I can login remotely but without the security problems that something like sshd would cause.. I don't have sshd/telnetd running at all and with firehol I've had no problems... BUT!

I get portscanned more than a vietnamese hooker! I've been looking at freenx
and I'd like to have atleast two layers of security if possible.. One of you
ubuntu aficionados must have the answer.

---

### Post by heimo on 2006-02-23
I'm not fan of this technique, but maybe it's something you're looking for - it's called port knocking:
[http://www.linuxjournal.com/article/6811](http://www.linuxjournal.com/article/6811)

Other tips would be to use key based authentication
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

And if you know the networks from where you're going to initiate ssh connections, you can naturally use firewall to allow connections only from those sites.

---

### Post by klepto on 2006-02-24
Thanks for the tips,

If it weren't for this great community I'd be insane and pulling my hair out until I was bald. I installed nxfree with no issues and I will use my own keys and keep them on a thumbdrive for safe keeping.. linux/win clients really help alot too.. ssh is on a non standard port.

---

