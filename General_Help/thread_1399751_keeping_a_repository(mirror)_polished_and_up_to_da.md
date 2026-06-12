---
title: "keeping a repository(mirror) polished and up to date"
date: 2010-02-06
forum: General Help
---

### Post by dakiluxa on 2010-02-06
Hi, i installed an Ubuntu repository for Argentina in one of the servers where i work.

The thing is, i really need them to be up to date and working as good as possible.

I have managed so far to keep them relatively up to date by running this on my crontab:

# m h  dom mon dow   command
0 */3 * * * /var/ubuntu/scriptrepo-cd.sh && date >> /var/ubuntu/debugrepo.txt
0 */3 * * * /var/ubuntu/scriptrepo.sh && date >> /var/ubuntu/debugrepo-cd.txt

and on the scripts: 

RSYNCSOURCE=rsync://mirror.anl.gov/ubuntu-iso/CDs/
BASEDIR=/var/ubuntu/archive/releases

rsync --recursive --times --links --hard-links \
      --stats \
      --exclude "Packages*" --exclude "Sources*" \
      --exclude "Release*" \
      ${RSYNCSOURCE} ${BASEDIR}

rsync --recursive --times --links --hard-links \
      --stats --delete --delete-after \
      --exclude "project/trace/${HOSTNAME}" \
      ${RSYNCSOURCE} ${BASEDIR}
/var/ubuntu/archive

the other one uses archive.ubuntu.com



All help is appreciated. We really want to provide the best service possible and we look forward to become the official mirror for Argentina.


PS: we also want to host source code, different architectures and everything that is ubuntu

---

