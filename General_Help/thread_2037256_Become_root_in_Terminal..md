---
title: "Become root in Terminal."
date: 2012-08-04
forum: General Help
---

### Post by Jetrab on 2012-08-04
Hi all ubuntu users :) Im totatly fresh at this. Installed yesterday and im enjoying it. But i was thinking i should get the apt-get upgrade by now. But i must be misstyping the CMD to write as root in the terminal. (noobie question). Q quick respond maybe ;) ?. 
Thanks !!

       :guitar:

---

### Post by mastablasta on 2012-08-04
```
sudo apt-get update
sudo apt-get upgrade
```
for system* update.*


see here for system *upgrade*:
[http://www.liberiangeek.net/2011/10/how-to-upgrade-to-ubuntu-11-10-oneiric-ocelot-from-ubuntu-11-04-natty-narwhal-via-the-console-server/?ModPagespeed=off](http://www.liberiangeek.net/2011/10/how-to-upgrade-to-ubuntu-11-10-oneiric-ocelot-from-ubuntu-11-04-natty-narwhal-via-the-console-server/?ModPagespeed=off)

---

### Post by sisco311 on 2012-08-04
Welcome to the forums!

Please check out the community documentation:
[uhelp]community/RootSudo[/uhelp]

---

### Post by dcstar on 2012-08-04
> **Jetrab said:**
> Hi all ubuntu users :) Im totatly fresh at this. Installed yesterday and im enjoying it. But i was thinking i should get the apt-get upgrade by now. But i must be misstyping the CMD to write as root in the terminal. (noobie question). Q quick respond maybe ;) ?. 
Thanks !!


Why are you using the terminal when there are perfectly good GUI apps for this?

It is no longer 1980.

---

### Post by woxuxow on 2012-08-04
to upgrade the system`s packages like kernel (linux) you should use dist-upgrade

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Jetrab on 2012-08-04
thanks for answers :) Update is running now.

---

### Post by Jetrab on 2012-08-04
> **dcstar said:**
> Why are you using the terminal when there are perfectly good GUI apps for this?

It is no longer 1980.

well.. i like typing.. so thats why i do it. >_>

---

### Post by thek3nger on 2012-08-04
You can also type once

```
sudo su
```

if you don't want to type "sudo" for every command.

---

### Post by ryanyeah on 2012-08-04
> **dcstar said:**
> Why are you using the terminal when there are perfectly good GUI apps for this?
It is no longer 1980.

Nice trolling. :D

> **thek3nger said:**
> 
```
sudo su
```
 
I guess that would be to act as the existing user, but just with root permissions? Rather than switching to proper root by 'sudo su -"?

---

### Post by dcstar on 2012-08-04
> **ryanyeah said:**
> Nice trolling. :D


You have got to be joking. These forums are full of posts from people using the terminal who basically have no idea what they are doing and just copy instructions that they obviously have no understanding of - all because misguided people think that they are helping novice users by giving them terminal commands.

Use the GUI tools provided to safely achieve the results that a mistyped or inappropriate terminal command can potentially cause a problem if used - especially root level commands.

---

### Post by Cheesemill on 2012-08-04
> **thek3nger said:**
> You can also type once

```
sudo su
```if you don't want to type "sudo" for every command.

You shouldn't use 'sudo su', it doesn't handle switching environment variables properly.
If you want to get a root shell you should instead use:
```
sudo -i
```

---

### Post by Primefalcon on 2012-08-04
I am all for telling people the graphical way... But I am supporting of people learning the terminal as well since it is a very very powerful tool, far more powerful than any gui......

the command your looking for btw is

```
sudo apt-get update; sudo apt-get dist-upgrade
```

for reference you can learn more about commands by reading the documentation for example

man apt-get

will tell you all about the apt-get command and everything it ca do

---

### Post by gifford on 2012-08-04
Good advice dcstar!

---

