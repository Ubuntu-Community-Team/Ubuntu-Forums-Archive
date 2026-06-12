---
title: "Not able to access Postgres pg_hba.conf file"
date: 2011-03-03
forum: General Help
---

### Post by leidago on 2011-03-03
Hi All

I have ubuntu desktop version 10 LTS installed on a virtual. I installed postgresql 8.4linux distro and PgAdmin 3 through the software center and it seems to work fine, except that when i try to configure the pg_hba.conf file (through pgAdmin3) it does not save the settings i make. 

Basically i do the following:

Load/open the pg_hba.conf file and the IP address(es) from which i want it to accept connections

Save and reload server.


When i save and close and then re-open the file, the settings that i made are not there.
Another strange thing is that after every second reload of the server, the server stops running and i get the server cannot start error.


 After getting some advice i tried accessing the DATA folder of my postgresql installation(that's where i was told the pg_hba.conf file is located) to open the file with geditor and save the changes directly. but the DATA folder cannot be accessed by any user other than the postgres user.

As you might have guessed by now, the purpose of trying to access the hba.conf file is to enable connections to the database from my LAN.

Can anyone help? Because i do not know how to log into the system as postgres user as i do not recall ever creating that user.

---

### Post by gigaferz on 2011-03-03
if you know the location of the conf file you can do this
press alt f2or go to a shell and type
gksudo nautilus
put your password and it will open a nautilus windows, from there you go to your conf file and edit it then save it.

---

### Post by leidago on 2011-03-05
Thanks mate, that worked for me!

---

### Post by gigaferz on 2011-03-08
good to hear that.

now can you please mark the thread as solved?

thnx

---

