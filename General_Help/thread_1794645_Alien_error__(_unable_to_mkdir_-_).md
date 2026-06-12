---
title: "Alien error  ( unable to mkdir -: )"
date: 2011-07-01
forum: General Help
---

### Post by chimericidol on 2011-07-01
Hey guys I have a problem with alien on Ubuntu 11.04 64bit. When I try to convert Maya 2012 packeges I get this error in all of them.

Running this command:
```
sudo alien -cv adlmapps4-4.0.35-0.x86_64.rpm
```


I get this output:
```
	LANG=C rpm -qp --queryformat %{NAME} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{VERSION} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{ARCH} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{PREUN} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{LICENSE} adlmapps4.rpm
	LANG=C rpm -qp --queryformat %{PREIN} adlmapps4.rpm
	LANG=C rpm -qcp adlmapps4.rpm
	rpm -qpi adlmapps4.rpm
	LANG=C rpm -qpl adlmapps4.rpm
	mkdir -
mkdir: cannot create directory `-': File exists
unable to mkdir -:  at /usr/share/perl5/Alien/Package.pm line 257.

```

Any ideas? Is it alien bug, the rpm fault or maybe I am doing something wrong?

---

