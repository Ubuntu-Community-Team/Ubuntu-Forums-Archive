---
title: "n00b question: Navigating to remote unshared directories"
date: 2010-03-03
forum: General Help
---

### Post by 98cwitr on 2010-03-03
In windows I can use a UNC path to access an entire drive, I can go 

Start
Run
\\ipaddress\c$
authenticate 

and then I have access to the entire windows file system on C:, basically the entire drive is mounted and I have full control access. Is this achievable in Ubuntu without the use of SSH or telnet?

---

### Post by sebastianabate on 2010-03-03
Yes, you can install SAMBA ([www.samba.org](www.samba.org)) and configure it to share any directory you want.

---

### Post by doas777 on 2010-03-03
easy way is to install ssh on the "server" box ([https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)). 

then from a client, just open a nautilus window, and enter:
```

ssh://<servernameOrIP>

OR

ssh://<username@servernameOrIP>

```

and it will open nautilus to the / on the "server"

---

### Post by doas777 on 2010-03-03
> **sebastianabate said:**
> Yes, you can install SAMBA ([www.samba.org]("http://www.samba.org")) and configure it to share any directory you want.

sharing / would be problematic, since you can't sudo a samba connection, so you would have only your normal users root.

---

### Post by 98cwitr on 2010-03-03
samba's installed and it's going going to work like that I'm already using it and i dont want to mount the share at all; hence the "unshared" in the thread title. I was trying not to use ssh, but if it's the most practical solution...

---

### Post by spiky001 on 2010-03-03
hi sorry to jump in here i,m trying the very samething I have ssh on sever as described, then when I ssh://ip  I get the correct address in address bar but i,m in laptop home folder not desktop home?

sorry my mistake corrected ip address opps

---

### Post by 98cwitr on 2010-03-03
Now if I could just get my dan netgear router's DNS to resolve names properly I'd be happy. 

I changed the port for security reasons so I just open terminal and type

ssh -v -p *portNumber* ip

now I want a different SSH password rather than it being the sudo account on my server. I'll look for the docs on that (I know I can use RSA keys, but security is a higher priority than convenience at this point). Can anyone tell me how to do that real quick? Didn't see that option in the ssh_config file.

---

### Post by doas777 on 2010-03-03
> **98cwitr said:**
> samba's installed and it's going going to work like that I'm already using it and i dont want to mount the share at all; hence the "unshared" in the thread title. I was trying not to use ssh, but if it's the most practical solution...

it prolly  won't work easily with samba, because you need to have rights to the folders in addition to having a share configured to allow you access. as such, since you don't own anything in / it will be hard to share it.

---

### Post by 98cwitr on 2010-03-03
yes, I totally understand that...I just was wondering if there was a different way other than SSH...samba is not a feasible option.

---

