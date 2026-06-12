---
title: "perl scripting write problem"
date: 2011-08-04
forum: General Help
---

### Post by irakla7777777 on 2011-08-04
hello .

i have problem with this script. 
script does not work when z.txt is empty

open FILE, "< /home/user/Desktop/z.txt" or die $!;
while(<FILE>){
chomp;
$out=$_;
$in="somename";
if($out ne $in){
print "file content not equal somename \n";
}
}

i could not find anything in google that solves my problem.

sorry for bad  english :)

---

### Post by Dave_L on 2011-08-04
Explain "does not work".  What do you expect the script to do when the file is empty?

By the way, it's helpful to use CODE tags when posting code, like this:

```
#!/bin/perl

open FILE, "< /tmp/z.txt" or die $!;
while(<FILE>) {
	chomp;
	$out=$_;
	$in="somename";
	if($out ne $in) {
		print "file content not equal somename \n";
	}
}
```

---

### Post by irakla7777777 on 2011-08-04
i want to start bash file when file is empty .

how to get it work ?

---

