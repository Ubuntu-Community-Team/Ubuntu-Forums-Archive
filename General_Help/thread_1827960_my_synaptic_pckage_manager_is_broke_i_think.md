---
title: "my synaptic pckage manager is broke i think???"
date: 2011-08-18
forum: General Help
---

### Post by metalhead088 on 2011-08-18
E: Could not open file /var/lib/apt/extended_states - open (2: No such file or directory)
E: Unable to determine the file size - fstat (9: Bad file descriptor)
E: _cache->open() failed, please report.


When i opened my synaptic package manager it comes up with this, i tried to install avast anti virus, now when i try to remove it off the terminal it comes up with this, im quite a noob and im unable i can sort this out myself.

~$ sudo apt-get --purge remove avast4workstation
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

also my package manager has come up with crashing too, i have no idea i would assume it was because of trying to install avast and it didnt like it please help i like natty alot lol

any help with this would be great :)

---

### Post by jerrrys on 2011-08-18
number 1

open a terminal and enter
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

this will hopefully fix that broke package

number 2:

you cannot have another package manager open at the same time your doing this

---

### Post by metalhead088 on 2011-08-18
okay ive done that exactly to the letter, i then had this  response in terminal

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
does this mean i have to reinstall ubuntu?

i then tested to see if synaptic package manager would work and it came up with the same thing again.

---

### Post by jerrrys on 2011-08-18
go to:

System>administration>software sources>other software

and uncheck "**cdrom**"

---

### Post by metalhead088 on 2011-08-18
okay unfortunately that didnt work, what do i do next? is there a function to roll back the system a few days like windows or something?

---

### Post by jerrrys on 2011-08-18
nope, no such handy little button

do a sudo apt-get update and post any errors please

---

### Post by angry_johnnie on 2011-08-18
that's really odd.  the last message you got just told you it couldn't find cdrom.  so unchecking cdrom should do it :p

try

```
gksu gedit /etc/apt/sources.list
```

and comment out (add a # at the beginning) the cd rom entry (usually the first line).

it should look like this:

```
# deb cdrom:[Ubuntu ... so on
```

if you find any more lines that mention a cdrom, just do the same.

then save it, and run

```
sudo apt-get update
```

if you get any more errors, it should be about something other than the cdrom

---

### Post by jerrrys on 2011-08-18
i should add that variations of a window restore can be added

---

### Post by metalhead088 on 2011-08-18
okay ive just done the source list, but it came up with this

Could not open file /var/lib/apt/extended_states - open (2: No such file or directory)
E: Unable to determine the file size - fstat (9: Bad file descriptor)

if there is some sort of roll back it probably would go handy, im not brilliant with sudo, and obviously i have done something wrong to have this happen.

---

### Post by angry_johnnie on 2011-08-18
:o sure looks ugly!

in terminal, type:

```
cd /var/lib/apt
```

and then

```
ls -a
```

see if ti comes back with an "extended_states" file, or with "extended_states.bak"


if you do have one, try renaming it

```
sudo mv extended_states extended_states_two
```

apt should create a new one, so just try installing anything, or updating:

```
sudo apt-get update
```

if it doesn't, try creating one yourself. run:

```
touch extended_states
```

you may also need to change ownership

```
sudo chown root.root extended_states
```

and give yourself read permission

```
sudo chmod a+r extended_states
```

then try

```
sudo apt-get update
```

---

### Post by jerrrys on 2011-08-18
is extended_states part of **dpkg** package?

---

### Post by angry_johnnie on 2011-08-18
> **jerrrys said:**
> is extended_states part of **dpkg** package?

apparently, it is.

it may also help to run

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

---

