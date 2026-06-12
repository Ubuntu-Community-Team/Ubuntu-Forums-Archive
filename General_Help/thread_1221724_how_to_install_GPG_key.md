---
title: "how to install GPG key"
date: 2009-07-24
forum: General Help
---

### Post by wstay on 2009-07-24
Can someone please explain how to install GPG key?
I click on a link [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) to download and install the GPG key. But what I get is as follow:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.9 (GNU/Linux)
mQGiBEoOI1QRBADrv7Qk8VmJRhz7IM4ney/U7lcXYjlvKDxphfXkJxcjOxSOaJXt
LO09GirJSD/vl/3rJ5KY1i8aln4Ji7ZsxEV9mdYSpXKmTIOZpW7Jp7kQE5fxehfX
hvbjTeDF2ZSGDMVPG6m0wffmXac+OwK/cI28s9dK7RH+O0dk1WQ3vMV7vwCgz6hq
OPgOxLqqaMFknqaYy71OflsEALAebD9KOTvIEtqiV+JFpehzTZ M/zJFn0gpx8gLh
KrK4sauAxgBFo+Juhzjcq0zh4bG2jXkfX/Nwlgli9wucp9Yv60W2QACd4yin3574
7/FYElAcuykQCgzqY0cRCD2VPAFJLU4mVWCS4qfWJgLd9JR8zD/BZYLJFdIXHRD+
FxU4A/4leZ/WI1WUv+5g0AO5qDLoxKG7XjR5Wmu3L8STbXqB/XgN/msxogUxoJyc
ccxcMbp8ZqWp4iZ+gHEIyqcpFTC586lFrmtNgiLw+0g4eBSbvk jheHoU6miZXI5E
J6+iMiVw2Z1ma9yxpU4DmjbBcnbPK67GHBMm7hrz/vyvrYefYbQrU2Ftc3VuZyBV
bmlmaWVkIExpbnV4IERyaXZlciBSZXBvc2l0b3J5IEtleYhmBB MRAgAmBQJKDiNU
AhsDBQkFo5qABgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ9e MmFuRoEKWMMACd
EvpR0bbt6dapsx0p3kJ/NnT7KRoAnRjIGfA8WkcJk2TpvuendZMQrbAAuQINBEoO
I1QQCADghwFR2w+c2Wy8cgmDkIcN1Sx/fM6U/e0LQbmGpYodvW0xw2oyOBXwDpok
G/TJ02ZbGMM9cGPfflOfztRYJQJ6olS6TMTieIlY/7898j3jEnnzh8P+d71bpH5d
58Rkdffaz6LVZX9vJZYErHlQK09Dgu3FYd0M8C38bpPAGf1CnX 4e2LFgnk9TkJWA
ABgLzt6yUiHkcitmXwU8wWSspI7BhFulz6mYFfXdJzwWXTqBPD Nl5yQydufnwBnv
42c83owOPitmnS//4nYDIhOFeBHzX2E7kaps0QI3nm5gCsLEwB9nKjb8ojyygAlS
gUUU8oYTjYRd+f/qIjTd0qHjqbOTAAMFB/0SES8+e5T0xm36ZooLdx68HXhSzvWE
EjUoFyuMydAToMI/XXAIZS8jrR7V9VS+51EiSbtVglU/FqjuLO48k4k1vAAp/GgT
7YhALFYyEHSdIF4Fx/NV/p2H9fEW4CQA/zslsLYVl/wrnYEf57j3A1wolFY5G0A+
cwv/RPwU6RysUEQxQWPVqxZ5rHaC2QJ+8QPTrZjkQgEsm+xwKtQ7OF KV05IBs5Cb
s4fF2rPfhyrwDolLbpYAA81lpiRlMY4TtNa+wIXXuJiD4KACdw Hib24fZDTioX5Z
GaN/7597HIAb3TjFI0My1JDcYRVwiXdlx1kQ//3IdccyFpb3Fb+EXHdNiE8EGBEC
AA8FAkoOI1QCGwwFCQWjmoAACgkQ9eMmFuRoEKVFjwCeLokkRp cEL9WZmgILwN5r
GBU//IYAniVhb+EnOfIyLmy/d6EzaLai5/RW
=t8A/
-----END PGP PUBLIC KEY BLOCK-----

The problem is how I can get this to install on my Ubuntu system because I need to add the repository: [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) in the Synaptic Package Manager and it gives me this error message:
W: GPG error: [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F5E32616E46810A5.

---

### Post by sisco311 on 2009-07-24
Save the key in a file on your desktop, go to Synaptic > Settings > Repositories > Authentication tab, click the *Import Key File* button and import the file createn on your desktop.

EDIT: or open a terminal and copy paste this commands (line by line):
```
wget http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg
sudo apt-key add suldr.gpg
rm suldr.gpg
sudo apt-get update
```

---

### Post by bacil on 2009-07-24
there is one line missing after you get gpg key from server you should add it in to your keyring

```
gpg --export --armor E46810A5 | sudo apt-key add -
```

so the first line should be :-))

```
gpg --keyserver keyserver.ubuntu.com --recv E46810A5 
```

---

### Post by bacil on 2009-07-24
> **sisco311 said:**
> Save the key in a file on your desktop, go to Synaptic > Settings > Repositories > Authentication tab, click the *Import Key File* button and import the file createn on your desktop.

i was using your previous version as reference :-) now i have to add keyserver line as well :-)

---

### Post by sisco311 on 2009-07-24
This key is not available from keyserver.ubuntu.com. 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678
```
or
```
gpg --export --armor 12345678 | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv 12345678
```
works for the ppa repos but not for this one.

i have edited my first post. :)

---

