---
title: "Stop apt updating specific packages?"
date: 2010-01-07
forum: General Help
---

### Post by llawwehttam on 2010-01-07
I am one of the people having problems with the newest mesa update and so have downgraded libgl1-mesa-dri and libgl1-mesa-dri to version 7.4 to fix the problem.

I have stopped synaptic from updating them but if i run sudo apt-get upgrade than they update again. Is there a way of stopping apt from updating specific packages?

---

### Post by bodhi.zazen on 2010-01-07
As root (sudo -i to become root):

```
echo "<package_name> hold" | dpkg --set-selections
```

See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

See Section 7.12 :

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

Or you can also put a package on hold in synaptic.

---

### Post by llawwehttam on 2010-01-07
I already held them back in synaptic but it still updated in apt-get. Your command fixed that though so thanks for that.

Oh and btw wouldn't ```
sudo su -c  'command to be run as root'
``` be better than ```
sudo -i
``` as it wouldn't leave the user logged in as root. (safer for noobs)

I have used linux for a long time but mostly used distros that used yum so I'm unused to apt. Only started using ubuntu a year ago.

---

### Post by bodhi.zazen on 2010-01-07
You can skin the cat in more then one way =)

I do not know about sudo su -c complex_command_with_pipes

with sudo, with complex commands, you need to so:

```
sudo bash -c "echo 'package_name hold' | dpkg --set-selections"
```

---

### Post by llawwehttam on 2010-01-07
> **bodhi.zazen said:**
> You can skin the cat in more then one way =)

I do not know about sudo su -c complex_command_with_pipes

with sudo, with complex commands, you need to so:

```
sudo bash -c "echo 'package_name hold' | dpkg --set-selections"
```


OK thanks for that. This is what I love about linux. It doesn't matter what distro you use but you still learn something new every day.

---

### Post by bodhi.zazen on 2010-01-07
> **llawwehttam said:**
> OK thanks for that. This is what I love about linux. It doesn't matter what distro you use but you still learn something new every day.

Indeed, and FYI, you can indeed sudo su -c 'complex command | with pipes'

I ***had*** to check, :lolflag:

---

### Post by llawwehttam on 2010-01-07
> **bodhi.zazen said:**
> Indeed, and FYI, you can indeed sudo su -c 'complex command | with pipes'

I ***had*** to check, :lolflag:
Thanks for that update. That gave me a bit of a confidence boost. :lolflag:

---

