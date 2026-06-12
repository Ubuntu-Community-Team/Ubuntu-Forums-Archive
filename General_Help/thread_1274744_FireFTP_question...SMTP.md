---
title: "FireFTP question...SMTP"
date: 2009-09-24
forum: General Help
---

### Post by DapperMe17 on 2009-09-24
Hi,

FireFTP & OpenSSH

I'm trying to connect with a server, to transfer over a file.

I can connect fine & get the RSA2 key accept/deny popup, which is great!

However, I want to verify the RSA2 key listed in FireFTP is the same as the one listed in the server SSH RSA file. Obviously, the two keys must be the same, but are in different formats. 

On the server, how can I verify that the two formats of the same key, actually are the same?

---

### Post by toupeiro on 2009-09-25
> **DapperMe17 said:**
> Hi,

FireFTP & OpenSSH

I'm trying to connect with a server, to transfer over a file.

I can connect fine & get the RSA2 key accept/deny popup, which is great!

However, I want to verify the RSA2 key listed in FireFTP is the same as the one listed in the server SSH RSA file. Obviously, the two keys must be the same, but are in different formats. 

On the server, how can I verify that the two formats of the same key, actually are the same?

The two keys aren't necessarily the same, but they are paired.  You want to generate your RSA keys and share the public key with other hosts.  when you try to connect with your private key, if it knows about your public key, it authenticates you.  Do NOT share your private key.

---

### Post by DapperMe17 on 2009-09-25
Sure, that I know. 

However the plain test RSA key on the server (in /SSH) appears to be in one format....ex) AAAAA7rst0 

FireFTP fires the RSA2 key at me (in the pop-up box) in the format of....ex) d9:4t:4l:


Obviously, FireFTP is firing me the correct key from the server side. I do know the server side "public" key, however, they don't have the same format. 

Could FireFTP be automatically converting it to a .ppg format or OPen SSH? 

If so, how would I take the server side "public" key & convert it so that I could "visually" compare the keys?

---

### Post by DapperMe17 on 2009-09-30
bump

---

