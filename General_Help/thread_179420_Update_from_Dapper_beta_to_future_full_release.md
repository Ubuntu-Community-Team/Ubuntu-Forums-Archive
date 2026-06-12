---
title: "Update from Dapper beta to future full release"
date: 2006-05-19
forum: General Help
---

### Post by iMac on 2006-05-19
Would it be easy to upgrade to the final release of Dapper Drake from the beta? Or would it be better to do a clean install of Dapper once it is released?

                                                                                    Mike

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=iMac]Would it be easy to upgrade to the final release of Dapper Drake from the beta? Or would it be better to do a clean install of Dapper once it is released?

                                                                                    Mike[/QUOTE]
You will just need to run "sudo apt-get update && upgrade" (that is the same as sudo apt-get update and sudo apt-get upgrade but in one command) you do not need to do a clean install or a long dist-upgrade. You will just upgrade a few packages. You will keep all your settings and programs.

---

### Post by iMac on 2006-05-19
ok thanks very much!

---

### Post by dirwood on 2006-05-19
same thing to upgrade from breezy?

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=dirwood]same thing to upgrade from breezy?[/QUOTE]
No, to update breezy you will need to grab a Dapper sources.list and then run:

> sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by dirwood on 2006-05-19
what would be better: doing the dist upgrade, or a fresh install?
I've got a recent install, so not too much stuff to backup.

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=dirwood]what would be better: doing the dist upgrade, or a fresh install?
I've got a recent install, so not too much stuff to backup.[/QUOTE]
I would recommend a clean install. Dist-upgrades can go horribly wrong. Do a clean install if possible. If you choose to dist-upgrade:

1. Backup important data.
2. Before dist-upgrading, log out of X.
3. Make sure ubuntu-desktop is installed.

---

