---
title: "aptitude and dpkg-query reporting different maintainers for the same package"
date: 2011-04-19
forum: General Help
---

### Post by astrostl on 2011-04-19
```
dpkg-query -W -f='${Package}\t${Maintainer}\n' python2.7
```yields

```
python2.7       my@email.address

```This is expected, but

```
aptitude search '?installed' -F "%p %m"|grep ^python2.7

```yields

```
python2.7                             Ubuntu Core Developers <ubuntu-devel-discu
``` and that is not expected.

Can anyone explain the discrepancy?  ${Maintainer} is described in the dpkg-query man page, and %m at [http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s04s01.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s04s01.html")

---

