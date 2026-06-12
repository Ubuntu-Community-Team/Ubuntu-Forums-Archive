---
title: "is the command sudo apt-get install -f dangerous??"
date: 2012-04-04
forum: General Help
---

### Post by Vbcoder on 2012-04-04
hey, my software centre is saying it needs to be repaired and isnt working and blah blah, apparently as part of fixing it I have to run

Sudo apt-get install -f

When I run this it says it is possibly very dangerous and that nearly 4Gb of Hard Disk space will be freed.

What the hell should i do?

---

### Post by philinux on 2012-04-04
> **Vbcoder said:**
> hey, my software centre is saying it needs to be repaired and isnt working and blah blah, apparently as part of fixing it I have to run

Sudo apt-get install -f

When I run this it says it is possibly very dangerous and that nearly 4Gb of Hard Disk space will be freed.

What the hell should i do?

The -f flag means this.

-f, --fix-broken

I've used it many times. Could you post the full message you get.

---

### Post by Vbcoder on 2012-04-04
well right now I just ran it and got something different, it says

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by philinux on 2012-04-04
> **Vbcoder said:**
> well right now I just ran it and got something different, it says

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

If you've got synaptic open etc it wont run that's why it cant get a lock.

---

### Post by Vbcoder on 2012-04-04
I dont have synaptic running 
[FONT=monospace]Been trying to fix this for hours, when i open software centre it says I cant install or remove anything until its repaired thee catalog, when i click repair it gives an error, so not useful.

Also im quite new to Ubuntu
[/FONT]

---

### Post by philinux on 2012-04-04
> **Vbcoder said:**
> I dont have synaptic running 
[FONT=monospace]Been trying to fix this for hours, when i open software centre it says I cant install or remove anything until its repaired thee catalog, when i click repair it gives an error, so not useful.

Also im quite new to Ubuntu
[/FONT]

Ok what I'd do is this. Reboot to make sure no apt running.

Then once logged in run the command as before.

---

### Post by Vbcoder on 2012-04-04
ok i just shutdown and restarted, when i ran

Sudo apt-get -f install

it told me to run 

Sudo dpkg --configure -a

which gave me:

dpkg: dependency problems prevent configuration of man-db:
 man-db depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
dpkg: error processing man-db (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.13-20ubuntu5.1); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Setting up sysv-rc (2.88dsf-13.10ubuntu4.1) ...
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on libc6 (>= 2.9); however:
  Package libc6 is not installed.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on libc6 (>= 2.4); however:
  Package libc6 is not installed.
 initscripts depends on upstart; however:
  Package upstart is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 libc6-dev
 upstart
 initscripts

---

### Post by dino99 on 2012-04-04
i think you may have installed an untrusted app (non genuine ubuntu) from third party, that brings this mess.

Try some cleanings into a terminal, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

Can you post the result of:   cat /etc/apt/sources.list

---

### Post by philinux on 2012-04-04
> **Vbcoder said:**
> ok i just shutdown and restarted, when i ran

Sudo apt-get -f install

it told me to run 

Sudo dpkg --configure -a

which gave me:

dpkg: dependency problems prevent configuration of man-db:
 man-db depends on libc6 (>= 2.8); however:
  **[COLOR="Red"]Package libc6 is not installed.[/COLOR]**
dpkg: error processing man-db (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.13-20ubuntu5.1); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Setting up sysv-rc (2.88dsf-13.10ubuntu4.1) ...
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on libc6 (>= 2.9); however:
  Package libc6 is not installed.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on libc6 (>= 2.4); however:
  [COLOR="Red"]**Package libc6 is not installed**[/COLOR].
 initscripts depends on upstart; however:
  Package upstart is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 libc6-dev
 upstart
 initscripts

Try sudo apt-get install libc6

---

### Post by woxuxow on 2012-04-04
> **philinux said:**
> The -f flag means this.

-f, --fix-broken



-f means --fix-missing

---

### Post by raja.genupula on 2012-04-04
> **MustafaJF said:**
> -f means --fix-missing

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

-f, --fix-broken

-m, --ignore-missing, --fix-missing

---

### Post by philinux on 2012-04-04
> **MustafaJF said:**
> -f means --fix-missing

Please read man apt-get :

>  -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place. This option, when used with
           install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option is sometimes necessary when
           running APT for the first time; APT itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be so corrupt as to require manual
           intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may produce an error in some situations.
           Configuration Item: APT::Get::Fix-Broken.


Although --fix-missing works too.

But -f is less typing.

---

### Post by woxuxow on 2012-04-04
i think you should 
first close any software that use apt or sources.list like ubuntu software center 
then open the terminal type 
sudo apt-get --purge autoremove
next
sudo apt-get --fix-missing install

---

### Post by raja.genupula on 2012-04-04
> **MustafaJF said:**
> i think you should 
first close any software that use apt or sources.list like ubuntu software center 
then open the terminal type 
sudo apt-get --purge autoremove
next
sudo apt-get --fix-missing install

whats the use of purge in a autoremove command ?

---

### Post by philinux on 2012-04-04
Lets get back on topic rather than mess with semantics.

-f is less typing.

The op is missing libc6 from his install. See post 9

---

### Post by fiatveritas on 2012-04-04
Have you tried to update Ubuntu? I know I had trouble getting ```
sudo apt-get -f install
``` to work because I wasn't updating Ubuntu frequently.

---

### Post by nothingspecial on 2012-04-04
If libc6 isn't going to be installed then you have bigger problems than your package manager.

Are there any other symptoms?

---

### Post by philinux on 2012-04-04
> **nothingspecial said:**
> If libc6 isn't going to be installed then you have bigger problems than your package manager.

Are there any other symptoms?

In the error message it says not installed not "not going to be installed".

I agree though that package should not just go missing, very odd

---

### Post by woxuxow on 2012-04-05
> **philinux said:**
> Please read man apt-get :



Although --fix-missing works too.

But -f is less typing.

your`re right i was wring
in the document you have introduced and apt`s man --fix-broken is true not --fix-missing

---

### Post by woxuxow on 2012-04-05
> **raja.genupula said:**
> whats the use of purge in a autoremove command ?

to remove configure files

---

### Post by tmNihonsuki on 2012-09-12
> **Vbcoder said:**
> hey, my software centre is saying it needs to be repaired and isnt working and blah blah, apparently as part of fixing it I have to run

Sudo apt-get install -f

When I run this it says it is possibly very dangerous and that nearly 4Gb of Hard Disk space will be freed.

What the hell should i do?

Anybody else reading this should tread very carefully.  I followed these instructions and virtually bricked my laptop.  I can make a suggestion about what the -f stands for...

---

