---
title: "Script for Pack in separated volumes and send per Email your folders?"
date: 2010-05-22
forum: General Help
---

### Post by frenchn00b on 2010-05-22
Hello,

Few folders to send per email of 50-100 MB, is there some homemade scripts for that doing the job in a single command line?

ex.
```
packnsend   10mb /folder me@gmail.com
```

it woudl zip to 10mb volumes the folder and send per mutt the volumes ...

---

### Post by frenchn00b on 2010-07-05
cat /usr/bin/packnsend 
```
#!/bin/sh

echo "packnsend coded by Frenchn00b"
if [ "$1" = "" ] ; then
	echo "format: packnsend size email_address packingname  source1 [ source2 source3 ...] "
	echo "Source can be a folder"

	else 

	echo "Lets start the work"
	FO="$(mktemp -d)"
	echo "$FO created"
	mkdir $FO
	echo Packing
	rar a -v$1  "$FO/$3"   "$4" 
	echo Sending
	cd $FO
	ls -ltrah
	for each in * ; do
		echo "$each sending..."
		echo "$each $(date)" | mutt -a "$each" -- "$2"
		echo "$each sent"
	done
	echo Done
fi


```



ENJOY DUDES !

---

