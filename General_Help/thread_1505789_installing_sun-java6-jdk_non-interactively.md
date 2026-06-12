---
title: "installing sun-java6-jdk non-interactively"
date: 2010-06-09
forum: General Help
---

### Post by meonkeys on 2010-06-09
Anyone know an easy way to non-interactively install the package "sun-java6-jdk" on 10.04? It's in the lucid "partner" repository.

Here's what I'd like to automate:

```
sudo sh -c 'cat >> /etc/apt/sources.list' <<EndOfPartner
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
EndOfPartner
sudo apt-get update
sudo apt-get -y install sun-java6-jdk
```

The script, when run headless, hangs on the last line since that package, during install (or configure or something), pops up an interactive dialog forcing a user to hit TAB, then ENTER, then ENTER again.

---

### Post by dcstar on 2010-06-10
> **meonkeys said:**
> Anyone know an easy way to non-interactively install the package "sun-java6-jdk" on 10.04? It's in the lucid "partner" repository.

Here's what I'd like to automate:

```
sudo sh -c 'cat >> /etc/apt/sources.list' <<EndOfPartner
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
EndOfPartner
sudo apt-get update
sudo apt-get -y install sun-java6-jdk
```

The script, when run headless, hangs on the last line since that package, during install (or configure or something), pops up an interactive dialog forcing a user to hit TAB, then ENTER, then ENTER again.

This might work for a download .bin, but I don't know about .deb packages:

[http://www.unix.com/302401897-post7.html](http://www.unix.com/302401897-post7.html)

---

### Post by surfer on 2010-06-29
did you solve the problem? the closest thing to a soulution i found is 
[here]("http://www.coreyhulen.org/2010/04/unattended-java-install-on-linux/"). but that does not work either...

---

### Post by surfer on 2010-06-29
oh, actually this does work!

run this
```
/bin/echo "sun-java6-plugin shared/accepted-sun-dlj-v1-1 true" | /usr/bin/debconf-set-selections
```
before you install.

i use puppet to do this; the corresponding puppet file looks like
```

#!/usr/bin/puppet --verbose

class sun_java6 {



  exec
    { "/bin/echo \"sun-java6-plugin shared/accepted-sun-dlj-v1-1 boolean true\" | /usr/bin/debconf-set-selections":
        alias     =>  "debconf-set-selections-sun-java6-plugin";

      "/bin/echo \"sun-java6-bin shared/accepted-sun-dlj-v1-1 boolean true\" | /usr/bin/debconf-set-selections":
        alias     =>  "debconf-set-selections-sun-java6-bin";

      "/bin/echo \"sun-java6-jre shared/accepted-sun-dlj-v1-1 boolean true\" | /usr/bin/debconf-set-selections":
        alias     =>  "debconf-set-selections-sun-java6-jre";

    } 


  package 
  { 
    "sun-java6-plugin":
      require   => [ Exec["debconf-set-selections-sun-java6-plugin"],
                     Package[sun-java6-bin],
                     Package[sun-java6-jre] ],
      ensure => installed;

    "sun-java6-bin":
      require   => Exec["debconf-set-selections-sun-java6-bin"],
      ensure => installed;

    "sun-java6-jre":
      require   => Exec["debconf-set-selections-sun-java6-jre"],
      ensure => installed;
  }

}

#####################################

include sun_java6

```

---

