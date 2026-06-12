---
title: "Installation/Removal of Gnome DO"
date: 2012-01-25
forum: General Help
---

### Post by bga117636 on 2012-01-25
Hi!

I tried to install gnome do, but got an error during installation, so I try to remove it and re-install. But when I try to remove it I get this message in Terminal:


root@martin-laptop:/home/martin# sudo apt-get -f purge
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
1 pakker ikke fullt installert eller fjernet.
Må hente 498kB med arkiver.
Etter denne operasjonen vil 0B ekstra diskplass bli brukt.
Hent:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe gnome-do 0.8.3.1+dfsg-1ubuntu1 [498kB]
Hentet 498kB på 1s (366kB/s)    
(Leser database ... 170496 filer og kataloger er installerte.)
Gjør klar til å bytte ut gnome-do 0.8.3.1+dfsg-1ubuntu1 (ved bruk av .../gnome-do_0.8.3.1+dfsg-1ubuntu1_amd64.deb) ...
Pakker ut erstatningen gnome-do ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: gammelt post-removal-skript returned error exit status 1
dpkg - prøver i stedet et skript fra den nye pakken ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: Feil ved behandling av /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_amd64.deb (--unpack):
 underprosessen nytt post-removal-skript returnerte feilstatus 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: feil ved opprydding:
 underprosessen nytt post-removal-skript returnerte feilstatus 1
Behandler utløsere for hicolor-icon-theme ...
Behandler utløsere for desktop-file-utils ...
Behandler utløsere for python-gmenu ...
Rebuilding /usr/share/applications/desktop.nb_NO.utf8.cache...
Behandler utløsere for man-db ...
Behandler utløsere for python-support ...
Det oppsto feil ved behandling av:
 /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone know what to do?

---

### Post by jamesisin on 2012-02-03
Why are you signed in as root (and using sudo)?

What method did you use to install gnome-do?  What happened then?

How did you uninstall gnome-do?

---

### Post by raja.genupula on 2012-02-03
1 . please give us information in english , because i am sorry i am unable to get matter .

2. what errors you got while installation , if you provide them , then we will try to help you 

i got a link [http://www.techrepublic.com/blog/opensource/install-and-configure-gnome-do-in-ubuntu-unity/2535](http://www.techrepublic.com/blog/opensource/install-and-configure-gnome-do-in-ubuntu-unity/2535)

please accept my 1,2 and provide information .

Thank you very much .

---

### Post by bga117636 on 2012-02-16
Well, I tried to get the terminal to work in english, but I cannot figure out how. 

I seem to have found the problem, but no solution.

There appears to be two different obstacles: when I try to remove Gnome Do, the terminal tells me that the package is in an inconsistent state, and must be re-installed in order to be removed. But when I try to re-install, I get these two errors:
Sub-process /usr/bin/dpkg returned an error code (1)

Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'

I tried to figure out how to install the specific directory with aptitude, but no luck :(

---

