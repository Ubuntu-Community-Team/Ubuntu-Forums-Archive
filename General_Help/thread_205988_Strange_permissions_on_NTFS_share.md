---
title: "Strange permissions on NTFS share"
date: 2006-06-29
forum: General Help
---

### Post by ashrack on 2006-06-29
I am unable to access certain files on my NTFS drive thru dapper. These are some of the files:
```
 ls -la
total 128
dr-xr-xr-x 1 root tom 65536 2006-04-20 13:53 .
dr-xr-xr-x 1 root tom 65536 2006-05-01 15:00 ..
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e17.Night.Terrors.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e18.Identity.Crisis.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e19.The.Nth.Degree.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e20.Qpid.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e21.The.Drumhead.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e22.Half.a.Life.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e23.The.Host.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e24.The.Mind's.Eye.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e25.In.Theory.avi
?--------- ? ?    ?       ?                ? Star.Trek.TNG.s04e26.Redemption.Part.I.avi

```
and when trying to copy them to an XFS share I get this:
```
cp: cannot stat `Star Trek - TNG4/Star.Trek.TNG.s04e26.Redemption.Part.I.avi': Input/output error

```

The line in FSTAB responsible for mounting the drive:
```
/dev/hda6       /media/d        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

Needless to say that if I boot back into Win2k3 than these files are accesible.

---

