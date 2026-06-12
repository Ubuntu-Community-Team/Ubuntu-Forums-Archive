---
title: "Problem with install / uninstall"
date: 2011-04-11
forum: General Help
---

### Post by katezer on 2011-04-11
Hello,
I was installing curl for PHP when all my LAMP server gone crazy.
After many walkarrounds got PHP back. Then I realize a new error comes: ```
Fatal error: Call to undefined function mysql_connect() in...
```

So I try some stuff like reinstalling php5-mysql module, uncommenting that php.ini line with extension=mysql.so...

Well, I think some time ago I installed python3 and with all my installing/reinstalling/... my packages gone crazy somehow and now I am here:

```

sudo dpkg --configure -a
S'estÃ* configurant software-center (1.0.3) ...
/var/lib/dpkg/info/software-center.postinst: 12: pycentral: not found
dpkg: s'ha produÃ¯t un error en processar software-center (--configure):
 el subprocÃ©s installed post-installation script retornÃ* el codi d'eixida d'error 127
S'estÃ* configurant hplip-data (3.9.8-1ubuntu2) ...
/var/lib/dpkg/info/hplip-data.postinst: 6: update-python-modules: not found
dpkg: s'ha produÃ¯t un error en processar hplip-data (--configure):
 el subprocÃ©s installed post-installation script retornÃ* el codi d'eixida d'error 127
S'han trobat errors en processar:
 software-center
 hplip-data

```

sudo apt-get install -f -> Same error
sudo apt-get update -> No problems

Well, and upgrade or any other dpkg apt-get command usually says the error code before or this one that is more or less the same

```
S'estÃ* preparant per a reemplaÃ§ar hplip-data 3.9.8-1ubuntu2 (fent servir .../hplip-data_3.9.8-1ubuntu2.1_all.deb) ...
/var/lib/dpkg/info/hplip-data.prerm: 6: update-python-modules: not found
dpkg: avÃ*s: seqÃ¼Ã¨ncia de Â«pre-removalÂ» antiga returned error exit status 127
dpkg - s'estÃ* provant la seqÃ¼Ã¨ncia del paquet nou en el seu lloc...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: s'ha produÃ¯t un error en processar /var/cache/apt/archives/hplip-data_3.9.8-1ubuntu2.1_all.deb (--unpack):
 el subprocÃ©s seqÃ¼Ã¨ncia pre-removal nova retornÃ* el codi d'eixida d'error 127
/var/lib/dpkg/info/hplip-data.postinst: 6: update-python-modules: not found
dpkg: s'ha produÃ¯t un error en netejar:
 el subprocÃ©s installed post-installation script retornÃ* el codi d'eixida d'error 127
S'han trobat errors en processar:
 /var/cache/apt/archives/hplip-data_3.9.8-1ubuntu2.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

BTW, I have ubuntu karmic 9.10
Seems problems are about python + software-center + hplib-data?

Thank you in advance!

---

### Post by mörgæs on 2011-04-11
Karmic will be out of support in a few weeks, so there is no point in trying to fix errors in this release. 

Best is to do a clean install of 10.04.2 or 10.10 and install the server packages here, as a first step. Write again if you still have the problem.

---

### Post by katezer on 2011-04-11
That's right. I was thinking to do a clean install with the version that will be released later this month but as I use it as a webserver I was asking just if there was an easy fix that it was worth for this few days. 

Anyway. Thank you for the advice :)

---

