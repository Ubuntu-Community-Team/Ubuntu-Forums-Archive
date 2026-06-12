---
title: "Browsing ubuntuforum.org"
date: 2006-04-27
forum: General Help
---

### Post by rabside on 2006-04-27
hi!
After installing Ubuntu Breezy I can browse the web very fast but with some sites I have a lot of problems. For example, with ubuntuforum.org I can open only 2 topic, if I try to open another one Firefox (or opera) doesn't load the page.

net configuration:
linuxbox, macosx and a windows machine behind a dhcp router. only linux can't load some pages. i've tried with static ip and dhcp but result is the same. in resolv.conf there are my provider's dns ip.

Can u help me, pls?

---

### Post by rabside on 2006-04-27
up!
pls help me!!!

---

### Post by AndrewCaul on 2006-04-27
I'm having trouble understanding your problem. Are you saying that you can only navigate the Ubuntu forums in two tabs? Can you open other sites?

---

### Post by rabside on 2006-04-27
I'll explain my problem better :)
if I try to navigate this forum I can load only 2 topics: if I try to read another topic firefox can't download the page but I can browse all the web, my connection doesn't hung up. I have the same problem with assistenza.tiscali.it.
Under win all work without problems.

thx in advance for ur help :)

---

### Post by Ramses de Norre on 2006-04-27
It's just a very wild guess but could you post the output of following command: ```
ls -lA ~/.mozilla/firefox/*.default|grep -i cache && ls -lA ~/.mozilla/firefox/*.default/Cache

```

---

### Post by rabside on 2006-04-28
rabside@rubuntu:~$ ls -lA ~/.mozilla/firefox/*.default|grep -i cache && ls -lA ~/.mozilla/firefox/*.default/Cache
drwxr-xr-x  2 rabside rabside    2256 2006-04-28 19:14 Cache
-rw-r--r--  1 root    root        783 2006-04-27 10:58 extensions.cache
totale 4625
-rw-------  1 rabside rabside  19654 2006-04-28 09:51 01A38C85d01
-rw-------  1 rabside rabside  90562 2006-04-28 19:14 03771B9Fd01
-rw-------  1 rabside rabside 103996 2006-04-28 19:14 03771BCFd01
-rw-------  1 rabside rabside  22175 2006-04-28 09:38 05FB45B8d01
-rw-------  1 rabside rabside  26941 2006-04-28 09:38 0A3CD195d01
-rw-------  1 rabside rabside  30286 2006-04-28 09:38 0A3FD195d01
-rw-------  1 rabside rabside  30169 2006-04-28 09:51 167BFBCFd01
-rw-------  1 rabside rabside  28243 2006-04-28 09:42 29AC1C23d01
-rw-------  1 rabside rabside  73940 2006-04-28 09:48 2F075EF1d01
-rw-------  1 rabside rabside  19001 2006-04-28 09:55 33AC679Ad01
-rw-------  1 rabside rabside  96687 2006-04-28 09:48 33BCEA39d01
-rw-------  1 rabside rabside 112604 2006-04-28 19:14 43F70EDAd01
-rw-------  1 rabside rabside  80837 2006-04-28 19:12 43F719ACd01
-rw-------  1 rabside rabside  76691 2006-04-28 19:14 43F74357d01
-rw-------  1 rabside rabside  90653 2006-04-28 09:51 43F74D5Dd01
-rw-------  1 rabside rabside 119951 2006-04-28 19:12 43F7584Bd01
-rw-------  1 rabside rabside  84590 2006-04-28 19:12 43F75896d01
-rw-------  1 rabside rabside  73005 2006-04-28 19:12 43F75EAAd01
-rw-------  1 rabside rabside  17923 2006-04-28 09:38 4C947D8Fd01
-rw-------  1 rabside rabside  35457 2006-04-28 09:51 4D0F42E6d01
-rw-------  1 rabside rabside  20796 2006-04-28 09:51 4DD61C50d01
-rw-------  1 rabside rabside 147345 2006-04-28 09:36 51A31503d01
-rw-------  1 rabside rabside  24932 2006-04-28 09:40 5389D0BEd01
-rw-------  1 rabside rabside  42568 2006-04-28 19:12 562436B1d01
-rw-------  1 rabside rabside  17712 2006-04-28 09:55 58D222EFd01
-rw-------  1 rabside rabside  17833 2006-04-28 09:48 60471E6Dd01
-rw-------  1 rabside rabside  24481 2006-04-28 09:51 6070273Ed01
-rw-------  1 rabside rabside  96779 2006-04-28 19:14 62602E56d01
-rw-------  1 rabside rabside  18564 2006-04-28 09:43 67F59ACFd01
-rw-------  1 rabside rabside  19137 2006-04-28 19:14 71BF0375d01
-rw-------  1 rabside rabside  10866 2006-04-28 19:14 72C9D3F9d01
-rw-------  1 rabside rabside  19137 2006-04-28 19:14 738CA155d01
-rw-------  1 rabside rabside  24256 2006-04-28 09:38 77DFB5FBd01
-rw-------  1 rabside rabside  22176 2006-04-28 09:38 7B63C6FEd01
-rw-------  1 rabside rabside  18535 2006-04-28 09:51 8457EAC5d01
-rw-------  1 rabside rabside  46250 2006-04-28 19:14 84D55A98d01
-rw-------  1 rabside rabside  43098 2006-04-28 09:51 84DA80CDd01
-rw-------  1 rabside rabside  11296 2006-04-28 09:38 8D860808d01
-rw-------  1 rabside rabside  12324 2006-04-28 09:41 8FF48260d01
-rw-------  1 rabside rabside  22173 2006-04-28 09:38 979F880Ad01
-rw-------  1 rabside rabside  17271 2006-04-28 09:55 9A729CE4d01
-rw-------  1 rabside rabside  33210 2006-04-28 19:14 A4C37521d01
-rw-------  1 rabside rabside  19608 2006-04-28 19:14 A686EF49d01
-rw-------  1 rabside rabside  60952 2006-04-28 09:48 A926F49Dd01
-rw-------  1 rabside rabside  18996 2006-04-28 09:37 AAC6AA36d01
-rw-------  1 rabside rabside 149581 2006-04-28 19:12 AAF566B5d01
-rw-------  1 rabside rabside  42374 2006-04-28 09:56 AD724507d01
-rw-------  1 rabside rabside  49152 2006-04-28 19:12 B33F0A8Fd01
-rw-------  1 rabside rabside  72970 2006-04-28 19:12 B384DCB7d01
-rw-------  1 rabside rabside  42648 2006-04-28 09:38 B8667C6Dd01
-rw-------  1 rabside rabside  21008 2006-04-28 09:38 B97BA48Dd01
-rw-------  1 rabside rabside 545792 2006-04-28 19:14 _CACHE_001_
-rw-------  1 rabside rabside 343040 2006-04-28 19:14 _CACHE_002_
-rw-------  1 rabside rabside 929792 2006-04-28 19:14 _CACHE_003_
-rw-------  1 rabside rabside  16660 2006-04-28 19:11 _CACHE_MAP_
-rw-------  1 rabside rabside  25411 2006-04-28 09:37 D3177C09d01
-rw-------  1 rabside rabside  67891 2006-04-28 09:38 D740379Cd01
-rw-------  1 rabside rabside  20570 2006-04-28 09:42 D9CCD4A2d01
-rw-------  1 rabside rabside  18535 2006-04-28 09:48 DD29C52Dd01
-rw-------  1 rabside rabside  19082 2006-04-28 09:51 E074208Fd01
-rw-------  1 rabside rabside  33217 2006-04-28 09:37 E2D74274d01
-rw-------  1 rabside rabside  18161 2006-04-28 09:41 E32D26E7d01
-rw-------  1 rabside rabside  13774 2006-04-28 09:41 E88D407Cd01
-rw-------  1 rabside rabside  29896 2006-04-28 09:48 EDDB3299d01
-rw-------  1 rabside rabside  19654 2006-04-28 09:48 F27689BDd01
-rw-------  1 rabside rabside  53121 2006-04-28 19:14 F5374237d01
-rw-------  1 rabside rabside  23590 2006-04-28 09:41 F6873299d01
-rw-------  1 rabside rabside  20799 2006-04-28 09:48 FD0D84E4d01
-rw-------  1 rabside rabside  41981 2006-04-28 09:38 FDFDF0CFd01
rabside@rubuntu:~$


is it right?

---

### Post by Ramses de Norre on 2006-04-28
Too wild guess..

---

### Post by rabside on 2006-04-29
Solved!
it was fasterfox plugin: if I set it to turbo performance I jave the problems. also with windows!

---

### Post by Bloch on 2006-04-29
Can you tell us a little bit more about how you solved the problem?
Was it a problem in the fresh install of Firefox or was it a problem you caused yourself somehow?
If it is something that goes wrong in a fresh install of firefox then we need to know about it.

---

### Post by rabside on 2006-04-29
yep, fresh install.
firefox version 1.5.0.2 and fasterfox 1.0.3.
in the fasterfox panel select turbo loading or turbo performance (I have the italian version and it is "Caricamento turbo"). Then try to open 3 topic at once on ubuntuforums.org or 3 pages on assistenza.tiscali.it

try it!

---

### Post by rabside on 2006-04-30
[QUOTE=rabside]yep, fresh install.
firefox version 1.5.0.2 and fasterfox 1.0.3.
in the fasterfox panel select turbo loading or turbo performance (I have the italian version and it is "Caricamento turbo"). Then try to open 3 topic at once on ubuntuforums.org or 3 pages on assistenza.tiscali.it

try it![/QUOTE]
you can see the same behavour under windows

---

