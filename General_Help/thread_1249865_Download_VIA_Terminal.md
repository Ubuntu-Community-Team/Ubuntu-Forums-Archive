---
title: "Download VIA Terminal"
date: 2009-08-25
forum: General Help
---

### Post by chandru155 on 2009-08-25
Hi Guys,
           My download speed at terminal is around 200KB which is my original download speed. (I saw while installing some softwares using apt-get command). Is there any command to download files from internet( for example exe files,bin,etc etc)

I want the command some thing like

downloadUrl [www.softpedia.com/MySoftware.exe](www.softpedia.com/MySoftware.exe) /home/chandru/Desktop/MySoftware.exe
(downloadUrl Source Destination)

I used Download For x. Its download speed is very low(50 to 60 KBS) and in mozilla its around 80KBS. Then i downloaded the same software in Windows Xp via Internet download manager, the speed is 190 to 200KBS. ( i used the same link)

So, can anyone tell is there any build in command? or which is the best download manager in ubuntu. I want to download at my maximum speed(200KB)

---

### Post by Bachstelze on 2009-08-25
wget

```
cd Desktop
wget http://somewhere.org/something.exe
```

---

### Post by chandru155 on 2009-08-25
Thanks. That worked. Is there any resuming capability?
(For resuming capability should i use download manager?)

---

