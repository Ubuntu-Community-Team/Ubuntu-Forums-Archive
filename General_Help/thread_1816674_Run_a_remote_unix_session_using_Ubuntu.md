---
title: "Run a remote unix session using Ubuntu"
date: 2011-08-02
forum: General Help
---

### Post by digitrac on 2011-08-02
Hi,
 
Ubuntu newbie here!
 
At the moment I am using Hummingbird Exceed on a windows PC to display X windows from a Unix server. The actual Exceed tool I use is called 'hwm' which I believe is basically an pc based X Windows manager. I do not need to configure anything other than the client computer name, IP address and screen definition and the server will then allow a connection and display the X windows on the client. I was wondering if there is an equivalent application I can run using Ubunto as a client insted of a Windows PC?
 
Cheers,
 
digitrac

---

### Post by aeiah on 2011-08-02
you should just be able to use ssh with the -X option. give it a shot:```
ssh username@server -X 'hwm'
```

---

