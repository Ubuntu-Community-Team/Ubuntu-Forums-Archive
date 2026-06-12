---
title: "Samba problem or Network problem.."
date: 2012-07-14
forum: General Help
---

### Post by Jorel on 2012-07-14
Hi guys,
 
can you help me? because i noticed most of the times i needed to restart  /etc/init.d/networking for my "shared files" to back on the line, is possible for my server's network to be automatically up and never go down? or is it my LAN card that  is having a problem? and when i restarted Samba "service smbd restart" everything i shared is now gone and cannot be located... 
 
im just confused :confused:

---

### Post by Rexilion on 2012-07-14
When it happens, could you please provide the following output?

```
sudo dmesg | tail -n10
```

---

### Post by rslater on 2012-07-14
Have you checked to see if your network card 'sleeps' in powersave mode?

---

### Post by Jorel on 2012-07-17
Hi rslater and Rexilion,

i saw the problem,, its with my Windows machine, i reformat it and monitor again my server's performance and noticed that it does not go down or disconnect,,,

thanks for your time guys..

---

