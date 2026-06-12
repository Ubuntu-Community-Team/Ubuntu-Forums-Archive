---
title: "BASH assign variables with spaces"
date: 2010-06-06
forum: General Help
---

### Post by propagation_of_sound on 2010-06-06
I have this BASH script to queue Handbrake encodes for my iPod (I'm new at BASH):
```
#!/bin/bash
i=0
echo "Enter baseName:"
read baseName
echo "Enter title num, -1 to finish:"
read titleNum
until [ "$titleNum" -eq -1 ]; do
	i=$i+1
	echo "Enter filename:"
	read currentFile
	{fileName[$i]}="$currentFile"
	{nums[$i]}="$titleNum"
	echo "Enter title num, -1 to finish:"
	read titleNum
done
numOfLoops=$i+1
i=1
while [[ $i -lt $numOfLoops ]]; do
	HandBrakeCLI -i /dev/sr0 -I -b 700 -x "level=30:bframes=0:cabac=0:ref=1:vbv-maxrate=768:vbv-bufsize=2000:analyse=all:me=umh:no-fast-pskip=1:subme=6:8x8dct=0" -2 -E faac -6 stereo -R 48 -Y 240 -X 320 -e x264 -t ${nums[$i]} -o $baseName${fileName[$i]}
	i=$i+1
done
```
But if I use this input:
```
josh@josh-desktop:~/scripts$ ./HandBrakeScript.sh
Enter baseName:
/media/Media/Media/Video/BSG/Series 4/
Enter title num, -1 to finish:
2 
Enter filename:
02 test.m4v
./HandBrakeScript.sh: line 11: {fileName[0+1]}=02 test.m4v: command not found
./HandBrakeScript.sh: line 12: {nums[0+1]}=2: command not found
Enter title num, -1 to finish:
```

Why is it thinking my variable assignation is a command?

Thanks in advance

-j

---

### Post by pedro_orange on 2010-06-06
I would imagine you would need to put quotes around the variable name? I'm not a BASH expert by any means though

---

### Post by geirha on 2010-06-06
[http://mywiki.wooledge.org/BashGuide/Arrays](http://mywiki.wooledge.org/BashGuide/Arrays)

```

...
read -p "Enter filename: " -e "fileName[i++]"
...
for ((i=0; i < ${#fileName[@]}; i++)); do
  some_command ... "${fileName[i]}"
done
```

The quotes are NOT optional.

Oh and i=$i+1 will not increment i. i=$((i+1)) or ((i++)) will

---

### Post by propagation_of_sound on 2010-06-06
FixedItMyself :)

I just had to remove the curly brackets from around the array variable names. Now it works a charm. 

Wish Handbrake would get their GUI sorted...

---

### Post by lavinog on 2010-06-06
> **propagation_of_sound said:**
> 
```
josh@josh-desktop:~/scripts$ ./HandBrakeScript.sh
Enter baseName:
/media/Media/Media/Video/BSG/Series 4/
Enter title num, -1 to finish:
2 
Enter filename:
02 test.m4v
./HandBrakeScript.sh: line 11: {fileName[0+1]}=02 test.m4v: command not found
./HandBrakeScript.sh: line 12: {nums[0+1]}=2: command not found
Enter title num, -1 to finish:
```

Why is it thinking my variable assignation is a command?

Thanks in advance

-j

It looks like you need to remove the curly brackets:
```


	fileName[$i]="$currentFile"
	nums[$i]="$titleNum"

```

---

