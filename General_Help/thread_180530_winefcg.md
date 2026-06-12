---
title: "winefcg"
date: 2006-05-22
forum: General Help
---

### Post by jorge.maravi on 2006-05-22
I just instaled wine from automatix, and i ran winecfg
The only thing i saw is

root@j-maravi1:/home/jmaravi# winecfg
wine: creating configuration directory '/root/.wine'...

sizeof(RADEONDRIRec) == 100, devPrivSize 100

sizeof(RADEONDRIRec) == 100, devPrivSize 100
h
root@j-maravi1:/home/jmaravi# exit
exit
jmaravi@j-maravi1:~$ winecfg
wine: creating configuration directory '/home/jmaravi/.wine'...

sizeof(RADEONDRIRec) == 100, devPrivSize 100

sizeof(RADEONDRIRec) == 100, devPrivSize 100


And nothing else...

After check ps -ef | more,i can see something is running in background..

root@j-maravi1:/home/jmaravi# ps -ef | grep wine
jmaravi 8261 8107 0 10:57 pts/0 00:00:00 /usr/bin/../lib/../bin/wine-pthread winecfg.exe
jmaravi 8264 8261 0 10:57 pts/0 00:00:00 /bin/sh /usr/bin/../lib/../bin/wineprefixcreate --quiet --wait --prefix /home/jmaravi/.wine-Z3NwOj
jmaravi 8281 8264 0 10:57 pts/0 00:00:01 rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
jmaravi 8284 1 0 10:57 ? 00:00:00 /usr/bin/../lib/../bin/wineserver
root 8429 8168 0 11:10 pts/1 00:00:00 grep wine


Is this normal?????
Is something wrong??
Does it take so long???

Thanks

JOrge

---

