---
title: "rscsi =no way to make it work"
date: 2012-03-21
forum: General Help
---

### Post by camelseller on 2012-03-21
Hello forum,
I spended more tha two week trying to make rscsi work!
I need it because I want to use my server's dvd-burner from some of my clients in my lan. Does anyone know how to make it work?

This is my /etc/default/rscsi
```
DEBUG=/tmp/RSCSI
USER=*
ACCESS=*	localhost	1	1	0	0
```

This is the way I use my dvd-burner localhost-mode

```
# wodim dev=/dev/sr0 -scanbus
scsibus1:
	1,0,0	100) 'HL-DT-ST' 'DVDRAM GMA-4080N' '0L33' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
```
but when I try ```
wodim dev=REMOTE:rscsi@localhost -scanbus
rscsi@localhost's password: 
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```
or
```
wodim dev=REMOTE:rscsi@localhost:1,0,0 -scanbus
rscsi@localhost's password: 
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

Please Help!

---

### Post by camelseller on 2012-03-24
up

---

### Post by camelseller on 2012-03-30
up

---

