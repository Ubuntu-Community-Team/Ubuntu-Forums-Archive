---
title: "build-essential and php-apd"
date: 2006-02-20
forum: General Help
---

### Post by SleightfulMind on 2006-02-20
I have spent the last several hours trying to install the apd extension for php. I come here out of frustration, hoping that someone can help me figure this out. Since I am running php4, first I downloaded the latest release of apd for php4. I did this by running "pear download apd-0.9.1.tgz". Next I ran "pear install apd-0.9.1.tgz" and I get the following output:

```
18 source files, building
running: phpize
Configuring for:
PHP Api Version:         20020918
Zend Module Api No:      20020429
Zend Extension Api No:   20021010
building in /var/tmp/pear-build-root/apd-0.9.1
running: /tmp/tmpasGKuR/apd-0.9.1/configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
`/tmp/tmpasGKuR/apd-0.9.1/configure' failed
```

So, I did some research and found that I should run "apt-get install build-essential". When I do so, I get the following output:

```
Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
```

What can I do to resolve this issue?

Thanks!

---

### Post by SleightfulMind on 2006-02-21
No one has any ideas on this?

---

### Post by munk on 2006-03-05
There's a package for APD called php4-apd. At least in Breezy. Might be worth checking out instead of using the tarball.

- Andy

---

