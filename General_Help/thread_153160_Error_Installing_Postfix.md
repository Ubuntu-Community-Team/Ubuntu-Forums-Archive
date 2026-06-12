---
title: "Error Installing Postfix"
date: 2006-03-31
forum: General Help
---

### Post by playmobiel on 2006-03-31
> ****@frodo:~$ sudo apt-get install postfix
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
postfix is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geÃ¯nstalleerd, 0 verwijderen en 0                                                                               niet opgewaardeerd.
4 pakketten niet volledig geÃ¯nstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...                                                                                                                   postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: fout bij afhandelen van postfix (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van mailx:
 mailx is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geÃ¯nstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd                                                                              .
dpkg: fout bij afhandelen van mailx (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mutt:
 mutt is afhankelijk van postfix | mail-transport-agent; maar:
  Pakket postfix is nog niet geconfigureerd.
  Pakket mail-transport-agent is niet geÃ¯nstalleerd.
  Pakket postfix die voorziet in mail-transport-agent is nog niet geconfigureerd                                                                              .
dpkg: fout bij afhandelen van mutt (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van mysql-server:
 mysql-server is afhankelijk van mailx; maar:
  Pakket mailx is nog niet geconfigureerd.
dpkg: fout bij afhandelen van mysql-server (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 postfix
 mailx
 mutt
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone knows how to solve this error?
Thanks,

---

### Post by playmobiel on 2006-04-01
No one knows?

---

### Post by Ramses de Norre on 2006-04-01
sudo apt-get -f install 
(you should translate the dutch, don't think there are much people here understanding it)

---

### Post by playmobiel on 2006-04-01
Yes that would be smart , i didn't have that in my mind , but the problem is sloved now , i just reinstalled my ubuntu , because the force also didn't work 

Thanks

---

