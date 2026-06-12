---
title: "Running an .sh file"
date: 2009-08-09
forum: General Help
---

### Post by Lars Emil Gutt on 2009-08-09
Im trying to install a driver for an internet harddisk.
With it was a linux driver, lea-linux-1.0.0.sh, but i when i write: 
$ sh lea-linux-1.0.0.sh
in the console it just says: 
LEA v1.0 - Extracting archive... please wait

LEA v1.0 has failed to extract
Try to use "sudo" lea-linux-1.0.0.sh

and when i use sudo it does the same thing again.

---

### Post by Barafu Albino Cheetah on 2009-08-09
Try calling script with -? or --help.  It may just not find required files.

---

### Post by Narada on 2009-08-09
You could also run ```
sh --verbose lea-linux-1.0.0.sh
``` and paste the output.

---

### Post by Lars Emil Gutt on 2009-08-09
When i run:

sh --verbose lea-linux-1.0.0.sh

it says:

sh: Illegal option --

---

### Post by wojox on 2009-08-09
Try:
```
sudo ./lea-linux-1.0.0.sh
```

---

### Post by Narada on 2009-08-09
> **Lars Emil Gutt said:**
> When i run:

sh --verbose lea-linux-1.0.0.sh

it says:

sh: Illegal option --

Try a -v instead?

---

### Post by Lars Emil Gutt on 2009-08-09
Like this:

 sh -v lea-linux-1.0.0.sh

If i do that it says:

#!/bin/sh
PROJECT=LEA
VERSION=1.0
echo ""

echo "$PROJECT v$VERSION - Extracting archive... please wait"
LEA v1.0 - Extracting archive... please wait
echo ""

size="`awk '/^__END__/ { print NR+1; exit 0; }' $0`"

usage()
{
	echo "Try to use \"sudo\" $0"
}

tail -n +$size $0 | tar xz -C / > /dev/null 2>&1
if [ $? -eq 0 ]; then
	echo "Extracted Lacie_Ethernet_Agent to /"
	ldd /usr/local/bin/LaCie_Ethernet_Agent | grep "not found"
	if [ $? -eq 0 ]; then
		echo "Clean..."
	fi
else
	echo "$PROJECT v$VERSION has failed to extract"
	usage
fi
LEA v1.0 has failed to extract
Try to use "sudo" lea-linux-1.0.0.sh

exit 0

---

### Post by Bonster on 2009-08-09
sudo sh drag-your-sh-file-into-the-terminal

then run it

---

### Post by Lars Emil Gutt on 2009-08-10
Dosent work. It says the same thing about failing to extract.

---

### Post by Lars Emil Gutt on 2009-08-19
Working now

---

